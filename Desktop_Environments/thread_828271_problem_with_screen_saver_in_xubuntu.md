---
title: "problem with screen saver in xubuntu"
date: 2008-06-13
forum: Desktop Environments
---

### Post by systemshock869 on 2008-06-13
i just installed xubuntu on an older machine for my grandpa (we'll see how long it stays on here) and have run into a problem that needs to be fixed asap.

i was looking at the screen savers, and i clicked on one called ant-something.  i can't get into the screen saver configuration program or i would tell you the exact name.  anyways it froze my computer, so i rebooted.  when i went to get back into the screen saver program, it had been set on that screen saver, so it immediately freezes!  and if the computer sits for 10 minutes, it will freeze.

is there a configuration file somewhere i can edit that will set it as something else?

---

### Post by videodrome on 2008-06-13
Can you go into the Synaptic Package Manager (start menu/system/) and uninstall it from there? Just search for "screensaver" and see which ones are installed.

---

### Post by greyfox1 on 2008-06-13
I recall this same thing happened to me a while back on Ubuntu Gutsy.  IIRC it only happened once, and I was able to change to another screen saver.  Weird.  Maybe some sort of OpenGL problem?  This is one of the 3d-rendered screensavers.

---

### Post by systemshock869 on 2008-06-14
i searched through the synaptic package manager, and reinstalled everything that had anything to do with a screensaver.  no luck so far.  i may end up just re-installing xubuntu.  i'd rather figure this out the hard way though.  to get some experience.
any other ideas?
is there an error log file i could print on here for you guys to check out?

thanks alot by the way :)

---

### Post by x1a4 on 2008-06-14
Hi,

Remove the file ~/.xscreensaver, then start the Screensaver Preferences.  This will reset it to defaults.

---

### Post by Chainz on 2008-06-15
As for me same happens with "Molecule".
Both in preview or when screen saver starts after idle time.

it has probably something to do with: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

---

### Post by systemshock869 on 2008-06-16
> **x1a4 said:**
> Hi,

Remove the file ~/.xscreensaver, then start the Screensaver Preferences.  This will reset it to defaults.

sorry i'm sort of a noob. what directory does the ~/ signify?

---

### Post by Chainz on 2008-06-16
> **systemshock869 said:**
> sorry i'm sort of a noob. what directory does the ~/ signify?

~ is representation (or kind of shortcut) to your home directory (i.e. /home/user/).
If you just type ~ (tylda) in a Nautilus (or actually any other application as a path) it will automatically bring you you home directory.

But why don't you just try:
> Go into the Synaptic Package Manager (start menu/system/) and uninstall it from there. Just search for "screensaver" and see which ones are installed ;)

---

