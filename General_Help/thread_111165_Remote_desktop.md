---
title: "Remote desktop"
date: 2006-01-01
forum: General Help
---

### Post by Jammy_Stuff on 2006-01-01
I was wondering if it is possible to install remote desktop on XUbuntu. If you can, how do I?

---

### Post by zoiks on 2006-01-01
You can use vnc, if that's what you're after.  Basically (after installing the required packages)

1) On machine 1, enter "vncserver :x" where x is a number like 1.  Do this as a regular user.
2) On machine 2, run "vncviewer" and tell it to connect to machine 1, using port "590x", where x is the same from #1.

You can man vncviewer and vncserver for details.

Also, X forwarding works, but is much slower.

---

### Post by Jammy_Stuff on 2006-01-01
I can't seem to find the required packages so I downloaded Tight VNC. How would I go about compiling the source?

---

### Post by zoiks on 2006-01-01
[QUOTE=Jammy_Stuff]I can't seem to find the required packages so I downloaded Tight VNC. How would I go about compiling the source?[/QUOTE]

I wouldn't compile it, just install from the repos.

vncserver and xvncviewer should do the trick (search using synaptic).  I'm a little confused myself about all the versions available in ubuntu.  You might or might not have to uncomment some of your sources in /etc/apt/sources.list to get them to show up.

---

### Post by Jammy_Stuff on 2006-01-01
My XUbuntu machine isn't connected to the internet though, just a LAN. So can someone please tell me how to compile it?

---

### Post by DaMasta on 2006-01-01
./configure
make
sudo make install

---

### Post by Jammy_Stuff on 2006-01-01
When I do the make command, it come up with an error

> WaitFor.c:410: error: 'fd_set' has no member named 'fds_bits'

What should I do now? Also once I get this working, is there any way I can set it up to automatically log in and run the vnc server on boot up?

---

### Post by DaMasta on 2006-01-01
Do you not have the cd? It'll be much easier that way.

---

### Post by Jammy_Stuff on 2006-01-01
Which CD? The Ubuntu one? I do but when I searched for VNC and intalled all of them, it still wouldn't work. What packages am I looking for?

---

### Post by DaMasta on 2006-01-01
You don't have an app call vncserver? Or xvncviewer?

---

### Post by Jammy_Stuff on 2006-01-01
I've got xvncviewer but not vncserver. What can I do?

---

### Post by zoiks on 2006-01-01
Seriously, don't bother compiling it, unless you either like pain or are itching to be a geek.  A machine running ubuntu should really have internet access for software installation/updates.  That said, browse

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

to find .deb packages for the stuff you need.  Then you can use "dpkg -i <.deb file>" to install them.

---

### Post by DaMasta on 2006-01-01
If you have the cd in your sources.list, apt-get install vncserver.

---

### Post by Jammy_Stuff on 2006-01-01
Tried that:

```
Reading package lists... Done
Building dwpwndency tree... Done
Package vncserver is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package vncserver has no installation candidate
```

---

### Post by DaMasta on 2006-01-01
Try tightvncserver then.

---

### Post by Jammy_Stuff on 2006-01-02
I downloaded vncserver to a USB disk and copied it to my home directory. I need to upgrade both my libgccl (to 1:4.0.2 or above) and my libstdc++6 (to 4.0.2-3 or above). Where can I get those files from?

---

### Post by DaMasta on 2006-01-02
Yeah but apt-get install tightvncserver will install what it needs. Did you try that?

---

### Post by zoiks on 2006-01-02
[QUOTE=Jammy_Stuff]I downloaded vncserver to a USB disk and copied it to my home directory. I need to upgrade both my libgccl (to 1:4.0.2 or above) and my libstdc++6 (to 4.0.2-3 or above). Where can I get those files from?[/QUOTE]

Browse the repositories with a web browser.  It's all in there.

---

### Post by Jammy_Stuff on 2006-01-02
I can't find the libs in the repositories.

---

### Post by zoiks on 2006-01-02
[QUOTE=Jammy_Stuff]I can't find the libs in the repositories.[/QUOTE]

You're right, I couldn't find them either.  I don't know where they are, they must be somewhere.  In any event, since you're planning on using these computers networked, would it kill you to connect them to the internet and let synaptic or apt-get download all the required files automatically?  It's really fast!

---

### Post by Jammy_Stuff on 2006-01-02
I went on google and did a search for site:packages.debian.org "package name"

Came up with the packages. I'll install them now and hope for the best.

---

### Post by popie on 2006-01-02
I just installed vnc4server and it works great. There are full instructions in the first post of this thread:

[http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc](http://www.ubuntuforums.org/showthread.php?t=76638&highlight=gdm+vnc)

The one change I had to make:
Didn't work at first, my vnc viewer client wouldn't connect. Worked after making one critical change:
	In /etc/xinetd.conf, change as follows (put the brace on its own line):```
old:
service vnc1024 {

new:
service vnc1024
{

```

---

