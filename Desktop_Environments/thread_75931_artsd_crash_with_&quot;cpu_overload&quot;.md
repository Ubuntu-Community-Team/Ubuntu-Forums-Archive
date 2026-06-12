---
title: "artsd crash with &quot;cpu overload&quot;"
date: 2005-10-14
forum: Desktop Environments
---

### Post by rosslaird on 2005-10-14
It looks kind of ominous, that "cpu overlaod" message. It appears along with the artsd crash message that crops us every couple of days. I leave my system on all the time, and sometimes I discover the message when I first visit the computer in the morning. Interestingly, it has never happened during the daytime. Only when the computer is idle.
Sometimes I get the "cpu overload" message, sometimes just a message saying that artsd has crashed. My sound works fine, and the kde audio module is set up to use alsa, which seems to be working. Also, arts sometimes seems to restart itself. If I run artsd from a console after a crash, I get this:

can't register Arts::MidiManager
There are already artsd objects registered, looking if they are active...

Error: Can't add object reference (probably artsd is already running).
       If you are sure it is not already running, remove the relevant files:

       /tmp/ksocket-ross/Arts_SoundServerV2
       /tmp/ksocket-ross/Arts_SoundServer
       /tmp/ksocket-ross/Arts_SimpleSoundServer
       /tmp/ksocket-ross/Arts_PlayObjectFactory
       /tmp/ksocket-ross/Arts_AudioManager


Suggestions are welcome.

Ross

---

### Post by daller on 2005-12-05
Did you solve this?

I'd give KDE3.5 a go, if I were you!

---

### Post by rosslaird on 2005-12-05
Yup, 3.5 fixed the problem.

---

