---
title: "core dumps in Breezy disabled?"
date: 2006-02-21
forum: Desktop Environments
---

### Post by hectorC on 2006-02-21
Hello,

I've been trying to use the latest version of Rosegarden (MIDI sequencer) and after compiling successfully I found that it is crashing at startup. After this, I recompiled the program configuring it with the debug option in order to get a core dump to show to the developers. I found that even though it is rebuilt with debug and I set ulimit to unlimited, I'm not getting any core file after the crash. Someone at the Rosegarden mailing list told me that maybe core dumps are disabled in Breezy. Is this true? If that's the case then, is it possible to enable it? I'm not an experienced programmer so I don't really know what other options I have.

Thank you,


Hector.

---

### Post by art on 2006-02-21
Yes they are disabled for security reasons. To enable core dumps for the current session 
ulimit -c 1024
HTH

---

### Post by hectorC on 2006-02-21
[QUOTE=art]Yes they are disabled for security reasons. To enable core dumps for the current session 
ulimit -c 1024
HTH[/QUOTE]

Thanks for your reply. In fact I tried

ulimit -c unlimited 

and I couldn't get any core dump file. If it is not in the Ubuntu side maybe is Rosegarden's.

---

### Post by art on 2006-02-21
Well I don't know why it wouldn't work. Maybe it is program related. Also it seems at some point there were some problems dumping multithreaded applications, maybe this one is one of those, I don't know...

---

### Post by art on 2006-02-21
I just wrote a simple C++ program which will generate a core dump in the current directory, just to test that there is nothing else wrong.
TO test 

mv generatelist.cxx.txt generatelist.cxx
mv fdblist.txt fdblist
g++ -o GenList generatelist.cxx
./GenList

This should cause the system to create a core dump. If it does then it is the Rosegarden related thing probably

---

