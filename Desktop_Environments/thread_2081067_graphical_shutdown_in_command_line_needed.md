---
title: "graphical shutdown in command line needed"
date: 2012-11-05
forum: Desktop Environments
---

### Post by madnbri on 2012-11-05
Hi,
I want to start the shutdown window from command line, like this:
[IMG]http://i45.tinypic.com/rrqxc6.png[/IMG]
```
$ sudo halt
``` doesn't work correctly (because it couldn't DO), that's why I want to use this form.

Thanks in advance for Your answers.

Regards,
m

PS: Buttons are "Cancel" and "Shutdown" of course

---

### Post by LewisTM on 2012-11-06
That's a dialog produced by the Xfce Session Menu a.k.a. Action Buttons plugin. I don't think you can directly call it from the command line.

You can call the logout dialog with 
```
xfce4-session-logout
```
or shutdown directly (no confirmation) with 
```
xfce4-session-logout --halt
```

Cheers!

---

### Post by madnbri on 2012-11-07
> **LewisTM said:**
> That's a dialog produced by the Xfce Session Menu a.k.a. Action Buttons plugin. I don't think you can directly call it from the command line.

You can call the logout dialog with 
```
xfce4-session-logout
```or shutdown directly (no confirmation) with 
```
xfce4-session-logout --halt
```Cheers!

This is the way. Thank You!

---

### Post by LewisTM on 2012-11-07
Excellent! Please mark as SOLVED.

---

### Post by madnbri on 2012-11-15
> **LewisTM said:**
> Excellent! Please mark as SOLVED.
No! It's a really terrible OS.
I WANT to halt automatically from command line without password! I WANT, because I NEED (I mean crontab and $ ... && sudo halt). It is also impossible still yesterday, because xfce4-session-logout --halt asks the password again. I hate it.
I tried to edit sudoers AGAIN, but it doesn't work of course. No way.
For example:
```
$ sudo visudo
``````
User_Alias SHUTDOWNUSERS = user
Cmnd_Alias SHUTDOWNCNMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
SHUTDOWNUSERS SHUTDOWNCMNDS = NOPASSWD: SHUTDOWNCMNDS
<esc>:wq
visudo: Warning: Host_Alias `SHUTDOWNCMNDS' referenced but not defined

```[COLOR=Red]BUT THERE IS NOT DEFINED OR REFERENCED ANY Host_Alias! I HAVE GOT User_Alias and Cmnd_Alias ONLY.[/COLOR]
Of course I tried any other way using something like this:
```
user ALL=(ALL:ALL) NOPASSWD: ALL
```It asks passwd any way.
Can I get help?

---

### Post by Lars Noodén on 2012-11-15
You seem to have a typographical error.  'SHUTDOWNC**NM**DS' should be 'SHUTDOWNC**MN**DS'

---

### Post by madnbri on 2012-11-15
> **Lars Noodén said:**
> You seem to have a typographical error.  'SHUTDOWNC**NM**DS' should be 'SHUTDOWNC**MN**DS'
No. I've typed here, not copied from sudoers. It is correct there.

---

### Post by Lars Noodén on 2012-11-15
Sorry I missed it the first time around "SHUTDOWNUSERS *SHUTDOWNCMNDS* = NOPASSWD: SHUTDOWNCMNDS" should be "SHUTDOWNUSERS **all** = NOPASSWD: SHUTDOWNCMNDS".  That position / field is for the host name and you have no host alias specification covering "SHUTDOWNCMNDS".

---

### Post by NikTh on 2012-11-15
> **madnbri said:**
> 
I WANT to halt automatically from command line without password! 

Have yout tried this ? => [http://ubuntuforums.org/showpost.php?p=11700789&postcount=3](http://ubuntuforums.org/showpost.php?p=11700789&postcount=3)

Thanks

---

### Post by madnbri on 2012-11-15
> **Lars Noodén said:**
> Sorry I missed it the first time around "SHUTDOWNUSERS *SHUTDOWNCMNDS* = NOPASSWD: SHUTDOWNCMNDS" should be "SHUTDOWNUSERS **all** = NOPASSWD: SHUTDOWNCMNDS".  That position / field is for the host name and you have no host alias specification covering "SHUTDOWNCMNDS".
OK, I've corrected the Host_Alias mistake, but still doesn't work. sudo halt asks password.

---

### Post by Lars Noodén on 2012-11-15
sudo seems to be fussy. Try using the whole path as you have written it in /etc/sudoers when calling shutdown.

```

sudo /sbin/shutdown -k 

```

---

### Post by madnbri on 2012-11-15
> **Lars Noodén said:**
> sudo seems to be fussy. Try using the whole path as you have written it in /etc/sudoers when calling shutdown.

```

sudo /sbin/shutdown -k 

```

Everything is the same: pass needed. (A little comment: gentoo works correctly... ...the linux...)

---

### Post by Lars Noodén on 2012-11-15
Can you copy and paste the exact rules you have in sudoers?

---

### Post by madnbri on 2012-11-15
> **Lars Noodén said:**
> Can you copy and paste the exact rules you have in sudoers?
```

# User alias specification
User_Alias  SHUTDOWNUSERS = user

# Cmnd alias specification
Cmnd_Alias  SHUTDOWNCMNDS = /sbin/shutdown, /sbin/reboot, /sbin/halt

# User privilege specification
root  ALL=(ALL:ALL) ALL ## original root
SHUTDOWNUSERS ALL = NOPASSWD: SHUTDOWNCMNDS

```

---

### Post by Lars Noodén on 2012-11-15
Strange.  If I copy and paste that into /etc/sudoers.d/shutdown, then I can run shutdown via sudo without a password.  In other words, it works for me.  I'm not sure what to suggest.

---

### Post by madnbri on 2012-11-15
> **Lars Noodén said:**
> Strange.  If I copy and paste that into /etc/sudoers.d/shutdown, then I can run shutdown via sudo without a password.  In other words, it works for me.  I'm not sure what to suggest.

I have to thank Your help and patience. I run out of this second one by ubuntu. Installing and setting up of Gentoo is really uncomfortable, but that is still linux, not something like windows - I know the solution: upgrade to gentoo.

Thanks for everything.

---

### Post by madnbri on 2012-11-15
> **madnbri said:**
> I have to thank Your help and patience. I run out of this second one by ubuntu. Installing and setting up of Gentoo is really uncomfortable, but that is still linux, not something like windows - I know the solution: upgrade to gentoo.

Thanks for everything.

Yeees!

[LIST=1]
[*]When I tried to install gentoo, bootup failed. I didn't know why, but this happened earlier also (because of incorrect driver on liveCD for example - no problem), the solution is using systemrescuecd instead of original gentoo installation iso. That one failed also... Ugh!
[*]There is something really strange. Back to xubuntu installation CD, boots up, trying to backup existing system - failure.
[*]Try to clear all and reinstall: boots up, but cannot create new partition table - bang! The original partition table is confused. Where are my partitions? Nowhere, but there are only two of my originals (/dev/sda1 /dev/sda2) and some extras something like *root* stuff, gear, gadget, etc.
[*]I've dusted a very old Debian installer CD, and created the partitions by fdisk of that.
[*]Back to xubuntu installer CD, and installed a completely new system. **Now it works perfect**.
[/LIST]
I have got a new question than:[INDENT]What happened?
[/INDENT]

---

