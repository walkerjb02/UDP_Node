# I really enjoyed working on this component of the Accounting Project. This component is the standalone version of the program which will link nodes in a network together, creating a web of connections and as a result, a decentralized ledger which is a big part of blockchain technology. I decided to use UDP over TCP as a connection type because UDP, while being less reliable than TCP, is faster, which is important when one considers how time consuming PoW can be, and does not have any flow / congestion control protocols. Due to that unreliablility that comes from UDP, messages are sent twice to ensure the sender recieves messages without having to further complicate the program with something like an acknowledgement system. Furthermore, the network allows for systems to enter and exit freely, periodically establishing new connections with system entrants. 
# 
# What's more interesting is how the program works. Because they're on the same network, only port numbers matter in this situation. But, hosts do not/cannot know intutively which port numbers to send information to. So, upon start, hosts broadcast their port number to all ports (except its own) on a network while, simultaneously, checking for incoming port numbers. If the host recieves a port number, it appends the port to a list which will be utilized once the host wants to send a message. Once 30 seconds have passed, the process splits off into multiple threads, allowing for the user to send messages while also continuing to check for incoming messages, while also periodically broadcasting it's own port number for any new systems which might enter the network. When a message is recieved, the receiving host will apply several filters to the message in order to determine whether it should be added to the port list or displayed on screen. If a message is to be sent, the sender refers to its aforementioned list of saved port numbers and beams the message to all port numbers on that list, creating that web which could be used for something like a distributed ledger.
#
# Another really neat thing about this component is, because each host is both the client and the server in the model and the protocols mirror each other, each host only needs this UDP_Node program to be connected to other nodes. One final note is this program is intented to be ran with more than two hosts and messages cannot be sent until the phrase "message?" appears on screen.
