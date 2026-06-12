---
title: "gdesklets grey screen bug!"
date: 2007-07-03
forum: Desktop Environments
---

### Post by aata on 2007-07-03
HELP!
my gdesklets refuses to start! 
what do i do? i believe its that same grey screen bug thats been reported in launchpad, but none of those solutions, along with several others i located, work! when i start gdesklets in the terminal, it takes its time saying ´connecting to daemon´, after which it gives me this error message:

```
Starting gdesklets-daemon...
Connecting to daemon [        ###  ]
==========================================================[07/03/07-11:09:11]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/local/bin/gdesklets: line 399 <module>
in /usr/local/bin/gdesklets: line 273 parse_command
in /usr/local/bin/gdesklets: line 177 __open_profile
in /usr/local/bin/gdesklets: line 158 __client_daemon
in /usr/local/lib/gdesklets/main/client.py: line 288 get_daemon
[EXC]/usr/local/lib/gdesklets/main/client.py

[---]  283                 daemon = connection
[---]  284                 if (daemon):
[---]  285                     break
[---]  286             except socket.error:
[---]  287                 pass
[ERR]> 288             time.sleep(0.1)
[---]  289 
[---]  290         print "\r" + " " * 40 + "\r",
[---]  291 
[---]  292         if (not daemon):
[---]  293             sys.exit(_("Cannot establish connection to daemon: timeout!\n"
[---]  294                         "The log file might help you solving the problem."))

```

i have tried replacing the /usr/lib/gdesklets file with the corresponding one from the synaptic deb package, but that doesnt work either. and compiling from the source code give pretty much the same error. i need help!

f=im running fiesty fawn 7.04.
if you need any more details, just reply to the post.
thanks in advance.
aata

---

### Post by aata on 2007-07-03
can anybody help? ive been waiting for ages!

---

### Post by sandi_ro on 2008-07-15
I am seeeing the same on ubuntu 8 seems to be because of a AF_UNIX socket.connect error this occurs in main/client.py. this is for the stock ubuntu package. 

trying to compile the 0.36 sources will give some error: 
checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.10.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.12.0) were not met:


hack hack , tried fedora 7 and all is ok ...

---

