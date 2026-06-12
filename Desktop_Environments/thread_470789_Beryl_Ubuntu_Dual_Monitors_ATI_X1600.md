---
title: "Beryl Ubuntu Dual Monitors ATI X1600"
date: 2007-06-11
forum: Desktop Environments
---

### Post by TheFuzz4 on 2007-06-11
Hey All,

Well first off I'm a NOOB just switched over this weekend and I'm very happy with the Ubuntu system.  I have it setup as my primary OS now.  I still have my windows install on there as a backup for now but it will soon go bye bye.
Ok so here is where my problem lies.  I would love to get beryl setup and installed.  I've gone through the HOW-TO on this and did everything as instructed but here is what happens when I switch my session over to the Gnome with XGL.  Sometimes when I log in it only has a gray background with a X for the cursor kinda like in Fedora when it is first starting up and I get panels ontop of both my screens with no menu's.  So the only thing I can do is reboot the X server then log back in except this time I now get my complete desktop and the panels have there menus on them but I cannot click on anything so the only thing left is to restart the X server and log back into the regular Gnome.  If anyone has any ideas as to this please let me know.  Thanks.

---

### Post by Soybean on 2007-06-11
I don't have an answer for you, but I thought I should warn you: ATI card + dual monitors + beryl is about the most difficult possible setup you could have. I've seen a few people asking about doing it, but I haven't seen any solid answers from someone who's succeeded. So... I think it ought to be possible, but you should be prepared for it to be extremely tricky/frustrating. As you're probably aware, Beryl is still very much beta software, and there are problems with the ATI Linux drivers. Trying to add dual monitors to the mix is just a recipe for disaster. ;)

I've got an NVidia card, so I haven't really looked into it much, but here are 3 things I would look at if I were trying to do it myself (don't know if they'd actually help, it's just where I'd start):
1) Big-desktop: [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)
2) Nested X sessions (look into the "xnest" package)
3) Multi-screen setup using the SVN version of Beryl: [http://forum.beryl-project.org/viewtopic.php?f=34&t=3408](http://forum.beryl-project.org/viewtopic.php?f=34&t=3408)

Note that the 3 things are (probably) mutually exclusive -- I don't know if any of them will work, but I'm pretty sure that they won't work together. That's about all I've picked up on the subject. Good luck!

---

### Post by TheFuzz4 on 2007-06-11
Thanks I'll take a look at that and check it out.  Right now I'm using MergedFB as my dual setup so maybe the big desktop will allow me to do it.  I'm at work at the moment so I'll have to wait till I get home to try it out.

---

### Post by TheFuzz4 on 2007-06-13
I think that for the time being I'm just going to hold of on the Beryl install.  I've got pleanty of other new toys here to keep me occupied.  I love my Ubuntu install.  Wonders why I didn't make the switch earlier.  Can you run KDE in Ubuntu?

---

### Post by jimbo99 on 2007-06-14
It is my understanding that beryl has problems with ATI drivers.  Or rather one of the components necessary for beryl to work properly is missing from the ATI drivers and ATI has been shy on when they will resolve the issues.  People are crying out for the support but I haven't heard a word from them on what they will do and when they expect to have it done.  nVidia has had the support for quite a while.

I guess there's a way to do it with the open source drivers.  Am not real sure about that.  I also guess there's a way to make it work with XGL.

I know a friend that tried it on his ATI card had he went through hell trying to get it to work.  Yet a mutual friend set his Ubuntu up with his nVidia card in a matter of minutes.

My friend learned of the compromises in buying ATI products.  Not that their hardware is bad.  It is kick ***.  ATI just has had a reputation spanning nearly 20 years of putting out the crappiest of drivers.

---

