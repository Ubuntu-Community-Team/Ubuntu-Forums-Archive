---
title: "Orca screen reader espeechfactory server not found"
date: 2013-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lineofaborder on 2013-02-10
I am trying to run orca screen reader on ubuntu 11.10.

If I execute it enabling universal access I get no speech, and if I execute orca via the command line I get the following error in terminal:

```


me@machine:~$ orca
kill: 42: Operation not permitted


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 133, in init
    _initSpeechServer(moduleName, None)
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 117, in _initSpeechServer
    raise Exception("No speech server for factory: %s" % moduleName)
Exception: No speech server for factory: speechdispatcherfactory


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 151, in getSpeechServer
    return SpeechServer(info[0])
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 178, in __init__
    e = __import__(_getcodes(engine),
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 442, in _getcodes
    raise Exception("No code table for %s" % engine)
Exception: No code table for Default Synthesizer


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 151, in getSpeechServer
    return SpeechServer(info[0])
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 196, in __init__
    stdin=PIPE, stdout=PIPE, stderr=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 133, in init
    _initSpeechServer(moduleName, None)
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 117, in _initSpeechServer
    raise Exception("No speech server for factory: %s" % moduleName)
Exception: No speech server for factory: espeechfactory


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 133, in init
    _initSpeechServer(moduleName, None)
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 117, in _initSpeechServer
    raise Exception("No speech server for factory: %s" % moduleName)
Exception: No speech server for factory: speechdispatcherfactory


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 151, in getSpeechServer
    return SpeechServer(info[0])
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 178, in __init__
    e = __import__(_getcodes(engine),
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 442, in _getcodes
    raise Exception("No code table for %s" % engine)
Exception: No code table for Default Synthesizer


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 151, in getSpeechServer
    return SpeechServer(info[0])
  File "/usr/lib/python2.7/dist-packages/orca/espeechfactory.py", line 196, in __init__
    stdin=PIPE, stdout=PIPE, stderr=PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 133, in init
    _initSpeechServer(moduleName, None)
  File "/usr/lib/python2.7/dist-packages/orca/speech.py", line 117, in _initSpeechServer
    raise Exception("No speech server for factory: %s" % moduleName)
Exception: No speech server for factory: espeechfactory

Speech not available.



```It's a long list of error suggesting speech servers are not available for the user.

If I execute via

```
sudo orca
```It runs but it reads only orca gnome interface (preferences, etc),
I suppose because other parts of the system are run without sudo command, If for instance instance I try to read a sudoed gedit text it works, so I suppose there are wrong settings for the normal user.

Any suggestions?

---

### Post by street4 on 2013-03-30
I've the same problem: no speech

Any suggestion?

---

