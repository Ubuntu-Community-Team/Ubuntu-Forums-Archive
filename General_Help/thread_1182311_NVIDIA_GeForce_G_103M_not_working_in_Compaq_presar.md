---
title: "NVIDIA GeForce G 103M not working in Compaq presario"
date: 2009-06-08
forum: General Help
---

### Post by Sergio7676 on 2009-06-08
Hello everybody!

I cannot find the drivers for my NVIDIA GeForce G 103M to work. I visited the nvidia website but apparently there are not drivers for this card. I cannot enable compiz effects, play games and playing films overload my cpu...

Please, It would be great to get some help

Thanks in advance!!

---

### Post by Tynach on 2009-06-08
You seem to be correct...

However, try going to System > Administration > Hardware Drivers, and see if there are any drivers you can install/use.

---

### Post by Sergio7676 on 2009-06-09
Hi Tynach, thank you for your response. I have already tried it but
there are not drivers available...

---

### Post by FeydRauthaHarkonnen on 2009-06-09
I just bought a Compaq Presario CQ61-104SL and have the very same problem :frown:

---

### Post by Sergio7676 on 2009-06-09
I guess we would have to wait for an update... May be we could write to Nvidia and ask them if they are going to make a driver for linux...

---

### Post by Laya on 2009-06-11
Hi! I have the same problem in my presario CQ61. Who can welp us? Please, i don't know what to do... Thanks!

---

### Post by Sergio7676 on 2009-06-11
I am sorry Laya, I wish I could help you but I have not found a solution. Finally I did have to reinstall Vista but I will reinstall Ubuntu as soon as the problem is solved.

Cheers


Sergio

---

### Post by Tynach on 2009-06-12
I personally dual-boot on my Presario... But, I just have a GeForce 8200M G, and there are drivers available for that...

This is very unlike nVidia. They usually have splendid Linux support.

---

### Post by Laya on 2009-06-12
Thanks for the answers!! Perhaps nvidia make the driver, i want it a lot. I will downgrade to vista ;) with dual boot. 
I believe that companies should edit controller compatible with all OS. If i can make work the sound by the speakers ([http://ubuntuforums.org/showthread.php?t=1184791](http://ubuntuforums.org/showthread.php?t=1184791)), i will continue with ubuntu. I hope to do.

---

### Post by zibuntu on 2009-07-01
iwe "solved" this problem on my cq61-100so, by installing the latest betadrivers from nvidia, thats the easy part..
the hard part was to create a custom EDID, wich is needed because
the nvidia driver has a bug that causes the EDID to be wrongly read, afaik.
i made a custom one and i now get the correct resolution, i dont know if i can recomend this as it might screw things up, but if you do want to try it, i can attach it i guess, else wait for new nvidia drivers.

---

### Post by Sergio7676 on 2009-07-01
Hi zibuntu!

I would appreciate that you attach your "fix". Where did you find the beta drivers? I went to the Nvidia web site but I found nothing!

Cheers and thank you for your response!

):P

---

### Post by zibuntu on 2009-07-01
> **Sergio7676 said:**
> Hi zibuntu!

I would appreciate that you attach your "fix". Where did you find the beta drivers? I went to the Nvidia web site but I found nothing!

Cheers and thank you for your response!

):P


read thruogh it all, also you might want to print it, as you wont be able
to have xorg running= just a console.

First the drivers.
[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/NVIDIA-Linux-x86_64-185.19-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/NVIDIA-Linux-x86_64-185.19-pkg2.run)   <=64bit
[ftp://download.nvidia.com/XFree86/Linux-x86/185.19/](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/)   <=32bit

nvnews forum where they are announsed
[http://www.nvnews.net/vbulletin/showthread.php?p=1976912](http://www.nvnews.net/vbulletin/showthread.php?p=1976912)

You might want to dl my attachment and unzipit.
copy the edid.bin file to /etc/X11/ you can do that in a console by..
cd /path/where/edid.bin/was/downloaded
sudo cp edid.bin /etc/X11/

short on how you install the drivers.
change to a console "ctrl+alt+f1"

login
sudo /etc/init.d/gdm stop      
"cd to the dir where the nvidia driver.run are."
sudo sh NVIDIA-Linux-x86_64-185.19-pkg2.run
"follow the instructions in the installer"
sudo nvidia-xconfig

now, if everything is ok, you have the drivers installed.
and if you start xorg again you might be lucky and it works.

sudo /etc/init.d/gdm start  

if it however doesnt work, like for me, i had 6 small clones on my screen
all of them 640x480 in resolution.

ctrl+alt+f1 to console again
sudo /etc/init.d/gdm stop 
sudo nano -w /etc/X11/xorg.conf

add a line under Device 
"ony add the line marked in **bold**"
[I]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G 103M"[/I]
    **option    "CustomEDID" "DFP-0:/etc/X11/edid.bin**"
*EndSection*

ctrl+o    to save file in nano
ctrl+x    to exit nano

that line makes the card use my custom edid file from my attachment,
if you downloaded it and placed it in /etc/X11,
you can put it somplace else, but then you have to edit the line correctly.

start gdm again.

sudo /etc/init.d/gdm start 

now it should work unless i explained it wrong, you did wrong,
or something else happend, or you dont have the same display as i do.

[B]NOTE, this EDID is only for the 15,6" led screen part number b156xw02 V0
if you have any other screen on your cq61 it might not work, also,
i take no resposibility, it works for me, it might not for you...[/B]

ALSO,if you dont get it to work, and want xorg to work again like before.
do this.....

ctrl+alt+f1
sudo /etc/init.d/gdm stop
sudo nano -w /etc/X11/xorg.conf

change driver to "nv" and put a "#" infront of the option, or remove the option line, up to you

[I]Section "Device"
    Identifier     "Device0"
 **   Driver         "nv"**
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G 103M"[/I]
    **#option    "CustomEDID" "DFP-0:/etc/X11/edid.bin**"
*EndSection*

ctrl+o save
ctrl+x and exit
sudo /etc/init.d/start

ill be around for questions if you have any.
GL, have fun, this is what makes linux great.

---

### Post by Sergio7676 on 2009-07-01
Hi Zibuntu

Thank you very much for you response!!. I am afraid that is a bit too technical for me. Anyway, I´ll try your "possible" solution.
There are two things that I really love about Linux,its OS and its Community!!

Thanks again!


:guitar:

---

### Post by Pales66 on 2009-08-09
[FONT="Times New Roman"]Hi Zibuntu

Many thanks for solution, and it works indeed.
I bought a CQ61-115EE just yesterday and I used the newly released "[FONT="Courier New"]NVIDIA-Linux-x86-190.18-pkg1[/FONT]". It will give you the choice to run [FONT="Courier New"]nvidia-xconfig[/FONT] on its own.
And when I find these six desktops and in order not to remember the long line I just fired "[FONT="Courier New"]sudo gedit /etc/X11/xorg.conf[/FONT]" from a terminal window, and copying the line "[FONT="Courier New"]#option "CustomEDID" "DFP-0:/etc/X11/edid.bin[/FONT]" to where it belongs and restarting gdm.
It is working like charm with all the wooos of compiz fusion :)

Thank you for making my life easier. Now I can brag my friends with my new notebook.[/FONT] 

Pales66

---

### Post by androjes on 2009-08-22
Thank you for you help :KS! 
It's works! woow super

---

### Post by beny-4.56 on 2009-08-26
my friend have Compaq presario CQ45. where should i get the edid.bin file?

---

### Post by fotonic on 2009-09-04
[FONT=Arial][SIZE=2]Hi zibuntu. I followed your guide.

I  downloaded th[/SIZE][/FONT][FONT=Arial][SIZE=2][U]e drivers 
[/U][ftp://download.nvidia.com/XFree86/Linux-x86/185.19/](ftp://download.nvidia.com/XFree86/Linux-x86/185.19/)   <=32bit

[/SIZE][/FONT] [FONT=Arial][SIZE=2]and then I installed them, following your instructions.  
Then I run "sudo /etc/init.d/gdm start and I didn't had 6 small clones on my screen, but the nvidia logo and after the login the resolution was ok.
Then I run "System/Preferences/Nvidia X Server Settings and tried to configure my video card in order to get my external monitor (HP w2207h, with pivot function, resolution 1680x1050 and 1050x1680) to work. Then, after abiliting TwinView and editing  /etc/X11/xorg.conf with [/SIZE][/FONT][FONT=Arial][SIZE=2] the Option XRandRRotation "true" under the Section DeviceI have now this "xorg.conf".

After this steps:

- Monitor resolution is good, both on the laptop and on the external monitor;
- Dual monitor works, also with rotation.
- **Audio does not work**, or better said, **it works only through the headphones,** but **not through the speakers** of the laptop.

[/SIZE][/FONT][FONT=Arial][SIZE=2]So I followed this two guides 
[/SIZE][/FONT][FONT=Arial][SIZE=2][http://monespaceperso.org/blog-en/20...tu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")
[/SIZE][/FONT] [FONT=Arial][SIZE=2][/SIZE][/FONT]
 [FONT=Arial][SIZE=2]https://help.ubuntu.com/community/HdaIntelSoundHowto
as suggested from 
[http://ubuntuforums.org/showthread.php?t=1179999](http://ubuntuforums.org/showthread.php?t=1179999)
but didn't fix the problem.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]
So I have some questions for you or for the other people who read this thread.

1) Have you got the same audio problem?

2) When I run the command "cat /proc/asound/card0/codec#* | grep Codec" I get this two lines:

[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2]Codec: IDT 92HD75B2X5
Codec: Nvidia ID 3
[/SIZE][/FONT][/INDENT][FONT=Arial][SIZE=2]
Do you have the same sound card?

3) Since after the installation of the nvidia drivers I had no six clones, I didn't edit the xorg.conf with the option Custum Edid. Do yuou think I should do this?

4) You say your EDID is only for the 15,6" led screen part number b156xw02 V0. How can I discover which is my screen part number?

Thank you very much,
fotonic[/SIZE][/FONT]

---

### Post by fotonic on 2009-09-04
Sorry I forgot to say that I run Ubuntu 9.04 (WUBI) on a leptop Compaq presario CQ61 with NVIDIA GeForce G 103M.
This is my /etc/X11/xorg,conf:


xorg.conf.2schermi-twinview-noaudioportatile
xorg.conf.backup
xorg.conf.noaudio
xorg.conf.separateXsession
xorg.conf.twinview
paola@ubuntu:~$ cat /etc/X11/xorg.conf.2schermi-twinview-noaudioportatile 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder63)  Fri Apr  3 13:02:44 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LGD LP156WH1-TLA3"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce G 103M"
    Option       "RandRRotation" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: 1366x768_60 +0+0, DFP-1: nvidia-auto-select +1366+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by fotonic on 2009-09-04
I found the solution for my audio problem!
Read my post in: [http://ubuntuforums.org/showthread.php?p=7897428#post7897428](http://ubuntuforums.org/showthread.php?p=7897428#post7897428)

---

### Post by calin_ionut on 2009-10-02
thank you zibuntu for your time! ;) I just install the nvidia driver from Synaptic Manager version 180.44 on a Compaq CQ61-125EQ then add that file  "edid.bin" and modify the xorg file and it works like a charm.

Cheers!

---

### Post by olofven on 2009-10-15
A million thanks!! As of Ubuntu 9.10, I only needed to do the following:
1. Activate the Nvidia restricted drivers in >System>Administration>Hardware drivers
2. Copy your edid.bin to /etc/X11/
3. Edit /etc/X11/xorg.conf as you described (added the line: **option    "CustomEDID" "DFP-0:/etc/X11/edid.bin**")
4. Restart

I dont know how to check which edid, but I noticed that its listed in the Nvidia X settings tool found in the Sytem>Admin.. menu efter activating the restricted driver. Look under "GPU 0", to the right it says "Display devices". Can be hard to see if you have 6 screens. With Ubuntu 9.10 I finally got the guts to try, since you can always deactivate the restricted driver easilly even with 6 screens. And if you cant reach the restart button to the right, just go to the terminal in the applications menu and type "sudo reboot" followed by your passw + ENTER.

Again, thanks!
(specs: Compaq CQ61 with Gforce G103M)

---

### Post by Apopas on 2009-10-25
[http://www.nvnews.net/vbulletin/showpost.php?p=2029745&postcount=20](http://www.nvnews.net/vbulletin/showpost.php?p=2029745&postcount=20)

---

### Post by Magmarules on 2009-11-11
Guys hows the rest of the hardware working? Im considering buying this computer for work. But i need that the 3d accelaration, wireless and mic work. Mic being the least important. Also multi monitor support would be great.

---

### Post by Sergio7676 on 2009-11-14
> **Magmarules said:**
> Guys hows the rest of the hardware working? Im considering buying this computer for work. But i need that the 3d accelaration, wireless and mic work. Mic being the least important. Also multi monitor support would be great.


Everything works the graphic card needs some work done (in this thread you have got the solution).On the other hand the sound needs some work (speakers), but you can find the solution at the forum (I am sorry I don´t have the adress right now). I do not know about multiple monitors.

Cheers and good luck!!!

By the way thanks to everybody that make the contribution in this thread, my graphic card works like a charm!!.

---

### Post by AntonioTheGreat on 2010-03-14
The trick works perfectly on my Ubuntu 64 bit with a Nvdida 103m card! Thanx!

---

### Post by drizhal on 2011-12-13
gracias, mas facil imposible :popcorn:


********
jajejijoju

---

### Post by manofwar95 on 2011-12-13
In the mean time looks like you're going to have to settle for [B]Nouveau. :(
[/B]

---

