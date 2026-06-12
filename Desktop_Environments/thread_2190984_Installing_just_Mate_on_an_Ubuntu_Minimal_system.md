---
title: "Installing just Mate on an Ubuntu Minimal system"
date: 2013-11-30
forum: Desktop Environments
---

### Post by newb85 on 2013-11-30
I'm doing a little experimenting with installing Ubuntu minimal and building desktop systems from there.  (I'm working on VirtualBox.)  I was feeling a little nostalgic, so I thought I'd try Mate.  Another that I tried was Gnome.  I noticed a slight difference in the result.

With Gnome, I simply installed Gnome and restarted the VM, and presto, I was greeted with the GDM login screen and everything worked from there.

Contrast that with Mate.  I added the Mate repository, installed the signing key, and installed mate-desktop-environment.  Upon restarting, I was greeted by the CLI login.  After a little digging I found out I had to install xinit.  Now, whenever I start the system, I still get the CLI login, but once I log in, I can
```
xinit /usr/bin/mate-session
```
and presto, I have the Mate DE.  Of course, since I've already logged in through the CLI in order to xinit, I never see the GUI login screen for mate.

So, what I'd like to know is this: how do I set the Mate system to go to the GUI automatically, so that (as with Gnome) when I start the machine, I see a graphical login screen?  I would imagine it has to do with making the xinit command run automatically, but I don't know how to set that up, or what user needs to run it.

---

### Post by ibjsb4 on 2013-11-30
I have not used Mate, but I wonder ..

Instead of xinit, should you not be going through your display manager?  Which DM do you run with mate?

---

### Post by ajgreeny on 2013-11-30
mate uses mate-display-manager (mdm) presumably a fork of the gnome-2 gdm.  Did that install when you added mate to your system, and is it set to start at boot?

---

### Post by tgalati4 on 2013-11-30
Mate has a lot of piece parts that need to be installed to work correctly.  I prefer to use Linux Mint Mate which has the heavy lifting already done and it is fairly lightweight as well.

---

### Post by newb85 on 2013-11-30
I'll have to check whenever I get back to that machine whether MDM was installed. I would assume it was, since I hadn't installed any other display managers. (Aren't display managers needed for more than logging in? )

Are you installing Mint Mate (the DE) in an Ubuntu minimal system, or are you talking about just installing Mint (the whole system)?

---

### Post by buzzingrobot on 2013-11-30
There are a few long posts at the MATE site (mate-desktop.org) from folks who've done installs on Ubuntu minimal.

i've done it.  Once I started adding the apps I wanted to use, etc., dependencies were brought in and it quickly became a not-so-minimal system.

---

### Post by newb85 on 2013-11-30
I'm not necessarily doing this to achieve a very minimal system.  (I realize that one can only cut so much from the requirements by switching DEs.)  It's more of a learning experiment.  I guess I'm a little curious as to why all the packages and settings needed to make Mate run were not included in the metapackage.

---

### Post by newb85 on 2013-11-30
Oh, it looks like the system doesn't have Mate Display Manager installed.  It does have Mate-Session-Manager installed, which "can be started from a display manager, such as MDM."  The funny thing is, Mate Display Manager isn't even in the repos.  (There is a package mdm, but it's something completely unrelated, and it's from the universe, not the mate repo.)

---

### Post by buzzingrobot on 2013-12-01
> **newb85 said:**
> Oh, it looks like the system doesn't have Mate Display Manager installed.  It does have Mate-Session-Manager installed, which "can be started from a display manager, such as MDM."  The funny thing is, Mate Display Manager isn't even in the repos.  (There is a package mdm, but it's something completely unrelated, and it's from the universe, not the mate repo.)

Follow the MATE install directions for your specific release of Ubuntu provided by the MATE team at [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download).  You'll get all the necesssary components. I doubt a complete MATE is in Ubuntu's repos.

Note that the Debian instructions on that page include installing the "mate-desktop-environment-extra" meta-package, while it is not listed for an Ubuntu install. I always install it on Ubuntu.  It brings in a good number of useful packages; I've never had a problem with it.

---

### Post by tgalati4 on 2013-12-01
[http://blog.linuxmint.com/?p=2493](http://blog.linuxmint.com/?p=2493)

---

### Post by newb85 on 2013-12-02
> **buzzingrobot said:**
> Follow the MATE install directions for your specific release of Ubuntu provided by the MATE team at [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download).  You'll get all the necesssary components. I doubt a complete MATE is in Ubuntu's repos.

Note that the Debian instructions on that page include installing the "mate-desktop-environment-extra" meta-package, while it is not listed for an Ubuntu install. I always install it on Ubuntu.  It brings in a good number of useful packages; I've never had a problem with it.

Those directions are exactly how I installed MATE.  I had even installed mate-desktop-environment-extra.  I meant that MDM isn't even in the MATE repositories for Ubuntu Saucy.

---

### Post by buzzingrobot on 2013-12-02
> **newb85 said:**
> Those directions are exactly how I installed MATE.  I had even installed mate-desktop-environment-extra.  I meant that MDM isn't even in the MATE repositories for Ubuntu Saucy.

Ah.

Believe MDM has been solely a Mint effort for some time.  It's in their repos: [http://packages.linuxmint.com/](http://packages.linuxmint.com/).

---

### Post by newb85 on 2013-12-03
So, I decided to try gnome-session-flashback (a.k.a.-fallback) on another VM.  To my surprise, it had the same problem as mate--no display manager was installed automatically, nor was xinit.  What really has me scratching my head is why I can't install GDM on either my mate system or my gnome-fallback system without also installing basically all of Gnome.

---

### Post by ibjsb4 on 2013-12-03
Unless you used --no-recommends with your fallback install, you also installed Unity.  Here's how I do a basic fallback desktop.

```
sudo apt-get install xserver-xorg lxterminal firefox synaptic xinit && sudo apt-get install --no-install-recommends gnome-session-fallback nautilus
```

Then in ~/.xinitrc it will read

```
exec gnome-session-fallback
```

And the panels will be black on black at first boot, adjust the background color.

If you want a DM instead, I have found that lightdm works well with fallback, this will bring in a lot of packages though.

---

