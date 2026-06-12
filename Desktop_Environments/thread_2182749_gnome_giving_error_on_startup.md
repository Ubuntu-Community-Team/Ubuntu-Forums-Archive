---
title: "gnome giving error on startup"
date: 2013-10-22
forum: Desktop Environments
---

### Post by rohitashharitanwar on 2013-10-22
Hi,
    I am using ubuntu for some time. I installed 12.04 some days ago and it was working fine but yesterday when I started ubuntu it gave an error "can' t write bytes: broken pipes". Then I logged into tty and tried to start gnome session but it gave error "can't start display" something like it. then I installed startx and it is working fine. Is there something I should do like uninstalling gnome, if yes then how to do it.
             Thanks..

---

### Post by ibjsb4 on 2013-10-22
Try reconfiguring your display manager.

[https://wiki.ubuntu.com/LightDM#Running_LightDM_by_default](https://wiki.ubuntu.com/LightDM#Running_LightDM_by_default)

---

### Post by rohitashharitanwar on 2013-10-23
Thanks for your reply.. 
I used command "sudo dpkg-reconfigure lightdm" and it waited for a second but nothing showed at the terminal. Then i typed "sudo stop gdm"  and it said "Unknown job: gdm". on logging out of lightdm that black screen showed and the error message "pipes broken" was there on the screen. Then I logged into tty and typed command "startx" but this time only ubuntu's default wallpaper showed up and nothing else. So I restarted my pc. Now its working but still its a little slow then it was before.
I want to uninstall gnome completely and then reinstall it but don't know it I should do it or how to do it. Please help...
Thanks...

---

### Post by ibjsb4 on 2013-10-23
When you say that you want to uninstall gnome, I am not sure what you mean.

You say that you are running gnome-session.  Gnome-session is gnome-classic with compiz window manager.  Is that what your running and want to remove?  Or is it gnome-shell you want to remove?

Ubuntu is built on Gnome3, that cannot be removed.

---

### Post by rohitashharitanwar on 2013-10-23
I am a newbie so I know little about all this stuff. I didn't know that gnome cannot be removed.

And yes i m running gnome-session at tty and it says that it cannot open display so i use startx instead. First time it worked and GUI appeared but next time when I logged out of GUI and ran startx at tty only the default theme of ubuntu appeared and nothing else and a click or drag of mouse made the screen look different at that place. So I restarted and it worked fine. This is happening everytime I logout of lightdm and try to run startx. Now I just want to know what should I do next and should I concern about all this.

---

