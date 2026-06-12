---
title: "Boot gnome while making a custom live cd?"
date: 2007-06-15
forum: Development CD/DVD Image Testing
---

### Post by inanutshellus on 2007-06-15
According to [the ubuntu wiki's page on Live CD Customization]("https://help.ubuntu.com/community/LiveCDCustomization") (User comments section at the bottom), I should be able to boot into gnome using **gdm**. And while it works it brings up a login prompt... But on a live cd it's not supposed to have a login prompt, so... how do I get past this login prompt, or avoid it?

I'm new to Ubuntu and I assume "Recovery Mode" on the grub boot menu is single-user mode... 

Any insight would be very much appreciated!

Thank you!

---

### Post by smartboyathome on 2007-06-15
If you want to make a LiveCD like it says in the wiki, use UCK. It is made by the person who made the livecd wiki page, and is a whole lot quicker. ;)

---

### Post by inanutshellus on 2007-06-15
I took a cursory look at UCK and found the script approach more confusing than just chroot'ing into the livecd environment and installing what I needed from the command line.

I wanted to boot up gnome to see if everything I had installed (some packages had to be compiled, for example Tora with Oracle support) worked and see if I could set up some defaults for the livecd default user (for example setting up some Eclipse plugins).

If it's easy to do that using UCK then I'll definitely take a second look at it.

Also, I found this application called Reconstructor that seems promising. It will even let you specify the boot, start up, desktop and shut down splash graphics, but I read on these forums that there are some problems with it. 

Is there a straightforward method of specifying these from commandline without resorting to these apps, that apparently have adverse side effects?

---

### Post by smartboyathome on 2007-06-15
Don't use Reconstructor. UCK is WAY better, as you have to do everything by command line in it (the GUI does not work very well), and it gets even MORE confusing than UCK. Also, there is hardly anything done on it anymore, so it is pretty much at a stand-still. I would stick to UCK if I were you.

---

