---
title: "Gnome looks strange (like Win3.1)"
date: 2011-08-09
forum: Desktop Environments
---

### Post by bemymonkey on 2011-08-09
Hi everyone!

I'm finally ready to tackle my problem ;): A few months ago, I let Ubuntu download some update packages (automatically via the update manager), and something happened to the interface - some parts of it seem to have reverted to a legacy interface of some kind. Oldish looking icons, solid grey toolbar backgrounds...

[IMG]http://dl.dropbox.com/u/7086491/pictures/ubuntu.gif[/IMG]

It annoyed me so much that I set up a new Ubuntu VM. Then, a few weeks ago, the same thing happened again - let Ubuntu download updates automatically and reboot the VM, and once again, the interface looks all weird.


It still works, of course, but it just looks strange, and anything but aesthetically pleasing.


Anyone here seen this before? I tried searching, but tbh, I had no idea what to search for. So sorry if it's been handled before, and thanks in advance ;)


-edit- As you can see, I'm running Ubuntu in VMWare Player, with VMWare Tools installed, on a Win7 Pro 64bit host. Not sure if that matters... everything else seems to work fine.

-edit2- Just tried [this]("http://dl.dropbox.com/u/7086491/pictures/ubuntu.gif") - first logon after deleting the config files and logging out, the interface looks normal again, with the dark greyish black traditional Ubuntu style taskbars... then, a few seconds later, everything goes ugly again. What gives? :(

---

### Post by bemymonkey on 2011-08-11
Nobody? :(

---

### Post by terry_a_g on 2011-08-11
That is the default gtk theme, Raleigh.  Check your theme settings.

---

### Post by bemymonkey on 2011-08-11
[IMG]http://dl.dropbox.com/u/7086491/pictures/ubuntu2.gif[/IMG]

Selecting a different theme only changes the window title bars.

Is there some other place to set themes?

---

### Post by imortalninja161 on 2011-08-11
hmm thats what my GUI looked like before i did updates after my first install of Ubunut :/ strange it go's back to that after a update.

go to ubuntu softwear centre 
downloade compiz and simple compizconfig settings manager then open compizconfig manager and enable unity

---

### Post by bemymonkey on 2011-08-15
Hmmm, I don't think Compiz will work on my setup - doesn't that require real hardware acceleration? Could be difficult because of VMWare.

I'll give it a shot though...

-edit- Looks like more stuff is screwy:

[http://dl.dropbox.com/u/7086491/pictures/packagedependencies.gif](http://dl.dropbox.com/u/7086491/pictures/packagedependencies.gif)
That's the error I get when I try to install Simple CompizConfig. Compiz was already installed...

Could that have something to do with my weird optical glitches?

And I don't want Unity, by the way - just the regular old Ubuntu interface, but less ugly than it's looking at the moment.

---

### Post by grahammechanical on 2011-08-15
This happens to me from time to time. I think that it happens when the desktop loading process does not read the correct theme fast enough (just a wild guess). In your appearance panel you will find a custom theme has been created. Resetting the theme does not work as you have found out. A reboot will. That is my experience. Sorry.

Regards

---

### Post by bemymonkey on 2011-08-15
Unfortunately, a reboot doesn't help. Did once, but since it happened the second time, no amount of reboots has fixed the problem... :(

---

### Post by BigSilly on 2011-08-15
[It's a common and ongoing problem]("http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnome+theme+reverts+default").No fix sadly as of yet, or so I am led to believe. I'm hoping the move to Gnome 3 as the base for Ubuntu 11.10 will finally see an end to this problem, but I'm not holding my breath...

---

### Post by bemymonkey on 2011-08-18
That's ridiculous. And to think, I was thinking of dual-booting for even more Linuxy goodness...

-edit- uninstalling GDM and installing lightDM with apt-get worked... jeeeze, of all the hoops...

Thanks for the link to the other thread btw.!

---

### Post by Frogs Hair on 2011-08-18
Here is one possible fix option . [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by BigSilly on 2011-08-20
> **Frogs Hair said:**
> Here is one possible fix option . [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

Thank you very much for that. Clearly this is becoming a bit of an issue for Ubuntu, and I'm glad to see them taking it seriously after leaving it far too long. I had this problem with Maverick as well as Natty, and what with this and a number of other oft-reported problems I was having, I decided to switch distros.

I really hope to see the Ubuntu experience improve from 11.10 onwards, and I think it will.

---

