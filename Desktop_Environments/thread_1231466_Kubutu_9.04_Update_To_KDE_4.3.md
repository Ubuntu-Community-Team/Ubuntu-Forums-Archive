---
title: "Kubutu 9.04 Update To KDE 4.3"
date: 2009-08-04
forum: Desktop Environments
---

### Post by izizzle on 2009-08-04
It hasn't appeared on Kubuntu's page yet, so I was wondering if anyone knows how I can update my Kubuntu 9.04 install to KDE 4.3? 

Thanks.

---

### Post by Virtualboxbuntu on 2009-08-04
I believe that you need to enable Kubuntu's backport repositories. It says on Kubuntu.org:

Add this to /etc/apt/sources.list```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```
Then
```
sudo aptitude update
```
Then use your update manager. Beware that other unstable software is in that repository, watch what you update.

---

### Post by Virtualboxbuntu on 2009-08-04
I just tried it myself, and I recommend that if you try this, back up all important data. I totally screwed up my KDE and I have to reinstall now.

---

### Post by izizzle on 2009-08-04
Thanks guys. Looks like Kubuntu did indeed update their page, just a little late. 

You say you screwed up your KDE? HOW? Now I'm scared...

EDIT: I just UPDATED and it says I have 98 blocked updates. Do you guys think I sould continue upgrading?

---

### Post by Raboch on 2009-08-04
I wouldn't continue updating if I were you. I followed the kubuntu site's directions and messed up my kde like Virtualboxbuntu did. Good thing I had gnome to fall back on so I could disable the 4.3 repository and remove 4.2 and my kde settings then reinstall it. Then I checked the kubuntu site again and this time they said to add two repositories. Fine, so I added the second one and reactivated the first and updated 4.2 to 4.3... and it got messed up again.

Absolutely unacceptable. Sigh... I wanted to get 4.3 and thought that updating kubuntu'd be the easiest path. But I guess I'll look around for a distro with good support for my macbook and that'll update to 4.3 without hassle.

---

### Post by izizzle on 2009-08-04
Bummer....it's not fair. I was so excited for the 4.3 release...and now this. One of the dark sides of Kubuntu I guess.

On the Kubuntu site it says the following: "KDE 4.3 packages are now available.

To see what's new, see the release announcement

Users of our latest development release, Karmic, can upgrade to the latest packages. Note: The last few parts are still building and will be available in a few hours.

Users of our stable 9.04 release can install it from the Kubuntu Backports PPA. You need both lines.

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu) jaunty main

It is strongly recommended that you verify the integrity of these packages by installing the archive's GPG key. You may do this by saving the PUBLIC KEY BLOCK available from this page to a file and importing it from the authentication tab in KPackageKit's software sources window.

Then refresh and do a full upgrade.

**Packages for Jaunty are not officially supported**. KDE 4.3 will be part of Kubuntu Karmic 9.10 to be officially released this October."

---

### Post by iopo on 2009-08-05
The announcement has changed again: we are back to a single repository:

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

by the way, I see 67 blocked updates: I guess they are still updating the repository. I suggest to wait.

Cheers

---

### Post by iopo on 2009-08-05
Wait, I guess there is a bit of confusion: the announcement on the Kubuntu forum shows two repositories.

[http://kubuntuforums.net/forums/index.php?topic=3105560.0](http://kubuntuforums.net/forums/index.php?topic=3105560.0)

who should we trust, kubuntu.org or kubuntuforum.net?

---

### Post by indigest on 2009-08-05
I followed the instructions here:
[http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)

Then I ran "sudo apt-get dist-upgrade" in order to get the blocked updates/upgrades.  Everything's running fine after the upgrade.  The color scheme is a bit lighter, so the contrast is no longer as good in the taskbar.  It might just take a while to get used to, though.  If not, I can always try to mess around with the color schemes.

The Banshee (1.5.0) notifications are now much bigger, which is nice.

My network manager no longer shows that it is connected, it is only showing the plug symbol, even though it actually is connected.  Also, the "i" icon in the system tray is greyed out even though there are no notifications.  Before, it would disappear when there were no notifications.  I'm not sure if this is a bug or the intended behaviour.

---

### Post by pmlxuser on 2009-08-05
an the 
"It is strongly recommended that you verify the integrity of these packages by installing the archive's GPG key. You may do this by saving the PUBLIC KEY BLOCK available from this page to a file and importing it from the authentication tab in KPackageKit's software sources window."

when you click to get the PUBLIC KEY BLOCK from the site you can't get it are you people also experiencing the same

---

### Post by iopo on 2009-08-05
+1 for kubuntu.org

[http://www.linux-archive.org/kubuntu-user/346993-error-upgrading-kde-version-4-3-a.html](http://www.linux-archive.org/kubuntu-user/346993-error-upgrading-kde-version-4-3-a.html)

---

### Post by izizzle on 2009-08-05
The Kubuntu site says that the last few parts are still building. I'll check back in a couple of hours...

---

### Post by jimbo99 on 2009-08-05
KDE 4.3 can and will screw up some installs, and rather badly.  Disheartening as it is much of it has to do with their unwillingness to support pre-existing custom configurations, even as simple a customization as a different icon set.

Those that have had a messed up desktop you can overcome it with a bit of work.  If you don't have ubuntu-desktop installed you should do that.  Pressing Alt+CTL+F1 will get you to a terminal log in window.  From there you just log in normally.  Then install the ubuntu-desktop.  Yes, it will install a lot of extra stuff. 

Once you have that you should reboot and see if you can get to the graphical log in window.  If you can then change your session to gnome.  If you can't then if you are automatically taken to a kubuntu desktop (but with everything screwed up) press alt+f2 and type in logout.  Choose the logout and that should take you back to where you can log in and choose the session you want.

Once at the gnome desktop you should go to your synaptic package manager and find all instances of KDE 4.x that are installed. I also unchecked the 3rd party repository but you may not have to do that.  Once done you should reboot.  

I then used the instructions at this blog to get KDE back up and running:

**[http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html](http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html)**

The problem that persisted after that was in having a customized icon set.  I loaded system settings, went to appearance, and then to icons and chose the default Oxygen icon set.  I then did some re-arrangements.

This is a bit shy on details but I should be most of you though the process of getting your KDE back up and running. 

I agree they messed up and they will continue to mess up unless you yell loudly and often.  Let them hear you when they screw up like this.

---

### Post by Virtualboxbuntu on 2009-08-05
I have successfully upgraded to KDE 4.3. I followed the instructions on Kubuntu.org, but as somebody else here suggested (I think) instead of using update manager, I used ```
sudo apt-get dist-upgrade
``` which actually installs everything you need.

I think I'm going to go enjoy some KDE 4.3 goodness right now. :D

---

### Post by izizzle on 2009-08-06
Well, I decided to update and I need a little help. While updating (I did it from the terminal), it asked me if I wanted to keep the current /etc/kde4/kdm/kdmrc file or overwrite it. So, should I choose to keep my current file or overwrite it with the new one?

Thanks.

---

### Post by izizzle on 2009-08-06
Yay! I have successfully upgraded to KDE 4.3!! 

The only downside is, I'm stuck with the default Oxygen icons.

---

### Post by krazyd on 2009-08-06
> **izizzle said:**
> Yay! I have successfully upgraded to KDE 4.3!! 

The only downside is, I'm stuck with the default Oxygen icons.

So was I so I reverted to default settings by deleting ~/.kde/

I did this:
Log out of my session.
Ctrl-Alt-F1 to go to tty1.
Backup my ~/.kde to kde.tar
```
tar -cvvf kde.tar .kde/
```
Delete ~/.kde
```
rm -rf .kde
```
Restart
```
sudo shutdown -r now
```

Then after a restart KDE went to defaults for 4.3. I just had to copy my ktorrent config back into the new ~/.kde from my backup (I had some half-downloaded torrents)

---

### Post by izizzle on 2009-08-07
Thanks Krazyd. I did that, but it removed ALL my setings (Bespin configs, color schemes, etc), so I reverted back to the backup...I guess I'll stick with KDE icons until I get the time to redo everything.

---

### Post by NormanFLinux on 2009-08-07
I installed mine from the Jaunty backports repository and upgrade was complete with no problems. I've removed the backports after the upgrade since I don't want to install untested software.

---

