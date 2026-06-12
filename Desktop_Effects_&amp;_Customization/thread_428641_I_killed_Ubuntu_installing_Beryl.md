---
title: "I killed Ubuntu installing Beryl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by psyopper on 2007-04-30
Help!

I was following the Beryl installation guide here:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL")

I downloaded everything as directed and it looked like it all installed just fine. 

I decided on the alternate startup option because I don't plan on running any OpenGL programs:

> For GNOME: Instead of adding a separate desktop session, you could alter your standard X session. This is not recommended for most users (see above). It might be useful however if you do not want to set up a separate X session for Beryl for some reason.

So I edited  /etc/gdm/gdm.conf-custom and added the following at the bottom (as recommended):

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

I saved, closed and restarted my computer. 

Now I can't boot into Ubuntu. 

When I restart the computer the splash screen comes up and the progress bar moves forward. Right when the login screen *should* open my monitor flickers black then goes to a black screen with red white and blue writing saying something along the lines of "X Server could not start" Then I get dropped to a terminal with a blinking cursor.

I know it's my fault, I'm a *very* new Linux user, this is my first experience with Linux, I just installed Ubuntu two days ago. 

What should I do? Is there some way I can edit the /etc/gdm/gdm.conf-custom from the terminal to remove what I did so I can get back into Ubuntu? Should I just reinstall Ubuntu?

---

### Post by aidanr on 2007-04-30
hit ctrl+alt+F6, login and type

```
sudo nano /etc/gdm/gdm.conf-custom
```

remove the stuff that you added, save and exit and type 

```
sudo reboot
```

---

### Post by psyopper on 2007-04-30
Thanks for the fast reply aidanr!

First, I'll be more specific about what I am seeing. When I drop out of the normal boot sequence I get a blue screen with a red border and the following message:

Failed to start X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? [yes] [no]

I select no and get another screen similar in appearance to the one above:

X Server is now disabled. Restart GDM when it is configured properly [OK]

I select OK and get dropped to a black screen similar to a terminal. It's really more like old school DOS in appearance. It has a list of sequences that it properly loaded. The final item on the list is:

* Running local boot scripts (/etc/rc.local)  OK
_


The underscore above is the cursor I get, at a fast blink. There is nothing preceeding the cursor.

I CAN type at the cursor but hitting ctrl+alt+F6 does not get me a login. And trying:

sudo nano /etc/gdm/gdm.conf-custom

followed by [Enter] does absolutely nothing.

So I thought about it for a minute and decided to boot from the live CD. Once it loaded I browsed over to the installed etc/gdm/gdm.conf-custom and it did not appear to contain the changes I thought I had made. I checked etc/gdm/gdm.conf out of curiosity and they weren't there either.

So... I thought I may as well reinstall, two days isn't too much to loose, especially on a learning curve. But when I tried the installer it moved me to the disk partitioner and wouldn't let me install to the partition I had created.

I'd rather fix the problem because it's the better option for actually LEARNING Linux. Is there anything I can do?

Thanks in advance for any assistance!

---

### Post by kpolice on 2007-04-30
That's why running as a separate session is a better option :P , it's easier to fix it.

Just undo every change you made but instead of using a GUI you will have to use an editor like vi or nano.

---

### Post by aidanr on 2007-04-30
boot up in recovery mode (hit escape when grub is loading)

---

### Post by psyopper on 2007-04-30
> **kpolice said:**
> That's why running as a separate session is a better option :P , it's easier to fix it.



Yeah, I recognize that now... :) 

> **kpolice said:**
> Just undo every change you made but instead of using a GUI you will have to use an editor like vi or nano.


I'd like to do just that, but remember, I'm new to Linux - I have no idea HOW to do that...

[quote=aidnar]boot up in recovery mode (hit escape when grub is loading)[/quote]

Sigh... no joy. I hit escape and I get the same thing as described above, except that when it drops me out to the shell I get:

]^ _

where the underscore is the fast blinking cursor. 

I also tried Ubuntu (recovery mode) from the multi-boot menu and I get "invalid string" and it halts.

---

### Post by psyopper on 2007-04-30
RESOLVED

I resolved this by booting to the Live CD, going into the terminal and using:

sudo gedit

This opened gedit with Super User powers. I did manage to find the correct /etc/gdm/gdm.conf-custom and drag/dropped it into gedit. 

The trick is that when browsing Places/System in Ubuntu the *currently running* OS will display as "filesystem". Since I was browsing on the hard drive I had to identify it as the volume size. 

Here's the kind of creepy part - Super User on the Live CD does not have a password, thus I was able to edit the otherwise restricted file. Actually, I see this as being quite handy for problems in the future...

---

