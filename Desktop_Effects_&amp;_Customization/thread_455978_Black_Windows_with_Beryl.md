---
title: "Black Windows with Beryl"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by ksudbury on 2007-05-27
Pretty much all my windows are black, I am running Feisty with the Ubuntu restricted Nvidia driver. 

See my screenshot attached to see exactly wats going on.

My GFX card is a NVIDIA GeForce 6150


This is how I installed Beryl: 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list 
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install beryl beryl-manager emerald-themes 
sudo nvidia-xconfig --add-argb-glx-visuals
sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop 
cp  /usr/share/applications/beryl-manager.desktop ~/Desktop/beryl-manager.desktop
echo -e "Logout now and then press \e[0;31mCTRL+ALT+BACKSPACE\e[0m to restart xorg"
echo "Installation completed !"


Any ideas? 
Thanks

---

### Post by rothgar on 2007-05-27
I have the same problem.  Mine windows will be fine for a while though and then they will just go black.  If you scroll up the window (double click the title bar) then unscroll the window it goes back to normal but I don't know a permanent fix for the problem.

---

### Post by ksudbury on 2007-05-27
I have found a fix for this it is a bug with Nvidia drivers, this is a temp fix until they release a patch. 

Right click on the Beryl Emerald go to "Advanced Beryl Options" then "Rendering Path" then select "Copy"

That fixed it for me, apparently it id slower however I figured slower is better than black windows :D 



Hope that helps a few people!

---

### Post by nevernamed on 2007-05-28
I couldn't find a place to put this. I was using the built in desktop effects that come with Fiesty, and it asked me to activate the nvidia driver. I said yes, it downloaded the necesary files. It said that I had to run desktop effects again when the new nvidia driver was running. I rebooted. Everything worked fine until the login screen was supposed to come up. The screen went totally black. I still heard the African drums, but I was unable to do anything. control+alt+backspace restarted x and nothing happened. I can boot to the recovery mode... but I really don't know what to do. Does anybody know why this has happened (the bug in the driver that you mentioned?) and how to correct it? Thanks in advance.

---

### Post by bobbleSmurf on 2007-05-30
nevernamed - I had the same trouble. I'm using a Toshiba laptop and got a black screen that started to turn white in a kind of auroric haze - pretty but made me feel that my screen was going to explode!

Apparently it's because the driver isn't finding the right display device - can't find the original post but I had to add the following line to the nvidia device section of my /etc/X11/xorg.conf file:

```
Option    "UseDisplayDevice"    "DFP"
```(DFP - Digital Flat Panel) Don't know if this is the same method external monitors and such. It doesn't seem to be the same bug as the black window syndrome, as I still had that after sorting out the initial black screen. The nvidia device section of my xorg.conf looks like:

```
Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 460 Go]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
    Option        "UseDisplayDevice"    "DFP"
EndSection
```In regard to black windows - I've left the Rendering Path on Automatic (rather than copy) but have changed the Rendering Platform to > Force AIGLX and don't seem to be getting anymore black windows (or is that black widows:lol:) - haven't tried too many other options as I think that really would be avoiding my work! Desktop effects does slow my computer down quite a lot, but not sure that isn't normal.

Just got to get the "goes to sleep and never wakes up" problem fixed now!

---

### Post by FuturePilot on 2007-05-30
> **K31TH said:**
> I have found a fix for this it is a bug with Nvidia drivers, this is a temp fix until they release a patch. 

Right click on the Beryl Emerald go to "Advanced Beryl Options" then "Rendering Path" then select "Copy"

That fixed it for me, apparently it id slower however I figured slower is better than black windows :D 



Hope that helps a few people!
Yes selecting the Copy option worked for me too. It's caused by a bug in the Nvidia driver and it's been around way too long.

---

### Post by twistedtwig on 2007-05-31
any ideas on how to fix this for non beryl people please?

---

### Post by nevernamed on 2007-05-31
hmm.... well interesting fixes that you proposed for me.... but I can't log in because the display drivers won't let x start. I suppose I could edit the xorg.conf file via recovery console.... but I wouldn't be able to finish your fix.
Do you see where I'm coming from? What you recommend?

---

### Post by bobbleSmurf on 2007-06-04
you should be able to shift to a text console by typing:
```
ctrl+alt+f1
```(or ...+f2 ...+f3 upto ... +f6 - each are separate text consoles. your graphical console is on ctrl+alt+f7) that will allow you to log in and then you can edit your xorg.conf file as follows.

**First back it up!**
Changing directory first is easier, but obviously be a little careful with the system files.
```
cd /etc/X11
```then make a copy of your original for backup. something like:
```
sudo cp -i xorg.conf xorg.conf.bkp
```(I've used -i so that it prompts you if you will be overwriting an existing file. Having to use sudo as its all root permission locked, may be asked to enter your password)

then alter the xorg.conf file (I've chosen nano to do this but other editors work the same)
```
sudo nano xorg.conf
```add the line that I posted before in the device section with the "nvidia corporation..." identifier (that is if you are using a laptop - may work similar for desktops, but don't know exactly):
```
Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 460 Go]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
[I]    Option        "UseDisplayDevice"    "DFP"
[/I]EndSection
```save by pressing **F3**

exit by pressing **F2**

reboot the system
```
sudo reboot now
```... I think... but as I am writing this, I don't want to try it out! might not need the "now" or to type it in caps ("NOW")...

then either:[LIST]
[*]whoop with joy when you get to see those pretty ubuntu graphics
[*]curse my sullied soul when you can't see nothing and your brain hurts from trying[/LIST]I hope this works for you... I know how frustrating it can get!

---

