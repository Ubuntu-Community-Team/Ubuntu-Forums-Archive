---
title: "BUG??? num lock, shift, ctrl key does not work!"
date: 2008-06-03
forum: Desktop Environments
---

### Post by gtdaqua on 2008-06-03
I use Hardy Kubuntu 32 bit Desktop and often when working with VMWare Console, my shift/control keys do not work when I switch back to hardy desktop. It works only inside VMWare console. 

Its becoming a pain because all my passwords are case sensitive and I have to use the mouse to log out and log back in. Worse if lock the desktop - I have to open another session, kill kdm and start over! 

This problem happens only when i work  with VMWare which is frequent! It happened during Hardy Alpha releases but its cropping up again! 

I cant event do a "ps aux | grep" to query VMware services because of the "pipe" in the command!

---

### Post by louieb on 2008-06-03
> **gtdaqua said:**
> I cant event do a "ps aux | grep" to query VMware services because of the "pipe" in the command!

Not much help with the keys not working 

 you could add an alias to your .bashrc  

```
alais  psg='ps aux | grep whatever'
```

Good Luck.

---

### Post by gtdaqua on 2008-06-03
But why is this happening? If numlock wont turn (or shift/control not working), whats the possible reason?

---

### Post by gtdaqua on 2008-06-04
bump???

---

### Post by bhaverkamp on 2008-06-04
I am seeing this as well. Several times over the last few days. I am also running Vmware WS 6.03 and cannot try running without it but I do only see it so far on the one system running WS.

---

### Post by bhargavakumark on 2008-06-04
I have encountered the same problem too. Even shutting down vmware, does not restore shift key capability.

---

### Post by captaintrav on 2008-06-04
I'm using WS 6.03 with Hardy AMD64, have the same problem.  Bugs have been filed and enough noise is being made.  Other distributions are seeing this problem, and it happens across several versions of VMWare, Xorg, Gnome, and KDE.  So far it is looking like some sort of Xorg bug, but I guess all we can do is be patient.  A temporary workaround/fix is to create a shortcut/launcher to setxkbmap, which when ran, will restore normal functioning of modifier keys.

---

### Post by gtdaqua on 2008-06-05
> **captaintrav said:**
> I'm using WS 6.03 with Hardy AMD64, have the same problem.  Bugs have been filed and enough noise is being made.  Other distributions are seeing this problem, and it happens across several versions of VMWare, Xorg, Gnome, and KDE.  So far it is looking like some sort of Xorg bug, but I guess all we can do is be patient.  A temporary workaround/fix is to create a shortcut/launcher to setxkbmap, which when ran, will restore normal functioning of modifier keys.

Now, thats more like it! 

Let's see if this actually works. Hope this need not be 'sudoed' or its no good.

---

### Post by captaintrav on 2008-06-05
> **gtdaqua said:**
> Now, thats more like it! 

Let's see if this actually works. Hope this need not be 'sudoed' or its no good.

No, it does not.

---

### Post by bhaverkamp on 2008-06-05
I have filed a bug against this with VMware. They also suggested the setxkbmap work-around. I have not yet had an opportunity to test this work-around. They are working on it.

---

### Post by bhaverkamp on 2008-06-05
I was just able to reproduce this problem on my system and the setxkbmap trick seemed to work for me.

---

### Post by pano79 on 2008-08-28
The 'setxkbmap' solved the problema also for me :)
Thanks

---

### Post by jgrocha on 2009-02-04
The same problem in Ubuntu Jaubty, with VMWare Workstation 6.5.1 build-126130
**setxkbmap** solved my problem (for now).

The last thing I changed (related with keyboard) was adding several xkeymap.keycode lines to /etc/vmware/config to allow the use of the arrow keys in the virtual machine (see [http://ubuntuforums.org/showthread.php?t=971593](http://ubuntuforums.org/showthread.php?t=971593))

---

### Post by svinchon on 2011-03-01
I have the same problem under ubuntu 10.10 using VMware Player 3.1.3 build-324285.

Has any progress been made since Feb 2009?

The "setxkbmap" command seems to work once logged in but what if my screen gets locked?

---

