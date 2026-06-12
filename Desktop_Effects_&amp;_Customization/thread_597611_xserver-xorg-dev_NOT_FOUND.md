---
title: "xserver-xorg-dev NOT FOUND"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by sleepylabrat on 2007-10-30
Hello,

I am totally new to Ubuntu and fairly new to Linux. I just installed the Gutsy Gibbon last night and am trying to get the cube working. I have the ATI All-In-Wonder 9700 Pro video card installed and was told that I needed to install the drivers (envy was suggested). I found this link: [http://www.pendrivelinux.com/2007/02/23/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/2007/02/23/installing-proprietary-video-drivers-for-ubuntu/) and after entering in the command for #2 (sudo dpkg -i envy*.deb), I get this:

Selecting previously deselected package envy.
(Reading database ... 90746 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu8_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

Apparently there are some dependencies. So I tried "sudo apt-get install xserver-xorg-dev" and received this message in return:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev

Now I don't know what to do... Can somebody please help me?

Thanks in advance :)

---

### Post by Zorael on 2007-10-30
```
$ sudo dpkg -i envy*
<spam of missing dependencies>
$ sudo apt-get install -f
```

Does that help?

Also, there's [a newer version of Envy](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb) than the one you'e trying to install. :>

---

### Post by sleepylabrat on 2007-10-30
Thanks Zorael for the quick reply and for the new version of envy!

I'm still getting this error message when running "sudo dpkg -i envy*":

Selecting previously deselected package envy.
(Reading database ... 90746 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu10_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

And if I go ahead and run "sudo apt-get install -f" afterward, I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fakeroot
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  envy
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2994kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91110 files and directories currently installed.)
Removing envy ...

I think I need to install all those dependent packages but I don't know how :( Can somebody walk me through?

Thanks again!

---

### Post by FranMichaels on 2007-10-30
Hello,

First thing,
I'm running Ubuntu Gutsy, what version do you use?

```
apt-cache search xserver-xorg-dev
xserver-xorg-dev - X.Org X server -- development files
```

So the package is in the repositories. However, maybe not all are enabled?
System -> Administration -> Software Sources
Make sure everything is checked.

As for envy, I've never used it, but you can use gdebi to install the package and gather it's dependencies.

Either double click your .deb or
```
sudo gdebi envy.deb
```
(change envy.deb to whatever it's called. Just making sure ;) )

Good Luck. :KS

P.S. Something handy when working from terminal
If you have a file called envy-blah-blah, typing for example env, then hitting tab will complete it for you.
If there are several files, like envy1, envy2, etc. Hitting tab twice will list the options so you can narrow it down. 
Saves on typing! :)

---

### Post by Zorael on 2007-10-30
**Most** odd, I've never had issues with apt-get install -f, it has always done the trick for me.

Check your software sources, I guess. I get the feeling those packages should be in the main or universe repositories, though.

edit: er, yes, like the above poster said, sources sources. :>

---

### Post by sleepylabrat on 2007-10-30
Hi FranMichaels,

Thanks for the reply :) 

I just installed Gutsy last night.

Nothing happened when I ran "apt-cache search xserver-xorg-dev". The next prompt appeared. Then when I double-clicked on the .deb file, a "Package Installer - envy" window popped up saying "Error: Dependency is not satisfiable: xserver-xorg-dev".

PS. Thanks for the typing tip also. Some of those filenames are SO LONG.

---

### Post by Zorael on 2007-10-30
```
$ apt-cache search xserver-xorg-dev
```

What does that output?

Or, if you don't feel at home using terminals, search for xserver-xorg-dev in Synaptic. :) I like the terminal way though, rarrw.

edit: My point is, xserver-xorg-dev **should** be satisfiable, I really can't see why not. Since it isn't for you, apt-get install -f can't solve dependencies and instead removes envy.

---

### Post by sleepylabrat on 2007-10-30
YOU GUYS ARE THE BEST!

I checked the sources like you guys said and there's a lot of activity going on right now. Things are downloading left and right! I'll keep you posted!

Thanks a million!

---

### Post by 3dgimp on 2007-11-01
Having the exact same problem. In terminal when I type "apt-cache search xserver-xorg-dev" it displays nothing and goes to the next line. If I double click on my envy.deb file, it tries to do something, and then says "Error: Dependency is not satisfiable: xserver-xorg-dev".

Any ideas? I've done all the above to no avail. This is a fresh install of gutsy that I completed about an hour ago. So I don't think I need a fresh install.

Thanks

Ed

---

### Post by Zorael on 2007-11-01
Again, you probably need to enable more software sources (repositories).

I don't know the command to look up which one you need, but it's likely the **universe** one.

You can change this in Synaptic (Software -> Repositories), or in the Add/Remove Programs application.

---

### Post by pfatty on 2008-02-01
I was having a similar issue but I was receiving "Error:  Dependency is not satisfiable:  module-assistant"

I ended up, out of frustration, just typing 'envy' in the terminal.  The program launched, notified me of a broken package, repaired it,  and I am now rebooting with my video card driver installed.

---

