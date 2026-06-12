---
title: "How to disable black screen (idle delay) on login screen ?"
date: 2015-06-22
forum: Desktop Environments
---

### Post by adri12 on 2015-06-22
Hi all,
I'd like to know how to disable the idle delay on the login screen ?
I use Ubuntu Gnome 14.04.2 LTS on five computers in my school, and the students think they are switched off ...
I have tried a lot of things, but no real results :(.
Thanks a lot ;).

---

### Post by adri12 on 2015-06-27
Bump please :(.

---

### Post by Jonners59 on 2015-06-28
> **adri12 said:**
> Hi all,
I'd like to know how to disable the idle delay on the login screen ?
I use Ubuntu Gnome 14.04.2 LTS on five computers in my school, and the students think they are switched off ...
I have tried a lot of things, but no real results :(.
Thanks a lot ;).
What do you mean by idle delay...?

I use the Lightdm settings from the menu or Ubuntu teaks and or Grub repair to fix, manage anything boot and login.

---

### Post by v3.xx on 2015-06-28
Several forum hits on it

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+boot+grub+timeout&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+boot+grub+timeout&sa=Search&cof=FORID:9)

---

### Post by Jonners59 on 2015-06-28
Isn't this about the login screen, not the GRUB delay?

---

### Post by v3.xx on 2015-06-28
> **Jonners59 said:**
> Isn't this about the login screen, not the GRUB delay?
Ok :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+login&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=auto+login&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Jonners59 on 2015-06-28
Well lets see.  Hopefully between us we have answered the question.

---

### Post by ajgreeny on 2015-06-30
At the login screen none of the session configurations for either screen-standby, screensaver or light-locker are being used so it must surely be a setting in the monitor or monitors themselves.

---

### Post by yetimon_64 on 2015-06-30
> **ajgreeny said:**
> At the login screen none of the session configurations for either screen-standby, screensaver or light-locker are being used so it must surely be a setting in the monitor or monitors themselves.

If the session hasn't been logged into it may possibly be related to the console itself that the log in screen is running on. If you don't log into any x session at all the CLI will also time out and blank the screen after about 10 minutes. There is a kernel setting that can be set in /etc/default/grub to stop the console timing out that may possibly help here.

On this install I have added "consoleblank=0" to the "GRUB_CMDLINE_LINUX_DEFAULT" line in /etc/default/grub file eg.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **consoleblank=0**"
```

```
gksu gedit /etc/default/grub
```Opens the file for editing OP, though you may need to install "gksu" in Ubuntu if it is not already installed.

Add in the consoleblank=0 to the line as shown in the first code box above (only bolded here for emphasising the change required :-))

Then by running,
```
sudo update-grub
```
I get no more screen blanking on the tty consoles if no session is running. Maybe this will help if it is not related to any monitor DPMS settings etc.   Regards, yeti.

---

### Post by ajgreeny on 2015-06-30
Oh boy!

It is amazing how we can all learn something new almost every day in this Linux business.  I was totally unaware of that **consoleblank=0** grub option in the /etc/default/grub file.

Thanks for that info yetimon_64

---

### Post by CantankRus on 2015-07-01
This works for me to disable blanking at the greeter.

Change the user lightdm idle-timeout.
The default setting is "**300**".
```
sudo -i
xhost +SI:localuser:lightdm
su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter idle-timeout **0**
exit
exit
```

---

### Post by adri12 on 2015-07-03
Hi all,
Thanks for your replies ;).
I will have a look when I will be at work, in two hours.

> Isn't this about the login screen, not the GRUB delay?
It is exactly that :).

---

