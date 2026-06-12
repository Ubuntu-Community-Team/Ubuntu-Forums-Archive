---
title: "Dell Clutter Launcher - Available to download?"
date: 2009-04-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joey-elijah on 2009-04-14
Is the custom dell launcher available to download anywhere? If so where and what is it called in packages etc? 

I really like the look of it and would prefer it to my full NBR interface.

[IMG]http://farm4.static.flickr.com/3046/2944621881_bc1c140b36.jpg[/IMG]

---

### Post by joey-elijah on 2009-04-15
Does dell have any repos it might be on, perhaps?

---

### Post by Brandon Williams on 2009-04-18
I can't believe anyone prefers the Dell launcher. You might like how it looks, but it's very badly integrated with the rest of the system. Even if you like the look, I recommend against using it.

But if you insist, look here: [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/)

The line you want to add to your sources.list is:

deb [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/) hardy-dell-mini universe

It's called dell-launcher.

---

### Post by joey-elijah on 2009-04-19
> **Brandon Williams said:**
> I can't believe anyone prefers the Dell launcher. You might like how it looks, but it's very badly integrated with the rest of the system. Even if you like the look, I recommend against using it.

But if you insist, look here: [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/)

The line you want to add to your sources.list is:

deb [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/) hardy-dell-mini universe

It's called dell-launcher.

It can't find a 'dell-launcher' and manually looking through the pools, nor can i.

---

### Post by Brandon Williams on 2009-04-19
> **joey-elijah said:**
> It can't find a 'dell-launcher' and manually looking through the pools, nor can i.

Are you running an lpia architecture install? If you're running an i386 install, then dell-launcher wouldn't show up for you.

Looking in the Packages file for hardy-dell-mini universe, you'll find that the lpia architecture package is located here:

[http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/universe/binary-lpia/](http://dell-mini.archive.canonical.com/dists/hardy-dell-mini/universe/binary-lpia/)

You'll have to fix the packaging to allow you to install it on i386, though. You might be better off installing from source.

---

### Post by joey-elijah on 2009-04-19
> **Brandon Williams said:**
> Are you running an lpia architecture install? If you're running an i386 install, then dell-launcher wouldn't show up for you.


That would explain it then. I'm not quite ready to downgrade back to 8.04 just to try out a launcher...

I do appreciate you finding it for me - I've asked everywhere and no one had a clue.

---

### Post by Brandon Williams on 2009-04-19
If you search around on this forum, there's an article somewhere about converting i386 packages to lpia. You might be able to apply the method in reverse to convert this lpia package to i386. I don't know if it will actually work in reverse, but it's worth a try.

Otherwise, change 'deb' to 'deb-src' in sources.list, and try 'apt-get build dell-launcher' to see if it will build for i386 with the existing source bundles.

---

### Post by joeydawson on 2009-04-28
I agree that the dell launcher app is better than eebuntu remix

I need a little help though.
the dellbuntu disk i have clears the hdd
what i want to do is install 8.04
then install the launcher.
Hopefully then i can dual boot with windows.

I'm just getting the knack of installing stuff using terminal
so if anyone knows the code for installing the dell launcher it would be a great help.

---

### Post by joey-elijah on 2009-04-28
> **joeydawson said:**
> I agree that the dell launcher app is better than eebuntu remix

I need a little help though.
the dellbuntu disk i have clears the hdd
what i want to do is install 8.04
then install the launcher.
Hopefully then i can dual boot with windows.

I'm just getting the knack of installing stuff using terminal
so if anyone knows the code for installing the dell launcher it would be a great help.

If you download from the link above then it's just a simple double click! If you're not using a lpia then you can simple force install it *[I]with *sudo dpkg[/I] -i --*force*-all package_name.deb 

It may not be the cleanest or best way, but it works with no issues.

---

### Post by snowpine on 2009-04-28
> **joeydawson said:**
> I agree that the dell launcher app is better than eebuntu remix

I need a little help though.
the dellbuntu disk i have clears the hdd
what i want to do is install 8.04
then install the launcher.
Hopefully then i can dual boot with windows.

I'm just getting the knack of installing stuff using terminal
so if anyone knows the code for installing the dell launcher it would be a great help.

The Dellbuntu disk is a complete hard drive restore image. It will take over your entire drive, then if you want to dual boot, you can install Windows after the fact, however, consensus on the forums is this is more difficult than installing windows first, then Ubuntu.

Also be aware the Dell image will only work well on a Dell Mini, and there is no upgrade path from 8.04.

---

### Post by xboxSlayer on 2009-09-16
Is it possible to install this on a i386 9.04 system? I tried the force install option that was suggested but it said it was missing packages.

dpkg - warning, overriding problem because --force enabled:
 package architecture (lpia) does not match system (i386)
Selecting previously deselected package dell-launcher.
(Reading database ... 155777 files and directories currently installed.)
Unpacking dell-launcher (from dell-launcher_0.8.16_lpia.deb) ...
dpkg: dell-launcher: dependency problems, but configuring anyway as you request:
 dell-launcher depends on belmont-config-travel | belmont-config; however:
  Package belmont-config-travel is not installed.
  Package belmont-config is not installed.
 dell-launcher depends on libclutter-0.6-0; however:
  Package libclutter-0.6-0 is not installed.
 dell-launcher depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not installed.
Setting up dell-launcher (0.8.16) ...

Configuration file `/etc/xdg/autostart/dell-launcher.desktop', does not exist on system.
Installing new config file as you request.

---

### Post by melat0nin on 2009-12-13
I'd also like to install this on 9.10 (MSI Wind). Tried installing the deb as per the instructions above but I get the same dependency problems as the user above.

Any ideas?

---

