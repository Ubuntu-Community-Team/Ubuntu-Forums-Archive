---
title: "[SOLVED] Awesome Window Manager 3.0"
date: 2008-10-15
forum: Desktop Environments
---

### Post by mondoUNC on 2008-10-15
I've read about and used older versions of [AWM]("http://awesome.naquadah.org/") and really loved it. I just noticed 3.0 is out, but there is very little information on it. I tried using the guide in the wiki for [building from a git checkout]("http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-Ubuntu-git"). I did my best to follow the instructions but its all a bit out of my league.

Has anyone else tried out AWM 3? I'd really love it if someone could help me get it installed on my computer. I know I'm facing a lot of difficulty trying to learn Lua as I use and configure it, but it seems like a fun and exciting project. I'd really hate to have to wait until it gets easier to install.

To get things started...Following the guide, I think this is where things fell apart:

edit debian/rules and change "--disable-xcb" into "--enable-xcb", and comment out "dh_shlibdeps", save, then

```
$ sudo dpkg-buildpackage -rfakeroot
$ sudo dpkg -i ../libcairo2_1.6.0-0ubuntu2_i386.deb ../libcairo2-dev_1.6.0-0ubuntu2_i386.deb
```

---

### Post by Crymsin_Veggie_Eater on 2008-10-15
I found all the packages listed in Synaptic, but I am not quite sure what I'm doing either.

---

### Post by Crymsin_Veggie_Eater on 2008-10-15
So after being a dumb*ss and deleting grub (in an unrelated issue), I noticed that Awesome appears under the option for sessions on the log in screen after booting up your box. I loaded it up and it came up as a black screen with the numbers one through nine on the top and I was confused so I switched back to gnome to do research. I hope my random discoveries help you in your travels and hey maybe together we can figure this stuff out!:KS

---

### Post by mondoUNC on 2008-10-16
It sounds like you got it up and running, but If you've installed through synaptic it might be an older version. Looking in Synaptic on my system, it says its only up to Awesome 2Final. I've used this version before and its really nice (there is documentation on the forums about getting some nice customizations) but its not the newest version. AWM3 just came out in september so I'm sure it will be a while before you even see it in the backports.

I want to use 3 becuase they've switched to LUA, so I don't want to crease this awesome setup in 2 and then not be able to move it to 3 (which has a lot of bug fixes and is more stable).

---

### Post by Crymsin_Veggie_Eater on 2008-10-16
Well it's not all smiles and rainbows yet. If I log on to the awesome session it logs out in less than 10 seconds and starts running the restart code. Any ideas why?:(:confused:


P.S. Synaptic is distributing version 2.0 but since I am a new awesome user I will stick to it for the support.

---

### Post by cknight on 2008-10-21
> **mondoUNC said:**
> I've read about and used older versions of [AWM]("http://awesome.naquadah.org/") and really loved it. I just noticed 3.0 is out, but there is very little information on it. I tried using the guide in the wiki for [building from a git checkout]("http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-Ubuntu-git"). I did my best to follow the instructions but its all a bit out of my league.

Has anyone else tried out AWM 3? I'd really love it if someone could help me get it installed on my computer. I know I'm facing a lot of difficulty trying to learn Lua as I use and configure it, but it seems like a fun and exciting project. I'd really hate to have to wait until it gets easier to install.

To get things started...Following the guide, I think this is where things fell apart:

edit debian/rules and change "--disable-xcb" into "--enable-xcb", and comment out "dh_shlibdeps", save, then

```
$ sudo dpkg-buildpackage -rfakeroot
$ sudo dpkg -i ../libcairo2_1.6.0-0ubuntu2_i386.deb ../libcairo2-dev_1.6.0-0ubuntu2_i386.deb
```

Well, I may be able to help a little.  I've just successfully installed awesome from git following the same instructions as you.  I too mucked up my first install.  To clean up and try again, I simply deleted the util folder created on my first attempt (caution, make sure you've got the correct util folder as this command is very unforgiving and will wipe it clean without any prompting):
```
rm -rf util
```

Then, I restarted from the beginning of step 5 again.  Where I went wrong the first time was only executing the code in the code blocks.  However, it is necessary to do the following:
```
edit debian/rules and change "--disable-xcb" into "--enable-xcb", and comment out "dh_shlibdeps", save, then..
``` Do this by the following:
```
gedit debian/rules
```
then search/replace both instances of "--disable-xcb" with "--enable-xcb". Finally, search for "dh_shlibdeps" and place a '#' (without quotes) at the start of the line to comment it out.  Save and exit.

Further on, where it says:
```
make && sudo make install
``` this should really be
```
cd awesome
make && sudo make install
```

Good luck! (And I feel for you, I have absolutely no idea what 99% of what I did was!)

---

### Post by mondoUNC on 2008-10-23
thanks cknight, I went back to the [walkthrough]("http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-Ubuntu-git") and it looks like you were right they've changed the code in that section to edit the debian rules from the terminal.

I deleted the util folder and redid the walkthrough and succesfully installed awesome 3.0

---

