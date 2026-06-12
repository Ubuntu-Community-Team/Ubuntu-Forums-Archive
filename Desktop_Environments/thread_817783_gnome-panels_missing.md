---
title: "gnome-panels missing"
date: 2008-06-03
forum: Desktop Environments
---

### Post by jimmy2975 on 2008-06-03
Hi, 

I am using the 8.04 and did a update a couple od days back. TOday, my gnomepanes are missing. killall gnome-panel does nothing. I have read through the forums and looks like a many others have had the same problem. I have removed and re-installed the gnome-panel w/o any success. How do I get back my panels? Any comments/suggestions are appreciated! 

Thanks
Jimmy

---

### Post by jimmy2975 on 2008-06-04
can someone atleast give me some clues as to where to start for a fix. I have removes ubuntu-desktop and reisntalled and still have the problem.!!Plz help

JImmy

---

### Post by velusoundar on 2008-06-04
$sudo apt-get install gnome-panel
$gnome-panel


this works for me.

---

### Post by Sealbhach on 2008-06-04
I had that problem a few days ago.

Here's what fixed it for me:


[http://ubuntuforums.org/showthread.php?t=812972](http://ubuntuforums.org/showthread.php?t=812972)

```
sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by abiezerm on 2008-06-04
> **velusoundar said:**
> $sudo apt-get install gnome-panel
$gnome-panel


this works for me.

that works for me..

i unistall evolution and looks like one dependency wass gnome-panel.

luck!

---

### Post by primowalker on 2008-06-04
$sudo apt-get install gnome-panel
$gnome-panel

This worked for me too.  And it disappeared after removing evolution.

---

### Post by drumanart on 2008-06-04
I have a similar problem. When I start the GNOME session I get all the folders and files from my home/martin folder on my Desktop. The failer showed up  when I tried to remove a file typing>** rm -r /home/martin/Desktop reaktor_5_keygen.exe**.

I tried to reinstall the GNOME DESKTOP

$sudo apt-get update
$sudo apt-get install gnome-panel

without success.

---

### Post by OmniCloud on 2008-06-04
Guys, when removing things, Synaptic will tell you everything else that depends on the file your removing. 

Some apps that are installed by default--like Evolution--isn't a wise thing to remove if you don't know what your doing yet. 

Read wiki, understand that just because a program is called "music player" doesn't mean it consist of files that only affect your system when playing music? 

I'm still a newbie myself, but you do have to take a little bit of time to realize your not in Windows anymore.

If it's a simple error with your panel, like it's crashing, you could always just delete the configuration and it'll fix itself.

If your panel is gone, then it's likely you removed it by uninstalling an application on your system.

---

### Post by drumanart on 2008-06-04
Thanks, you are perfectely right, but if you could be so kind and telling me where to find the configuration file that has to be erased I would be very pleased.

---

### Post by jimmy2975 on 2008-06-04
I have tried everything.

gnome-panel restart
killall gnome-panel

Removed ubuntu-desktop and reinstalled
My system is upto date.

Right now I have the panels and are behaving the way it should. The panels did not come up 4 out of 6 reboots !!!! I have no clue what is happening. Any idea?

I have even removed gnome and re-installed it. 

Thanks
Jimmy

---

### Post by OmniCloud on 2008-06-04
> **drumanart said:**
> Thanks, you are perfectely right, but if you could be so kind and telling me where to find the configuration file that has to be erased I would be very pleased.

[http://forums.fedoraforum.org/showthread.php?t=177734](http://forums.fedoraforum.org/showthread.php?t=177734)

There's a link in my post with users who had the same problem...

Like i said, this method is only if your panel is crashing. By removing the config (.gconf .gconfd) you reset your panels. And they go back to default of when you first installed your OS. 

Jimmy may be having a different problem altogether tho. 

Here's a simple test. Make a new user account. and then check to see if the panel is funny;)

---

