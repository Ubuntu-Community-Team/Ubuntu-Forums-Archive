---
title: "[SOLVED] Poker 2D Opens, then Closes"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by coldstatue on 2007-07-25
Any ideas of where I need to start troubleshooting this? i haven't a clue.

Thank you

---

### Post by charlieg on 2007-07-25
Heh... *opens then closes*... I'm so ingrained in open source I thought assumed this would be regarding development!

Ok, first thing to do would be to run it from a terminal.  Open up a terminal (Applications->Accessories->Terminal) and run it from there.  The command is probably something like 'poker2d' - you can type 'pok' then press tab twice to see the possibilities.  (Note if tab autocompletes it to poker2d then that is the only matching command.)

Anyway, the purpose of running it in a terminal is that it should give you some output on the likely cause of the closing.

---

### Post by Ozor Mox on 2007-07-25
The same thing happens to me. The error in the terminal is...

```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/pokerclient2d/poker2d.py", line 149, in run
    reactor.run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 206, in callback
    log.callWithLogger(source, self._doReadOrWrite, source, condition)
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 48, in callWithLogger
    return callWithContext({"system": lp}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/log.py", line 33, in callWithContext
    return context.call({ILogContext: newCtx}, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 59, in callWithContext
    return self.currentContext().callWithContext(ctx, func, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/python/context.py", line 37, in callWithContext
    return func(*args,**kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 203, in _doReadOrWrite
    self._disconnectSelectable(source, why, didRead == source.doRead)
  File "/usr/lib/python2.5/site-packages/twisted/internet/posixbase.py", line 255, in _disconnectSelectable
    selectable.connectionLost(f)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 576, in connectionLost
    Connection.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/twisted/internet/tcp.py", line 416, in connectionLost
    protocol.connectionLost(reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1215, in connectionLost
    UGAMEClientProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 100, in connectionLost
    UGAMEProtocol.connectionLost(self, reason)
  File "/usr/lib/python2.5/site-packages/pokernetwork/protocol.py", line 93, in connectionLost
    self.protocolInvalid("different", PROTOCOL_MAJOR + "." + PROTOCOL_MINOR)
  File "/usr/lib/python2.5/site-packages/pokernetwork/pokerclient.py", line 1411, in protocolInvalid
    UGAMEClientProtocol.protocolInvalid(self, server, client)
  File "/usr/lib/python2.5/site-packages/pokernetwork/client.py", line 93, in protocolInvalid
    self.factory.established_deferred.errback((self, server, client),)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 261, in errback
    self._startRunCallbacks(fail)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 290, in _startRunCallbacks
    raise AlreadyCalledError
twisted.internet.defer.AlreadyCalledError: 

```

I read elsewhere that it's a broken package. I haven't gone any further with it, I just installed PokerTH instead.

---

### Post by coldstatue on 2007-07-28
installing POK3D and all dependencies fixes this problem,and poker2d will work

---

