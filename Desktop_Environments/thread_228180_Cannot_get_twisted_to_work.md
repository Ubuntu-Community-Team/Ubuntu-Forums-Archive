---
title: "Cannot get twisted to work???"
date: 2006-08-02
forum: Desktop Environments
---

### Post by billym on 2006-08-02
Any help would be greatly appreciated. This is what I did so far.

1) installed ubuntu.
2) installed twisted using apt-get install python2.4-twisted
3) created script twisted.py:

from twisted.internet.protocol import DatagramProtocol
from twisted.internet import reactor

class Echo(DatagramProtocol):
    
    def datagramReceived(self, data, (host, port)):
        print "received %r from %s:%d" % (data, host, port)
        self.transport.write(data, (host, port))

reactor.listenUDP(5768, Echo())
reactor.run()

4) when I run it I get:

ImportError: No module named internet.protocol

---

