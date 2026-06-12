---
title: "No icons in desktop, can't open any folders (nautilus)"
date: 2009-04-24
forum: General Help
---

### Post by tokico on 2009-04-24
Hi!

I updated today to 9.04 and after a couple of reboots, Nautilus just stopped working. It shows no icons in the desktop and I can not open any folders. If I open it using the console, it gives me the following error (as a normal user or as root):

```
GLib-ERROR **: /build/buildd/glib2.0-2.20.1/glib/gmem.c:156: failed to allocate 1073741824 bytes
aborting...

```

Could somebody please help me?
Many thanks, tokico.

---

### Post by tokico on 2009-04-24
Would it be a Glib problem?

---

### Post by manuelb on 2009-04-24
Interesting as it's trying to allocate exactly 1 gigabyte of memory, i wonder if it's trying to build a preview of some gigantic jpg picture? Does gconf-editor start?!

---

### Post by tokico on 2009-04-24
> **manuelb said:**
> Interesting as it's trying to allocate exactly 1 gigabyte of memory, i wonder if it's trying to build a preview of some gigantic jpg picture? Does gconf-editor start?!

Yes it does. I have not got such a big file in my desktop or in my home folder. And I only have 512 MB of RAM (1.5 GB of swap, though).

---

### Post by manuelb on 2009-04-24
Ok, so we may resolve it in one go, now let's paste here the output of this CLI command:

```

gconftool -g /apps/nautilus/preferences/thumbnail_limit

```

I bet it say 1 Gb, so we are going to lower it a bit for your system, i guess 10Mb should be fine for any thumbnail you would have to preview ;)

---

### Post by manuelb on 2009-04-24
What's the output of that command?

---

### Post by manuelb on 2009-04-24
I got to go now, in case you could try to set a lower value for images to get thumbnailed: start gconf-editor, browse to **/apps/nautilus/preferences/thumbnail_limit** and change the value to 10485760 (10mb) then restart it.
I don't know if that could resolve it but better try simple things first!

---

### Post by delectomorfo on 2009-04-24
I have the exact same problem, and I did what you suggested about changing the thumbnail size. Did not work. Any ideas?

---

### Post by tokico on 2009-04-24
> **manuelb said:**
> what's the output of that command?

10485760. 10 mb.

---

### Post by manuelb on 2009-04-24
Try to run this:

```

strace -o out.txt nautilus

```

Then open the generated out.txt and put it here.

---

### Post by tokico on 2009-04-24
> **manuelb said:**
> Try to run this:

```

strace -o out.txt nautilus

```

Then open the generated out.txt and put it here.

The file is too big to paste, I'll upload it: [http://www.zshare.net/download/59135144a4a14a74/](http://www.zshare.net/download/59135144a4a14a74/)

The terminal output is:
```
GLib-ERROR **: /build/buildd/glib2.0-2.20.1/glib/gmem.c:156: failed to allocate 1073741824 bytes
aborting...
ptrace: umoven: No such process
trace: ptrace(PTRACE_SYSCALL, ...): No such process

```

---

### Post by tokico on 2009-04-24
Doesn't anyone know how to solve this? I can't really work (well) with Ubuntu without easy access to my folders...

---

### Post by hunterguy86 on 2009-04-24
I'm having this same issue, however it seems that it only happens when I have a CD in the drive.

---

### Post by Phantastes on 2009-04-25
I have the same issue. When I had a cd in the cd/dvd drive I could not open any folders. Now when I removed the cd things are working fine. Any ideas?

---

### Post by tokico on 2009-04-25
> **hunterguy86 said:**
> I'm having this same issue, however it seems that it only happens when I have a CD in the drive.

> **Phantastes said:**
> I have the same issue. When I had a cd in the cd/dvd drive I could not open any folders. Now when I removed the cd things are working fine. Any ideas?

NOW I remember. This happened when I inserted a CD in the drive. Now that I removed it, the icons in the desktop appear and nautilus works properly.

This is a very serious bug, I'm going to report it ASAP.

---

### Post by tokico on 2009-04-25
I already reported the bug:

[https://bugs.launchpad.net/bugs/366616](https://bugs.launchpad.net/bugs/366616)

---

### Post by Quirion on 2009-04-25
Please try running nautilus manually from a terminal, as described in [https://bugs.launchpad.net/bugs/366262](https://bugs.launchpad.net/bugs/366262).

---

### Post by Zunino on 2009-04-27
I am also seeing this problem. And I can also confirm that it is related to having a disc in the drive. When that is the case, Nautilus becomes unresponsive.

Regards,

-- 
Ney André de Mello Zunino
[http://blog.zunino.eti.br/](http://blog.zunino.eti.br/)

---

### Post by artiee on 2009-04-28
Had the same problem but got it fixed. No icons on desktop and couldn't open folders. Reboot didn't work. XFCE-desktop worked though (it doesn't use nautilus). Taking CD from drive fixed the problem.

---

### Post by Zunino on 2009-04-28
Hello, there!

Just wanted you guys to know that I've managed to fix the problem here by following the advice in this [post]("http://comsciprof.wordpress.com/2009/04/28/problems-in-opening-home-folder-via-places-in-ubuntu-904-jaunty-jackalope/") I found. All one has to do is change the permissions of a shared library, namely **libnautilus-brasero-extension.so**, by running:
```
sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so
```I hope this works for you guys too.

Best regards,

-- 
Ney André de Mello Zunino

---

### Post by borrisl on 2009-04-29
I'm a newbie, so this bug was really causing me pain.  Your solution worked.

---

### Post by FactTech on 2009-05-02
A better solution that is less likely to cause problems down the road is to get the proposed update for brasero (2.26.1-0ubuntu1) from the jaunty-proposed repository. To do this:

1) Enable the proposed package repository using System -> Administration -> Software Sources (see [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for details).

2) Create a file /etc/apt/preferences to describe the priority of packages found with conflicting versions in multiple repositories (again, see [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for details). This will prevent Update Manager from wanting to automatically install every proposed update in the pipeline.

3) Launch Synaptic via System -> Administration -> Synaptic Package Manager

4) Locate the brasero package (e.g. by typing "brasero" in the quick search box at the top)

5) Click on the brasero package to highlight it and select Package -> Force Version in the Synaptic menu.

6) Choose the jaunty-proposed version of the package (2.26.1-0ubuntu1) from the drop-down menu and click "Force Version".

7) Also force the version for the libbrasero-media0 package if this isn't handled automatically.

8) Click the "Apply" button near the top of Synaptic.

After it's done, this problem should disappear. If this seems like too much hassle, you can just wait for the update to be officially released, but I don't know how long that will take.

This bug is known to the developers -- see [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/335942](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/335942) for more information.

---

### Post by justiceandfreedom on 2009-05-03
I have a similar problem. Every time when I try to run gnome-settings-daemon, totem, rhythmbox, brasero, I get the same error message:
GLib-ERROR **: /build/buildd/glib2.0-2.20.1/glib/gmem.c:156: failed to allocate 2777797896 bytes
Apparently everything else works, but my desktop looks quite ugly without the gnome-settings-daemon.:(

---

