---
title: "ati radeon xpress 200m"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by modustollens on 2007-10-04
I have been trying to get the desktop effects working on my laptop.  I have followed a good many 'how to' posts on multiple sites and I have queried my more capable ubuntu friends but I have not been successful yet.

My video card is an ati radeon express 200m.  There are lots of others with this particular card who who have reported problems getting the 3d acceleration working.


The ATI site claims:

"737-26907: Unsupported Features with ATI Linux Drivers

    The information in this article applies to the following configuration(s):

        * AIGLX
        * Beryl
        * Compiz
        * MythTV
        * TV TIME

    Currently, the following features are not supported with ATI Linux drivers.

        * AIGLX, Beryl, Compiz, MythTV, TV TIME
(https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge)"

Some of the online advice I found recommends updating the ATI driver first, which I find odd given the above.

Some users have stated that their ATI card works, but these are not users with the ATI radeon xpress 200m.

Has anyone got this particular card ATI working with either beryl or compiz? 

I am still searching and tinkering; should I be successful I'll post my procedure here; but if anyone has some advice I welcome it.

Thanks, 
MT

---

### Post by meindian523 on 2007-10-04
> **modustollens said:**
> 
Some users have stated that their ATI card works, but these are not users with the ATI radeon xpress 200m.

Has anyone got this particular card ATI working with either beryl or compiz? 

Yes,I have.

> **modustollens said:**
> 
I am still searching and tinkering; should I be successful I'll post my procedure here; but if anyone has some advice I welcome it.


I did these.

1>Installed fglrx driver from Restricted Drivers Manager.(BTW,I had Beryl working earlier,so the ATi site content is ********)
2>Installed Xgl

```
sudo apt-get install xserver-xgl
```

3>Wrote a script for Xgl to start automatically,copied from ubuntuguide.org.....
```
sudo gedit /usr/local/bin/startxgl.sh
```

4>Entered the following in the gedit window that opens:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```
Warning:For gnome only.There was a variant for KDE,but I don't remember it now.

5>Made the script executable:
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

6>Added a Gnome with Xgl session in the sessions menu available in login:
```

sudo gedit /usr/share/xsessions/xgl.desktop
```

7>Enter the following in the gedit window taht opens:

```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

8>Made the script executable:
```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

9>Added Vorian's repos to my sources.list(I don't know whether these are still available)
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras
```

10>Update and upgrade:
```

sudo apt-get update
sudo apt-get upgrade
```

11>Installed Compiz-Fusion
```

sudo apt-get  install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

12>Logged out,while logging in,selected Gnome with Xgl session from the Sessions menu

13>Pressed Alt+F2

14>Entered compiz --replace(that's a double dash ie - - without the space in between) 

and voila!

---

### Post by meindian523 on 2007-10-04
I think this is equivalent to a HOW-TO!:-P

---

### Post by meindian523 on 2007-10-04
You might get an error of unauthenticated keys due to missing public keys,but it's ok,we trust vorian.

---

### Post by luisromangz on 2007-10-04
I also have a Radeon Express 200M, and it works just the above poster wrote. The only difference is that I use Treviño's repository for the compiz packages. These packages are updated almost twice a week, so the have the newest features (ocasionally some bugs, too).

Check [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) for the deails.

---

### Post by modustollens on 2007-10-04
meindian523, 

Thank you for your sage advice and precious code: my machine is now flipping and swirling on a four-sided cube; I tried about 5 other 'how to' suggestions for ATI cards so I am happy that it worked this time.

I must now search and learn about these plug-ins.  The effects so far seem to run fine; my machine is the most inexpensive laptop one could buy about 1 year ago; it was less than 800 dollars (Canadian) and it has a 1.4 Celeron-m (its a Toshiba Satellite a 110). I put in another gig of ram just after I bought it; but I am surprised at how well it runs given the cost.

There were a few bugs and errors during the install, and the public key issue you mentioned arose.  The synaptic update manager reported that the dependencies were "broken"; I let the software run its course and the errors disappeared and the effects are still working.  I have only been using Ubuntu for about 15 days and I am not sure exactly what 'broken'  means but I assumed that the software would know what it is best to do.

The CompizConfig settings Manager is without any icons; I'll search around and see what comes up about this issue; maybe the only icon that is supposed to be there is the white page with the red x?

When I search for 'compiz' in the package manager a few uninstalled options pop up, e.g., 
"compiz-extra: extra third party plugins for compiz."  If I select 'install' it says that a whole bunch of other files will be removed, e.g., compiz; needless to say I am a bit coy about tinkering now that its working, though if I screw it up I will follow your instructions again...

Thanks,
MT

---

### Post by asousa on 2007-10-04
Does anyone know if this procedure will work with the x1200? That is oboard ATI video on my new ASUS mobo...

thanks

---

### Post by santiagoward2000 on 2007-10-06
I could run Beryl and Compiz-Fusion with my Xpress m200.

---

### Post by Faud on 2007-10-06
> **modustollens said:**
> meindian523, 


The CompizConfig settings Manager is without any icons; I'll search around and see what comes up about this issue; maybe the only icon that is supposed to be there is the white page with the red x?

Thanks,
MT

Gratz on getting it started. It shoulnt be a white page with an X on it and nothing else


> I also have a Radeon Express 200M, and it works just the above poster wrote. The only difference is that I use Treviño's repository for the compiz packages. These packages are updated almost twice a week, so the have the newest features (ocasionally some bugs, too).

Check [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) for the deails.

I would check out this guys suggestion for your packages

---

### Post by Faud on 2007-10-06
> 9>Added Vorian's repos to my sources.list(I don't know whether these are still available)

Code:
deb [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras
deb-src [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras10>Update and upgrade:

Code:
sudo apt-get update
sudo apt-get upgrade11>Installed Compiz-Fusion

Code:
sudo apt-get  install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

This is where your packages start and end. Meindian523, I think you wrote an awesome how-to here. I think it will help a lot of people with this card. Props to you

---

### Post by hamishau on 2007-10-15
Just letting you know that on an ASUS A6Rp laptop (Celeron 1.6 GHz, 1 GB RAM shared 128 MB with video card, which is Radeon Express 200M), this works PERFECTLY! I am running Feisty 7.04.

I had a few issues with the ATI driver, but used the Envy utility to uninstall and reinstall it, and then all worked as above. Am now enjoying playing with various effects.

From a productivity point of view I may end up disabling most of them! But they are certainly sure to amuse people who seem them when I do have them on!

Thanks very much for the work you have put into this thread.

Hamish

---

### Post by meindian523 on 2007-10-15
@All

Thanx for the glowing tributes.The wok above is not really my brainchild or something.I just copy-pasted instruction to install my version of C-F and did the same here(ie copy-pasted) so i could help others.Particularly,I did these steps to MIGRATE from Beryl to C-F.It was a lot easier than doing C-F from scratch.:)The original tutorial was Vorian's,so tributes to him,but his so-called *UPDATED* HOW-TO has all questions and answers and no HOW-TO!So this had to be repeated somewhere.Therefore.....

---

### Post by sandpaperback on 2007-10-17
This worked perfectly for me on the first try.  Thank you so much.  There seem to be a few bugs here and there (like a large black area when I first open Firefox), but nothing unbearable.  Thanks!

---

### Post by tadah on 2007-10-27
> **meindian523 said:**
> 
9>Added Vorian's repos to my sources.list(I don't know whether these are still available)
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras
```


after this step i get:
**GPG error: [http://debs.vorian.org](http://debs.vorian.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BFD361BD74C79EA**

[img]http://static.linkomanija.net/pic/smilies/confused.gif[/img]

and if i ignore it, after **compiz --replace** i get:
```

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

what do i do wrong?

---

### Post by vmsda on 2007-10-27
> **meindian523 said:**
> ...

12>Logged out,while logging in,selected Gnome with Xgl session from the Sessions menu

13>Pressed Alt+F2

14>Entered compiz --replace(that's a double dash ie - - without the space in between) 

and voila!

I have an HP Pavilion with this very same graphics card, and newly installed Gutsy. I followed the instructions in the quoted append but, in step 12, instead of logging out, I accidentally shutdown and restarted. After a lot of thinking, all I get is a black screen :confused:. If this  is due to my misstep, any hints on how to correct the situation?

Thank you in advance.

---

### Post by santiagoward2000 on 2007-10-27
> **vmsda said:**
> I have an HP Pavilion with this very same graphics card, and newly installed Gutsy. I followed the instructions in the quoted append but, in step 12, instead of logging out, I accidentally shutdown and restarted. After a lot of thinking, all I get is a black screen :confused:. If this  is due to my misstep, any hints on how to correct the situation?

Thank you in advance.

Hi vmsda,
Sorry to hear it's not working. I don't know how to fix this, but I believe it has nothing to do with your "misstep".

---

### Post by meindian523 on 2007-10-28
Well,a reboot and black screens have got nothing to do with each other.....AFAIK.I just said logout and log back in since only that is required to have the changes take effect.

And maybe I should add a disclaimer:
I'm NO expert!
The above procedure was done in Feisty.I've no idea about Gutsy until my requested CDs arrive.I think this issue was raised in very many threads related to C-F.A search of the forums would throw up good results.

---

### Post by vmsda on 2007-10-28
> **meindian523 said:**
> ... I just said logout and log back in since only that is required to have the changes take effect.

For a start, thank you all for your feedback, even if (and especially if) from non-experts :). 

1.Regarding the quote above, it strikes me as odd since, in my system, as soon as I enabled the ATI driver from the Restricted Drivers Manager window, the system informs me that a restart is needed in order for the changes to take effect. (Maybe because I have Gutsy and not Feisty, but somehow it does not look like this would be the case.)

2. I naturally delayed the restart until I had gone through meindian523's recipe, with the results which I sadly had to report in my previous append. :confused:

3. To recover from the black screen, I have to reboot in recovery mode. So today I decided to poke around in Xorg.0.log.old, and look what I have found in respect of my last botched attempt:

      Kernel Module Version Information
                Name: fglrx
                Version: 8.37.6
                Date: May 25, 2007
                Desc: ATI FireGL DRM kernel module
      Kernel model version does *not* match driver
      Incompatible kernel module detected - HW accelerated Open GL will not work

Maybe this is the reason for my problem. Wouldn't it be nice to have an expert around to give a hint on how to fix this?!

---

### Post by meindian523 on 2007-10-28
> **vmsda said:**
> For a start, thank you all for your feedback, even if (and especially if) from non-experts :). 

1.Regarding the quote above, it strikes me as odd since, in my system, as soon as I enabled the ATI driver from the Restricted Drivers Manager window, the system informs me that a restart is needed in order for the changes to take effect. (Maybe because I have Gutsy and not Feisty, but somehow it does not look like this would be the case.)

The installation of Restricted Drivers does require a reboot,what I meant was that the installation of Xgl,installation of C-F,addition of Gnome with Xgl session don't need reboot to take effect.A simple kill of Xserver and re-login would enable those changes..... 

> **vmsda said:**
> 2. I naturally delayed the restart until I had gone through meindian523's recipe, with the results which I sadly had to report in my previous append. :confused:

Maybe that's what caused the problem.....I rebooted as soon as I was told to(If I am getting you correctly,you installed everything and then went in for reboot,right?)

> **vmsda said:**
> 3. To recover from the black screen, I have to reboot in recovery mode. So today I decided to poke around in Xorg.0.log.old, and look what I have found in respect of my last botched attempt:

      Kernel Module Version Information
                Name: fglrx
                Version: 8.37.6
                Date: May 25, 2007
                Desc: ATI FireGL DRM kernel module
      Kernel model version does *not* match driver
      Incompatible kernel module detected - HW accelerated Open GL will not work

Maybe this is the reason for my problem. Wouldn't it be nice to have an expert around to give a hint on how to fix this?!

Cool,I didn't know such a log existed.....!I guess what you need to do is do a kernel update.....not sure tho'....you might want to hang around till the experts come along......

Regards

---

### Post by sevenearths on 2008-02-14
this is all good and well, though does anyone know how to do this on kubuntu. I don't want to move back to ubuntu, I like the interface of KDE to much :)

---

### Post by santiagoward2000 on 2008-02-15
> **sevenearths said:**
> this is all good and well, though does anyone know how to do this on kubuntu. I don't want to move back to ubuntu, I like the interface of KDE to much :)

Hi!
Well, that depends on which version you are using. If you are in Gusty this is much simpler. First install your card's drivers using **Restricted Drivers Manager**. Then, open **Adept** and install **compiz** and **xserver-xgl**, or open a Konsole and type:
```
sudo apt-get install xserver-xgl
sudo apt-get install compiz
```
Then restart your computer and try to run:
```
compiz --replace
```
That should do it.
If you are using Feisty or older, then just follow this guide, but replacing **gedit** with **kate** and **exec gnome-session** with **exec startkde**.
I think that's it. Just post if you have any problems!
Goode luck!!! :KS

---

### Post by meindian523 on 2008-02-18
Also,it's now preferable/advisable to install using Forlong's guide since they are packages backported from Gutsy for Feisty users and enjoy support for updates and suff.....also other eye-candy like AWN and stuff presume that by default you have been using Forlong's instructions to install C-F.

[http://ubuntuforums.org/showthread.php?t=536149](http://ubuntuforums.org/showthread.php?t=536149)

---

### Post by broadbeans on 2008-03-30
> **meindian523 said:**
> Yes,I have.



I did these.

1>Installed fglrx driver from Restricted Drivers Manager.(BTW,I had Beryl working earlier,so the ATi site content is ********)
2>Installed Xgl

```
sudo apt-get install xserver-xgl
```

3>Wrote a script for Xgl to start automatically,copied from ubuntuguide.org.....
```
sudo gedit /usr/local/bin/startxgl.sh
```

4>Entered the following in the gedit window that opens:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```
Warning:For gnome only.There was a variant for KDE,but I don't remember it now.

5>Made the script executable:
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

6>Added a Gnome with Xgl session in the sessions menu available in login:
```

sudo gedit /usr/share/xsessions/xgl.desktop
```

7>Enter the following in the gedit window taht opens:

```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

8>Made the script executable:
```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

9>Added Vorian's repos to my sources.list(I don't know whether these are still available)
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras
```

10>Update and upgrade:
```

sudo apt-get update
sudo apt-get upgrade
```

11>Installed Compiz-Fusion
```

sudo apt-get  install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

12>Logged out,while logging in,selected Gnome with Xgl session from the Sessions menu

13>Pressed Alt+F2

14>Entered compiz --replace(that's a double dash ie - - without the space in between) 

and voila!

I followed these instructions and it did not work initially on my Gutsy installation.  Then I undid everything and updated everything (about 261MB), rebooted.  Then included the restricted drivers and hurray, it worked like a charm.  Thanks Meindian :guitar:  I can now do all the fancy stuff with Compiz with my ATI Radeon Xpress 200 graphics card including the cube gears, fire, water, etc.  I have increased the RAM allocation to 128MB as I have 4Gig RAM!  My desktop is looking wonderful.  I was about to buy a new graphics card and now I won't.  

I now want to try to get something working on my Inspiron 4000 laptop which has the 128 AGP ATI Rage Mobility card.  But I guess it won't support compiz though I have managed to get direct rendering working on it after following instructions from a thread.

---

