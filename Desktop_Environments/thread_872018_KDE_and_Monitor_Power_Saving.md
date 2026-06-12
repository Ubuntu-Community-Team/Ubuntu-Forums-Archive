---
title: "KDE and Monitor Power Saving"
date: 2008-07-27
forum: Desktop Environments
---

### Post by drumz on 2008-07-27
(I posted on this before, unfortunately I can't update that original posting so pardon me for starting a new thread on the topic.)

I have not been able to get the power saving settings for my monitor (KDE menu -> System Settings -> Monitor & Display -> Power Savings) to stay set across logouts.

Originally, it just wouldn't stay set so recently I completely deleted the .kde directory in my home directory and started over from scratch.  That did the trick, but only for a few days.  Now it's back to the same thing - make the change and it works during that login session but as soon as I log out it's reset to being 'off'.

Has anyone else experienced this, or does someone have a suggestion on how to trace what's going on so I can get it set permanently?

Thanks!

---

### Post by warp99 on 2008-07-27
The settings for the monitor are kept inside the file in your home directory under '~/.kde/share/config/displayconfig.rc'. Either the permissions for the file are incorrect or the file does not have read/write settings. Open a terminal and issue the following:

```
 ls -ls ~/.kde/share/config/displayconfigrc
```

it should return something like this:

```
4 -rw------- 1 user user 176 2007-10-10 10:13 /home/user/.kde/share/config/displayconfigrc

```

now the 'user' should be your user name while the permissions 'rw' should be the same. If not post the output to this thread plus the output of the following:

```
ls -als ~/
```

You may have a problem with permissions and/or ownership throughout your home directory.

---

### Post by drumz on 2008-07-27
Thanks for replying....

The permissions on the file:

[FONT="Courier New"]ls -ls ~/.kde/share/config/displayconfigrc
4 -rw------- 1 username username 175 2008-07-27 15:09 /home/username/.kde/share/config/displayconfigrc[/FONT]

My home directory is also backed up automatically to another system when I log out (~/.kde/shutdown/backup.sh).  I looked at the backup and the file there has the proper settings indicating that it IS saving my changes to the file and they are staying put throughout the logout process.  It almost appears that something is resetting it on login...

---

### Post by warp99 on 2008-07-27
> **drumz said:**
>   It almost appears that something is resetting it on login...

Until you track down the problem you can edit the file and add the following parameters under [Screen0]:

```
dpmsEnabled=on
dpmsSeconds=3600

```

That will set the time to 1 hour. You can set time according to the times listed in the GUI dialog, just make sure it's in seconds. After saving the file don't logout but instead press 'crtl-alt-backspace' to reload X-server. See if the settings persist.

---

### Post by drumz on 2008-07-27
ironically enough i was just editing my previous post when you replied....

The file IS being preserved across logout/logins and reboots.  it appears that whatever process reads the file and does handles the power for the monitor isn't reading the file or starting.

Between logins if I go into the power saving panel nothing is set, even though the file contains the settings from the last time I set them.  Once I set them they work only for that session and are still set if I go back in during that session (but not if log out/in again).

Thanks for your help!

---

### Post by warp99 on 2008-07-27
> **drumz said:**
> 
Between logins if I go into the power saving panel nothing is set, even though the file contains the settings from the last time I set them.  Once I set them they work only for that session and are still set if I go back in during that session (but not if log out/in again).

Thanks for your help!

It could be that they are not being preserved because X-server does not recognize that the monitor is DPMS capable. I would suggest that you edit you xorg.conf and add the following within the "Monitor" portion of the file:

```
Option "DPMS" "true" 
```

So the section looks something like this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
       Option          "DPMS" "true"
EndSection

```

If that does not work you can always change the file ownership to 'root' that way the file will never be overwritten when you login.

---

### Post by drumz on 2008-07-27
The DPMS option was already set in the xorg.conf file...

Well, at least I know it's keeping my changes in the display config file....I just need to figure out what happens after making the changes on the power saving panel.  I did a 'ps -ef' before and after and there weren't any changes, so it doesn't appear to be restarting any particular process....

---

### Post by warp99 on 2008-07-27
> **drumz said:**
> The DPMS option was already set in the xorg.conf file...

Well, at least I know it's keeping my changes in the display config file....I just need to figure out what happens after making the changes on the power saving panel.  I did a 'ps -ef' before and after and there weren't any changes, so it doesn't appear to be restarting any particular process....

Well the setting for DPMS are set with a program called xset. If you open a terminal and type 'displayconfig' then change the settings and apply you'll see in the terminal xset resetting the time out. So for some reason either xset in not running during login or failures to set the parameters. You can also look inside your ~./xsession-errors log to set if there is a problem during login. 

If you're running another program, xscreensaver for example, which uses xset that program may be turning off the DPMS as suggested in this post:

[http://ubuntuforums.org/showthread.php?t=203449](http://ubuntuforums.org/showthread.php?t=203449)

The last thing you could do is make a script for xset to turn on the features during login with something like this:

```
#!/bin/bash

/usr/bin/xset dpms 3600 3600 3600


```

---

### Post by drumz on 2008-07-28
Thanks for the xset command, worse case is I'll just use a script on login to set it like you suggested.

I looked in the .xsession-errors file, and there are some.  I cut out a bunch of non-related log messages at the top of the file, so the first item of interest is the 'Could not find 'guidance-power-manager.py' executable' line.

Then I cut out a bunch of other lines, including some Evolution realated ones (it's set by my session to auto start on login), which is immediately followed by a series of 'X Error: ...' messages which end the file.

The 'guidance-power-manager.py' exists although it's not in my path.  'guidance-power-manager' is though, and it's a regular shell script which launches the python script (which does exist in the place the shell script expects it to be).  The X errors I haven't researched yet...

[FONT="Courier New"]...(removed lines here)...
DCOP Cleaning up dead connections.
Could not find 'evolution-exchange-storage' executable.
Could not find 'guidance-power-manager.py' executable.
evolution-alarm-notify-Message: Setting timeout for 21717 1217304000 1217282283
...(removed lines here)...
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0xa00027
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2c01171
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a005bc
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a005bc
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2a005bc[/FONT]

---

### Post by warp99 on 2008-07-28
Well at least you found the cause of the problem. You should open a terminal and run the 'guidance-power-manager' if you have a laptop to see if there is an error calling the script. If there is an error I would try the following:

```
sudo dpkg-reconfigure kde-guidance-powermanager
```

That's the package that includes guidance-power-manager.py. If that doesn't help you could purge and reinstall the package since it has no dependencies:

```
sudo apt-get remove --purge kde-guidance-powermanager && sudo apt-get install kde-guidance-powermanager
```

and if there is still a problem check to make sure all of the important files were installed:

```
sudo dpkg -L kde-guidance-powermanager
```

If everything appears correct but the problem still exist I would search here on the forums, on Google, and over at [launchpad.net]("https://launchpad.net/ubuntu") for 'guidance-power-manager.py' to see if this is a known problem. If nothing exist you can fill out a bug report with some detailed information.

---

