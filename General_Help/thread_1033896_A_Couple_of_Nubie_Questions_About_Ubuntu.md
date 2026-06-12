---
title: "A Couple of Nubie Questions About Ubuntu"
date: 2009-01-07
forum: General Help
---

### Post by ram2008 on 2009-01-07
****I'm new to Ubuntu so I hope these questions don't sound stupid.  Anyway, I have a guest account on my Ubuntu system for a friend who uses my computer from time to time.  I noticed that the icons for three of my Windows drives are on the desktop of the guest account.  I don't want that person to have access to those drives.  How do I remove them from the guest desktop (and yet keep them on my desktop)?  I tried to remove them but was told that only root could remove them.

Second question is about my screen setup.  Each time I boot Ubuntu I have to reset the screen refresh rate for my monitor to restore the screen size.  For some reason the X config file is not saving it.  When I try to save the value at the NVIDIA X Server settings page, I get the message "Unable to create new X config backup file '/etc/X11/xorg.conf.backup".

Thanks for any help you can give to help me resolve these issues.

---

### Post by collinp on 2009-01-07
> **ram2008 said:**
> I'm new to Ubuntu so I hope these questions don't sound stupid.  Anyway, I have a guest account on my Ubuntu system for a friend who uses my computer from time to time.  I noticed that the icons for three of my Windows drives are on the desktop of the guest account.  I don't want that person to have access to those drives.  How do I remove them from the guest desktop (and yet keep them on my desktop)?  I tried to remove them but was told that only root could remove them.

Second question is about my screen setup.  Each time I boot Ubuntu I have to reset the screen refresh rate for my monitor to restore the screen size.  For some reason the X config file is not saving it.  When I try to save the value at the NVIDIA X Server settings page, I get the message "Unable to create new X config backup file '/etc/X11/xorg.conf.backup".

Thanks for any help you can give to help me resolve these issues.

I cannot answer your first question, but to your second one, run in terminal:
```
sudo nvidia-settings
```
then do the changes you need and save.

---

### Post by simtaalo on 2009-01-07
> **ram2008 said:**
> 
Second question is about my screen setup.  Each time I boot Ubuntu I have to reset the screen refresh rate for my monitor to restore the screen size.  For some reason the X config file is not saving it.  When I try to save the value at the NVIDIA X Server settings page, I get the message "Unable to create new X config backup file '/etc/X11/xorg.conf.backup".

Thanks for any help you can give to help me resolve these issues.

press alt+f2 then type "gksudo nvidia-settings" it will usually autocomplete. you should have no problems saving changes now. the problem was that you weren't running the settings program as a root-user therefore you didn't have sufficient authority to make the changes to the xorg.conf. i made the same mistake when i first switched over, drove me mad for a while lol.

---

### Post by ram2008 on 2009-01-08
Hi guys and thanks for your help.  It solved the problem I was having at the time.  I posted a reply here yesterday but for some reason it isn't here.  That's a bit puzzling.  It was to thank you for your help.

Now, however, I'm having other display problems.  From the very little I know about Ubuntu, it sounds like I'm having a problem with the X server.  For example, when I call up a terminal, all I see on the screen is a white square where the terminal should be.  Also the top bar on all windows is missing.  For example, for Firefox that blue bar (at least here) at the top that includes the X at the upper right and the Maximize and minimize boxes are all missing since the whole bar is gone.  Consequently if I want to close Firefox I have to go to File and choose Exit or Close.  If the window doesn't have a File menu, then I can't close it at all!  What does that sound like to you?  This just started a couple of nights ago.

---

### Post by jskandhari on 2009-01-08
incase you have compiz as a windows binder .. just restart "gdm" gnome desktop manager in the terminal and it should be done. and place it in the startup

---

### Post by ram2008 on 2009-01-09
Hi jskandhari,

Thanks for responding to my post.  I think you were responding to my last post about video display problems, but being very new to Ubuntu, I didn't quite understand what you were asking me to do.  The problem has since been resolved but I would still like to know exactly what you were suggesting.  If you don't mind explaining it in nubie language, I would much appreciate it.  It might be useful in the future.  Turns out that the video display problem that I posted about was caused by a particular setting for the NVIDIA card.  I had opted just a couple of days ago, maybe even yesterday (the day the problem first showed up), to turn on visual effects.  Once I turned them off, the problems went away.

---

### Post by mssever on 2009-01-09
> **ram2008 said:**
> I'm new to Ubuntu so I hope these questions don't sound stupid.  Anyway, I have a guest account on my Ubuntu system for a friend who uses my computer from time to time.  I noticed that the icons for three of my Windows drives are on the desktop of the guest account.  I don't want that person to have access to those drives.  How do I remove them from the guest desktop (and yet keep them on my desktop)?  I tried to remove them but was told that only root could remove them.
I'll take a crack at your first question. Assuming those Windows partitions are on internal hard drives, they're probably listed in /etc/fstab. To edit fstab, hit <Alt>F2, then type ```
gksudo "gedit /etc/fstab"
```There are two things you can do to thwart snooping guests:

[LIST=1]
[*]Change the mount point away from the default. I'm actually not sure if this will work, but it's worth a try. (I keep my desktop icons hidden, so I really don't know what's on the desktop of a default system.) To change the mount point, edit the second field of the relevant line(s). The mount point MUST exist and be a directory, and it SHOULD be empty.
[*]Change the permissions, so that even if guests can see an icon, they won't be able to see its contents. This assumes that you're the only person who has a legitimate need to see the drives' contents.
[LIST=1]
[*]First, find your uid and gid. Both are probably 1000, but to be sure, issue the command "id".
[*]In fstab, locate the options field for each partition. It's the fourth field.
[*]Append the following, WITHOUT SPACES, to the existing options. If your uid or gid is different from 1000, make the appropriate change:```
,uid=1000,gid=1000,umask=007
```
[/LIST]
If you have multiple accounts that have a legitimate need for access to those partitions, create a group for that purpose, add the authorized users to that group, and substitute that group's gid above.
[/LIST]
Once you've saved your changes, you'll have to remount your partitions in order for the changes to take effect. For each partition: ```
sudo umount /path/to/previous/mount/point
sudo mount /path/to/new/mount/point
```(If you didn't change the mount points, then both paths will of course be the same.)

Hope this helps. By the way, to understand what I did permissions-wise, be sure to read up on Linux permissions and umasks.

---

