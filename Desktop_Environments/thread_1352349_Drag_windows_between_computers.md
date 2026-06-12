---
title: "Drag windows between computers"
date: 2009-12-11
forum: Desktop Environments
---

### Post by JHuizingh on 2009-12-11
I'm looking for a software package that allows you to drag windows between computers.  I found synergy, which is like a virtual kvm that lets you use a single keyboard an mouse on different computers.  I would like to find something that takes it to the next step and allows you to drag a window from one computer onto another computer.  Does anybody know of a package like this?

---

### Post by 3Miro on 2009-12-11
Unless you have one X-server and two computers, then it will not work.You may look into remote desktop, it might be something like what you need.

---

### Post by roggenschrotbrot on 2009-12-12
been searching for something like this a few years ago, as far as i know until today there is no valid solution for transferring application-instances between two workstations.

i guess the closest thing to this behavior would be to use one of the two workstations as a thin-client, but i have no idea to log in two station simultaneous at one x-session, maybe the man pages have an answer to that.

---

### Post by FiVAL on 2009-12-14
Just like the plasma screen in het office of NCIS ;-)

(NCIS : [http://bgavideo.files.wordpress.com/2009/02/ncis.jpg](http://bgavideo.files.wordpress.com/2009/02/ncis.jpg))

I'm also looking for a way to push an app. (in copy) to
an X Server on a different machine...

---

### Post by opensensesolutions on 2010-02-04
Initiate a vnc session with a resolution big enough to span both monitors. Then run a vnc viewer on each machine and view the appropriate half.

You will probably also need x2x to control the two computers with one keyboard/mouse automatically as you move the mouse from screen to screen.

---

### Post by vertago1 on 2013-02-11
Here is a thought experiment.

Say the two computers had a ssh session between each other with X server forwarding. Could you issue a kill-stop to a process and then somehow port it over to the ssh session on the other machine before resuming it and thus move the window from one machine to another?

---

### Post by vertago1 on 2013-02-11
I did some more searching and found two tools:

Xpra and xmove

Xpra is supposed to be newer. I may take a look at using these and write back what I find.

---

### Post by oldos2er on 2013-02-12
Old thread closed, please start a new thread.

---

