---
title: "Kubuntu Install Issues"
date: 2008-01-22
forum: Desktop Environments
---

### Post by msgkar03 on 2008-01-22
I have downloaded Kubuntu twice and burned it twice.. Each time Ive tried to boot off the CD I get the "Loading Linux Kernel" bar that fills up to 100% but then just stops. It has done this every time.  I'm on a dell inspiron laptop.  I run ubuntu currently, but have also tried to install it off a clean unformatted harddrive.  Any Ideas?

---

### Post by gunksta on 2008-01-23
Weird. You could try the alternative CD. Install the base system, log in, and then:

sudo apt-get install kubuntu-desktop

I don't know why the KDE install isn't working. What kind of a computer is it?

Laptop? Desktop? Video Card?

---

### Post by TeaSwigger on 2008-01-23
Also suggest trying the alternate CD. It is for installation only - not a live CD - and the installation is text mode only, but it is just as easy to install from and often works where the live CD versions won't. As a tip, I suggest using the test that you'll see in the options menu when you boot the alternative CD, since it makes sure the CD & drive are good first.

Many of the problems running or installing from the live CD seem to be caused certain graphics cards or low RAM. Those would be the areas I'd look into first. Kubuntu / ubuntu / Xubuntu do tend to need above 256mb RAM. If it's struggling with them you might look into other distros, for instance Fluxbuntu.

---

### Post by gunksta on 2008-01-23
Perhaps if the OP would post the specs of his system it would be a little easier to understand where the problem is coming from.

[LIST]
[*]RAM
[*]Graphics Card
[*]Laptop / Desktop[/LIST]Also, after downloading the Kubuntu .iso file, did you check to make sure the hash signature matched? I just want to make sure we are dealing with a good download.

You can get the utility here:

[http://www.fourmilab.ch/md5/](http://www.fourmilab.ch/md5/)

---

