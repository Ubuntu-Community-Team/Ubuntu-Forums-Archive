---
title: "Gnome panels frozen - please advise urgently"
date: 2006-07-11
forum: Desktop Environments
---

### Post by fabertawe on 2006-07-11
Hi folks,

Well I guess the honeymoon period's over :roll: ...had a good couple of weeks and then today this...

I'd installed xpenguin (I think it's called) and the panel applet for it and when I tried to add the panel applet it froze the 'add applet' window and the panels. I managed to kill it but was then presented with the error box - "I've detected a panel already running and will now exit". The desktop itself is useable but the panels, top and bottom, are frozen with the exception of the waste bin which, when clicked, opens and and it's right click menu is also accessible. I have the menus on the top bar but all my app icons and the tray with the clock are gone.

I've searched high and low for an answer to this and have tried various things including using the following commands (in a multitude of different ways as suggested in many other threads)...

```
sudo killall gnome-panel
sudo dpkg-reconfigure gnome-panel
```

I've tried deleting launchers from '~/.gnome2/panel.d/default/launchers' and even deleting the whole of '~/.gnome2' itself. I've also tried logging in with different sessions, all to no avail.

I would appreciate any suggestions right now as I'm pretty desperate and don't want to have to reinstall (again!).

I'm using Ubuntu Dapper 6.06 with the AMD64-K8 kernel.

Thanks ... Paul

---

### Post by fabertawe on 2006-07-12
Anyone? Just take 30 seconds to throw me a one line suggestion (but keep it clean!) ;-)

Paul

---

### Post by noneofthem on 2006-07-26
I have got the exact same problem here. No solution yet. Tried your entries as well. No luck... Help, please!

Thanks

Amir

---

### Post by fabertawe on 2006-07-26
> **noneofthem said:**
> I have got the exact same problem here. No solution yet. Tried your entries as well. No luck... Help, please!

Thanks

Amir

Hi Amir,

I couldn't wait long with my desktop in that state and reinstalled. I still haven't come across an answer I'm sorry to tell you :( If you do get it fixed then please post the answer here.

Paul

---

### Post by Murgle on 2006-08-27
well, I seemed to have solved the problem for my by:
```
sudo apt-get remove xpenguins xpenguins-applet --purge
```
```
pkill gnome-panel
```

as a side note, it also seemed to reset my panels to the default state... I consider it a small price to pay for having working panels again.

---

### Post by fabertawe on 2006-08-28
Glad you found a resolution Murgle and thanks for posting. It's good that this problem has some feedback for anyone else searching the forums.

Cheers ... Paul

---

### Post by Anonii on 2006-08-28
Be patient :)

Also, if the problem was still on, even after a reboot. You could try:

killall metacity

that would kill the window manager, and probably restore your gnome-panels, 
unfortunately I dont know what else you could do, and that was just a temporary solution because you would have to kill metacity, in every reboot.
(Its allright for me, since I reboot once every 4 days or something)

---

### Post by gotgenes on 2006-09-02
I've experienced this same problem. It appears to be a critical bug in xpenguins-applet. See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364590](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364590)

I'm going to re-file the bug.

For anyone else who experiences the easy way to get control of your desktop again is to open a terminal and issue:
```
killall xpenguins-applet
```

---

### Post by Wormsie on 2006-10-01
I experienced the same problem. I solved it by deleting .gnome, .gnome2, .gnome2_private, .gconf, .gconfd **and probably most important of all, .themes**

After that, it was back to the basic Ubuntu setup and I had to find all the themes and such again.

I don't really know which files are the most important ones, but deleting .themes seemed to fix everything. Funny. And if that didin't work, find more .-directrories to delete. :p

---

### Post by welshbyte on 2007-01-30
[https://bugs.launchpad.net/ubuntu/+source/xpenguins-applet/+bug/37669](https://bugs.launchpad.net/ubuntu/+source/xpenguins-applet/+bug/37669)

Seems to be still occuring on feisty. If anyone could set that bug to confirmed, it'd help the process. Cheers.

---

### Post by ComplexNumber on 2007-01-30
**fabertawe**
just curious, but why are you using sudo to execute the following command:
(sudo) killall gnome-panel



using sudo to kill the panel is not going to have any effect on *your own* panel in *your own* account, but is only going to restart the root account's panel.

---

### Post by fabertawe on 2007-02-02
> **ComplexNumber said:**
> **fabertawe**
just curious, but why are you using sudo to execute the following command:
(sudo) killall gnome-panel

using sudo to kill the panel is not going to have any effect on *your own* panel in *your own* account, but is only going to restart the root account's panel.

I was brand new to Ubuntu (and Linux) when I had this problem and was trying any suggestion I could find on the forums.

Paul

---

