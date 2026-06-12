---
title: "I have installed beryl but it does'nt work at all!!  NEWBIE!"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by Antonio44 on 2007-07-01
Ok so this is my situation. I have an ATI radeon xpress 200m card in my gateway laptop. I really want to have beryl and all the effects and such. I don't want to screw it up so I need advice from someone who unlike me knows what they are doing. I am not sure what info you guys need or anything. Just ask and tell me how to get it and I will get it for you. I have installed beryl, beryl manager, envy, I have some ATI Catalyst thing in accessories. In the select window manager option of the beryl icon I select beryl, and all my windows flash some and it goes back to metacity or compiz. Compiz doesn't work either. When I try to enable desktop effects I get "composite extension not installed" or something to that effect. I am really lost. Please anyone who will help and willing to work with me it will be much appreciated.

---

### Post by limbourg31 on 2007-07-01
well compiz will not run simultaneously with beryl... but since it seems you installed beryl, try running beryl in the terminal and post the outputs

---

### Post by Antonio44 on 2007-07-01
Lol I am VERY new to beryl. How do I go about running it?

---

### Post by limbourg31 on 2007-07-01
do you mean it wont' even start? in that case try the terminal thing i said before, just type "beryl" in the terminal.. otherwise the beryl settings manager might work

---

### Post by Antonio44 on 2007-07-01
I didn't know what to type in the terminal I meant. lol.

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension


That is what I got, what do I do now?

---

### Post by limbourg31 on 2007-07-01
reinstall beryl since it seems something for startup might be missing... sudo apt-get install beryl

---

### Post by Antonio44 on 2007-07-01
Ok I did that and this is the output from it. 

lee@lee-laptop:~$ sudo apt-get install beryl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
beryl is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
  libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libopensync0
  libglib-java libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Now what do I do?

Thanks,

A.

---

### Post by Antonio44 on 2007-07-01
Can anybody help?

---

### Post by walkerk on 2007-07-01
in terminal:
```
beryl-manager
```

what happens?

---

### Post by Antonio44 on 2007-07-01
The little drop down menu appears.

---

### Post by walkerk on 2007-07-01
mess with a few fuctions in there.. for window manager select beryl.. for window decorator select beryl..

what now?

---

### Post by dougfractal on 2007-07-01
From my experience from an compaq laptop having a ati 200m I had to use XGL

try following :-
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Installing_Xgl_and_Beryl)

It may help.
I'll have a look at the xorg.conf files tomorrow and send them here. I had to use radeon driver not the fglrx

in terminal type

```
glxinfo | grep direct
```

 If it returns 
> 
direct rendering: Yes
you're in business.

---

### Post by Antonio44 on 2007-07-01
Ok I tried that and it is not working for me. Can anyone walk me through this?

---

### Post by dougfractal on 2007-07-01
"in terminal type

glxinfo | grep direct

If it returns

direct rendering: Yes"


Did it return :-

> direct rendering: No ?

Can you display the output of 

```
beryl
```
then we can see the "Beryl system compatibility check"

---

### Post by russo.mic on 2007-07-02
I had that same card in my old HP laptop, and I got beryl running great.

But you have to use ATI's drivers, and you have to use XGL.  AIGLX won't run due to ATI's crappy driver.

I could walk you through it all day long, but he best advice I can give you is this:

Go to [www.beryl-project.org](www.beryl-project.org) and follow there instructions for installing the ATI driver, XGL and beryl.  They won't fail you.

Russo

---

### Post by j_medic78 on 2007-07-02
I'm having issues with Beryl as well! I have a Dell E1505 with an ATI X1400. I followed the tutorial I found here [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643) but it's still not working. When I log into the XGL session, and start the Beryl Manager, nothing happens. Then when I go into console and type "beryl", this is the message I get

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0


I'm a noobie, so I have no idea what this means! Thanks for any help in advance!

---

### Post by dougfractal on 2007-07-02
This is my driver section for an "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
which provides beryl on AGLX

In terminal  (HINT: mouse select, then middle button click to paste)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
sudo gedit /etc/X11/xorg.conf
```

replace 'Section "Device"' with this.  The** Identifier** will need to be the same as in the original xorg.conf

```
Section "Device"
#	Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
        Identifier  "Videocard0"
	Driver "radeon"		#"fglrx"     #ati driver
	BoardName "ATI Radeon"
	VendorName "ATI"
	Option "MergedFB" "off"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "True"
	Option "UseInternalAGPGART" "no"
	Option "backingstore" "true"
	Option "AllowGLXWithComposite" "true"
	Option "RenderAccel" "true"
EndSection

```

make  sure you have at least  these
```
Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "fbdevhw"
        Load  "glx"
        Load  "record"
        Load  "freetype"
        Load  "type1"
        Load  "synaptics"
        Load  "dri"
EndSection

```

Include this 
```

Section "DRI"
        Group        0
        Mode         0666
EndSection
```

save [ctrl]+s

In terminal ,  This will make sure all is installed then restart X
```
sudo apt-get install beryl beryl-manager
sudo /etc/init.d/gdm restart
```

In terminal
```
beryl
```

my beryl output.
> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048 )

Reloading options
beryl: water: GL_ARB_fragment_program is missing
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing


good luck

---

### Post by j0sh097 on 2007-07-02
> **dougfractal said:**
> "in terminal type

glxinfo | grep direct

If it returns

direct rendering: Yes"


Did it return :-

 ? Antonio44  Antonio44 is offline


Can you display the output of 

```
beryl
```
then we can see the "Beryl system compatibility check"

Hi, i've got the same card as  Antonio44, and when i type 'glxinfo | grep direct' i get 'direct rendering: Yes'. But when i go to 'Select window manager' and select 'Beryl' i get the same problem as Antonio44. Everything just blinks and goes back to Metacity. Can someone help me please?
Here is what i get when i type 'beryl' in terminal
```
josh@josh-laptop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

---

### Post by advanracing62 on 2007-07-03
i've got the same thing ^ going to beryl project to do their tricks.

---

### Post by russo.mic on 2007-07-29
Make sure after you install xorg-driver-fglrx you hit 

sudo aticonfig --initial

in the terminal.

and please, before you do, backup your /etc/X11/xorg.conf.

Russo

---

### Post by Runamok on 2007-07-29
advanRacing62, and j0sh097

I'm using an m300 and AIGLX (not fgxlr), but in my xorg.conf I have to include the following code all the way at the bottom. 

```
 Section "Extensions"
	Option "Composite" "enable"
EndSection
```

Does that code appear in your xorg.conf?

---

