---
title: "screen resolutions only recognize 800 X 600"
date: 2008-08-10
forum: Desktop Environments
---

### Post by abrand888 on 2008-08-10
I am running on my Optiquest Q9 a screen resolution of 1024 X 768 in Windows but in screen resolutions it doesn't show anything other than 640 X 480 and 800 X 600. In my old version of Ubuntu 7 I was running 1024 X 768. My monitor is a 19" monitor.

How can I get higher resolutions.

Thanks

---

### Post by overdrank on 2008-08-10
> **abrand888 said:**
> I am running on my Optiquest Q9 a screen resolution of 1024 X 768 in Windows but in screen resolutions it doesn't show anything other than 640 X 480 and 800 X 600. In my old version of Ubuntu 7 I was running 1024 X 768. My monitor is a 19" monitor.

How can I get higher resolutions.

Thanks

Hi and I am assuming you are using Hardy 8.04, what is the model of the graphics card? Have you tried using the command ```
gksu displayconfig-gtk
```

---

### Post by abrand888 on 2008-08-10
My motherboard has built in graphics and I am not yet using a graphics card. I guess from your reply that if I was using a graphics card it might see higher resolutions.

Might it be possible to use the built-in graphics on the motherboard ? I am using a ECS motherboard GF6100-M754.

Where do I enter the command, in terminal mode ?

Thanks

---

### Post by abrand888 on 2008-08-10
> **abrand888 said:**
> my motherboard has built in graphics and i am not yet using a graphics card. I guess from your reply that if i was using a graphics card it might see higher resolutions.

Might it be possible to use the built-in graphics on the motherboard ? I am using a ecs motherboard gf6100-m754.

Where do i enter the command, in terminal mode ?

Thanks

:ks

---

### Post by overdrank on 2008-08-10
> **abrand888 said:**
> My motherboard has built in graphics and I am not yet using a graphics card. I guess from your reply that if I was using a graphics card it might see higher resolutions.

Might it be possible to use the built-in graphics on the motherboard ? I am using a ECS motherboard GF6100-M754.

Where do I enter the command, in terminal mode ?

Thanks

Hi and yes you can use the terminal or the alt, F2 keys. The web says you motherboard has the nvidia 6100 graphics chipset and have you enabled the drivers under system, administration, hardware drivers?

---

### Post by abrand888 on 2008-08-10
I just enbabled the Nvidia drivers, computer rebooted but as soon as I typed in the password, the screen went blank and I get a screen signal over range. I then rebooted hit escape selected both 2.6.24 19 and 16 generic recovery and I still get signal over range after typying in my password.

At this time I can not get into Ubuntu. How can I get back into Ubuntu ?

---

### Post by overdrank on 2008-08-10
> **abrand888 said:**
> I just enbabled the Nvidia drivers, computer rebooted but as soon as I typed in the password, the screen went blank and I get a screen signal over range. I then rebooted hit escape selected both 2.6.24 19 and 16 generic recovery and I still get signal over range after typying in my password.

At this time I can not get into Ubuntu. How can I get back into Ubuntu ?

You may try and boot into recovery mode and use the xfix option. Which is the usually the second choices from the grub. Hopefully this will get you back to the desktop.

---

### Post by abrand888 on 2008-08-10
Xfix fixed it and I then continued to normal boot but every time I enable the Nvidia drivers and I tried it four times, it states signal over range. Is there another way like what you wrote before to get to 1024 X768 because something is either wrong with Nvidia driver in Ubuntu or maybe Ubuntu has a problem itself.

Thanks.

---

### Post by richie42 on 2008-08-10
> **abrand888 said:**
> Xfix fixed it and I then continued to normal boot but every time I enable the Nvidia drivers and I tried it four times, it states signal over range. Is there another way like what you wrote before to get to 1024 X768 because something is either wrong with Nvidia driver in Ubuntu or maybe Ubuntu has a problem itself.

Thanks.

Your problem seems eerily similar to mine....

---

### Post by pietjanjaap on 2008-08-11
With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by armandh on 2008-08-11
similar problem other hardware

it was the monitor's PnP function not working 
a different monitor got all the resolutions due it.
this was right after installing 8.04.

---

### Post by RikoW on 2008-08-11
Hi,

I had some strange resolution issues when I upgraded to 8.04. This on a laptop with an internal 1024x758 screen, which sometimes is hooked up via a docking station to a TFT with 1280x1024. However, I would never get a high resolution on this which the standard tool.

For, installing grandr from the repositories and setting the resolution with it fixed my problems.

Hope, it'll help you, too :)

Good luck,

              Riko

---

### Post by abrand888 on 2008-08-11
pietjanjaap

I would appreciate it if you could explain to me in simple terms what I need to do to get the video driver working. I am new at this and simple steps directing me will greatly be appreciated.

Thanks

---

### Post by abrand888 on 2008-08-11
> **RikoW said:**
> Hi,

I had some strange resolution issues when I upgraded to 8.04. This on a laptop with an internal 1024x758 screen, which sometimes is hooked up via a docking station to a TFT with 1280x1024. However, I would never get a high resolution on this which the standard tool.

For, installing grandr from the repositories and setting the resolution with it fixed my problems.

Hope, it'll help you, too :)

Good luck,

              Riko
what is grandr and how can I use it ?

Thanks

---

### Post by abrand888 on 2008-08-11
I decided to try Ubuntu 7.10 to install on my drive because I brought home a graphics card and it corrupted Ubuntu 8.04 and it showed me a resolution of 1024 X 768. My problem with 7.1 was that it didn't recognize my cable connection like Ubuntu 8.04 automatically so there must be something wrong with the Nvidia 6100 driver.

I would like very much to stay with 8.04 and will appreciate help in getting 8.04 to work with 1024 X 768 resolution.

Thanks

---

### Post by RikoW on 2008-08-12
> **abrand888 said:**
> what is grandr and how can I use it ?

Thanks

"grandr" is a gui interface to xrandr

```
> man xrandr
NAME
       xrandr - primitive command line interface to RandR extension

Xrandr is used to set the size, orientation and/or  reflection  of  the
outputs for a screen. It can also set the screen size.  There are a few
global options; the rest modify a  particular  output  and  follow  the
specification of that output on the command line.


```

to install, open a terminal and type:

```

> sudo apt-get install grandr

```

to start it, use again the command line and just type
```

> grandr

```

The GUI is just easier to use. You fire it up and it detects the connected screens and shows the available resolution.

What I had to do to get the correct resolution when connecting my external big screen was:
- turn of the internal display (tab Basic, set Off)
- in the section for the external screen select the mode/resolution by hand in the basic tab, click apply

that was it! The screen resolution settings using System -> Preferences -> Screen Resolution didn't do anything for me.

All this, I did with the video driver Ubuntu installed by default. Mind you, I'm having an ATI radeon card ...

Hope that helps,

    Riko


PS: Before I was running the previous Ubuntu LTS (6.06?) which didn't require any gymnastic like that.

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by abrand888 on 2008-08-12
I goofed. I was in terminal mode and typed in sudo apt-get grandr instead of sudo apt-get install grandr and I am unable to do anything because it states that I interupted dpkg and must run it manually.

Please tell me how to get out of my jam. I appreciate your help and need more assistance.

thanks

---

### Post by RikoW on 2008-08-12
Hi,

I'm not sure, I understand what happened :( Your first (goofed) command should have just resulted in an error message, but not block apt-get from being used further:

```

> sudo apt-get grandr
E: Invalid operation grandr
> sudo apt-get install grandr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grandr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Maybe, you just close your terminal, open a new one, issue

```
sudo apt-get install grandr
```

and post the output.

You could also try to install grandr using synaptics. However, if there is something wrong with dpkg, I suspect synaptic will not run either.

Cheers,

                Riko

---

### Post by abrand888 on 2008-08-12
Hi,

I figured out my problem and was able to install grandr but it only shows 800 X 600 and not any higher resolutions.

Any new ideas to try ?

Thanks for your help once again

---

### Post by RikoW on 2008-08-12
could you post the output of 

```

> xrandr
```

from a terminal?

---

### Post by abrand888 on 2008-08-12
screen 0  minimum 640 X 480  current 800 X 600 maximum 800 X 600

defaulted connected 800 X 600+0+0 0mm X 0mm

800 X 600   61.0*

640 X 480   61.0*

I was able to get automaticall 1024 X 768 when I installed Ubuntu 7.04 so the driver in 7.04 found the resolution automatically and this version not yet.

---

### Post by RikoW on 2008-08-12
Well at least, that confirms that your installation only supports 800x600 resolution.

I would guess, that means you need to update the graphics driver. I'm sorry to say, that it's a long, looonnnngggg time since I had to do that and never since I'm running Ubuntu. Following one of the hints in the previous posts, you could try and install the nvidia driver using envyng:

```

> sudo apt-get install envyng-gtk
> sudo envyng-gtk

```

This little gui lets you install nvidia and ati drivers as I just saw. However, from here on you are on your own, if there is no other kind soul to give you advise.

Good luck,
 
            Riko

---

### Post by abrand888 on 2008-08-12
RikoW,

I am back to square one. I did everything you stated and at first I thought I was in 1024 X 768 but as soon as I rebooted, I was back to 800 X 600. I believe I have four choices to contemplate.

1. Buy another graphics card and see if I can get 1024 X 768
2. Leave it the way it is at this time.
3. Go back to ver 7.04 because the Nvidia driver works better than in ver 8.04 but I don't understand why it didn't configure my cable connection to automatically go on line. Would you be able to assist me if I were to go back to Ubuntu 7.04 ?
4. Ask Nvidia why their driver doesn't work in 8.04 ?

What are your thoughts ?

Thanks again. I appreciate your help.

---

### Post by RikoW on 2008-08-12
> 
I am back to square one. I did everything you stated and at first I thought I was in 1024 X 768 but as soon as I rebooted, I was back to 800 X 600. I believe I have four choices to contemplate.


Did you install something via envy?
Why did you think it worked originally? What is the output now when you run xrandr?

> 
1. Buy another graphics card and see if I can get 1024 X 768
2. Leave it the way it is at this time.
3. Go back to ver 7.04 because the Nvidia driver works better than in ver 8.04 but I don't understand why it didn't configure my cable connection to automatically go on line. Would you be able to assist me if I were to go back to Ubuntu 7.04 ?
4. Ask Nvidia why their driver doesn't work in 8.04 ?


I would not give up yet on your card and 8.04 (even though at the moment I don't really have a good idea how to continue). I read somewhere that some older Nvidia drivers work better than the latest one. If I remember the envyng-gtk window correctly, it gives you the choice of 3 versions. Did you try the other one, too?

Your network card issue under 7.04 surprised me. Usually cable connections should be pretty painless. Did you google if your card is supported under Linux. You could also post in the networking section of this forum and describe what you tried to do but didn't work (not to bring this thread off topic).

Cheers,

              Riko

PS: you don't happen to speak german, do you? :)
[http://wiki.ubuntuusers.de/Nvidia-Grafikkarten]("http://wiki.ubuntuusers.de/Nvidia-Grafikkarten")

---

### Post by abrand888 on 2008-08-12
Hi RikoW,

I don't speak German although it is a beautiful language. I am born in the states.

There were only two choices but I am not 100% sure so I will run it again tonight. I am at work. Evidently Ubuntu 7.04 driver works better than 8.04.

My network is built in the motherboard. Since I have a number of drives I can try it on another drive soon but I would like to get the Nvidia driver working in Ubuntu 8.01

So it is back to the drawing board.

Thanks again. This is interesting stuff and I will not give up just yet.

Arthur

---

### Post by RikoW on 2008-08-12
Good luck to you, then! Post back here if you are successful (or not)

Whenever you try a new driver, it's a good idea to look at the screen resolution settings in System -> Preferences -> Screen Resolution and the output of xrandx. That will tell you, if the higher resolution was at least detected. Maybe, you arrive at a point where it is "merely" a question of setting it properly ...


Keep my fingers crossed,

                     Riko

---

### Post by i6p0 on 2008-08-12
Just my two cents.  I also upgraded to 8.04 and had exactly the same problem.  7.04 worked just fine with built-in drivers at 1024x768.  However, 8.04 only allowed up to 800x600.  

I spent about a full day trying various envy alternatives, with most of them showing me a white screen and forcing me to access the computer by SSH command shell. 

I gave up. I'm back to 7.04 until I feel like spending some more time on it.

Here's the lspci:

02:07.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

---

### Post by abrand888 on 2008-08-12
Rikow,

I tried all the manual drivers in Ubuntu 8.01 and they didn't work. I had to run Xfix and then normal boot to get things back.

There is a bug in Nvidia drivers in Ubuntu 8.01 that should be fixed.

I reinstalled Ubuntu 7.04, I am running at 1024 X 768 no problems  it found my cable modem and I am on line. I thank you and others. You all tried and I did the same but there is a bug that has to be fixed sometime in the future.

I will stay with 7.04 and monitor the events for the future.

abrand888

---

### Post by RikoW on 2008-08-13
Hi Arthur,

I'm glad to hear you found a working solution for you. Honestly spoken, I didn't really find much of a difference in the day-to-day use of consecutive Ubuntu versions.

I had one more proposal for you. I remembered last night while brushing teeth :) that I also had to reduce the color depth from 24bit to 16bit before I could get the highest resolution. Just in case you to want to do some more playing at some point, or someone else stumbles across this thread, this is what I did:

Make a back-up copy of the file /etc/X11/xorg.conf (of course :)

Open xorg.conf with you favorite editor and change the entries in the screen sections of the file that look like the following:

```
Defaultdepth    24
``` 
or
```
Depth   24
```

from 24 to 16, e.g.

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    16
        SubSection "Display"
                Depth   16
                Virtual 1280    1024
                Modes           "12080x1024@60"  "1024x768@60"  "800x600@60"    
"800x600@56"    "640x480@60"
        EndSubSection
EndSection

```

Then restart the xserver via ALT-CTRL-BACKSPACE and login again to see if that made any difference. I did for me, but only after login, the login screen itself is still in the smaller 1024x768 resolution and I gave up on it.

Enjoy you working 7.04 environment,

              Riko

---

### Post by abrand888 on 2008-08-13
RikoW,

Thanks for your thoughts. I will file it away but I will stay with Ubuntu 7.04 since I got everything working. At some time in the future I will play around with video editing and I believe 24 bit color depth is more important than 16 bit. The only reason Ubuntu interests me is that when I surf the internet I save all the files to a USB drive and then I bring them into Windows and have Kapersky Virus checker check the files before using.

I also am playing around with Windows 64 bit operating system doing video editing. So a whole new field awaits me. I am running three different dedicated computers so there aren't any overlapsping problems.

Again thanks. I personally believe that whatever driver Ubuntu used in 7.04 for Nvidia, they should use the same driver in 8.01. Somewhere there is a bug but that is for them to figure out.

Be well.

---

### Post by jstateson on 2008-08-13
I too cannot get past 800x600 with 8.0.4.1 and 64 bit version.  I thought I needed the ati driver (fglrx) and after installing it using synaptic my next reboot gave me a white screen that I never recovered from.

A "fix" of the x server did not restore the screen.  Currently, it boots to a login that is 800x600 but once I logon the screen goes white.

I restored the original xorg.conf file but that has no effect.  Googleing "rage xl ubuntu" shows a number of resolution problems and let me here.

A suggestion was to delete the xorg.conf file.  I will try that when I get home.  This mombo, Tyan 2882D, does not have an AGP slot, only PCI-X. I tried an old Matrox PCI video board in the only 5volt PCI slot and the display seemed to be 1024x768, but it was unreadable.  I went back to the builtin video and my white screen returned.

I have 2 other ubuntu systems working fine, but they have nvidia drivers and are 32bit, not 64.

FWIW, the current xorg.conf is the original generic that does not even list a driver.

Any help is appreciated.  

..TIA..

---

### Post by XPuntu on 2008-09-28
Hi Riko,

I modified my xorg file as you suggested but I have a virtual screen bigger than my display now. (So I have to use my mouse to move from one part of the screen to another. Is that because of the virtual display size bigger than my max resolution (1280x1024).

Also, your line "Modes           "12080x1024@60" should be "1280x1024@60 right?

What about the line "Virtual 1280    1024"?

Is there anything missing here? Maybe 1280x1024?

Thanks.

---

### Post by RikoW on 2008-09-28
> 
I modified my xorg file as you suggested but I have a virtual screen bigger than my display now. (So I have to use my mouse to move from one part of the screen to another. Is that because of the virtual display size bigger than my max resolution (1280x1024).


I should assume not. Ubuntu should still detect the maximum available resolution on the current screen. I have to admit, I'm not an expert in this stuff. I had a resolution problem when I changed to 8.04 and searched for a solution. That's what I found, and it works for me.

> 
Also, your line "Modes           "12080x1024@60" should be "1280x1024@60 right?


That;s of course correct :)

> 
What about the line "Virtual 1280    1024"?

Is there anything missing here? Maybe 1280x1024?


No, as far as I know, there is no x in between.

Good luck,

          Riko

---

### Post by XPuntu on 2008-09-28
Thanks for checking. I have a feeling my problem is related to something else being broken.

I had the hard drive in another system which I moved to a new location (long story) so I stuck the drive in this computer which is running on much older equipment. Everything else seems ok, just the resolution is a problem. I'll keep looking :)

---

### Post by RikoW on 2008-09-29
Well, if everythign else fails, you can install grandr from the respositories and set the resolution with that ... worked for me evrytime so far.

Good luck,

                Riko

---

### Post by Tater-kun on 2008-10-01
I had the same problem and tried the 

```
gksu displayconfig-gtk
```

And I messed with some of the configuration and noticed that my monitor was showing as "generic" instead of my monitor.  So, I changed it to my Monitor's make and model and I was able to set the screen resolution.  Once I did that, I saved and logged off and back in then TADA!  Problem solved for me.

Let me know if this helps anyone else!

Tater.

---

