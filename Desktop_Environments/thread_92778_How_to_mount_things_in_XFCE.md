---
title: "How to mount things in XFCE?"
date: 2005-11-20
forum: Desktop Environments
---

### Post by chickengirl on 2005-11-20
Would somebody PLEASE PLEASE PLEASE PLEASE PLEASE tell me how the heck to mount disks in XFCE? The xfce "mount manager" won't mount anything except my DVD-ROM drive, I've also got a CD-R and a flash drive and the "mount manager" doesn't even seem to see them.

XFCE's "documentation" is essentially non-existent and they seem to be unaware of the concept that anyone would actually want to *do* anything on xfce *other* than take pretty screenshots.

Look, I'm not afraid of the command line. If the only way to do it is from the command line I'm willing to do it, just tell me the freaking command. For my flash drive I've tried sudo mount -t vfat /dev/sda1 /various places but it will only ever let me read or write to it as root.

Is there SOME kind of REAL documentation for xfce or especially the "mount manager" available somewhere that I've missed??

PLEASE don't just ignore this! SOMEBODY here has GOT to know what the heck I'm talking about. I really doubt I'm the only person in the world who has ever tried to actually USE xfce.

This is the ONLY thing keeping me from being a happy ever after XFCE user.

---

### Post by foxy123 on 2005-11-20
run gnome-mount-manager and save sessions settings on exit... it will do it for you

---

### Post by aysiu on 2005-11-20
Can you calm down? No one's ignoring you. You posted this two minutes ago!

By the way, we're all volunteers here. Do you know why XFCE documentation stinks? No one wrote it. If you want to write it, write it.

That said, there's a simple fix to your problem. Hit Alt-F2 and type ```
gnome-volume-manager
```

**Edit**: I don't know what you're so anxious about. [A simple search for "automount xfce"](http://www.ubuntuforums.org/search.php?searchid=2593114) turned up a whole host of threads with the answer foxy123 and I gave you in this thread within minutes of you posting, not the least of which was [one of your threads asking the same thing a month ago](http://www.ubuntuforums.org/showthread.php?t=80304&highlight=xfce+automount) and getting the same answer!

---

### Post by foxy123 on 2005-11-20
[QUOTE=aysiu]Can you calm down? No one's ignoring you. You posted this two minutes ago!

By the way, we're all volunteers here. Do you know why XFCE documentation stinks? No one wrote it. If you want to write it, write it.

That said, there's a simple fix to your problem. Hit Alt-F2 and type ```
gnome-volume-manager
```[/QUOTE]
yes, not gnome-mount-manager, as I stated, mea culpa

---

### Post by chickengirl on 2005-11-20
[QUOTE=aysiu]Can you calm down? No one's ignoring you. You posted this two minutes ago![/QUOTE]

Sorry. I was a little touchy from googling "automount xfce" and finding oodles of people with the exact same question I had...... but nobody bothered to answer them. Or even say "gee, sorry, I don't know..."
Feels like that happens every time I have a question. Are my computing needs really that esoteric? Or does Google just hate me? :confused: 

> By the way, we're all volunteers here. Do you know why XFCE documentation stinks? No one wrote it. If you want to write it, write it.

Yeah, because *I* know everything there is to know about XFCE. :rolleyes:

> That said, there's a simple fix to your problem. Hit Alt-F2 and type ```
gnome-volume-manager
```

Get Big Brother to do it. Nice. xfce sure is lucky it chose to piggy-back instead of creating a fully-functional environment all by itself... Well, it works, anyway. Except for the fact that the xfce mount manager chokes when I try to unmount... oh well, it's junk anyway. Luckily I'm not *so* utterly retarded that I don't know how to *un*mount from the command line...

Thanks... I'm sorry for being an idiot.

> **Edit**: I don't know what you're so anxious about. [A simple search for "automount xfce"](http://www.ubuntuforums.org/search.php?searchid=2593114) turned up a whole host of threads with the answer foxy123 and I gave you in this thread within minutes of you posting, not the least of which was [one of your threads asking the same thing a month ago](http://www.ubuntuforums.org/showthread.php?t=80304&highlight=xfce+automount) and getting the same answer!

That thread got buried right after I posted it and I didn't know someone had found and resurrected it. Sorry.

---

### Post by taurus on 2005-11-20
Do the search from here, not google!!!

---

### Post by aysiu on 2005-11-20
[QUOTE=chickengirl]Sorry. I was a little touchy from googling "automount xfce" and finding oodles of people with the exact same question I had...... but nobody bothered to answer them. Or even say "gee, sorry, I don't know..."
Feels like that happens every time I have a question. Are my computing needs really that esoteric? Or does Google just hate me? :confused:[/quote] Taurus is right. Google will get you millions of useless results. If you must use Google, do this:

site:ubuntuforums.org automount xfce

> 
Yeah, because *I* know everything there is to know about XFCE. :rolleyes: I wasn't trying to be cheeky. I'm serious. My point is that stuff doesn't exist just because it should. It exists because users create it. Maybe once you do figure it all out, you can create the Xubuntu guide.

> 
Get Big Brother to do it. Nice. xfce sure is lucky it chose to piggy-back instead of creating a fully-functional environment all by itself... Well, it works, anyway. Except for the fact that the xfce mount manager chokes when I try to unmount... oh well, it's junk anyway. XFCE is a light desktop environment. Its primary appeal is its speed, not its full functionality. If it has to borrow from "Big Brother" every now and then, that's fine. 

> 
Thanks... I'm sorry for being an idiot.

That thread got buried right after I posted it and I didn't know someone had found and resurrected it. Sorry. Being an idiot is fine. I know because I'm an idiot, too. Getting impatient is not necessary. We're all volunteers here and other users. Glad it all worked out for you, though.

---

