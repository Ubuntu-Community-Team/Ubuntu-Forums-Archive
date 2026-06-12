---
title: "Vmware player - requires sudo to run"
date: 2005-12-13
forum: Desktop Environments
---

### Post by coldrick on 2005-12-13
Just downloaded and installed vmware's "player" app.

All works OK, except that if I just run /usr/bin/vmplayer, I get:

/usr/bin/vmplayer: line 177: /usr/lib/vmware/lib/wrapper-gtk24.sh: Permission denied
/usr/bin/vmplayer: line 177: exec: /usr/lib/vmware/lib/wrapper-gtk24.sh: cannot execute: Permission denied


If I instead sudo vmplayer, it all works.

Anyone else have this problem?

Regards,
David

---

### Post by khc on 2005-12-14
vmware requires root priviledge to work, it's not a problem, it's the way it should work.
If it works for you without being root, then that's a problem :-)

---

### Post by coldrick on 2005-12-14
So it's not a bug. However, I reckon it's a design error. There's nothing I can think of that should require root access to *run* a virtual machine. Install vmplayer, yes, but not to run it.

Regards,
David

---

### Post by zoiks on 2005-12-15
[QUOTE=coldrick]So it's not a bug. However, I reckon it's a design error. There's nothing I can think of that should require root access to *run* a virtual machine. Install vmplayer, yes, but not to run it.

Regards,
David[/QUOTE]

1) I have run vmware on one machine and vmplayer on two machines, all under ubuntu.  I can tell you that all required root privs to install, but not to run.  Never once have I had to run vmXXXX with root privs.

2) I would tend to agree that if it *did* require root privs, it would be a flaw.

When I start vmware on the machine I'm on (note, not player), two instances of /usr/lib/vmware/lib/wrapper-gtk24.sh start up, but both are running with user privileges.

Perhaps something got messed up during your installation, or perhaps you just need to 

```
chmod a+x /usr/lib/vmware/lib/wrapper-gtk24.sh
```

or some other file.  On my system wrapper-gtk24.sh has 555 perms.

---

### Post by alamba on 2005-12-15
In my case too I don't need root privs to run vmplayer on my ubuntu 5.10 system. Don't have the system with me right now will post the messages I get later. Also, in my case the app installed a icon under system in the main applications drop down. When I launch vmplayer with that it does'nt ask me for the root password, it runs just fine. 

Did you alien the rpm and then installed the deb or did you (like in my case) build it from a tar?

Akshay

---

### Post by coldrick on 2005-12-15
I used the vmware-install.pl script provided in VMware-player-1.0.0-18587.tar.gz

As I recall, tho, the install failed first time, so maybe there's some junk hanging around.

Thanks for the suggestions, and confirmation that it shouldn't require root.

Regards,
David

---

### Post by khc on 2005-12-16
Okay, my experience with vmware is only confined to the "real" vmware, I haven't tried the vmplayer thing actually. I was lucky enough to get my free copy at my university :-)

---

### Post by alamba on 2005-12-16
I'm using both vmware and vmplayer. Found that vmplayer is actually pretty convienient if you don't want to "write" anything to the virtual machine per se. 

David: I'm surprised that you're getting this problem by installing with the tar file. I did the same too and while I did have to download the gcc files for my kernel and some header files the installation with through without a glitch. I'm sorry I still have'nt posted any messages my vmplayer throws up yet since I have'nt had a chance to pick up this thread from home.

Akshay

---

