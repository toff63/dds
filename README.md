# Distributed Datastructures

Code for a talk about DDS and Message Patterns

**WARNING:** This is a bunch of code put together as a tool for demonstration purposes. Some parts are weird in order to illustrate concepts (I wouldn't really use pub/sub for ring coordination), other parts lack any semblance of safety features (using method names as service commands is extraordinarily unsafe), while still other parts aren't even implemented correctly.

TL;DR: This is a teaching tool. *Caveat emptor*.

## Videos

1. [Full Test](http://www.youtube.com/watch?v=rutUWd2Imts)

## TLDR

1. Distributed Hash Table (Consistent hash distributes data evenly and have minimum disruption when node is added/removed)
    1. Hash value range is dynamic and depends on the number of node: hash % nodes. When you add a node you cannot find 90% of the data
    2. Ring implementation (Consistent Hash). Keep track of which key range belong to each node. However, the range is attributed in an arbitrary manner. In the example, he uses the hash of the node name to determine the upper bound of the range of key it is responsible for.
    3. PartitionedConsistentHash The number of partition is fixed and each one is assigned to a node. Downside, you are limited in the number of node (1 per partition in the worst case)
2. Request/Reply: Forward request to node responsible for the data instead of saying we don t have it.
3. Publish/Subscribe: Use to let other nodes when a node arrive. A leader coordinate the cluster changes
4. Replication to handle node dying. Problem: conflict
5. Vector Clocks: Still needs to resolve conflicts
6. Use CRDTs to have conflict free datastructure
7. Merkel tree
8. Map/Reduce
