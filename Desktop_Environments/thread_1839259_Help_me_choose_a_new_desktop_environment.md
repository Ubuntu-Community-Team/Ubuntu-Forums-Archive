---
title: "Help me choose a new desktop environment"
date: 2011-09-05
forum: Desktop Environments
---

### Post by IGITIHI on 2011-09-05
My netbook is a eee 1201nl with 1GB ram. I am currently using Ubuntu Maverick with Gnome 2.32.0. I would like to try a lighter desktop environment because I don't care about eye candy, I just want more speed and responsiveness. I'm considering switching to Xfce or Enlightment.

1) Which one is lighter?
2) If I use any of them, will I be able to run all Ubuntu applications I am currently using? 
3) How can I try them without messing up my current install?

Your help will be greatly appreciated!

---

### Post by sanderd17 on 2011-09-05
> **IGITIHI said:**
> My netbook is a eee 1201nl with 1GB ram. I am currently using Ubuntu Maverick with Gnome 2.32.0. I would like to try a lighter desktop environment because I don't care about eye candy, I just want more speed and responsiveness. I'm considering switching to Xfce or Enlightment.

1) Which one is lighter?

XFCE is not that light anymore. LXDE is lighter and enlightment is not a complete DE but a window manager if I'm right.
> 
2) If I use any of them, will I be able to run all Ubuntu applications I am currently using? 

Sure. In any way, LXDE and XFCE use GTK libraries, so GTK programs will work as good as in Gnome. But QT programs will still work a bit slower than in KDE
> 
3) How can I try them without messing up my current install?

Just install the desktop environments from the software center. You will be able to choose between them when you have to type your password
> 

Your help will be greatly appreciated!

---

### Post by Johnb0y on 2011-09-05
as the above comment said, but i would recommend looking into upgrading your RAM first. would help alot. esp. with performance...:)

---

### Post by Linuxisfast on 2011-09-05
Lubuntu your best bet.

---

### Post by Frogs Hair on 2011-09-05
I have used the E17 core packages and a PPA on 11.04 and they both work . The problem is Enlightenment is incomplete and under heavy development , so I use it on a limited basis . There is also no way to update the E17 core packages and weather it will be available on the 11.10 final release is unknown .

---

### Post by Antarctica32 on 2011-09-05
I suggest Xfce

---

### Post by 2F4U on 2011-09-05
If you want a really light environment and stay within the Ubuntu family, I would suggest Lubuntu (LXDE). You can run all Gnome applications on it since it uses the GTK framework and Lubuntu is designed with less powerful hardware in mind.
If you want to try it, there is also lubuntu-desktop, which can be installed in an already running system alongside another desktop environment.

---

### Post by claracc on 2011-09-05
I also recommend you to try lubuntu, it is very light and quick.

You can install the lubuntu desktop from any ubuntu flavor simply adding a repository, as this link indicates: [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Install_Lubuntu_from_Ubuntu_or_any_Ubuntu_flavors](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Install_Lubuntu_from_Ubuntu_or_any_Ubuntu_flavors)

---

### Post by IWantFroyo on 2011-09-05
> **Johnb0y said:**
> as the above comment said, but i would recommend looking into upgrading your RAM first. would help alot. esp. with performance...:)

Is it possible to upgrade the RAM in a netbook? I heard you lose your warranty if you open a notebook/netbook...
Also, the motherboard is probably custom made to be small, and probably doesn't have extra card slots.
Although you might be able to swap out the 1GB card with a 3GB (if I'm correct) card.

Either way, 1GB works perfectly fine with LXDE. lubuntu-desktop is probably your best bet. Just search in Synaptic or use aptitude.

---

### Post by 3Miro on 2011-09-05
Here is what you do:

1. Go to this page:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

2. Install Gnome, KDE, XFCE and LXDE.
3. Try them out and see which one you like.
4. After picking a DE, remove the DE that you don't want (the site has instructions).

---

### Post by rojaasensei on 2011-09-05
I recommend Xubuntu for a combination of lightness and customization.

+1 for 3Miro's suggestion above regarding Psycho Cat.  It works flawlessly.

---

### Post by IGITIHI on 2011-09-06
I thank you all for your responses!

I have already installed LUbuntu and I want to try XUbuntu as well. I tried to follow the psychocat instructions and install the xubuntu-desktop package through the software center but I get a warning that I must remove lubuntu-desktop and lxdm in order to continue. Is there a way to try XUbuntu without removing LUbuntu first?

---

### Post by claracc on 2011-09-06
As this thread indicates: [https://lists.launchpad.net/lubuntu-desktop/msg01618.html](https://lists.launchpad.net/lubuntu-desktop/msg01618.html), it is safe to remove lubuntu -desktop since >  Lubuntu-desktop is
> > only used for upgrade (when you change the Lubuntu version) or initial
> > installation of lubuntu and can be safely removed. It would just need
> > adding back in when you go to update from, say, 10.04 to 10.10.
> > Lubuntu-desktop is what is called a 'meta-package' which, simply put,
> > is just a list of what to install

You can try xubuntu from live CD without installing it or uninstalling lubuntu.

---

### Post by IGITIHI on 2011-09-06
Ok, I finally decided to keep LUbuntu and remove Ubuntu. I followed the instructions I found here: 
[http://www.psychocats.net/ubuntu/purelxdemaverick](http://www.psychocats.net/ubuntu/purelxdemaverick)

However, this command removed the display drivers and I couldn't boot. Not even in failsafe graphic mode. So, I had to re-install Ubuntu-desktop and then install the nvidia drivers. Is there a safer way to switch to "pure" LUbuntu?

---

### Post by 3Miro on 2011-09-06
> **IGITIHI said:**
> Ok, I finally decided to keep LUbuntu and remove Ubuntu. I followed the instructions I found here: 
[http://www.psychocats.net/ubuntu/purelxdemaverick](http://www.psychocats.net/ubuntu/purelxdemaverick)

However, this command removed the display drivers and I couldn't boot. Not even in failsafe graphic mode. So, I had to re-install Ubuntu-desktop and then install the nvidia drivers. Is there a safer way to switch to "pure" LUbuntu?

My guess is that they should not have removed gdm, but I can't be sure. You can send them an e-mail to tell them about the issue.

If you have to reinstall, you can just install lubuntu without ever installing Ubuntu.

---

### Post by IGITIHI on 2011-09-07
> **3Miro said:**
> If you have to reinstall, you can just install lubuntu without ever installing Ubuntu.

I tried to reinstall but I got a message that lubuntu-desktop was already installed. That's why I reinstalled ubuntu-desktop in the first place.

---

### Post by 3Miro on 2011-09-07
> **IGITIHI said:**
> I tried to reinstall but I got a message that lubuntu-desktop was already installed. That's why I reinstalled ubuntu-desktop in the first place.

I meant reinstall the entire OS.

You can try the same psychocats command, just make sure you don't remove anything about "gdm".

---

### Post by william.smith3 on 2011-09-07
I would also recommend a RAM upgrade for the ASUS Eee PC 1201NL netbook. 

See this link for possible RAM upgrade options... [http://www.crucial.com/upgrade/compatible-memory-for/ASUS/Eee+PC+1201NL/list.html](http://www.crucial.com/upgrade/compatible-memory-for/ASUS/Eee+PC+1201NL/list.html)

Also, as for your DE, I would suggest XFCE since you want to stick with Gnome.

---

### Post by koleoptera on 2011-09-07
IMHO Xubuntu has lost its touch and become a bit to resource consuming..
Lubuntu on the other hand still serves the lightweight cause of existence.

---

### Post by TBABill on 2011-09-07
> **koleoptera said:**
> IMHO Xubuntu has lost its touch and become a bit to resource consuming..
Lubuntu on the other hand still serves the lightweight cause of existence.
 +1
 
When you are down on resources and not looking to upgrade hardware, LXDE is snappier and less resource hungry than Xfce.

---

### Post by Atamisk on 2011-09-07
I really like lxde after trying it. It's a great alternative once gnome2 loses support from the repos. Plus, if you have the hardware to do it, compiz works great in lxde. Because the DE is so light, compiz is a bit less of a hit. 

Basically, i'm a vote for lxde

---

### Post by Zeta-K on 2011-09-07
I LOVE and almost exclusively use awesome on my main computer. It takes a bit to learn and is buggy if you use nautilus(try PCMANFM), but uses so little resources that I was happy to deal with the learning curve.

---

### Post by IGITIHI on 2011-09-10
I have to thank you once more for all your replies, you've persuaded me to try lUbuntu and stick with it. Now two more questions:

1) How can I upgrade from lubuntu 10.10 to 11.04 using the terminal? I'm afraid that if I use the update manager, I'll end up with Ubuntu 11.04. Even the startup screen says Ubuntu and not lUbuntu...

2) Is there any way to get rid of Ubuntu completely? I suspect that the psychocats command didn't work as well as it was supposed to.

3) How can I make the "Alt Gr" and the special Fn keys of my eee 1201nl work? (I have a german keyboard)

---

### Post by claracc on 2011-09-10
> 1) How can I upgrade from lubuntu 10.10 to 11.04 using the terminal? I'm afraid that if I use the update manager, I'll end up with Ubuntu 11.04. Even the startup screen says Ubuntu and not lUbuntu...

2) Is there any way to get rid of Ubuntu completely? I suspect that the psychocats command didn't work as well as it was supposed to.

About first question, in a terminal you write: sudo apt-get update and then sudo apt-get upgrade. But if you want to get rid of ubuntu at the same time you get lubuntu 11.04 I recommend to do a fresh install of lubuntu 11.04:

You copy in a CD the iso of lubuntu 11.04, [http://lubuntu.net/blog/lubuntu-1104-released](http://lubuntu.net/blog/lubuntu-1104-released), boot the pc from the CD , choose your language and install, then follow the instructions ( I think this is the cleanest way).

---

### Post by IGITIHI on 2011-09-11
> **claracc said:**
> But if you want to get rid of ubuntu at the same time you get lubuntu 11.04 I recommend to do a fresh install of lubuntu 11.04

I have a dual-boot system with Windows 7 and Linux. If I follow your method, will I mess up the boot sector? Is the LUbuntu installer able to "understand" that it's a dualboot system?

---

### Post by claracc on 2011-09-12
The installation method of lubuntu dual boot win is the same as you followed when installed ubuntu along side win 7.

I have installed lubuntu 11.04 as the only OS in my old laptop, but when you choose to install lubuntu from live CD there is an option to install lubuntu side by side with other os's present, the bootloader will be grub2 which will take note of os's in the pc and let to boot one or another by choosing options.

Lubuntu 11.04 rocks, so I suppose its installer rocks too.

---

