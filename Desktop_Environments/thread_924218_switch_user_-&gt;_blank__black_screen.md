---
title: "switch user -&gt; blank / black screen"
date: 2008-09-19
forum: Desktop Environments
---

### Post by elaintarha on 2008-09-19
Hey,

I saw few other topics on this but not the same thing or any solution to it:

I have 2 users on 8.04 and when switching users the screen just goes black. Can press ctrl-alt-f1 to go to some text login but how do i get this to work?

Thanks,
TI
imo

---

### Post by mister_pink on 2008-09-19
Do you have an ati graphics card? I can't remember the exact nature of the issue, but I seem to remember having this issue when I had a radeon 9700 and as far as I could tell there was a bug in the restricted driver that completely prevented fast user switching. I never did find a workaround though.

---

### Post by elaintarha on 2008-09-19
> **mister_pink said:**
> Do you have an ati graphics card? I can't remember the exact nature of the issue, but I seem to remember having this issue when I had a radeon 9700 and as far as I could tell there was a bug in the restricted driver that completely prevented fast user switching. I never did find a workaround though.

I have no idea what card it is, its internal on the motherboard. i have fujitsu siemens scaleo L from 5 years back

---

### Post by elaintarha on 2008-09-20
hey this is really frustrating, how is my graphics card related to damned switch user!! heeeelp

---

### Post by Sef on 2008-09-20
>  		hey this is really frustrating, how is my graphics card related to damned switch user!! heeeelp 	

It would not being able to switch users.   Now what is your hardware, especially your graphics card.  

Applications > Accessories > Terminal

the paste or type in this code:

```
lspci
```

paste the results in this thread.

---

### Post by elaintarha on 2008-09-30
> **Sef said:**
> It would not being able to switch users.   Now what is your hardware, especially your graphics card.  

Applications > Accessories > Terminal

the paste or type in this code:

```
lspci
```

paste the results in this thread.

thanks but i'm back to XP i cant take this its too much hassle

---

### Post by atitupan1 on 2008-09-30
Hi,
Same problem not getting the correct solution I have 2 users on 8.04 but when switching the screen goes black.


________________________________________________________

[Houston Gift Shop](http://www.florist-flowers-roses-delivery.com/texas/houston_tx.html) [loans with no credit check](http://www.cheaponline-loans.co.uk/help/no-credit-check-loans.php) [pisos vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [download iPhone ringtones](http://www.myringtoneshub.com/specials/buy-cell-phone-ringtones.htm)

---

### Post by c-shadow on 2008-10-02
> **atitupan1 said:**
> Hi,
Same problem not getting the correct solution I have 2 users on 8.04 but when switching the screen goes black.


________________________________________________________

[Houston Gift Shop](http://www.florist-flowers-roses-delivery.com/texas/houston_tx.html) [loans with no credit check](http://www.cheaponline-loans.co.uk/help/no-credit-check-loans.php) [pisos vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [download iPhone ringtones](http://www.myringtoneshub.com/specials/buy-cell-phone-ringtones.htm)

Do you use the User switch applet?
I'm having the same problem since ubuntu 7.10. Sometimes after switching I get some console screen., but can still switch with CTRL-ALT-Fxx keys. Also switching via the power button on the panel works OK.

---

### Post by ricky045 on 2008-10-11
If I "Switch Users" and logon to a second user, all is well. If I "Switch
User" back again, all is well. But if I "Log off" the second user, the UAC
screen does not appear - just a blank, black screen that doesn't seem to let
me do anything! Have to force power off and reboot.

Anyone else experienced this?
===============================================
ricky045

[low rate loans](http://www.cheaponline-loans.co.uk/)

---

### Post by Avionix on 2008-10-11
I am having the same problem, if I switch user the screen goes black, it sometimes comes good again after 15 to 20 mins or my screen starts complaining that the resolution and refresh rate 'is not optimum'. The only way to get it back so far is to disconnect the power from the screen for 15 mins or so and then power it up again, it's very frustrating especially with 4 users on the machine. I/ve only had this problem since upgrading to Hardy from Dappper

---

### Post by Avionix on 2008-10-12
Hello Sef if you are there, the results of lspci are as follows:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I noticed nobody answered your question, I would like to sort this problem out. I have Hardy on my laptop which works perfectly and was installed fresh. It's just my desktop which I upgraded from Dapper which is giving me a lot of grief at the moment (see also my posts on not being able to mount USB devices)

Cheers,

Avionix

---

### Post by Avionix on 2008-10-13
Further info, it happens every time someone logs out now, sometimes the screen immediately complains about the resolution not being optimum. Anyone got any clues?

---

### Post by Avionix on 2008-10-26
This is really bugging me now, everytime someone logs out or switches user we have to disconnect the power from the screen and leave it for 20 mins or so, the audio indicates that a new log in screen has been presented but the screen is completely black. Has anyone got any idea how I would troubleshoot this?

---

### Post by Avionix on 2008-10-27
It appears to be a problem with my screen, the first thing I checked of course weeks ago.I had checked it with another computer and all appeared to be well. I had reason tonight to connect my company supplied laptop (which runs XP) to the screen and I got the same complaints about the resolution and refresh rate. I will report further when I have replaced the screen.

---

### Post by driven1 on 2008-11-20
It may be related to compiz, but I haven't had time to confirm. I have ati graphics, but the fast user switching applet worked fine when I first built the machine. After multiple upgrading and configuration, suddenly switching from one user to another causes the display to go blank/gray. I haven't had a chance to remove compiz to verify the solution. Hope to get to that this weekend. If it works I'll follow up here.

---

### Post by alladnsane on 2009-01-26
I have ubuntu 8.04 fully updated. integrated intel video.  desktop visual effects set to "none" on all users.

If I am logged on to user A, switch to user B, switch back to user A and logoff, switch to user B (already logged in) then try to switch back to user A, I get the blank black screen with flashing curser. I can alt Fx to tty terminal but alt F7 brings me back to black screen.

Changing users using the switch users option at the power button works fine

---

### Post by bastafidli on 2009-02-05
I have the same exact problem. 50% of the times I try to switch between users or 8.04 the screen goes to blank and ater a while monitor goes to sleep. I then have to repeatedly try CTRL+ALT+F7 or CTRL_ALT+F9 and after many tries I get back the lock screen password dialog and I may try to switch again. Multiple times the monitor also switches to wrong resolution (default is 1920x1200 and it switches to 1600x1200). This is with NVidia proprietary driver without any advanced effects turned on.

---

