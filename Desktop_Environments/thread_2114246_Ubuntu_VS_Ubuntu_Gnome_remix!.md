---
title: "Ubuntu VS Ubuntu Gnome remix?!?"
date: 2013-02-09
forum: Desktop Environments
---

### Post by NikiNfOuR on 2013-02-09
I am planning to upgrade to the ubuntu 12.10. But i heard that the GNOME in ubuntu is a bit unstable and no one is recommending it! The thing is that whether the Ubuntu Gnome Remix is stable and will it be recommended by you?? Or is it good to install gnome over unity?? (I will be using Gnome). And if it's good to install gnome over the unity, what is the difference??

Thanks in Advance.

---

### Post by ibjsb4 on 2013-02-09
Think I would be tempted to install both 12o4 (stable) and Remix.  You will never know how good or bad it is on your box until you try it.

---

### Post by uzumakifahim on 2013-02-09
I have installed Gnome shell over ubuntu 12.04 and my experience is pretty good. Actually if you install Gnome shell over general Ubuntu, then some specific packages related to unity will be in there. If you are determined that, you'll use Gnome shell permanently, then I think you don't need to take the burden of unity related package or anything like that. 

So, in my opinion if you only use Gnome then Ubuntu Gnome Remix is better choice for you.

---

### Post by grahammechanical on 2013-02-09
Where did you hear this

> But i heard that the GNOME in ubuntu is a bit unstable and no one is recommending it!

It is simply untrue! I have 12.04, 12.10, 13.04 and Ubuntu Gnome Remix 12.10 converted to 13.04. Add the fact that the Gnome people are still developing Gnome 3 DE and Gnome 3 shell to the fact that just a few people are developing Gnome Remix and I am not be surprised to find there are some issues on Gnome Remix.

I do not find any instability in Ubuntu Unity running on Gnome 3 DE. Gnome Remix is based upon Ubuntu so if Gnome 3 DE is unstable in Ubuntu then, it must also be unstable in Gnome Remix.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10")

Some people do not like the Unity user interface. Well, if you are one of those people then you will find that Gnome 3 shell is very similar. Do not forget that Ubuntu uses Gnome utilities in the distribution. Download both ISO images and try them out in a live session and make your own mind up.

---

### Post by Frogs Hair on 2013-02-09
I have been using the Gnome Shell very successfully on my Ubuntu installations since 11.10. The remix is not an option you can select during a normal Ubuntu upgrade so you will have to try it separately as stated by the others.

---

### Post by NikiNfOuR on 2013-02-13
Thanks for all the reply and i installed gnome remix 12.10!! My laptop is Samsung NP550P5C-S01IN, it's sound card is working and unlike the 12.04 LTS its utilising the 2.1 JBL speakers, THanks. But the laptop is heating too much! Why is that?? ANybody have any idea??

---

### Post by aspergerian on 2013-02-13
> **NikiNfOuR said:**
> But the laptop is heating too much! Why is that?? ANybody have any idea??

If Jupiter is still available for Ubuntu, give Jupiter a try. It allows you to tweak power use in laptops.

---

### Post by NikiNfOuR on 2013-02-13
> **aspergerian said:**
> If Jupiter is still available for Ubuntu, give Jupiter a try. It allows you to tweak power use in laptops.


I don't think it's available for 12.10. It's definitely heating than it should!! And another problem i encountered is after installing the bumblebee for nvidia drivers, i think it's not moved to the onboard graphics hence the same old one and a half hours battery backup...

---

### Post by aspergerian on 2013-02-14
I'm far from expert but wonder about:

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

from: [http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html)

---

### Post by sbnwl on 2013-02-14
Hi ,
I see your Samsung laptop has Nvidia GeForce GT 650M as another graphics, apart from onboard graphics. This might be the only reason of heavy power consumption (~36 Watts) on your laptop. Half of your problem would be solved if you had installed bumblebee properly. 

I had earlier tried Jupiter but it didn't make any difference for my machine.
You say bumblebee is installed in your lappy, but I recommend you to follow this page to go through carefully first, and then install bumblebee.

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Post if any difficulty.

---

### Post by markbl on 2013-02-14
> **NikiNfOuR said:**
> I am planning to upgrade to the ubuntu 12.10. But i heard that the GNOME in ubuntu is a bit unstable and no one is recommending it!
There was an older thread where some, including me, stated that gnome 3 (i.e. gnome-shell) seemed a little less stable on 12.10 compared to 12.04. Nobody would not recommend it though!

Actually, with 12.10 I also upgraded my PC to current gen hardware and graphics so I think my slight stability issues are to do with that, e.g. graphics driver issues. Gnome shell is fine.

I did not use gnome remix. I just did a standard ubuntu 12.10 desktop install then added the gnome 3 team ppa and installed gnome-shell. I understand that the net result is pretty much the same as gnome remix anyhow, particularly since I am using gdm instead of lightdm due to the  [race-condition bug with lightdm and a fast PC/SSD](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150).

I am very happy using gnome shell on ubuntu 12.10.

---

### Post by jhilp on 2013-02-15
I personally had no luck with the Ubuntu Gnome Remix. I like the Gnome 3 desktop environment, so I installed the Gnome desktop from the Ubuntu Software Center, within a standard 12.10 install. Just search "Gnome" in the software center and it comes right up. Part way through the installation, it will ask you to choose between GDM and LIGHTDM. Pick GDM. I tried several other ways of getting the Gnome desktop with Ubuntu without success, but this way worked for me. The nice thing about installing Gnome alongside of Unity is that you get the better software packages that come with Unity, especially the Ubuntu Software Center. It's much more user friendly than the archaic "Software" program that comes with Fedora or Ubuntu Gnome Remix.

---

