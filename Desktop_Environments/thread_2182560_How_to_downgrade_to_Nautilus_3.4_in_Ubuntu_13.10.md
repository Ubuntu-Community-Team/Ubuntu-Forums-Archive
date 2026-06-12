---
title: "How to downgrade to Nautilus 3.4 in Ubuntu 13.10?"
date: 2013-10-21
forum: Desktop Environments
---

### Post by lads on 2013-10-21
The functionality lacking in Nautilus 3.8 is just too much to bare; tree view, split screen, SVN and Git integration, etc. The tricks that did it in Ubuntu 13.04 don't work any more, how can it be done in 13.10?

Thanks.

---

### Post by lads on 2013-10-22
Hello everyone,

This is getting pretty serious. The first thing I noticed after upgrading is that Nautilus 3.8 does not integrate with Rabbit, thus there's no access to SVN or Git servers. But today there's something worse: SSH servers. Half of the time it fails to connecting, claiming failed authentication when all the credentials are correct; the other it connects successfully but then it only shows the first item in the root folder. Needless to say all of this works seamlessly with Nautilus 3.4, I need to downgrade otherwise this version of Ubuntu becomes useless.

Please help. Thanks.

---

### Post by mc4man on 2013-10-22
I would suggest you start looking for another file manager or something other than Ubuntu 13.10 as you can't simply downgrade nautilus back to 3..4
It may be possible to build 3.4 in 13.10 but you'd need to fix all the errors that gtk-3.8 will cause with that source & even then may find other problems

---

### Post by BrunoLotse on 2013-10-24
Hi:) Follow this link [http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)This is for 13.04 yet it might work with 13.10 as well.Cheers,Bruno

---

### Post by lads on 2013-10-24
Hi Bruno, this doesn't work on 13.10, it was one of tricks I was talking about.

---

### Post by paulisdead on 2013-10-25
I'm hating the new nautilus too, but I think I have found the solution, install nemo.  It's a fork of nautilus 3.4 before all the stupid started done by the Mint folks.  It still has the great old fashioned find as you type and bookmarks.  I'd expect it'll still have the features you're looking for too.

---

### Post by lads on 2013-10-25
I'm marking this thread as solved, for most matters and purposes [installing Nemo is the same as downgrading to Nautilus 3.4]("http://askubuntu.com/questions/360831/downgrade-to-nautilus-3-4-from-ubuntu-13-10-nautilus-3-8/365206#365206"). Its appearance can be tweaked into the default Unity style and it can also be set as the default file browser.

The only issue remaining is the integration with RabbitVCS, but since it doesn't work either with Nautilus 3.8 I guess I can't complain.

---

### Post by konklone on 2013-10-27
I don't think you should mark this as solved -- installing Cinnamon from their PPA can make it impossible to log in to Unity going forward. This happened to me, and I couldn't log back in until I removed all cinnamon packages (removed cinnamon and nemo, then did autoremove to remove the stuff they brought in with them).

Other people who've experienced this:
[http://ubuntuforums.org/showthread.php?t=2180202](http://ubuntuforums.org/showthread.php?t=2180202)
[http://ubuntuforums.org/showthread.php?t=2183781](http://ubuntuforums.org/showthread.php?t=2183781)

---

### Post by paulisdead on 2013-10-28
> **konklone said:**
> I don't think you should mark this as solved -- installing Cinnamon from their PPA can make it impossible to log in to Unity going forward. This happened to me, and I couldn't log back in until I removed all cinnamon packages (removed cinnamon and nemo, then did autoremove to remove the stuff they brought in with them).

Other people who've experienced this:
[http://ubuntuforums.org/showthread.php?t=2180202](http://ubuntuforums.org/showthread.php?t=2180202)
[http://ubuntuforums.org/showthread.php?t=2183781](http://ubuntuforums.org/showthread.php?t=2183781)
You don't need to install any additional PPAs to install nemo.

---

### Post by vmsman on 2013-10-28
Even installing Nemo/Cinnamon without the PPA does not fix the login issue in 13.10. As soon as you try to make Nemo the default file manager, the wallpaper goes black and all desktop icons disappear. Once you logoff or reboot, you will be caught in a login loop and not get back on until you:


open TTY (ctrl + alt + F1) and login at the console:

[FONT=Courier New]sudo apt-get remove --purge cinnamon*[/FONT]
[FONT=Courier New]sudo apt-get autoremove[/FONT]

Then shutdown and reboot. You will be able to login again. To restore your desktop wallpaper and icons plus make Nautilus the default again, enter a terminal (ctrl + alt + T):

[FONT=Courier New]xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search[/FONT]
gsettings set org.gnome.desktop.background show-desktop-icons true

For right now, Cinnamon/Nemo do not play well with Unity in Ubuntu 13.10. This is a Cinnamon/Unity problem. Hopefully we will see a fix soon.

---

### Post by paulisdead on 2013-10-28
This didn't happen to me and it doesn't sound like it happened to the OP either.  I think your problem is that you installed the full blown cinnamon, and not just nemo by itself.

---

### Post by rajesh6 on 2013-10-30
try the below procedure's, these may work for sure
1)
sudo add-apt-repository ppa:webupd8team/experiments
sudo apt-get update
sudo apt-get dist-upgrade
killall nautilus


or try this one
2)
sudo ppa-purge ppa:gnome3-team/gnome3

---

### Post by BrunoLotse on 2013-10-31
Here is ostensibly how to install Nemo without Cinnamon deps [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)Cheers, Bruno

---

### Post by lads on 2013-10-31
> **konklone said:**
> I don't think you should mark this as solved -- installing Cinnamon from their PPA can make it impossible to log in to Unity going forward.

I'm sad to hear this. I only installed a packaged named *nemo*, I have no *cinnamon* packages installed, nor do I intend to install any of them.

---

### Post by mc4man on 2013-10-31
If I was to use nemo then would probably use the builds as linked here (ppa has builds for all active Ubuntu releases
[http://ubuntuforums.org/showthread.php?t=2184959&p=12834290&viewfull=1#post12834290](http://ubuntuforums.org/showthread.php?t=2184959&p=12834290&viewfull=1#post12834290)

---

