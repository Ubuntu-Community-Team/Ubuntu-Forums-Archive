---
title: "HELP please - can't log in anymore....."
date: 2009-05-10
forum: General Help
---

### Post by heitjer on 2009-05-10
All,
I can't go past the loging screen in ubuntu 8.10 anymore. It boots up and at the screen I type in my user name and my password. It goes briefly into a back screen and then comes back to the login without any error message. If I type a wrong user or wrong password I get the typical message but no message is displayed when I enter my normal user and password.  

[LIST]
[*]I already tried to add a user & psw in GRUP and that did not help. The problem repeats under this user.

[*]Yesterday I did the "change session" at login screen and tried the failsafe terminal - but the problem repeated itself in this terminal. I could not log in. 

[*]I initially thought this was a X problem and used the xfix from GRUB. This was bad and I had to re-establish the old backup X11.conf
[/LIST]

Any idea what this is?


Update:
I just did a "startx" from the root termial in GRUB and got a desktop but got the following error message:

"User Switcher has quit unexpectedly. If you reload a panel object, it will automatically be added back to the panel."

In this desktop I really can't do anything - no mouse/keyboard. So I had to reboot.


Update 2:
From the login screen I did a CTR-ALT-F1 and got the terminal. when I try to log in as one of my users I see that I get the following:

QuadCore login:
ubuntu 8.10 QuadCore tty1

---

### Post by heitjer on 2009-05-10
Although I have a better machine but my problem appears to be the same as this one:
[http://www.youtube.com/watch?v=FyAiZj5WDHo]("http://www.youtube.com/watch?v=FyAiZj5WDHo")

---

### Post by abhilashm86 on 2009-05-10
try recovery mode, did you update kernal version before last login??
if you try in recovery it boots correctly, or try with old kernal login.

If you added any bootsplash images, at GRUB menu, press "e" to edit, then remove boot splash, press enter, then esc key, then "b" to boot, see this works, all the best..........

---

### Post by heitjer on 2009-05-10
Thanks for your reply - 

I tried the recovery mode and chnged back to kernel 2.6.27.-7 from my current .-11 but this die not help. It has the same issues. 

I did not add a boot splash. 

I am reading up as much as I can but seem to be running out of options. Here is another thing that I found:

```
ls -l /dev/null
``` 

returns

```
crw-rw-rw- 1 root root 1,2
``` 

so ths should be OK.

---

### Post by heitjer on 2009-05-10
I have read so many problems with regards to log in and especially GNOME that I am now actually rethinking to change the distro or back to Windows (that would solve a lot of things that I am struggeling with right now). But I made the decision to turn my back on Windows ones and for all. So I need some advice on this please before I really go nuts.

I can not use the "install --reinstall ubuntu-desktop" as I am not on the network and it wil not use this command from the CD. 

When I use a live CD I assume I can not choose to just re-install the GNOME desktop? 

So I assume I have to backup all my data and then completely wipe it out? 

Here is my problem with that - I installed VirtualBox and relicenced my Windows XP in there - I think I will have problems to re-licence it again after this wipe out. Is there a way to save this VirtualBox file (I read somewhere that this is one big file)....need advice. 

Also - I think if I just backup my HOME folder I should have everything - right? What about the hidden folders underneath?

---

