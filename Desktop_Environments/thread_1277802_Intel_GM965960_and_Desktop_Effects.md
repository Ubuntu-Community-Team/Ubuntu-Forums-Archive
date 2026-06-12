---
title: "Intel GM965/960 and Desktop Effects"
date: 2009-09-28
forum: Desktop Environments
---

### Post by meditatingfrog on 2009-09-28
Trying to get desktop effects enabled with my intel gm965/960 graphics adapter.  The intent here is to increase 2d performance by offloading some of it to 3d hardware.  So far, installed a new kernel based on this blog:  [http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html](http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html).  That seemed to have given me the option to enable desktop effects, but the ability to enable it was fleeting, and now enabling desktop effects is no longer possible.  

Now, I'm following this how to:  [http://wiki.compiz-fusion.org/Intel%20with%20AiGLX](http://wiki.compiz-fusion.org/Intel%20with%20AiGLX).  

I did try lxde, but 2d performance isn't that much better than in gnome to warrant the permanent change.

My system specs are duocore 1.47ghz processor, 2GB ram, integrated intel gm965/960 graphics.

I also enabled metacity compositing, by checking /apps/metacity/general/compositing_manager in gconf-editor.

---

### Post by meditatingfrog on 2009-09-28
followed this guide:  [http://wiki.compiz-fusion.org/Intel%20with%20AiGLX](http://wiki.compiz-fusion.org/Intel%20with%20AiGLX), after executing:  

LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp & 

the terminal shut down.  can't use alt commands, like alt-f2 or alt-tab, and selecting windows to move them doesn't work.  

messing around in my "new" environment before rebooting, to try and figure out the problem.

---

### Post by meditatingfrog on 2009-09-28
this how to didn't work for me:  [http://wiki.compiz-fusion.org/Intel%20with%20AiGLX](http://wiki.compiz-fusion.org/Intel%20with%20AiGLX).  Though compiz did seem to run, it wasn't functional.

moving to these:  

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by meditatingfrog on 2009-09-28
Checked out this forum:  [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875) regarding black listed compiz drivers.  I executed the command (copy and pasted) to add SKIP_CHECK=yes to ./config/compiz/compiz-manager but an attempt to enable compiz still failed.  It was an interesting command though, to add the line SKIP_CHECK = yes.  Something like:  mkdir -p ~/.config/compiz && SKIP_CHECK=yes >> ~/.config/compiz/compiz-manager.

---

### Post by andrea000 on 2009-09-28
Can you run compiz in the terminal

Applications->accessories->terminal 
type in the terminal
> compiz
and post the output

---

### Post by meditatingfrog on 2009-09-28
> **andrea000 said:**
> Can you run compiz in the terminal

Applications->accessories->terminal 
type in the terminal

and post the output

[http://paste.ubuntu.com/280955/](http://paste.ubuntu.com/280955/)

Do you have an intel graphics adapter?  I think I need to set up the "optimal" configuration listed in this how to:  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Update:  after breaking out of compiz from the terminal, my Xorg session basically became unusable.  Even tried to post this from my current Xorg session.  Couldn't move windows around, or alt-tab.  Also, interestingly, the title bars of programs disappeared, and could no longer click and drag them around.

---

### Post by andrea000 on 2009-09-29
> **meditatingfrog said:**
> [http://paste.ubuntu.com/280955/](http://paste.ubuntu.com/280955/)

Do you have an intel graphics adapter?  I think I need to set up the "optimal" configuration listed in this how to:  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Update:  after breaking out of compiz from the terminal, my Xorg session basically became unusable.  Even tried to post this from my current Xorg session.  Couldn't move windows around, or alt-tab.  Also, interestingly, the title bars of programs disappeared, and could no longer click and drag them around.

I have a Intel card on my laptop i had all kinds of problems with it.The card was blacklisted so i had to unblacklist it.
Running compiz from the terminal shouldn't have done anything to your x org but the title bars of programs disappearing
has me thinking about a similar problem i had on my laptop.All the window borders disappeared when i rebooted it did not help.
I found a bug report about the legacy full screen support in compiz when i turned that off and rebooted everything came back
and worked right.

(don't know if this helps but i hope it does)

---

### Post by meditatingfrog on 2009-09-29
> **andrea000 said:**
> I have a Intel card on my laptop i had all kinds of problems with it.The card was blacklisted so i had to unblacklist it.
Running compiz from the terminal shouldn't have done anything to your x org but the title bars of programs disappearing
has me thinking about a similar problem i had on my laptop.All the window borders disappeared when i rebooted it did not help.
I found a bug report about the legacy full screen support in compiz when i turned that off and rebooted everything came back
and worked right.

(don't know if this helps but i hope it does)

rebooting fixed it.  don't really have all kinds of problems with this card.  gnome works, but compiz doesn't.  just trying to get better performance out of it.  enabled compositing in gconf-editor, which helped a bit.  was going to try kde by typing sudo apt-get install kubuntu-desktop but the install didn't work.  was curious to see how it performed relative to gnome.  well, maybe some other time, gotta' go to sleep tonight.  

are you on irc?

---

### Post by andrea000 on 2009-09-29
No I'm not on irc sorry.

---

