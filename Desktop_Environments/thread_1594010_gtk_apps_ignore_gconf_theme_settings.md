---
title: "gtk apps ignore gconf theme settings"
date: 2010-10-11
forum: Desktop Environments
---

### Post by Correnos on 2010-10-11
I am having theme problems with a new Ubuntu 10.10 install. The theme settings in gconf are being ignored. Once I logged in for the second time into my ubuntu installation, I was greeted with the Raleigh theme in all applications except Appearance Preferences. I can remove .gconf to have my next login reset to the Ambience theme, but the one after that switches right back to raleigh and the gtk default icon theme. I am using an nvidia graphics card with proprietary drivers. This problem is not present on my laptop (also a new install of 10.10). Does anyone have a solution?

---

### Post by ankspo71 on 2010-10-12
Hi,
Open a terminal and run this command:
```
gnome-settings-daemon
```
Does that fix the theme for you?
If so, this is because your desktop starts before gnome-settings-daemon does(the timing is off). Unfortunately, that won't keep the theme applied after you restart. I'll go hunt for the solution... I remember seeing it a while ago.

Edit:
Here is one you can try to see if it helps. See the pst made by "serfcx"
[http://ubuntuforums.org/archive/index.php/t-688522.html](http://ubuntuforums.org/archive/index.php/t-688522.html)
This wasn't the post I was thinking of though... I'm still looking :)

---

### Post by ankspo71 on 2010-10-12
Hi,
If my above advice didn't help much, then this advice should help.

Open up your text editor and paste this code into a new document
```
#!/bin/sh
sleep 2 && gnome-settings-daemon ;
```
Save this file as "apply-theme.sh" and save it inside your home folder.

Next go to System > Preferences > Startup Applications.
Create a new entry so that script to be executed on startup:
Name = Apply Themes
Command = sh /home/yourname/apply-theme.sh

Don't forget to include the "sh" in the beginning of the command, and also change "yourname" to your own ubuntu username.

Log out then log back in several times to see if the problem ever comes back. The "sleep 2" amount can be adjusted too. The amount is measured in seconds.

The past few days I have been having a similar problem (sort of). My themes load correctly everywhere except nautilus and the right click menu on the desktop, which is also nautilus. The script above hasn't fixed my problem though.

---

### Post by Correnos on 2010-10-12
Actually, I reinstalled again (this was a new install) and the problem is not present. Odd. The only setting I think I changed was to set ext4 instead of btrfs as root, but that doesn't make much sense as my laptop is doing fine with btrfs. Strange all around.

---

### Post by mlentink on 2010-10-14
> **ankspo71 said:**
> The past few days I have been having a similar problem (sort of). My themes load correctly everywhere except nautilus and the right click menu on the desktop, which is also nautilus. The script above hasn't fixed my problem though.

As of today, I have the exact same problem, except for the fact that my desktop icons are also not themed. Since afaik the only update i applied today, I&#314;l revert to the previous kernel and see what happens.

---

### Post by Jungleboss on 2010-10-15
I also have this exact problem. I had to add a "killall -9 gnome-settings-daemon" to the start of my script as well to get it to work

But the problem persists with Nautilus for me as well :( Awaiting a solution for this in this thread ;)

I didn't have this problem before I installed the proprietary Nvidia drivers.

---

### Post by Jungleboss on 2010-10-16
This worked for me to restore the theme to Nautilus as well

[http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4](http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4)

---

### Post by ankspo71 on 2010-10-16
> **Jungleboss said:**
> This worked for me to restore the theme to Nautilus as well

[http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4](http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4)

Interesting... Thanks! The first command works for me just fine. :)

---

### Post by gesquive on 2010-10-18
Don't know if this will help anyone but I just ran

```
sudo apt-get install --reinstall gnome-settings-daemon
```

Then restarted and my settings have been working like normal since then.

---

### Post by sagara on 2010-11-02
> **gesquive said:**
> Don't know if this will help anyone but I just ran

```
sudo apt-get install --reinstall gnome-settings-daemon
```

Then restarted and my settings have been working like normal since then.

This worked like a charm for me thanks! =D
I'll let the peeps over at the [[COLOR="Red"]bug tracker[/COLOR]]("https://bugs.launchpad.net/bugs/649809") know about this.

---

