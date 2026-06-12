---
title: "custom xinitrc HELP"
date: 2008-05-02
forum: Desktop Environments
---

### Post by max_power on 2008-05-02
Objective: after boot, automatically login then start a program  (Wahcade a MAME front end) with out starting XFCE. In other words, boot into Wahcade without having to login first.

Can anyone give me a hand with this?

Thanks

---

### Post by kerry_s on 2008-05-02
xinitrc runs after startx, for what your talking about, you'd have to look at the upstart events. also you would need to start some kind of wm for the program to run on, assuming it's a gui program.

sorry, that's all i can offer. i use debian, in debian i would tell you to use rungetty for auto log in, ~/.bash_profile to startx, then you can use ~/.xinitrc to start the wm and then program.

---

### Post by kerry_s on 2008-05-02
sorry, i'm over thinking it. here's what i would suggest. install openbox(sudo apt-get install openbox) that gives you a blank wm, set gdm to start openbox(select openbox in the session menu) setup the auto login in gdm. then just setup the startup script to start your program, **red squirrel** can help you with that, i haven't used openbox in ages.

sorry about that, i haven't used a login manager in ages either. :)

---

### Post by urukrama on 2008-05-04
> **kerry_s said:**
> sorry, i'm over thinking it. here's what i would suggest. install openbox(sudo apt-get install openbox) that gives you a blank wm, set gdm to start openbox(select openbox in the session menu) setup the auto login in gdm. then just setup the startup script to start your program, **red squirrel** can help you with that, i haven't used openbox in ages.

I'm not sure if this is the advice the OP was looking for, but if it is, here is how you do it:

If you install Openbox from the repos or compile from source, you should have those session menus automatically in place. In case you do want to create them yourself, make sure they start "openbox-session" (should be in /usr/bin/openbox-session) and not just "openbox". Openbox-session launches Openbox and whatever you specify in the autostart file (the default is in /etc/xdg/openbox/autostart.sh ; copy that to ~/.config/openbox/)

Openbox is light, but there are lighter window managers around (e.g., twm).

---

### Post by Son of Silas on 2008-05-08
> **urukrama said:**
> I'm not sure if this is the advice the OP was looking for, but if it is, here is how you do it:

If you install Openbox from the repos or compile from source, you should have those session menus automatically in place. In case you do want to create them yourself, make sure they start "openbox-session" (should be in /usr/bin/openbox-session) and not just "openbox". Openbox-session launches Openbox and whatever you specify in the autostart file (the default is in /etc/xdg/openbox/autostart.sh ; copy that to ~/.config/openbox/)

Openbox is light, but there are lighter window managers around (e.g., twm).

OK, I am trying to do exactly the same as max_power, in that I want to boot straight straight to Wah!Cade.

I have installed openbox but I am really new to this. I have been using Ubuntu for about 6 months, I only started working with Xubuntu this week and I'm really struggling. Can you break this down into really easy, bite size steps for me?

I have opened the /xdg/openbox/autostart.sh file, but don't know what to put in it to launch Wah!Cade (from a terminal i would just type wahcade, do i just type that at the end of the file then copy it to ~/.config/openbox/ ?)

---

### Post by urukrama on 2008-05-08
> **Son of Silas said:**
> I have opened the /xdg/openbox/autostart.sh file, but don't know what to put in it to launch Wah!Cade (from a terminal i would just type wahcade, do i just type that at the end of the file then copy it to ~/.config/openbox/ ?)

The commands you add to the autostart file are the same as the ones you would use to launch it from a terminal, followed by & (this is important, otherwise nothing after it will launch!). So if you launch Wah!Cade with the command wahcade, you would add the following:

```
wahcade &
```

I wrote about the autostart file also in my Openbox guide (link in signature). Perhaps that will help as well.

---

### Post by Son of Silas on 2008-05-08
> **urukrama said:**
> The commands you add to the autostart file are the same as the ones you would use to launch it from a terminal, followed by & (this is important, otherwise nothing after it will launch!). So if you launch Wah!Cade with the command wahcade, you would add the following:

```
wahcade &
```

I wrote about the autostart file also in my Openbox guide (link in signature). Perhaps that will help as well.

Thanks for that, I think I'm getting somewhere now.

I have a question though. I can make the PC automatically login to xfce, how do i make it login to the openbox session by default instead?

When I select openbox session from the login window preferences, it ignores that and still boots into xfce. If i turn off auto login, and change the session to openbox session at the login prompt then it launces openbox OK.

What am I missing here? how do i make openbox the default session AND login automatically?

Also, How do I change the screen resolution of the openbox session? I want it to run at 800x600.

---

### Post by max_power on 2008-05-08
Hey Son of Silus thanks for picking up my thread.

could you please tell how you were able to auto login into xfce?

---

### Post by Son of Silas on 2008-05-09
> **max_power said:**
> Hey Son of Silus thanks for picking up my thread.

could you please tell how you were able to auto login into xfce?

Boot into xfce then:
Applications > Settings > Login Window
Type your Password
Click on the Security Tab
Select the Enable Automatic Login check box

I also modified the screen resolution by adding the line 
> xrandr -s 800x600 & to my autostart.sh

To fix the fact that the xfce desktop launched despite having selected 'openbox session' in the Default Session Login Window Preferences, I followed the following steps:

Before setting auto Login, Logout of Xfce
Select the sessions button from the login screen
change the session to open box session
login
When prompted select the option to make openbox your default session
once the blank openbox session has loaded, right click your mouse  on the desktop and select exit
At the login prompt select sessions again and choose xfce session
When prompted select the option to change sessions for this time only
When xfce has loaded turn on auto login as described above
reboot

Assuming that > Wahcade & is in your autostart.sh the PC will reboot into Wah!cade

---

