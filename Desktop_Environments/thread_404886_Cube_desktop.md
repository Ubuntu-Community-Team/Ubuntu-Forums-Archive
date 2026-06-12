---
title: "Cube desktop?"
date: 2007-04-09
forum: Desktop Environments
---

### Post by Vendeta on 2007-04-09
Is there a way to get a nice SIMPLE install of xgl or beryl because im a complete linux nooblet and ive goton around by using easyubuntu for most of my stuff is there a simple guide or even a thing that will do it all like easyubuntu? I have a nvidia card

---

### Post by raja on 2007-04-09
The installation is not too difficult, but it is unpredictable how well it will turn out, especially with an nVidia card. The best place may be the beryl installation wiki. What you want may be [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia"). 
For installing drivers for the nVidia card, you may find [envy]("http://www.albertomilone.com/nvidia_scripts1.html") useful.

---

### Post by Vendeta on 2007-04-09
Ive got the nividia drivers installed so i can just use that wiki link to install beryl? do u have  msn so u can help me through it cause when it comes to linux u mides well call me a 3 year old....

---

### Post by raja on 2007-04-09
You can follow the wiki for the nvidia cards. Make sure to backup the xorg.conf file before you make changes to it. That way if things dont work out, you can easily switch back to your original configuration. Please post if there are any problems and either me or someone else will help.

---

### Post by Vendeta on 2007-04-09
I followed it but when i start up nothing happends...
What did i do wrong?

---

### Post by igknighted on 2007-04-09
> **Vendeta said:**
> I followed it but when i start up nothing happends...
What did i do wrong?

You need to start beryl, it does not start by itself.  Run the command "beryl-manager" in the terminal to start it.  You can also add beryl manager to System->Preferences->Sessions if you want it to start at boot.

---

### Post by Vendeta on 2007-04-09
> bash: beryl-manager: command not found


and i did add it to sessions

---

### Post by raja on 2007-04-09
Are you sure you installed beryl-manager ? If the command was not found, you did not install it. Check if you did these steps - 

1. Add beryl repositories to sources.list
2. Install beryl, beryl-manager, emerald-themes
3. Changes to xorg.conf
4. restart x
5. Start beryl-manager.

---

### Post by Vendeta on 2007-04-09
Im not sure about the xorg.conf i think thats all that i didint do cause i remember emerald-themes
How do i do that file?

---

### Post by raja on 2007-04-09
xorg.xonf is the file that has the configuration options for the x window manager. Make a copy of your working conf file first 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confbkp
```

Now follow the instructions [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Configure_X.Org_to_use_the_new_nVIDIA_driver") to reconfigure xorg.conf.

---

### Post by johndavid400 on 2007-04-10
Vendeta:

What kind of Nvidia card are you using... and which driver did you isntall (the legacy or beta)? Also do you use KDE or Gnome... and which version of (K)Ubuntu are you using 6.06 (Dapper) or 6.10 (Edgy)?

I can write out a set of relevant instructions for you to get beryl working if you still need help. I sorted through the beryl instructions from their website and found which steps needed to be taken and which can safely be skipped.

I am currently using beryl on Kubuntu with an old Geforce mx4000 card with the Nvidia Beta driver and it works great.

---

