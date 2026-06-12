---
title: "Some apps only start interminal with sudo and DBus errors"
date: 2015-08-04
forum: Desktop Environments
---

### Post by Jonners59 on 2015-08-04
I am having some probs with my install.  I do not know whether it is all the result of me doing something silly trying to fix my Screenlets problem, following a solution I found - changed the entire /usr/bin ownership...  (I have resolved that) of if some of this was occuring before.

I can not launch users-admin at all, gparted and synaptic have to start in a terminal...  The output I get says, for instance.
```
sudo synaptic

(synaptic:9193): IBUS-WARNING **: The owner of /home/baronipc/.config/ibus/bus is not root!
Discarding: 1 over 9
Discarding: 2 over 9
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
```

In synaptic I can not get in to "Repositories" and in Ubuntu Software Centre, apps will not install.

I have purged ibus, liboobs-1-4 (don't think it was installed, but I got the instruction from an old thread), liboobs-1-5 and re-installed

```
ls -l /usr/bin/sudo
```
[HTML]-rwsr-xr-x 1 root root 151072 Mar 12 16:10 /usr/bin/sudo[/HTML]

```
ls -la /usr/bin | grep -v "root *root"
```
[HTML]total 355308
-rwxr-xr-x  1 root daemon     55560 Jan 10  2015 at
-rwxr-xr-x  1 root tty        14688 Dec 10  2014 bsd-write
-rwxr-xr-x  1 root shadow     55128 Apr 20 19:05 chage
-rwxr-xr-x  1 root crontab    36136 Oct 27  2014 crontab
-rwxr-xr-x  1 root mail       14856 Dec  7  2013 dotlockfile
-rwxr-xr-x  1 root shadow     23424 Apr 20 19:05 expiry
-rwxr-xr-x  1 root mail       14592 Dec  3  2012 mail-lock
-rwxr-xr-x  1 root mail       14592 Dec  3  2012 mail-touchlock
-rwxr-xr-x  1 root mail       14592 Dec  3  2012 mail-unlock
-rwxr-xr-x  1 root mlocate    39520 Nov 18  2014 mlocate
-rwxr-xr-x  1 root ssh       350360 Apr  9 10:48 ssh-agent
-rwxr-xr-x  1 root tty        27368 Feb 23 08:21 wall[/HTML]

```
 ls -la /usr/bin | grep -v "rwxr-xr-x\|^l"
```
 [HTML]total 355308
-rw-r--r--  1 root root         271 Aug  3 07:12 screenlets.old
-rwsr-xr-x  1 root root      151072 Mar 12 16:10 sudo[/HTML]

```
ls -ld /usr /usr/bin
```
[HTML]drwxr-xr-x 11 root root  4096 May 14 08:45 /usr
drwxr-xr-x  4 root root 86016 Aug  4 09:02 /usr/bin[/HTML]

Current version: 15.04 and up to date.

Any help, please

---

### Post by kerry_s on 2015-08-04
still have your installer ?

you could try booting live, copy the live /usr/bin to the disk /usr/bin replacing whats on the disk.

personally if i screwed up that bad, i'd just reinstall, no telling whats going to creep up.
anything using root should be used with caution, changing a file okay, screwing with a whole folder, your inner voice should have been screaming noooo
lol

---

### Post by Jonners59 on 2015-08-04
:-) it kinda was screaming, but I see from searching it happens all the time and most, like me in error, or following an "experts" advise.

Not sure one could just copy over the whole directory as there are items added by other apps.

I seem to be making progress.  just ran a cmd
```
ll /usr/lib/dbus-1.0/dbus-daemon-launch-helper
```

```
sudo chmod u+s /usr/lib/dbus-1.0/dbus-daemon-launch-helper
```

```
ll /usr/lib/dbus-1.0/dbus-daemon-launch-helper
```

Which have made a huge difference.
Can now access the Repositories in Synaptic, though I can't change anything
Can open Users and Groups now
Ubuntu Software Centre starts to download before complaining....

I had also run these earlier, but not sure what result they had, if any.
```
ls -la /usr/bin | grep -v "root *root"
```

```
ls -la /usr/bin | grep -v "rwxr-xr-x\|^l"
```

```
ls -ld /usr /usr/bin
```

Still a little way to go.  There is still at least one thing not correct to get these other issues.

---

### Post by Jonners59 on 2015-08-14
This didn't fully fix, so I rebuilt the machine:
Copied usr and etc to a folder in Home which was separately mounted anyway.
Made a backup of Synaptic Package Manager to my Home folder - File - Save Markings and don't for get to tick "Save Full State Not Only Markings"

Then rebuilt creating a separate dir for /usr and using the existing separate home folder (not tick the format option) and ensuring I used the same username

After rebuild and before I rebooted:
I updated the /etc/fstb with the backed up copy - alterations I had made
I updated the /etc/samba/smb.conf with the backed up copy - alterations I had made
I updated the /etc/samba/smb.conf with the backed up copy - alterations I had made
Reinstated the backup of Synaptic Package Manager from the back up I had made and copied the Keys and Sources from etc/apt/sources.list, /etc/apt/sources.list.d and /etc/apt/trusted.gpg.d from the old back up to the new, checking for duplicated of course.

Then rebooted with fingers crossed.

I then
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

And it should all work and look like it did before, but without all the annoying problems.... mine did.

---

