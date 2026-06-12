---
title: "Switching Back to Unity Greeter"
date: 2013-10-19
forum: Desktop Environments
---

### Post by osarusan on 2013-10-19
I just installed the ubuntustudio-desktop package from Ubuntu in order to get Ubuntu Studio on my computer, but I want to replace the login window that comes with Ubuntu Studio. It works poorly with multiple monitors, while the default Ubuntu login window (Unity Greeter?) works wonderfully with them.

Can someone tell me how to switch back to the default Ubuntu login manager?

---

### Post by grahammechanical on 2013-10-19
When we install an alternative desktop we usually get an option at the login screen to select which desktop to load. It then becomes the default desktop that we log in to. Do you not get that option? With more than one desktop installed an icon appears on the user/password panel. If we click that we see other desktop options.

Regards.

---

### Post by osarusan on 2013-10-19
It's not an issue of which desktop -- I can log in to Ubuntu or Ubuntu Studio no problem. What I mean is that the desktop greeter (either Unity-greeter or LightDM maybe?) is different and I would like to switch it back to the default one.

---

### Post by ABCC on 2013-10-19
I'm not sure which greeter Ubuntu Studio uses, but on my 13.04 the default greeter is lightdm. 

I've played around with a few different ones, all of them are simply system services so you can use update-rc.d to stop the ones you don't want and start the one you prefer. You can also easily play around with them by logging in to a vtty (ctrl+alt+f1), killing whicever is running and running e.g. sudo service start lightdm.

---

### Post by osarusan on 2013-10-19
Ok I figured it out. Studio also uses LightDM, it was just a matter of changing the greeter session to Unity-Greeter.

I just had to edit the 'greeter-session' option in '/etc/lightdm/lightdm.conf', then change the line

greeter-session=lightdm-gtk-greeter

back to

greeter-session=unity-greeter

---

