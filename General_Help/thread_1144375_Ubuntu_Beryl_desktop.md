---
title: "Ubuntu Beryl desktop"
date: 2009-04-30
forum: General Help
---

### Post by CTolley on 2009-04-30
It's me again Margaret.  <-- That's funny if you're a redneck geek.  Or old.  Anyhow, a buddy of mine showed me a youtube video today.  The title was "Ubuntu Beryl".  The reason I bring it up is because the desktop was four sides of a cube, the top and bottom were transparent to let you view all four and decide which one you wanted.  It was cool.  Is this an option for all that Ubuntu, or just a Beryl thing?  If it is an option, how do I get it?  I understand that my POS machine really has no reason to have such cool things, but I would love to play with it now so that when I build my next machine I can be the happiest man alive.

-Tolley

---

### Post by meeples on 2009-04-30
i have that, thats in compiz fusion :)

i think you have to download compizconfig settings manager from the repository so you can enable it, and you have to make sure you have 4 workspaces.

---

### Post by taurus on 2009-04-30
It's called compiz now.  If you install a driver for your graphic card that has the 3d capability, then you can play with the cude.  

System -> Administration -> Hardware Driver

---

### Post by UbuntuNerd on 2009-04-30
you can also look at this detail  [guide](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)

---

### Post by lovinglinux on 2009-04-30
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

and

[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by CTolley on 2009-04-30
Tell me again why I don't wake up and bow down to you gentlemen (and or ladies) every morning before my first cup of coffee?

---

### Post by CTolley on 2009-04-30
System -> Administration -> Hardware Driver
[COLOR="Red"]"No propriety drivers are in use on this system."[/COLOR]

"compiz config-settings-manager"
[COLOR="Red"]Done[/COLOR]

"System>preferences>Appearance>Visual Effects"
[COLOR="Red"]Desktop effects could not be enabled[/COLOR]

And that is my stopping point.  I am currently reading the two pages listed in the previous post.  It is entirely possible that my video card just sucks.

---

### Post by CTolley on 2009-04-30
Okay, I installed and ran compiz-check.

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 


What does it mean?

---

### Post by CTolley on 2009-04-30
After still further reading and doing everything that was listed in the othe pages, I don't have the 'cube' setup.  I do have four desktops that are indepent of each other according to windows open, but the same background is displayed, and there is no cool cube...

Is it simply my video card?

---

### Post by oldos2er on 2009-04-30
Open compizconfig-settings-manager, click 'Desktop,' uncheck Desktop Wall, check both Desktop Cube and Rotate Cube.

---

### Post by CTolley on 2009-04-30
did that, still no cube.  I do have four desktops, but I have no cube.  If it helps, I have four desktops with keys, no selection with mouse.
 
i.e., ctrl-alt-left/right works, ctlr-alt-mouse_buttons does not.

---

### Post by CTolley on 2009-04-30
Before I get stuck on the same background, does that happen anyway?

---

### Post by spillin_dylan on 2009-04-30
Yeah, Compiz will repeat your background for the other sides of the cube.  There is a workaround for this, too.  Does the cube actually rotate when you Ctrl+Alt+Left/Right, or just 'slide' over to the next workspace?  In Compiz Config Settings Manager -> Rotate Cube -> Bindings, is your Ctrl+Alt+(mouse) enabled?

---

### Post by CTolley on 2009-04-30
ctrl-alt-mouse is enabled, but ctrl-alt-direction can't be set.

I can set ctrl-alt-(button 1-9).  That is all.  I moved mouse left and right, up and down, but got no reaction.  I also have soft buttons of 'CTRL', 'SHIFT', 'ALT', and 'SUPER'.

---

### Post by NipplesAndLicks on 2009-05-01
nipplesandlicks@nipplesandlicks-desktop:~$ sudo apt-get install xserver-xgl
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? what do i do about this?

---

### Post by CTolley on 2009-05-01
Oh, and it just changes desktop.  No sliding, no rotating, just a flash change.  Oh, and after adding files to my desktop I notice that it's not really a fresh desktop, it's a clone with no windows open.

---

### Post by 3rdalbum on 2009-05-01
> **CTolley said:**
> Oh, and after adding files to my desktop I notice that it's not really a fresh desktop, it's a clone with no windows open.

Yes, that's how it works.

You need to quit any other package management software before typing that command. Even so, to my knowledge you can't get Compiz working on that chipset... I may be wrong. Sad to say but the VIA graphics are a POS on Linux. If you can put even a basic Nvidia card into your computer you'll be much happier - faster graphics and good Compiz support.

---

### Post by CTolley on 2009-05-02
I'll have to remember that when I build a replacement.  Thank you for the tip.  I'm not going to spend a lot of effort upgrading this comp since it doesn't have a good base to start with.  But hey, that's what happens when you buy a Sam's Club special.

---

### Post by DeMus on 2009-05-02
> **CTolley said:**
> It's me again Margaret.  <-- That's funny if you're a redneck geek.  Or old.  Anyhow, a buddy of mine showed me a youtube video today.  The title was "Ubuntu Beryl".  The reason I bring it up is because the desktop was four sides of a cube, the top and bottom were transparent to let you view all four and decide which one you wanted.  It was cool.  Is this an option for all that Ubuntu, or just a Beryl thing?  If it is an option, how do I get it?  I understand that my POS machine really has no reason to have such cool things, but I would love to play with it now so that when I build my next machine I can be the happiest man alive.

-Tolley

Be glad you have a "simple" videocard and cannot install compiz. When you would read many threads posted here, compiz is the main reason people have problems with their computers: they don't respond, they are slow, they crash. Better disable the desktop effects completely, right-click on your desktop, choose "Change Desktop backgrounds" and choose tab Visual effects. Select the top choice and you're home free. Not only will you have far less crashes, your computer will respond better.

---

