---
title: "how to change WM/remove LXDE?"
date: 2013-03-20
forum: Desktop Environments
---

### Post by idiotprogrammer on 2013-03-20
Hi, there, I changed window managers from Unity to LXDE, and then I screwed up. I accidentally deleted the main toolbar -- the one that shows you Start button which opens up applications.

I am having the damnest time trying to get it back or even to switch back to Unity temporarily. 

I wouldn't mind wiping out LXDE for now (and then reinstalling again), but I want to get rid of my failed settings. 

Also, I need a way to  get out of LXDE and launch a graphical login screen which can allow me to switch to a WM. Can anyone help? Thanks.

---

### Post by ibjsb4 on 2013-03-20
I did a little looking around and looks like a restart may do it.

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Restart_lxpanel](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Restart_lxpanel)

---

### Post by sudodus on 2013-03-20
You can probably still get a terminal window with ***ctrl + alt + t***
and a text screen with any of ***ctrl + alt + F1 ***to[I][B]ctrl + alt + F6
[/B][/I]and return to the graphic desktop environment with***ctrl + alt + F7***

See this link to convert between the different flavours of Ubuntu

[[COLOR=#ff0000]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

---

### Post by idiotprogrammer on 2013-03-20
i think I set my default window behavior in unity so as not to require a login. (ANd indeed, I notice that LXDE automatically starts me without login -- although it requires that I unlock the keyring). Will this affect my ability to change window managers? 

Will I need to use something like a *startx* command in the command line? Or will I use some sort of *unity --replace &* commend via command line when within the current WM? 
[http://askubuntu.com/questions/159505/how-to-switch-windows-manager-on-the-fly](http://askubuntu.com/questions/159505/how-to-switch-windows-manager-on-the-fly)

---

### Post by ibjsb4 on 2013-03-20
If you change your account so that a password is required at login, you will then also be able to change WMs.

---

### Post by idiotprogrammer on 2013-03-20
And how do you set user accounts to require a password at login? I'm sorry to be dense, but I can't seem to find this information. 

And LXDE only gives me a finite number of apps to add to the app menu. 

Is there a command which can call up an application to change default password? 

Remember I can do everything only in LXDE.I'm trapped!

---

### Post by idiotprogrammer on 2013-03-20
I don't know WHY it worked, but when I did this: **"sudo pkill X". ** that killed the X session and brought me back to the Unity session to login. I'm still going to have to figure out how to deactivate auto-login and also how to initialize lxde so I dont' make the window manager unusable.

---

### Post by idiotprogrammer on 2013-03-21
Update: I noticed that I must have forgotten to install lxdm -- the default login manager for LXDE. That gets included in one of the panels by default (or it's relatively easy to add to your menus). That probably caused my difficulties. 

Also. when in Unity, I opened Ubuntu software center, uninstalled lxde, then removed the LX directories in  ~/.config/lxde (lxpanel, lxterminal). Then in Ubuntu software center I reinstalled lxde, making sure to install lxdm as well.  Everything is dandy!

---

