---
title: "start kdm/gdm/x after unprivlaged user logs in"
date: 2010-09-10
forum: Desktop Environments
---

### Post by SP703 on 2010-09-10
I'm running ubuntu server on a home server which runs samba, ftp, and bittorrent 24/7. there is no need to be using the graphics capabilities of the system by having a desktop environment active 24/7 so to save power when i'm not using the desktop, i stop the kdm/gdm and x. This can be done easily by sudo start/stop kdm/gdm/x etc., but there are users in my home who are unprivileged on this computer but who would still like to use it from time to time and rather than having me login every time and start x for them, I would like to find an automatic solution to the problem.

I tried setuid scripts (which i found out fast didn't work), I tried compiling a small c program (again, setuid then start x) which i couldn't get to work, I also tried looking for a signal to send upstart when a specific user logs in so the appropriate environment could start but couldn't find one. I've only just started getting into upstart scripting and despite what I know, I am still very new to linux so it is quite possible I over looked something or that the problem is much more complicated than i think it is.

any ideas/advice/help is greatly appreciated :)

-s7ar

---

### Post by DemonBob on 2010-09-10
One way to do this, but you will have to set this up per user.

Login as them, and create a .xinitrc file in their home directory


```

nano ~/.xinitrc
```

Add this to the file. 
```
#!/bin/sh
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
# exec ion
# exec jwm
# exec wmaker
# exec startkde
# exec icewm
# exec blackbox
exec gnome-session
# exec startfluxbox
# exec startxfce4
# exec xfce4-session
# exec openbox
# exec startlxde
```


Now we need to make x start on their profile. 

All you have to do here is add the line 'startx' to your '~/.bash_profile' or '~/.profile'. 

```
nano ~/.bash_profile
```

add ```
startx
``` at the bottom of the file. 

Restart the computer and you should now have a console mode login. If you login as the user you followed these steps with it should start gnome. They will still have to login via the console screen, but it should start gnome as soon as they login.

If you add users to this server constantly, you can make the changes under /etc/skel and anytime you create a new user it will create the files automatically. 


It's been a while since i have done this, but it should work.

---

### Post by SP703 on 2010-09-13
Thanks for the reply!

That did seem to be a step in the right direction. When i logged in from the command prompt, KDE did kick in automatically. It started loading but when it reached the last step (where the big blue "K" symbol shows up) it crashed to a black screen with a mouse and loaded Kopete full screen. If I exit Kopete there is just a black screen with an active mouse pointer.

Other interesting side effects were KDE loaded on VT3 instead of VT7 (not a problem, just interesting) and a large amount of out put was printed to tty1. I'll try and get a picture of it to post but it was a bunch of jumbled stuff like the remaining battery power, timed out programs and some other things.

I fixed it by manually killing Xorg from tty2 and then "start kdm" and everything seemed to boot up ok.

I will try and get back here with pictures of the errors.

-s7ar

---

### Post by SP703 on 2010-09-13
[IMG]http://img534.imageshack.us/img534/7476/img1561rn.jpg[/IMG]

so in the broken desktop that comes up, i'm able to use Alt+f2 to launch plasma-netbook. I'm going to try adding plasma-netbook to the programs started in .bash_profile and see how that turns out.

Also there is a picture of some of the output that shows up on tty1. I can't figure out how to get it to go away, even after plasma-netbook is started it keeps printing.

-s7ar

---

### Post by SP703 on 2010-09-14
More info: the shutdown button and the power button pop-up don't work anymore. I'm going to try to find a work around that I used a while ago to fix it. Also every time I shut the computer down I loose all of my settings.

I guess the big question is what is the difference between 'exec startkde' in the .xinitrc file and executing 'sudo start kdm' in the terminal? is there anyway to make 'exec startkde' do everything that 'sudo start kdm' does?

Thanks for any more help :)

-s7ar

---

