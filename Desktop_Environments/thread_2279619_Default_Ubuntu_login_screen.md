---
title: "Default Ubuntu login screen"
date: 2015-05-24
forum: Desktop Environments
---

### Post by RobGoss on 2015-05-24
Hello everyone, I was messing around with my login screen and seem to mess things up a bit. I installed Lightdm and decided I don't like it at all so I tryed to remove it or at lease I tough I did but I can't seem to get my Ubuntu default login screen like I had it before when I installed Ubuntu. Thank you for any help with this.

---

### Post by Vladlenin5000 on 2015-05-24
LightDM is the default for Ubuntu.
Other flavors use different display managers by default but standard Ubuntu uses LightDM. Please check what you really installed.
A few examples of what you might have installed: LightDM (default, already installed), MDM, KDM, Slim, GDM, etc.

---

### Post by RobGoss on 2015-05-24
So how would I change the login screen? I had a Ubuntu login so I tough it was the default one.

I install lightdm and it's to simple so I wanted  to change it back but  not sure how. Thanks

---

### Post by Vladlenin5000 on 2015-05-24
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

The procedure is always the same, the name varies.

---

### Post by RobGoss on 2015-05-24
My login screen use to look like this [http://www.robgoss.com/images/Screenshot_Login_Screen_Ubuntu.jpeg](http://www.robgoss.com/images/Screenshot_Login_Screen_Ubuntu.jpeg) with the login box on the left.

---

### Post by deadflowr on 2015-05-24
Are you sure you didn't simply install lightdm-gtk-greeter?
Ubuntu uses a greeter session called unity-greeter.
Unity-greeter is what the default would be, with the login box off toward the left side.
Lightdm-gtk-greeter looks like a gdm login with the login box in the center.
Both greeters are built to be used with lightdm. 


If you did indeed install lightdm-gtk-greeter then you can also remove it, if you want...

---

### Post by RobGoss on 2015-05-25
Yes I'm sure [COLOR=#000000]lightdm-gtk-greeter is what I installed but how would I remove it with out interrupting [/COLOR][COLOR=#000000]Unity-greeter seeing they both use Lightdm.
I was trying to remove lightdm from the terminal but I'm still greeted by that small login box in the middle of my screen.

 And thank you so much for the help[/COLOR]

---

### Post by RobGoss on 2015-05-25
Thanks so much for the help. I found a fix for this and I wanted to share it here [http://askubuntu.com/questions/398966/how-to-return-the-login-screen-of-the-original-unity-ubuntu](http://askubuntu.com/questions/398966/how-to-return-the-login-screen-of-the-original-unity-ubuntu)

I was able to restore my default login by using this method from the terminal. I did not edit any of the greeter files because after I rebooted my default login screen was back.


```
 
[COLOR=#111111][FONT=Consolas]sudo apt-get purge lightdm-gtk-greeter

[/FONT][/COLOR]sudo add-apt-repository --remove ppa:lightdm-gtk-greeter-team/stable

[COLOR=#111111][FONT=Consolas]sudo apt-get update[/FONT][/COLOR]
```

---

