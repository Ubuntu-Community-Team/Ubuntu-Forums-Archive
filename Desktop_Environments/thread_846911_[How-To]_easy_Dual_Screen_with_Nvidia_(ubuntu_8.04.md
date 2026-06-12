---
title: "[How-To] easy Dual Screen with Nvidia (ubuntu 8.04)"
date: 2008-07-02
forum: Desktop Environments
---

### Post by mike16889 on 2008-07-02
i made a simple tutorial for setting up dual screen.

also available [HERE](http://flashplace.net/index.php?page=11) and to download [HERE](http://flashplace.net/Dual Screen.pdf)(PDF)

[CENTER]**[SIZE="5"]Setting up dual screen in Ubuntu 8.04 LTS Desktop[/SIZE]**

[SIZE="3"]nVidia[/SIZE]

*By Michael Richards*[/CENTER]


It took me a wile figure out how to do it but now that i'v done it its awesome. To start with you have to go into 'System > Administration > Hardware Drivers' and enable the 'Proprietary drivers' for the graphics card. You will most likely have to do a restart in order for the settings to take effect.

[CENTER][[IMG]http://img292.imageshack.us/img292/8966/screenshothardwaredrivedb6.th.png[/IMG]](http://img292.imageshack.us/my.php?image=screenshothardwaredrivedb6.png)[/CENTER]

Once you've done that you'll want to download and install the 'NVIDIA X Server Settings' app. To do this just go to 'Applications > Add/Remove...' then just do a search for 'nvidia' in the list of resualts selec 'NVIDIA X Server Settings' and check the box next to it.
[CENTER][[IMG]http://img131.imageshack.us/img131/3743/screenshotaddremoveapplwc4.th.png[/IMG]](http://img131.imageshack.us/my.php?image=screenshotaddremoveapplwc4.png)[/CENTER]

Click 'Apply Changes' and restart if need be. Then we want to configure the screens to do this go to 'System > Administration > Nvidia X Server Settings'. A small box will come up and you will need to select 'X Server Display Configuration'. The small box will get bigger and look somewhat like the windows nvidia control panel. One of your moniters will be disabled (probably the one on DVI) click on it in the window and click 'Configure'. Once you get to this point there will be two options for dual screen.



   1.Separate X screen


   2.TwinView


'TwinView' is only really any good if you have two or more identical screens because it spans the display over all screens. Were as 'Separate X screen' is better for multiple screens of varying resolutions and sizes. It will basically allow you to have two separate 'Desktops' allowing you to split up your screens into two different 'computers' for lack of a better word.


TwinView


setting up 'TwinView' is a sinch just check the box and apply it

[CENTER][[IMG]http://img103.imageshack.us/img103/5723/screenshotconfiguredispqd0.th.png[/IMG]](http://img103.imageshack.us/my.php?image=screenshotconfiguredispqd0.png)[/CENTER]

Separate X screen


Setting up 'Separate X screen' can be more difficult to set up first you want to select that instead of the other.
[CENTER][[IMG]http://img518.imageshack.us/img518/9548/screenshotconfiguredispdf3.th.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshotconfiguredispdf3.png)[/CENTER]

You will then want to set its location. For mine it was fine the way it is by default but you may need to change it. Once you have all your settings the way you like it you will need to 'Save to X Configuration File' if this fails you will have to take the following steps if not skip ahead to 'Restarting X'.


   1.Navigate to '/etc/x11/' and select the file 'xorg.conf' copy it and then past it to the same directory calling it something like 'xorg.conf_backup'.


   2.You will then need go into terminal ('Applications > Accessories > Terminal') and type following command:

     ```
 #: sudo gedit /etc/x11/xorg.conf
```


   3.You will probably be promoted for a password, enter it and continue on.


   4.A test editor will popup with a hole heap of stuff in it delete the lot and go back to the 'NVIDIA X Server Settings dialog and click 'Save to X Configuration File' then 'Show Preview.

[CENTER][[IMG]http://img80.imageshack.us/img80/72/screenshotsavexconfigurgm6.th.png[/IMG]](http://img80.imageshack.us/my.php?image=screenshotsavexconfigurgm6.png)[/CENTER]


   5.Copy the lot and then past it into the file you opened step 3. save and close the file


Restarting X


now restarting 'X' is easy, all you have to do is press 'Ctrl + Alt + Backspace'. BE WARNED it is nearly the same as restarting your computer but a lot faster so make sure you save documents and bookmark web pages before doing it.



[CENTER]**[SIZE="3"]THE END[/SIZE]**[/CENTER]

---

### Post by terry_gardener on 2008-07-02
thanks for the how to. 

i have found when at the stage using Save to X Configuration File it errors because you are accessing the nvidia settings using user account access to solve this you can just at the beginning opening the nvidia settings open the terminal and type "sudo nvidia-settings" and type in password and then when you get to the part to save the x config file it will work.

---

### Post by mike16889 on 2008-07-02
thanx. i'm new to ubuntu and linux in genaral so i was'nt shore of the cammand to luanch the nvidia-settings so i went the way i did know...

---

### Post by terry_gardener on 2008-07-03
the command to launch the nvidia settings is: 

sudo nvidia-settings

---

### Post by StickyC on 2008-07-12
I'm not seeing the nvidia X server settings package under Hardy for AMD64 - is this an i386-only package?

If so, is there an easy how-to for getting dual-view under Hardy for AMD64 (kinda paranoid about manually editing xorg.conf)

[UPDATE] User error - You need to make sure Add/Remove Applications is set to show: All available applications or Third Party Applications (it is not by default).

---

### Post by overdrank on 2008-07-12
> **StickyC said:**
> I'm not seeing the nvidia X server settings package under Hardy for AMD64 - is this an i386-only package?

If so, is there an easy how-to for getting dual-view under Hardy for AMD64 (kinda paranoid about manually editing xorg.conf)

[UPDATE] User error - You need to make sure Add/Remove Applications is set to show: All available applications or Third Party Applications (it is not by default).

HI and you can also use synaptic manager to install nvidia-settings.:KS

---

### Post by mike16889 on 2008-07-14
> **StickyC said:**
> 
[UPDATE] User error - You need to make sure Add/Remove Applications is set to show: All available applications or Third Party Applications (it is not by default).

sorry about not putting that in the tut i allready had that set in mine when i set up dualscreen...

---

### Post by vprasaj on 2008-07-14
Question for all with dual screen / twinview.
Do you get panels expanded over both screens?
Is video in fullscreen mode over both screens?
I can't make it work...

---

### Post by vprasaj on 2008-07-14
> **vprasaj said:**
> Question for all with dual screen / twinview.
Do you get panels expanded over both screens?
Is video in fullscreen mode over both screens?
I can't make it work...

Nevermind.

[Solution.]("http://ubuntuforums.org/showthread.php?t=859042")

---

### Post by drjonze on 2008-08-18
> **terry_gardener said:**
> thanks for the how to. 

i have found when at the stage using Save to X Configuration File it errors because you are accessing the nvidia settings using user account access to solve this you can just at the beginning opening the nvidia settings open the terminal and type "sudo nvidia-settings" and type in password and then when you get to the part to save the x config file it will work.

THANK YOU!!!

I spent hours on this yesterday. I read your post and fixed my issue in minutes. It was such a minor step. I thought it was odd that when I launched this app it didn't prompt for a password like all the other apps in Administration.

---

### Post by kunks112 on 2009-06-09
well I tried this method, and when I delete the inside of the file, I cannot resave into it. It saves I dont have the right privledges.

I cant delete the file and rename the backup either.

now I restarted and get nothing but a black screen.

can I get help on getting my moniters back up?

---

### Post by mike16889 on 2009-06-09
are you sure you were using the sudo prefix n ur commands?

---

### Post by bricedebrignaisplage on 2009-06-11
I have a nvidia GeForce4 MX 440 AGP 8x
An ok computer (P4 3GHz, 1GB of ram)

I want to have dual screen: one monitor as main and TV on the side, so that I can play a DIVX when my wife is using the computer.
I installed nvidia drivers using envy and also with jockey (gave same results) and configure the x server with 'nvidia x server settings'.

So I choose 'separate x screens' with xinerama enabled, save the configuration file and restart. It works... except that it's slow. It's especially visible when I run KStars: rotating the sky is REALLY slow. And it slows down over apps as well, maybe less evidently. Playing movies is a pain too.

But if I use a clone mode, everything's fine (except that I can't watch a movie while my wife is using the writing emails).

So I'd like to know if I'm doing something wrong, or is it because the nvidia drivers / X / xinerama / linux has a problem, or if it's because my video card is too old or damaged. I'd rather avoid to buy a new card and realize that it's still slow.

---

### Post by mike16889 on 2009-06-13
not sure how to help with that,  never used s-video out b4, but there is abit of a bug with compiz that may be a problem, run this script and if it fixes the problm just add it to start up.

```
#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
gtk-window-decorator --replace &
```

(place in a whatever.sh works best)

also, it is fairly probable its ur gcard, running duel screens can tax graphics performance quite hard sometimes, altho my old 6200 ran fine with 1280x1024+1690x1050 in 8.04 with thewobbaly windows enabled

---

### Post by bricedebrignaisplage on 2009-06-22
Thanks for your response mike16889

compiz is not installed (nor is gtk-window-decorator). I am using KDE 3.5. So I don't think that's the issue. Any other idea somebody?

I repeat my question: I'd like to know if I'm doing something wrong, or is it because the nvidia drivers / X / xinerama / linux has a problem, or if it's because my video card is too old or damaged. I'd rather avoid to buy a new card and realize that it's still slow.

---

### Post by mike16889 on 2009-06-22
sorry i'm outa idea's only used kde 4 like 20 mins on my eee, also dont have ubuntu installed atm so i can'tt fiddle round 2 see if i can replicate it.

would ya be able to try plugging in a second vga mniter in and see if its just s-video or a second screen in genaral?

---

