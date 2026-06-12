---
title: "Ati drivers"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Phristen on 2007-12-21
I followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") (manual way), and I finally got glxinfo to say Direct rendering: Yes.
Now my screensavers run ok and I get 2000 fps in glxgears...

However, my compiz doesnt want to use direct rendering, so the performance really sucks:> Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:5b63 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


I went in and installed xserver-xgl and that made compiz work (I finally got window blurring to work), but pretty much everything else stops working. Direct rendering in glxinfo says no, glxgears crashes X, and so do the 3d screensavers,
So I disabled the xgl server for now...

Anyway, can anybody tell me, what can I do about the **Checking for texture_from_pixmap: present. **? That's what seems to be killing me, help :confused:

P.S. Oh, and the card is radeon X550

---

### Post by MangasColoradas on 2007-12-21
Hi, I cant help as I am having my own ATI problems but I am very interested in the guide you linked to. I hope you get some feedback and good luck. :)

---

### Post by stueyboy on 2007-12-21
I used the latest version of the Envy script to install the most recent ATi drivers and Compiz worked OK afterwards with no tinkering.

---

### Post by MangasColoradas on 2007-12-21
I just borked my whole installation trying to follow that guide, I have saved some things I had downloaded by booting with the live cd and can get set up again pretty quick think, lol.

Not criticising the guide, I am sure it was my own fault. :(

I wouldnt know where to begin to fix it so I am gonna do a fresh install.

edit
I tried to revert to the old driver by following the guides instructions and get this BTW.

E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

---

### Post by mwolfe on 2007-12-22
MangasColoradas,
Before you got that error, there was probably a message about not being able to rename some compiz config file. Someone mentioned that you can delete the original file and that fixes it. I did this and it worked for me. However now i reinstalled the drivers and everything from scratch and i can't get compiz working. It gave me an error about /usr/loca/bin/compiz not being found, then i found another recent thread which explained that you needed to edit the compiz file and change the path 
these:
#COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
#PLUGIN_PATH="/usr/local/lib/compiz/"
PLUGIN_PATH="/usr/lib/compiz/"  

where the commented lines were the originals and the uncommented are the chagned paths..

So i did that and now when i run compiz it just keeps on looping giving me these messages:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b62 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b62 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b62 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b62 (prog-if 00 [VGA controller])
```

It does that over and over forever as far as i can tell.. Any ideas?

---

### Post by MangasColoradas on 2007-12-22
You might be right mwolfe, what get's me is even after a fresh install and using the standars restricted driver, I am getting black screens after logging on. This video card driver BS is ruining Ubuntu for me. :( It's my first ever try with Linux and I was getting to really like it too.

---

### Post by Ub1476 on 2007-12-22
The latest drivers from ATI (manual way) is very buggy. I suggest you use the one who is in the repos. If you still have problems after using the drivers from System>Administration>Restricted Driver Manager, please post the output of this command:

```
lspci | grep VGA
```

```
compiz --replace
```

---

### Post by Phristen on 2007-12-23
> **Ub1476 said:**
> The latest drivers from ATI (manual way) is very buggy. I suggest you use the one who is in the repos. If you still have problems after using the drivers from System>Administration>Restricted Driver Manager, please post the output of this command:

```
lspci | grep VGA
```

```
compiz --replace
```
If I use restricted drivers manager then X won't start at all.
That guide I linked to is the only one that works for me.

---

### Post by kshane on 2007-12-23
> **Phristen said:**
> If I use restricted drivers manager then X won't start at all.
That guide I linked to is the only one that works for me.

I loaded the new drivers after reading your original post.  I had the black screen instead of a logon window and the system just froze.  So, I installed the new version of Envy that's out and installed it that way and it worked fine.

You can get Envy here:  [http://albertomilone.com/wordpress/?cat=12](http://albertomilone.com/wordpress/?cat=12)

Envy works pretty well at installing the video drivers for Nvidia and ATI cards.

Kevin

---

### Post by sloggerkhan on 2007-12-23
Just want to reiterate: The latest ATI fglrx driver is not usable for widescreen monitors below HD resolution. (Really stupid flaw for a supposed 'bugfix' release.)

---

### Post by Phristen on 2007-12-23
Envy doesn't work, it leaves me with the default "ati" drivers.

---

### Post by andreas@mars on 2007-12-24
Hi,

I had a similar problem.
After installation of the latest driver COMPIZ was not working.

I followed the already mentioned instruction [Ubuntu Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Alternative:_Configure_the_Driver.2C_The_Manual_Way:") and ended up with a working driver but no desktop effects.

```

andreas@mars:~$ glxinfo | grep -i direct
direct rendering: Yes

andreas@mars:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7170 Release

```

This is what I did:

1. Uninstall xserver-xgl

2. Edit the file /etc/X11/xorg.conf

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Option	    	"VideoOverlay" "on"
	Option	    	"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
	Option 		"XAANoOffscreenPixmaps" "true"
EndSection

...

Section "ServerLayout"
...
	Option "AIGLX" "True"
EndSection

Section "ServerFlags"
        Option "AIGLX" "true"
EndSection

```

3. Create the file ~/.config/compiz/compiz-manager

```
SKIP_CHECKS=yes
```

4. Create the file /etc/xdg/compiz/compiz-manager. 
This is probably the same file as above controlling global settings and the configuration can be combined but I did it this way. 

There was already a compiz-manager.ubuntu file in  that directory and I copied it to compiz-manager. Then I add the WHITELIST statement.

```
# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"
WHITELIST=fglrx
```

After the last activity I was able to activate the desktop effects.

I hope this helps you as well. 
But summarizing my experiences - I should have kept the restricted driver from the Ubuntu repository. This would have saved me some hours trying to fix a previous working installation.

Andreas

---

### Post by Dreamlocked on 2007-12-24
About the guide everyone is following....
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Is it me, or did someone (accidentally) delete the passage :

```

sudo module-assistant prepare,update
sudo module-assistant build,install fglrx -f
sudo depmod -a

```

Doesn't omitting this make the whole installation process invalid?

---

### Post by Phristen on 2007-12-25
> Doesn't omitting this make the whole installation process invalid?I dunno, but 3 days ago (i.e. when i was doing this) that part was there, and i did it.


Basically, everything would have been great, but compiz just doesn't wanna use direct rendering :(
And when it starts, it sets that *something*_ONLY_INDIRECT variable, which disables the direct rendering.

So here are my choices: forget about 3d desktop but enjoy all the other GL goodies, or vice versa.... It's ridiculous :confused:

---

### Post by Dezinteres on 2008-01-02
Hello , 
The same is happening with my sapphire hd2600xt .I have to choose between desktop effects or direct renderintg.
If anyone knows a way to make them both work.. pls share with us .Thank u

---

### Post by Mr Greencastle on 2008-01-02
As far as I know, you can't have Direct Rendering and Compiz Fusion running at the same time with these new drivers. To everyone, I suggest using fusion-icon to run and switch between managers. Paste this command all at once in a terminal:
```
sudo apt-get install git-core && git clone git://anongit.opencompositing.org/users/crdlb/fusion-icon && cd fusion-icon && sudo make install
```
It *should* help to relieve your direct rendering woes, to use 3d apps, just right click the icon, and change the window manager to metacity. To switch back, change it to compiz.

Remember to add 'fusion-icon' without quotes to your sessions for it to start automatically when you login.

Hope that helps!

Mr Green

---

### Post by Saint Angeles on 2008-01-02
i have an X1550 using the 7.11 catalyst driver (fglrx) from [www.ati.com]("http://www.ati.com")

i downloaded the .run file to my desktop and in a terminal i did: ```
sudo sh at(tab)
```the tab will complete the filename. this is the only way i have been able to get compiz working.

i'll also post my xorg.conf for a few more ideas...

```
sudo gedit /etc/X11/xorg.conf
```careful cuz this file holds all the information for your display and input devices

EDIT:  FGLRX 7.12 doesnt work on my computer... ive tried every possible thing i could find. im not sure why.

---

