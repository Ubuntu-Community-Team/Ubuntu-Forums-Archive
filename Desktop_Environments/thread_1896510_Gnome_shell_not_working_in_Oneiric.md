---
title: "Gnome shell not working in Oneiric"
date: 2011-12-17
forum: Desktop Environments
---

### Post by Randymanme on 2011-12-17
As I've read about it, I'm supposed to be able to install gnome shell from Ubuntu Software Center and it will work.  Well, my gnome shell isn't working.  What do I have to do to get it working.  I have a gnome/openbox login option, but when I try to login to gnome/openbox, what I get is Ubuntu 2D, not gnome/openbox.

Please note that while I have Mint 12 on my computer, I also have Ubuntu 11.10.  This is an Ubuntu 11.10 question.

---

### Post by lolpenguin on 2011-12-17
If you install GNOME Shell, you should log in the the "GNOME" session, not "GNOME/Openbox" if you have it. I suggest installing GNOME Shell using Synaptic rather than USC, as handling of dependencies is better.

---

### Post by Randymanme on 2011-12-17
The "Gnome" session is what's "not working."  It's very slow and unresponsive.  I tried installing the Gnome Desktop Environment with extra components.  Logging out and back in to Gnome session.  No change.  I did a hard reboot, logged in the Gnome/openbox session and from there the following:

randyman@randyman-Dimension-8300:~$ gnome-shell
Window manager warning: Failed to load theme "Aurora": Failed to find a valid file for theme Aurora

Window manager warning: Screen 0 on display ":0" already has a window  manager; try using the --replace option to replace the current window  manager.
randyman@randyman-Dimension-8300:~$ sudo lightDM --replace
[sudo] password for randyman: 
sudo: lightDM: command not found
randyman@randyman-Dimension-8300:~$ sudo --replace
sudo: invalid option -- '-'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
randyman@randyman-Dimension-8300:~$ sudo export DISPLAY=:0
sudo: export: command not found
randyman@randyman-Dimension-8300:~$ export DISPLAY=:0
randyman@randyman-Dimension-8300:~$ gnome-shell --replace
Window manager warning: Failed to load theme "Aurora": Failed to find a valid file for theme Aurora

Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:eek:rg.freedesktop.PolicyKit1.Error.Faile  d: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:eek:rg.freedesktop.PolicyKit1.Error.Faile  d: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Dec 17 2011 06:49:31 GMT-0500 (EST)
Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP![http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11544023](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=11544023)

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

Window manager warning: Log level 16: NOTE: Not using GLX TFP!

gnome-shell-calendar-server[2108]: Got HUP on stdin - exiting
Segmentation fault
randyman@randyman-Dimension-8300:~$
______________________________________________________

What is GLX TFP?  I don't see it in synaptic.  I will remove Gnome Desktop Environment with extra components and Gnome with USC and then reinstall then with synaptic.  I've already installed aurora, but haven't yet checked to see if it makes any difference.

Thanks for the suggestion.

---

### Post by Randymanme on 2011-12-17
Just an update here.  Installing Aurora didn't help; no change.  After removing gnome shell and Gnome Desktop Environment with extra components with USC, I reinstalled them with synaptic.  And there is some progress; not as much as I'd like, but, still, some progress.  The gnome shell actually does open.  Before all I'd get was the top panel (with activities, time, and my name on the upper right) and when I'd click on activities, the entire panel would disappear and nothing else happened, not even ALT+F2.

Now, however, the actual gnome shell does open but moves in slow motion (as though my computer were swapping) and there's some random garbling of graphics.  Now, too, I can logout in the normal way instead of having to restart from the terminal, at then-best, or then-worse, do a hard reboot.  Gnome/openbox session still is Ubuntu 2D, though.

Thanks for the suggestion.  Please give more of them.

---

### Post by kensum on 2011-12-17
I believe your problem is that the 5200 nvidia card with the 173 driver does not support mutter's gl composting. I am not aware of a way around this.

---

### Post by mackaframa85 on 2011-12-18
Try falling back to the open source drivers and purge the restricted ones. I'm not exactly sure how to do this but you can probably find it easily.

---

### Post by Randymanme on 2011-12-26
> **kensum said:**
> I believe your problem is that the 5200 nvidia card with the 173 driver does not support mutter's gl composting. I am not aware of a way around this.

Thank you for your response and suggestion.

I would have accepted that were it not for the fact that the Ubuntu desktop (in 11.10) works flawlessly (as far as I can tell), as did Linux Mint's Mate (in Linux Mint 12).

As it is, I've implemented[SIZE=1] "Installing Gnome 3 on Ubuntu 11.10"[/SIZE] [SIZE=1]http://blog.flexion.org/2011/12/09/gnome-3-shell-ubuntu-11-10-oneiric/[/SIZE].  Everything would be perfect except that the background on the top panel is still garbled (but the font is okay).  The repositories and packages that Jan Hoffman recommends

sudo apt-add-repository ppa:jan-hoffmann/gnome-shell
sudo apt-add-repository ppa:aegirxx-googlemail/gnome-shell-extensions
sudo apt-add-repository ppa:gnome3-team/gnome3 
sudo apt-add-repository ppa:webupd8team/gnome3 
sudo apt-get install libglib2.0-bin gnome-core gnome-documents gnome-shell gnome-sushi gnome-tweak-tool gnomeshell-default-settings gtk3-engines-unico

includes MGSE's bottom panel extension, which works flawlessly better here (added to Gnomeshell on Oneiric 11.10) than it does on Mint 12.

If I decline to nitpick about the top panel background, I can mark this thread as solved.

---

