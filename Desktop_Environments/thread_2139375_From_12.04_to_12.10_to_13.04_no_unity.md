---
title: "From 12.04 to 12.10 to 13.04 no unity"
date: 2013-04-26
forum: Desktop Environments
---

### Post by mattmers on 2013-04-26
So I had been using Ubuntu 12.04 and I heard 13.04 was a good upgrade so I upgraded from 12.04 to 12.10 (because I wanted to keep all my files). In the process, I lost unity and decided I would not worry about it because I would just upgrade via terminal to 13.04. I finished it last night but still no unity, Any suggestions to gain it back in my case? I tryed a couple different things like reset unity but it did not work. Thanks in advance

---

### Post by ibjsb4 on 2013-04-26
Install a different desktop.  If you get the same results, it maybe your video driver.  An easy desktop to install in terminal:

```
sudo apt-get install gnome-session-fallback
```

And choose at boot (login) by clicking on the icon.

---

### Post by rrich1974 on 2013-04-26
i just wonder how is gonna be the upgrade from 12.04 lts to 14.04 lts.....just a guess!

---

### Post by VanillaMozilla on 2013-04-26
Lost your Unity?  What do you have instead?

You probably switched it at login.  Click on the symbol to the right of the password field, and you will get a dropdown box of choices.  Just choose Ubuntu.

---

### Post by Frogs Hair on 2013-04-26
The 12.10 version of unity is very different from 12.04 , so I can understand why it was was replaced, but was Unity not working or not installed is the question though. The reset commands for  Compiz and Unity  changed in 12.10 & 13.04. There is no Unity 2D in 12.10 + and the login selection is Ubuntu.

Reset Unity:  ```
setsid unity
```

Reset Compiz:```
sudo apt-get install dconf-tools
``` ```
dconf reset -f /org/compiz/
```

 Did you consider a file backup and clean installation instead of two upgrades ?

---

### Post by rrich1974 on 2013-04-26
i am afraid that it starts into tty. 
i think it is a video driver issue.

---

### Post by junctionIV on 2013-04-26
I had the same issues, most likely because I was using Nvidia drivers.  after my inital update to 13.04 I had to remove the nvidia drivers for my screen to even show anything with out being in tty.  I had to reinstall my Nvidia drivers, then I finall had a desktop, but then Unity was gone.  I ran this to get it back up(after testing some others that didn't work)
> dconf reset -f /org/compiz
gnome-session-quit
when i logged back in it worked.  I also had dconf-tools installed from an earlier apt-get and i think I tried using setsid unity multiple times, but I kept getting errors

---

### Post by grahammechanical on 2013-04-27
So, to recap. You get to a desktop but it does not have a top panel or the launcher. Right click the desktop and select Change Wallpaper. That will open System Settings. From there you can open Software & Updates and at the Additional Drivers tab you can experiment with video drivers. I have given up using Nvidia. I use Nouveau from now on.

To reset Unity first install dconf ```
sudo apt-get install dconf-tools
``` then ```
dconf reset -f /org/compiz/
``` then ```
setsid unity
```

You may need a log out and log in or a reboot.

Regards

---

