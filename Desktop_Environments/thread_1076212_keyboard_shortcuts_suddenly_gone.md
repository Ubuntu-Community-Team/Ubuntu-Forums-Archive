---
title: "keyboard shortcuts suddenly gone"
date: 2009-02-21
forum: Desktop Environments
---

### Post by josvanr on 2009-02-21
intrepid kde 4.1: this morning my keyboard shortcuts suddenly were not working anymore. When I try to re-define them in the system settings, this message appears:

Failed to contact the KDE global shortcuts daemon
Message: No such object path '/KdedGlobalAccel'
Error: org.freedesktop.DBus.Error.UnknownObject

any suggestions? (reboot didn't help)

jos

---

### Post by rjs987 on 2009-02-21
I also have Intrepid with the most updated KDE and yesterday had the exact same error symptoms as you. Happened just after I installed the most current updates so I am wondering if one of those updates has anything to do with it.

As I was typing this I just saw on my screen the announcement for 47 new updates available. Maybe there is a fix in there. I will report back after those are installed.

---

### Post by rjs987 on 2009-02-21
I did install the new updates but the commit failed. I used the provided option to attempt to resolve and that failed as well with this error:


> It seems that the recovery has failed. Please fix manually (try dpkg --configure -a and/or apt-get -f install) in terminal... 

The error was: 

APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --configure, -a ], 
    Sup-process returned error code 1, 
    Error processing kdebase-workspace-bin : dependency problems - leaving unconfigured., 
    Error processing kscreensaver : dependency problems - leaving unconfigured.

I tried dpkg --configure -a in terminal but that failed since kdebase-workspace-bin and kscreensaver were broken. I then ran apt-get -f install and that seems to have fixed it.

Now I can get to the Keyboard Shortcuts settings but there are 2 to choose from where I previously only had the one, Standard Keyboard Shortcuts and Global Keyboard Shortcuts.

Standard Keyboard Shortcuts is where I need to restore the shortcuts I use but the one I use the most is missing from the list! I use multiple desktops and run a vm in one desktop while running kontact in another and then my financial program in yet another. The problem now is that there is no option for setting a shortcut for switching desktops. I want that one back!

Any ideas?

---

### Post by rjs987 on 2009-02-21
OK, now all my shortcuts are back again.

There was no restart indicated or requested after the last batch of updates but a restart is needed. I also found out that the updates changed the themes I had selected. I really didn't care for the default background on the login screen but that changed as well. The desktop wallpaper reverted to the default for the new theme instead of the picture I had selected. Kmail also changed so it looks a lot more like my Outlook Pro at work. At least as far as the sorting and grouping by date. I originally did not have any grouping turned enabled. I don't really have an opinion on that result yet. Another change is that most of the gadgets on my task bar are now in a box with a solid background. This is better since those are the icons that would go transparent at times, usually when OpenOffice.org Writer has the focus. Now the icons inside the box do not go transparent with OOo Writer, but the other icons still do go transparent and also the analog clock gadget I have on the desktop flashes as before. Maybe put all the task bar gadgets or icons in solid box? I guess these things will have to wait until Kubuntu 9.04 and OOo 3.x.

At least the shortcuts are back and maybe a few other things are fixed.

---

### Post by txcrackers on 2009-02-21
KDE 4.2 is being placed into the active repositories. Until all the apps and libraries are updated, you might experience these kind of issues. There were some rather large changes between 4.1 and 4.2

---

### Post by josvanr on 2009-02-22
no luck for me yet, dpkg --configure -a doesn't do anything, apt-get -f install removes some packages, but no shortcuts are appearing. When I now run the update manager, i see

APT Error. Context:
    Package download failed, 
    [http://nl.archive.ubuntu.com/ubuntu/pool/universe/libi/libical/libical0_0.33-1_i386.deb:](http://nl.archive.ubuntu.com/ubuntu/pool/universe/libi/libical/libical0_0.33-1_i386.deb:) 403 Forbidden

hope this is a temporary problem.?? (I posted a new thread with this problem)


Josvanr

---

### Post by PurpleMonkeyKing on 2009-02-22
I haven't any luck getting my keyboard shortcuts back, either, but my apt-get is running fine without any problems.

Also, after my upgrade to KDE 4.2, no KDE programs make any sound. I can still play sounds from mplayer and other programs, but nothing that uses phonon.

Phonon shows no devices to pick from in the sound panel in System Settings, but I don't know how to make it detect my sound card. It doesn't make sense to me that ALSA works fine, but Phonon won't detect anything...

---

### Post by wieman01 on 2009-02-24
Same problem here. No matter how often I assign shortcuts, they don't stick after a reboot. Very annoying problem.

---

### Post by PurpleMonkeyKing on 2009-03-07
So did anyone figure out how to get the shortcuts working again, or did everyone else's problems fix themselves.

I've been without keyboard shortcuts or phonon sound for a few weeks now, and none of the updates I've installed have seemed to fix it. There has to be something I'm missing...

---

### Post by wieman01 on 2009-03-08
Can't put my finger on it, but I suspect it's something to do with permission in the home directory... something tells me that.

---

### Post by HavocXphere on 2009-03-08
> **PurpleMonkeyKing said:**
> So did anyone figure out how to get the shortcuts working again, or did everyone else's problems fix themselves.
Under regional settings, there is keyboard layout. Aside from languages, you can also set it to some of the more common keyboard types. etc Logitech. This seems to affect the shortcut keys somehow.

I got the daemon not running message too, but the shortcuts are mostly fine. i.e. the ones that were working still work. **Some** of the special keys never did/don't.

@wieman01: You could be on to something there. I remember setting ownership on all files in ~ back to me after some of them got root ownership from excessive sudo-ing. Started a thread about the command to set it back somewhere here...its in my threads started history...to lazy to search for it now.

---

### Post by wieman01 on 2009-03-08
> **HavocXphere said:**
> @wieman01: You could be on to something there. I remember setting ownership on all files in ~ back to me after some of them got root ownership from excessive sudo-ing. Started a thread about the command to set it back somewhere here...its in my threads started history...to lazy to search for it now.
Yes, I think I remember such a message as well. The system settings complaining about file ownership. I need to do some more research here.

---

### Post by PurpleMonkeyKing on 2009-04-25
I've finally got my keyboard shortcuts back after upgrading to Jaunty yesterday. This isn't quite the solution I wanted, but at least they're back now.

---

### Post by wieman01 on 2009-04-26
Same here!

---

