# README

## Distributed Key-Value Database

### High Level Approach

For this project of creating a Distributed Key-Value Database following the RAFT protocol, we first read the Raft paper in order to understand what needs to be implemented. We then started by first adding basic support for responding to client get() and put() requests, where the put request values were immediately inserted into the database. Then, we worked on implementing the Raft election protocol. This involved adding states to the replica - "leader", "follower", and "candidate" - and having the replica behave in a certain way based on its state. Once the election protocol worked properly and leaders were able to be replicated, we added in support for sending empty AppendEntries RPCs to act as keepalive messages. At this point, we were able to pass the necessary tests for the milestone. 

Next, we worked on log replication. This involved adding entries to the log when the leader received a put request, replicating these entries to the other replicas, checking that a replica's logs matched the leader's, and committing the entries once the entries have been replicated to majority of the replicas. Once all of these steps were implemented, we moved onto adding the additional safety support. 

---

### Challenges

The most significant challenge we encountered was following the Raft protocol in order to implement log replication, which took up the majority of our time and effort. Some of the parts we had difficulty with were what types of messages should be sent from a leader to a follower and vice versa, what to check for when receiving an AppendEntries RPC to ensure that the replica's logs matched the leader's, and how to know when to commit additional entries. We were able to successfully implement log replication after carefully reading the Raft paper and going to office hours. 

---

### Testing

We tested the code by running the given tests. We first checked that the program passed the simple and crash tests before trying to run the other tests. The crash tests helped us the most with figuring out if we implemented the election protocol properly. Additionally, we used print statements to check if we were sending the correct values in the messages. 
