Requirements: Linux OS, Python 2.7.12.

We only have a single "process" python script, not "./build" needed and no ./src/ directory
s
Master facing port defined by master. server facing ports are 20000 + pid and 25000 + pid, where pid is from 0 to n-1.

###################################################
Test cases:
Aside from the list of test cases provided, we added:

1. duplicateDecision.input
P0 crashes before sending decision. After timeout, master will ask P1 to decide. Then another two messages are sent to two processes.

2. crashDecisionResend.input
P0 crashes after sending decision to 2 and 3. When master asks 2 to propose again, 2 will inform others with its decided value while not running Paxos again.

3. crashDecisionSync.input
P0 crashes after sending decision to 2 and 3. When master asks 1 to propose again, 1 will send prepare to 2 and 3. Knowing their decision value, 2 and 3 will send "sync ack" to let 1 know that they have the decided value.

4. partialP1b.input


5. partialP2b.input


6. moreThanfFailure.input
