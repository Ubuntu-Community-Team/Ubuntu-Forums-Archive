---
title: "ubuntu 8.04 dosent like to browse files?"
date: 2009-05-15
forum: General Help
---

### Post by NTpspE on 2009-05-15
Hello,
I am using an Fijitsu Seimens Amilo 1705.

Some of the time, when browsing files, it'll just freeze the nautilus window, and then all nautilus will freeze, some of the time causing the panels to freeze too. 
Also, firefox seems to like freezing too, and if nautilus has frozen and if i try open firefox when nautilus has frozen, i end up with a lot of sleeping firefox processes. 

Any help?

---

### Post by NTpspE on 2009-05-15
Also, when this happens and i try run terminal, i get the window, and a blank box.
This happens to most programs when nautilus freezes :(

---

### Post by kanikilu on 2009-05-15
This may not apply in your case, but an apparently common cause of nautilus hanging is the file-preview feature, so you might try turning that off:

Open nautilus > Edit > Preferences > Preview > Set all the dropdown boxes to "Never".

If that's not the cause, try running nautilus from a terminal, and then watch the terminal for output if it hangs.

Lastly, I personally use several nautilus extension packages (nautilus-wallpaper, nautilus-share, nautilus-gksu, nautilus-open-terminal), if you are using some extensions, perhaps one is causing an issue? Maybe try removing them one at a time to see if you can isolate the problem...

---

### Post by NTpspE on 2009-05-15
> **kanikilu said:**
> This may not apply in your case, but an apparently common cause of nautilus hanging is the file-preview feature, so you might try turning that off:

Open nautilus > Edit > Preferences > Preview > Set all the dropdown boxes to "Never".

I'll try that, but i dont think its that, because all i did last time, was create a new file (the blank file, in the new file menu)
And i've done it before, some of the time it just does it when i click UP or back, and it just seems to occasionally do it

> **kanikilu said:**
> 
Lastly, I personally use several nautilus extension packages (nautilus-wallpaper, nautilus-share, nautilus-gksu, nautilus-open-terminal), if you are using some extensions, perhaps one is causing an issue? Maybe try removing them one at a time to see if you can isolate the problem...

I dont have any extensions, i installed 8.04 from the disk, and i dont really mess about installing extentions, it does what i want it to do allready :p

---

### Post by utnubuuser on 2009-05-15
Hi - Do other version s of Ubuntu run ok on this machine?  Might it be a hardware/driver related issue?
How about posting the output of lspci so people can see what's going on.

---

### Post by NTpspE on 2009-05-15
> **utnubuuser said:**
> Hi - Do other version s of Ubuntu run ok on this machine?  Might it be a hardware/driver related issue?
How about posting the output of lspci so people can see what's going on.

Okay, how do i go about doing that?
And i havent tried other versions. I didn't want to upgrade to feisty fawn, as i didn't want to loose the bottom bar for the mac-like dock.
And im in the process of upgrading to 8.10, but i stopped, as i was unsure if i'd loose the LTS?

---

### Post by NTpspE on 2009-05-20
It's still doing it, and its very annoying, especially when i loose a lot of work, which is why i moved from (the os that shall not be named) to ubuntu :p

---

### Post by utnubuuser on 2009-05-20
It was supposed to be > sudo apt-get install --reinstatll nautiluswith two hyphens instead of one.

And you might want to try another file-browser like PCman until you can get this fixed.

And...are you running Compiz?  Sometimes Compiz causes problems.

---

### Post by NTpspE on 2009-05-22
No i'm not running it, my computer can't really handle it.
I think my laptop dosent like linux at all, i mean 8.04 is the only version that works, and fedora boots so a squiggly white box lol.

---

### Post by utnubuuser on 2009-05-23
Yeah, laptops can be very particular. If you're having probs in one environment, ie. gnome, install xfce and try that instead.

Is it a new laptop?  Oldish?  P3, P4, or coreDuo?  Plenty of ram, (384meg or more)?

A good alternative to the full-blown Ubuntu-Gnome desktop is something called #!CrunchBang Linux.  It's based on the Ubuntu-minimal install and does very well on under-endowed systems.  - I recently had it set up on an older P3 laptop with 247meg of ram.  Very fast, lean, and clean.

Gnome really wants decent system specs.  You can install the xfce desktop right from within gnome, and when you restart, at login, go to Options and choose the xfce environment.

---

### Post by NTpspE on 2009-05-24
Its about two years old, fujitsu seimens amilo li 1705, and it has about 1 gig of ram i think.
Both my laptops have simmilar specs, and im running 9.04 fine on my other one.

---

### Post by HolyShnikes on 2009-09-17
I am having the same problem but no one is responding to my posts.  I really need some help.  Did you ever get it working?  I see this is an older post.

[http://ubuntuforums.org/showthread.php?t=1268268](http://ubuntuforums.org/showthread.php?t=1268268)

---

