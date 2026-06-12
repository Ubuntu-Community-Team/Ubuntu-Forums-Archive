---
title: "Beryl on Ubuntu-Intel Procesor"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Ivan_Linux on 2007-04-25
So, I'm using Ubuntu on my laptop IBM ThinkPad R50e, I have a Intel graphic card in it and I would like to install Beryl. The problem is I'm a newbie so I don't know what to do. I have found a guide how to install Beryl on Ubuntu here: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
But the guide is for computers with ATI graphic cards only. Could anyone help me by linking me with a guide how to install beryl on a computer using a INTEL graphic card? I would need a detailed step by step guide because I'm a newbie. Thanks in advance! Ivan.

---

### Post by Waappu on 2007-04-25
Hi

See if this helps.
[http://ubuntuforums.org/showthread.php?t=267232](http://ubuntuforums.org/showthread.php?t=267232)

---

### Post by Ivan_Linux on 2007-04-25
Thats for Edgy, I have Feisty Fawn.

---

### Post by Waappu on 2007-04-25
Hi

Sorry, didn't know.

Basic idea is find guide how to setup your video card in feisty. I don't have Feisty nor Intel card so cant help on that.

Then add repositorys to your /etc/apt/sources.list from here
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX#Add_repositories](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX#Add_repositories)
and then type in terminal
```
sudo aptitude update
sudo aptitude install beryl beryl-manager emerald emerald-themes
```

---

### Post by hyperair on 2007-04-25
I think all Intel cards already work flawlessly with Beryl and Compiz. Just go to your terminal and run this:

sudo apt-get install beryl emerald beryl-plugins-unsupported

Then to start Beryl, run "beryl-manager" in your terminal or run dialog.

To make Beryl start when you login, go to System->Preferences->Sessions and under the tab Startup Programs, add one with command beryl-manager.

Alternatively if you just wish to use Compiz, you can turn on Feisty's desktop effects. I tested it on my college's computers via LiveCD running Intel cards today, and Compiz runs fine, without any xorg.conf custom configuration. I didn't have time to run Beryl though.


EDIT: whoops looks like someone has posted before me. Anyway, Intel cards are supported for AIGLX in Feisty without any further configuration, just so you know. Also, the universe repository contains Beryl 0.2.1 which is slightly newer than the one in ubuntu.beryl-project.org. So, I suggest that you just enable the universe repository and install Beryl using the said commands

---

### Post by Ivan_Linux on 2007-04-25
So heres what I did. I typed: "sudo apt-get install beryl emerald beryl-plugins-unsupported" into the terminal, accepted... in the end i typed "beryl-manager" into the terminal but it says it doesn't recognise the command. :(  I really want to have beryl.

---

### Post by Ivan_Linux on 2007-04-25
could someone give me really detailed, step-by-step instructions please?

---

### Post by Waappu on 2007-04-25
Hi

```
sudo aptitude install beryl beryl-manager
```

---

### Post by Ivan_Linux on 2007-04-25
Thank you, it works!!!! Now, I just need 1 more thing. Can someone please tell me what do I have to do to startup beryl when loging in, and can someone please give me a list of commands to control the cube and stuff?

---

### Post by Waappu on 2007-04-25
Hi
Add Beryl to startup programs:

    * Go to System > Preferences > Sessions
    * Go to the Startup Programs tab
    * Click the Add button and type in beryl-manager
    * Exit

Hope it same in Feisty that is in Edgy =)

[http://wiki.beryl-project.org/index.php/Plugins/PluginOptions](http://wiki.beryl-project.org/index.php/Plugins/PluginOptions)
[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)

---

### Post by Iceni on 2007-04-25
> **Ivan_Linux said:**
> Thank you, it works!!!! Now, I just need 1 more thing. Can someone please tell me what do I have to do to startup beryl when loging in, and can someone please give me a list of commands to control the cube and stuff?

Go System->Preferences->Sessions
While under the "startup programs" tab click "New"
name: "Beryl"
Command: "beryl-manager"

You can spin the cube with ctlr+alt+arrows or with mousewheel near screen edges. You should probably set everything up in the beryl settings.

---

### Post by Waappu on 2007-04-25
Hi

Here is guide how to add beryl to startup programs in Feisty
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX#Configuring_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX#Configuring_Beryl)

---

### Post by Ivan_Linux on 2007-04-25
Thank You!!! I Am So Grateful You Couldn't Possibly Imagine!!!!!!!!!!!!

---

### Post by insane_alien on 2007-04-25
beryl works fine on the R50e , in fact i'm writing it from one right now. :D or i would be if the uni proxy system would let me connect to the repositories to fix a bit i borked :D

---

