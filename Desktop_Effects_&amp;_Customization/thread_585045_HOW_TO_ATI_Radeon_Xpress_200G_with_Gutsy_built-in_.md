---
title: "HOW TO: ATI Radeon Xpress 200G with Gutsy built-in effects"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by gerfuls on 2007-10-21
This exactly how i finally got to get my ATI Radeon Xpress 200G card to work with the new Gutsy effects. Note: this is my first guide! Hope this guide helps!

This guide assumes you know how to open and use the terminal and how the sudo command works. If you don't know how to use these things I suggest you learn by going to [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

First we need to install the fglrx driver from ATI. Open Synaptic from System >> Administration >> Synaptic Package Manager. In Synaptic go to the Settings menu and select Repositories. In the Downloadable from the Internet section make sure the "Propietary drivers for devices (restricted)" is checked. Close the Software Sources box and click on the "Reload" button in Synaptic. If a dialog box comes up warning you about the changed repositories then click Close.

Now close Synaptic and open the Restricted Drivers Manager from System >> Administration >> Restricted Drivers Manager. In the Component box of the window you should see something like "ATI accelerated graphics driver" click the check box next to it to install enable the driver. After this you will need to restart your computer.

Now that we have the driver installed we must configure the Xorg.conf

run this in the terminal:
```
sudo gedit /etc/X11/xorg.conf
```

Skip down to the bottom and find the lines like this:
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```
it may say "disable" rather than "0". Change the 0 or disable to 1 so it reads:
```
Section "Extensions"
        Option          "Composite"     "1"
EndSection
```

**Click save** and close the gedit window.

Now we have to install xgl. Run this in the terminal:

```
sudo apt-get install xserver-xgl
```

No more fancy scripts and sessions are needed any longer for xgl to work. In fact, if you try to use any special X sessions they will most likely fail! After it finishes you just have to logout and then back in.

The effects should be enabled by default but if not go to System >> Preferances >> Appearance. Go to the Visual Effects Tab and select either Normal or Extra. If you want to be able to customize the effects run this in the terminal:
```
sudo apt-get install compizconfig-settings-manager
```

After this is finished open up System >> Preferances >> Appearance again and you will see an extra option on the Visual Effects tab named Custom. If you select that option you can use the Preferences button to customize all of the Compiz Fusion effects. 

I hope this guide helped! Enjoy! :KS

---

### Post by Tachyon1000 on 2007-10-21
I have compiz-fusion working without setting composite to 1 so I am not sure that it is really necessary although you would think that it would be.  It's a bit confusing.  I used much the same method as you and it has worked fine for me since I upgraded to 7.10 but I never had compiz in 7.04 which I think is causing a lot of problems for people who did when upgrading.  All the effects, no complaints, with emerald themes too.

---

### Post by adityakavoor on 2007-10-21
thanks .....wil giv a try

---

### Post by gerfuls on 2007-10-21
let me know if something goes wrong

---

### Post by AnandKM on 2007-10-22
Thanks Gerfuls, the instructions worked fine with me.  Actually I have a ATI Radeon Xpress X1250.

---

### Post by Beggar on 2007-10-22
Several people I have been trying to help have reported that XGL is causing massive amounts of lag on there ATIs, mostly newer cards. Since I tend to just link to this thread, I wanted to point out that if you are trying to install desktop effects, you do not need to install xserver-xgl. Also if you do install it, find that it causes problems, then remove it, you need to set composite back to 1 as the uninstall sets it to 0 again. Thanks, and good luck!

---

### Post by adityakavoor on 2007-10-22
gerfuls ... u ROCK ,... thanks a ton:popcorn:

---

### Post by mellflores1 on 2007-10-22
:confused::confused:i followed all the instructions and am still getting the error message. then i have to go into the system monitor and close GNOME-Appearance. How do I uninstall the server thingy? I'm still a linux n00b.:confused::confused:

---

### Post by analox on 2007-10-23
> Several people I have been trying to help have reported that XGL is causing massive amounts of lag on there ATIs, mostly newer cards.

It happens to me. I have to remove xserver-xgl after all. What can I do in this case to enjoy the desktop effect :|

---

### Post by frithiof on 2007-10-23
Sweet simple howto.
Worked like a charm on my ASUS W3000N laptop with ATI Mobility Radeon 9600 .

Thanks a bunch gerfuls!

---

### Post by segalion on 2007-10-23
Hello.
I would like to know if it is possible to use compiz + radeon driver (not fglxr) on a ati X200M card.

Thanks in advance.

---

### Post by gamedesignerwol on 2007-10-23
I just wanted to say thank you for hanging out to help people with what you know...that is very cool....and thanks for your help

---

### Post by gerfuls on 2007-10-23
> **mellflores1 said:**
> :confused::confused:i followed all the instructions and am still getting the error message. then i have to go into the system monitor and close GNOME-Appearance. How do I uninstall the server thingy? I'm still a linux n00b.:confused::confused:
what video card do you have?

---

### Post by dislocated on 2007-10-23
Thanks gerfuls,

I have a Radeon Mobility X1400 in my Dell inspiron 6400 and this worked just great!

---

### Post by gerfuls on 2007-10-24
> **analox said:**
> It happens to me. I have to remove xserver-xgl after all. What can I do in this case to enjoy the desktop effect :|

wait until the new fglrx opensource driver comes out (supposedly about a week) and use AIGLX

---

### Post by gerfuls on 2007-10-24
> **segalion said:**
> Hello.
I would like to know if it is possible to use compiz + radeon driver (not fglxr) on a ati X200M card.

Thanks in advance.

I don't think so. Why don't you want to use fglrx?

---

### Post by segalion on 2007-10-25
> **gerfuls said:**
> I don't think so. Why don't you want to use fglrx?

Thats because I use TVout to see video over a TV set, and the ATI fglrx has a very big bug inside that make tvout unusable (See [http://ati.cchtml.com/show_bug.cgi?id=309](http://ati.cchtml.com/show_bug.cgi?id=309) ). The last opensource radeon driver version has tvout support that works fine with XV (to render video) (See [http://ubuntuforums.org/showthread.php?p=3467287#post3467287](http://ubuntuforums.org/showthread.php?p=3467287#post3467287) ).

But seems that opensource radeon drivers dont have DRI (acelerated 3D) support for radeon X200 (See [http://dri.freedesktop.org/wiki/ATIRadeon#head-b70b9c2adfa2ca59ff505f071d2dd6bf6b44eebb](http://dri.freedesktop.org/wiki/ATIRadeon#head-b70b9c2adfa2ca59ff505f071d2dd6bf6b44eebb) and  [http://megahurts.dk/rune/r300_status.html](http://megahurts.dk/rune/r300_status.html) ).

---

### Post by WiseguyY2K on 2007-10-26
Thank you very much was very easy follow for me, who is somewhat new to Ubuntu.  Thank you again!:KS

---

### Post by newman on 2007-10-26
This driver works worse than the old one. I have nothing but major screen tearing to no end, and mythtv is slow and choppier than ever. ATI really suck shittt.

---

### Post by justjc on 2007-10-29
I can\t belive it this actually worked to make my x1600pro able to use some of the compiz effects on my desktop (Gutsy) :guitar:

Thanks a lot!

---

### Post by mahehellraiser on 2007-10-30
Problem..............i installed gutsy freshly..then tried to enable the ATI driver in restricted drivers and getting an error  " couldnt apply changes fix the broken packages first" ...........i didnt do anything ....fresh installation and i tried this how to.....but not working.......any suggestions:confused::confused::confused::confused:

---

### Post by kane357 on 2007-10-30
I did what was said and i am now at a blank white screen on my ubuntu machine. What do i do now.

---

### Post by segalion on 2007-10-31
New ati fglxr driver solve tvout XV crop image bug.
But in my X200M, feisty+compiz efects dont work: same white screen when turn up desktop effects.

---

### Post by StewartG on 2007-11-01
Sweet - finally got my lovelly effects back!

Thanks for the guide. 

:)

---

### Post by kolenkolen on 2007-11-13
This works great!!!!! Thanks a lot!!!!

---

### Post by IF-Rit on 2007-11-13
My VGA is ATI Radeon Xpress 200M
Are this config will work too??
or i must add some config again??

---

### Post by maki_03 on 2007-11-17
I experience an extreme lag when installing "xserver-xgl" in my system. I have an ATI mobility radeon X1600.

When I run fglrxinfo it shows that i have 3d acceleration enabled. But when I ran glxinfo, "no" in direct rendering showed up. Running xglgears even crashes the xsession. I had to remove the xserver-xgl installation. After uninstalling, my system went back to normal.

So does this mean that I won't be able to use compiz/advance desktop effects in my computer?

---

### Post by dominikgeisler on 2007-12-05
Works perfectly on Xpress 200G. Thanks a lot!

---

### Post by beginner111 on 2008-01-06
I have the radeon xpress 200g, and when i reboot after enabling restricted driver, it tells me the computer is running in low screen graphics mode. If i continue and look back at the window with restricted driver, the ati driver is marked disabled. On top of that, the internet stops to work! And desktop effects still don't work.  Any help with successfuly enabling the ati restricted driver would be appreciated.

---

### Post by Praill on 2008-07-11
> **Beggar said:**
> Several people I have been trying to help have reported that XGL is causing massive amounts of lag on there ATIs, mostly newer cards. Since I tend to just link to this thread, I wanted to point out that if you are trying to install desktop effects, you do not need to install xserver-xgl. Also if you do install it, find that it causes problems, then remove it, you need to set composite back to 1 as the uninstall sets it to 0 again. Thanks, and good luck!

I can second this. XGL is not needed at all. XGL makes your system slow and diables direct rendering so you can't use 3D applications. Therefore, imo its not worth it at all.

I'm using an Inspiron 6400 w/ a ATI Mobility x1400 and I got compiz (with direct rendering) using doing this:

1) enabling the ati restricted driver
2) running this command which overrides some compiz script check that has been put in place for ati cards:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
3) and changing the xorg.conf file to "1" from "0"

Thanks for the help and good luck all.

---

