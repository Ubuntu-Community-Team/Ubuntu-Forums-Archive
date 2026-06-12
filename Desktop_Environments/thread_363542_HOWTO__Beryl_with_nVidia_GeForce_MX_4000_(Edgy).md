---
title: "HOWTO : Beryl with nVidia GeForce MX 4000 (Edgy)"
date: 2007-02-17
forum: Desktop Environments
---

### Post by ashmew2 on 2007-02-17
HI every1 , Please read the following guide to set up a working system with beryl (ONLY TESTED FOR PEOPLE WITH NVIDIA GEFORCE MX4000 GRAPHIC CARD AND EDGY EFT)[32 bit]

*********************DO NOT FORGET TO BACKUP ALL FILES BEFORE EDITING!!********************************

1)Download the great script Envy by clicking [Here]("http://albertomilone.com/nvidia_scripts1.html")    and then getting the "envy_0.8.1-0ubuntu6_all.deb" , Then double click the .deb file and select "Install Package".
2)Press CTRL+ALT+F1 and then type "envy".
3)Select to UNINSTALL NVIDIA DRIVER (This step is just to be safe).
4)It will download some stuff (i think around 20 MB or so) , then u again start envy and do "INSTALL NVIDIA DRIVER"
5)Drivers Installed!! When it asks you would you like to start the X Server , say Yes.
6)Read on...

In the terminal type :
```
sudo gedit /etc/apt/sources.list
```

In the file that opens , scroll to the bottom and add the line :
```
deb http://ubuntu.beryl-project.org edgy main
```

Save the file then again in the terminal :
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```
and ..
```
sudo apt-get update
```

Now all is left is installing Beryl , type in the temrinal :
```

sudo apt-get install beryl emerald-themes
```

Restart your X server (Ctrl+ALT+Backspace)
Login and after ur system loads , press Alt+F2 and type "beryl-manager". It will give u an icon in the top right corner of your screen (by default). Right click that icon and Select "Default Window Manager " to "Beryl". 
If Beryl is not working , read on...
JUst type  in terminal :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

```
Scroll to the bttom of the file and you should find a section named "Extensions" , Make it look like this :

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
Dont Panic if you dont have that section , u can just copy paste it into ur xorg.conf file. Now restart your X server (CTRL ALT Backspace) and try running Beryl Again. It SHOULD work....
*****IF u cant start your X server ******************** just press CTRL+ALT+F2 and login and then type :
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
If you want to make Beryl-Manager run at everytime u start your gnome desktop , u can do so :
Click System > Preferences > Sessions > Startup Programs > Add then type "beryl-manager" 
Press OK then close.


*******If Encountering the no title bar problem after installing/running Beryl*******************

Open up /etc/X11/xorg.conf in a text editor, as root.

```
sudo gedit /etc/X11/xorg.conf
```

Add these two lines before the EndSubSection part of the Section "Screen"


Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"

Save the file and then restart the X server (CTRL+ALT+BACKSPACE))
You should not be the encountering the Missing title bar again :)


-=Thanks for the tip Mr.Kasper!!!=-
===================------EnJoY====== ==========================-
Let me know if any other problems , ill try my best to help :D

---

### Post by ashmew2 on 2007-02-25
No1 found it useful yet.. ?

---

### Post by zeroblitzt on 2007-03-05
Worked great for me, thanks.

One question though, is it normal for my Firefox window not to have a Window control bar (thing at the top that displays title + the X in the top right corner)

EDIT: Well I guess I can't say it worked perfectly for me, but it still went smoothly. Anyway, I uninstalled it, because in my eyes it wasn't anything special, and it was just sucking resources.

---

### Post by rusty4r on 2007-03-08
well it worked great for me. I too encountered the "no title bar problem" but I've read in here somewhere how to fix that and I'll go find it now. 

This is the second time I have used your guide. I had to reinstall but I had your guide boomarked and it worked like a charm again.

Thank you

---

### Post by ashmew2 on 2007-03-09
Glad I could be of help :)
Btw , could u plz hook me onto how u solved the no title bar ? ill be more than happy to add it to the guide.. :)

---

### Post by rusty4r on 2007-03-09
Sure, I found it right after I posted.

It's another guide similar to yours and there is a couple of small differences and when I made those additions it solved the problem.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")
I skipped on down to the section titled Enable Aiglx. There are 3 instructions and I don't have any idea which one solves the problem but maybe you will. Then it says to restart x and my title bars are back.

Hope that helped you

---

### Post by jonwe195 on 2007-03-11
> **rusty4r said:**
> Sure, I found it right after I posted.

It's another guide similar to yours and there is a couple of small differences and when I made those additions it solved the problem.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")
I skipped on down to the section titled Enable Aiglx. There are 3 instructions and I don't have any idea which one solves the problem but maybe you will. Then it says to restart x and my title bars are back.

Hope that helped you

Hmm...nope, I can't say it helped me...I actually got Beryl working at first, but stupid as I was I thought "hmm...I don't know what that AIGLX-stuff is, but maybe it makes Beryl better...I'd better try it". Once I added the stuff in my xorg.conf my computer hangs whenever I start beryl-manager. The problem is that now it hangs even if I delete the things I added...I even deleted all beryl-related packages in synaptic, and installed them again, but it still doesn't work...I start beryl-manager, the red emerald comes up in the activity field (or whatever the name is), my icons disappear from the desktop, the title-bars dissappears from all open windows, and nothing happens when i click things...

Anyone got an idea what's wrong?
Thanks for any help!
/Jonatan

---

### Post by ashmew2 on 2007-03-13
hey jon , have u tried reverting to your old xorg.conf  ? I hope u backed it up before using Beryl , u can just restore the backup , completely remove beryl (if there are any packages left) and then try reinstaling Beryl from scratch.

---

### Post by adewale on 2007-03-14
mine seems a little different i got ubuntu christmas edition with beryl installed i later installed the nvidia driver i logged in i tried beryl then my pc freezes evn now at times before i login it freezes waht can i do? could it be my swap cause i have like 312mb of swap.thanks

---

### Post by ashmew2 on 2007-03-14
Hey , u mean to say christmas edition came with Beryl inbuilt ? After u installed the nVidia drivers , i think it must have modified your xorg.conf and that has to do with your freezing problems , can u try completely removing beryl and your graphic driver and installing the graphic driver first and then Beryl ? 
Do reply!!

---

### Post by adewale on 2007-03-17
sorry my reply took this long, had some problems. i tried removing beryl and reinstalling the driver it still froze my pc. i'll try and download the legacy driver. i hope that works

---

### Post by ashmew2 on 2007-03-24
> **adewale said:**
> sorry my reply took this long, had some problems. i tried removing beryl and reinstalling the driver it still froze my pc. i'll try and download the legacy driver. i hope that works

SOrry for the extremely late reply..i almost forgot to check this thread lol
listen
u can get the great script ENVY for easily installing ur graphic driver,..instead of manually doing so plus it will auto configure ur xorg.conf also

---

### Post by dupe576 on 2007-03-25
Hey.  I tried using your Envy program to install my drivers and it didn't work.  I ran the program, uninstalled and then installed.  Then restarted my computer and the X server wouldn't start up so I had to change the Xorg.conf file back to how it was originally.  I have a PCI geforce mx 4000.  If anyone knows how to solve this problem I would be eternally thankful.  I feel like I've tried everything and I still can't get these stupid drivers to work.  I'm really at my wits end.  I'm even considering buying a whole new graphics card just out of sheer frustration.

---

### Post by Kasper42 on 2007-03-25
Nice guide, ashmew2 :)

I'm experiencing similar problems to dupe576, when I run envy and try to install nvidia drivers. The driver 1.0-9755 which envy installs doesn't work and I have to install the driver manually through envy, choosing the 1.0- 7184 driver. I was just wondering if any other MX 4000 users had similar problems? I have installed beryl while running the 1.0-7184 driver but I get the error when running "beryl-manager" in the terminal:

>  Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Then I get a message telling me that glxinfo has crashed.

Is this due to running the 1.0-7184 nvidia driver? Can other MX 4000 users run the 1.0-9755 drivers? Thanks :)

---

### Post by dupe576 on 2007-03-26
Ok.. I just tried what Kasper42 said about manually installing the 7184 driver instead.... annnnddddd...   STILL not working. =( 

Am I just cursed?

Another thing I noticed that is kinda weird is in my xorg.conf file, my card is listed as being a GeForce MX4000 AGP 8x card when in fact it isn't AGP at all.. its PCI.  My motherboard doesn't even support 8x AGP, it only goes up to 4x.  So I have no idea where it is getting that from.  Could this be having an effect? Anyone have some thoughts on this?

...or maybe I'm just the only person that owns a PCI version of this card so no one has bothered to write drivers for it... that would be my luck.  

I don't know.  I'm frustrated as hell.  I got this card working in about 2 seconds for windows with the driver it came with.  What gives?

---

### Post by ashmew2 on 2007-03-26
Hello people , I own an GeForce MX 4000 AGP 8x (atleast it says so in xorg.conf lol) So..

@Kasper42
HI man , As far as i know whenever ive used Envy to install the drivers for my graphic card it has always downloaded and installed the 9631 drivers which u can download by clicking this : [herel]("http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html")
One thing i havent figured out that as far as i know our mx 4000 comes in the Legacy GPU..but when its drivers are installed they are not legacy.. lol ..so never mind .
Once you have your 9631 drivers installed , you should try following the last section of the guide : *******If Encountering the no title bar problem after installing/running ..."

Please let me know if that worked for you..
Every1 else who are having some problems with the legacy drivers do try installing the 9631 drivers and post back!!

Btw , are you guys using the new Graphical version of Envy ? If so  , do give the old good text version based one a try :)

---

### Post by ashmew2 on 2007-03-26
hey dupe476 , can u give me the exact name of your card and the name of the driver the cd came with including version number ?

---

### Post by dupe576 on 2007-03-26
Here's exactly what it says in the xorg.conf file: NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]

I looked for the version number in the driver CD and I found this in a PDF file titled "71.84_ForceWare_Release_70_Graphics_Display_Property_Users_Guide.pdf":
Driver Version: 71.84 for Windows
NVIDIA Corporation
March 2005

Then.. I looked at the device manager in windows and clicked on my video card.  There it shows the driver version number as 7.7.7.7.  Which one is right? I don't really know.  I am confused.


Here's some more information (dunno if this helps):
Processor: GeForce4 MX 4000
Video BIOS version: 4.18.20.42.61
IRQ: 16
Bus: PCI x0
Memory: 128MB
ForceWare version: 77.77  (similar second driver number)

And I believe the manufacturer is 3D Fuzion.

... hope this helps!

---

### Post by ashmew2 on 2007-03-27
Im really sorry for the lame replies lol , acctually im using Feisty Beta rite now and its pretty darn Goood!! Installing the nVidia driver was as easy as using ubuntu!! :D
I just did it in this way :
1)Download the 9631 driver for your graphic card : [9631 Driver]("http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html")
2) Once downloaded , save it to your desktop , then press CTRL+ALT+F1 and type : 

```
ps -ef|grep gdm
```

It will show you a bunch of processes , find the first one which starts with "root" and not your user name. See the id (or the number of the root gdm process) and then type :
```

sudo kill PUT THE NUMBER HERE
```

Example : sudo kill 4356
3) See your architecture by typing : 
```
uname -r
```
Then it will give u some output like : 2.6.20-13-386
so you do :
```
sudo apt-get install linux-headers-2.6.20-13-386
```

Replace 2.6.20-13-386 with the output it gives u with uname -r
```

sudo apt-get install linux-386
```
Again you should replace 386 with k7 or 686 , whatever the last part in ur uname -r

4)Backup your xorg.conf should anything go wrong :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

5) Now for installing the drivers :
```
sudo sh Desktop/NVIDIA-Linux-x86-1.0-9631-pkg1.run
```
 Just keep clicking ok ok :P and when it asks u shud it auto configure your xorg.conf say yes.
6) ```
sudo gdm
```
For starting the X server again!!

Should anything go wrong   , try : 
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And restart comp.

All done.
Some1 plz try this in Edgy and let me know if it works!!

---

### Post by ashmew2 on 2007-03-27
And dupe576 , if you have tried the 9631 drivers without luck , u could try using the 7182 drivers..i read somewhere they are know to work wid Nvidia MX 4000 PCI cards..

---

### Post by Kasper42 on 2007-04-01
Hey!

@Ashmew2, Sorry for the reply taking sooo long :(

Anyway, I've managed to install the 9631 drivers thanks to your guide :) Beryl seems to work except from the title bar. I did follow your instructions of how to make it work but I still can't see it :confused: 

When I run "beryl" I get the following in the terminal ...
> Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32



Thanks for all the help so far, I've just tried the cube and Beryl looks great!

.:EDIT:. Right, I looked around for people with the same error and found this thread [http://ubuntuforums.org/showthread.php?t=344323](http://ubuntuforums.org/showthread.php?t=344323)
I added > 
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True" 
to the end of the Module "Screen" section but nothing seemed to happen. I went into beryl-manager and disabled "Window Decoration" I then re-enabled it and the title bar re-appeared (in a nice neon-pink :) ) I'm learning how to use Beryl at the moment. Thanks again :)

---

### Post by ashmew2 on 2007-04-02
Hurray!!!
Glad I could help Mr.Kasper :)

---

