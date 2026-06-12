---
title: "Start x-server on bootup"
date: 2009-10-25
forum: Desktop Environments
---

### Post by aaron424 on 2009-10-25
How can you start the nvidia x-server on boot?

---

### Post by scorp123 on 2009-10-25
If everything is properly installed it should happen automatically. And if something isn't working then you should give way more info.

---

### Post by aaron424 on 2009-10-25
Like what? I have a geforce 9500 gt and installed the nvidia restricted pacage 180, I have to manually open the x server on login to get the settings, such as digital vibrance.

---

### Post by linux-hack on 2009-10-25
one option is t put make a scipt with startx commnand and lunch it on boot up in the bashrc script

---

### Post by aaron424 on 2009-10-25
Im a noob here so a little simpler explanation would be great:confused:

---

### Post by scorp123 on 2009-10-26
> **boogy9 said:**
> one option is t put make a scipt with startx commnand and lunch it on boot up in the bashrc script Why would you do that?? That's a dirty hack at best and not the proper way.

---

### Post by scorp123 on 2009-10-26
> **aaron424 said:**
>  Like what?  Like what Ubuntu version you installed? Ubuntu 8.04 LTS, 9.04 or maybe even the newest 9.10 release candidate? And are we talking about the desktop version or about the "Ubuntu Server" version? And is that a fresh install so we can assume everything is still as it was fresh after the installation or did you already tamper with it so we have to assume that the problem you experience now is an undesired side-effect and that there might be a few other problems you did not mention yet?

> **aaron424 said:**
>  I have a geforce 9500 gt and installed the nvidia restricted pacage 180 I have to manually open the x server on login to get the settings  But other than that it does work? E.g. no weird error messages or crashes?

Can you please try this (copy & paste!):
```
cd /etc/init.d
sudo update-rc.d kdm defaults

```

When it asks for a password: That's your own password. And nope, there won't be any stars, echoes, dots, or what not. The screen will remain black when you type your password. Just type it and hit the enter key. If you were succesful it will execute the command or else it will ask you again for the password.

What the command does: It tells the "init" boot-scripts to reinstall "kdm" (= KDE Display Manager) again as boot service into the "defaults" run levels. It seems for some reasons that this is missing in your case.

Can you try that please? And reboot? KDM should now appear automatically again. Once you have an automatically starting GUI again we can take care of the Nvidia-specific settings ...

---

