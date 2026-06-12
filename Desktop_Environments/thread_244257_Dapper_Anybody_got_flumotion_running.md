---
title: "Dapper: Anybody got flumotion running ?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by scotty64 on 2006-08-26
I am trying to set up flumotion, but getting stuck with errors:
When I am starting flumotion-worker I get the following errordump:

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/twisted/internet/tcp.py", line 530, in doConnect
    self.startReading()
  File "/usr/lib/python2.4/site-packages/twisted/internet/abstract.py", line 239, in startReading
    self.reactor.addReader(self)
  File "/usr/lib/flumotion/python/flumotion/twisted/gstreactor.py", line 126, in addReader
    self.simulate()
  File "/usr/lib/flumotion/python/flumotion/twisted/gstreactor.py", line 263, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.4/site-packages/twisted/internet/base.py", line 518, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.4/site-packages/twisted/internet/defer.py", line 229, in callback
    self._startRunCallbacks(result)
  File "/usr/lib/python2.4/site-packages/twisted/internet/defer.py", line 280, in _startRunCallbacks
    raise AlreadyCalledError

flumotion-admin complains with an errormessage "failed: GError raised: no element "alsasrc" when I try to set up. And I cannot proceed with the wizard. When I try to run a videostreaming only system I have no probs setting up the video interface, but cannot start the components.
I am getting errormessages that the worker cannot login to the manager and times out.

Thanks for any kind of help!

---

### Post by scotty64 on 2006-08-26
I got it running now :-P :
Just downloaded the latest source from flumotion.net, installed the needed .dev packages, compiled it and - here we go.:D :D :D :D :-({|= 
I am getting the impression that the package that comes with Dapper is broken.:(

---

### Post by R%&amp;92GH&amp; on 2007-01-03
I also installed flumotion from the sources from the website (version 0.22), but I cannot make it work. If i start the GUI i get an error ("coult not connect to host"). I tried starting the manager and the worker as the documentation in the website says, but i got some errors on the flumotion-worker and i cannot start it:

```

marc@BOX:~$ sudo flumotion-worker -d 4 -u user -p password
DEBUG [ 7276]                                  setup             gen 03 16:54:48      registry paths: /usr/local/lib/flumotion/python (flumotion/common/setup.py:49)
DEBUG [ 7276]                                  setup             gen 03 16:54:48      registering package path: /usr/local/lib/flumotion/python (flumotion/common/setup.py:51)
DEBUG [ 7276]                                  packager          gen 03 16:54:48      installing custom importer (flumotion/common/package.py:81)
DEBUG [ 7276]                                  manager           gen 03 16:54:48      Running Flumotion version 0.2.2 (flumotion/worker/main.py:218)
DEBUG [ 7276]                                  manager           gen 03 16:54:48      Running against Twisted version 2.4.0 (flumotion/worker/main.py:221)
DEBUG [ 7276]                                  manager           gen 03 16:54:48      Running against GStreamer version 0.8 (flumotion/worker/main.py:223)
INFO  [ 7276]                                  worker            gen 03 16:54:48      Connecting to manager localhost:7531 using SSL (flumotion/worker/main.py:240)
DEBUG [ 7276]                                  worker            gen 03 16:54:48      Starting reactor (flumotion/worker/main.py:251)
DEBUG [ 7276]                                  workerbrain       gen 03 16:54:48      Installing SIGTERM handler (flumotion/worker/worker.py:658)
DEBUG [ 7276]                                  worker            gen 03 16:54:49      FPBClientFactory: logging in with keycard <KeycardUACPP in state REQUESTING> (flumotion/twisted/pb.py:79)
DEBUG [ 7276]                                  worker            gen 03 16:54:49      _cbSendKeycard(root=<twisted.spread.pb.RemoteReference instance at 0xb72e1a4c>, keycard=<KeycardUACPP in state REQUESTING>, client=<flumotion.worker.worker.WorkerMedium instance at 0xb737ebec>, interfaces=['flumotion.common.interfaces.IWorkerMedium', 'twisted.spread.pb.IPerspective'], count=0 (flumotion/twisted/pb.py:89)
WARN  [ 7276]                                  worker            gen 03 16:54:49      Shutting down worker because of error: (flumotion/worker/worker.py:115)
WARN  [ 7276]                                  worker            gen 03 16:54:49      Access denied. (flumotion/worker/worker.py:116)
ERROR: Access denied.
DEBUG [ 7276]                                  worker            gen 03 16:54:49      Reactor stopped (flumotion/worker/main.py:262)
INFO  [ 7276]                                  worker            gen 03 16:54:49      All jobs finished, stopping worker (flumotion/worker/main.py:288)
marc@BOX:~$ 

```

I run it as root, so I don't undestand that "access denied"... Any idea?

---

