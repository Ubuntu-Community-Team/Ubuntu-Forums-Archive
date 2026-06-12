---
title: "Simplified: HowTo  Compiz Fusion on Ubuntu 7.04"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by bdtgp on 2007-07-12
So I've been looking around at all the Compiz Fusion HowTo posts and they all include a bunch of extraneous information -- So I'm simplifying it for you guys that have these basic requirements:

-Ubuntu 7.04 (32-bit)
-NVIDIA or an Integrated graphics card (it may work for those of you with ATI cards but some have expressed issues)
-The ability to read and follow directions


**STEP 1**: Remove old Compiz effects

Open up your terminal and type
```
sudo apt-get remove compiz-core desktop-effects
```


**STEP 2**: Add the repository to your sources list

Back in the terminal, type
```
sudo gedit /etc/apt/sources.list
```
Now in the window that just popped up, scroll to the bottom and add these lines
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
Save that and then close the window.  Now in your terminal type
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
```
Then this one
```
gpg --export --armor 81836EBF | sudo apt-key add -
```


**STEP 3**: Update your system

Continuing with our party in the terminal, type
```
sudo apt-get update
```
Then
```
sudo apt-get upgrade
```


**STEP 4**: Install Compiz Fusion

Type this in the terminal
```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```
Now Compiz Fusion is installed!  Now we just need to get it started.


**STEP 5**: Start Compiz Fusion

Hit Alt+F2 and enter this command
```
compiz --replace
```


**STEP 6**: Run Compiz Fusion when the computer starts

Well if you don't want to enter those commands every time you want to run Compiz Fusion then just do this.  Go up to your menu bar and select
System>Preferences>Sessions and click "New"
For the name type "Compiz Fusion" and for the command type either
```
compiz --replace
``` 


**STEP 7**: Where are my window borders?

If you don't have window borders at this point, don't fret!  We just need to add a line to the device section of your xorg.conf file.  Open up the terminal and enter
```
sudo nano /etc/X11/xorg.conf
```
Scroll down until you see the section labeled 'Section "Device"' In that section add this line:
```
Option "AddARGBGLXVisuals" "True"
```
Then hit Alt+F2 again and enter this
```
compiz --replace &
```
You should be all set with borders and everything!  To get it to run at start up you will need to run this for the Command when you click "New"
```
compiz --replace &
```

I hope that helps!  Let me know whether or not it works for you.

---

### Post by jdewire04 on 2007-07-15
I used your step by step guide for installing compiz fusion and it went flawlessly, until the very end. It seems my computer failed some sort of check... When i went to do the last step on your guide i get this error:

[I] "  john@john-desktop:~$ compiz --replace
   Fatal: Failed test: texture_from_pixmap support
   Checks indicate that it's impossible to start compiz on your system.  "[/I]

Any idea what this is, or even better how i could fix it?

A little information about my computer:

Amd athlon 64 2x dual core processor running at 4.4 Ghz
2 Gb of memory
320 Gig HardDrive
and a 512 mb ATi graphics card thats running on a "restricted" accelerated graphics driver 
(not sure what that means)

hrmm..just read a couple other forum threads and someone with a similar problem was suggested to install the latest drivers for his graphics card. Where can i find drivers for my card? 

I read that ATi is problematic for linux. How problematic? Fixable? or should i look into replacing the card (I just bought the thing) (but not so recently that I'd be able to return it...)


Thanks for your time.

---

### Post by dre1187 on 2007-07-16
hey guys, im tryin to install compiz fusion but anytime I go to install it I get an error saying that 
" E: Couldn't find package compizconfig-settings-manager "

anyway to get around this?

I've looked in other forums but no luck. Hopefully you guys can help me out. 

Thanks

---

### Post by Nessa on 2007-07-16
Worked smoothly. Thanks!

How do you add workspaces? I only have 2...

---

### Post by andrewsomething on 2007-07-16
@bdtgp

Your howto isn't going to work for everyone. You might want to update it to state what graphics card and drivers you are using since results will differ depending on that. Other than that, it should work for anyone who already had desktop effects or Beryl running previoulsy just as smoothly as you say...

@Nessa
Open up the setting manager and goto General Options. Find the setting for horizontal virtual size and set to four.

@jdewire04 
Yes there are some issues with ATI and Linux, but you can make it work. I'm running it with ATI. What model card do you have? You probably need to set up an XGL session. Try looking at this thread: [http://ubuntuforums.org/showthread.php?t=482773&highlight=xgl](http://ubuntuforums.org/showthread.php?t=482773&highlight=xgl)

---

### Post by Nessa on 2007-07-16
Yeah, I read that on another thread too. This is awesome!

Still doesn't run at startup but that's ok. :D

Happppeeeeeeeeeeeeeeeeeeeeeeeee!

---

### Post by andrewsomething on 2007-07-16
I actually think the two sided work space looks really cool. It's like fliping a piece of paper. I just need more space so I use the cube. =)

---

### Post by Nessa on 2007-07-16
How do you change the background of the cube?

---

### Post by andrewsomething on 2007-07-16
> **Nessa said:**
> How do you change the background of the cube?

Goto Desktop Cube>Appearance>Skydome from there you can change the gradient or use an image that is the correct size.

You can find some here: [http://www.compiz-themes.org/index.php?xcontentmode=6110&PHPSESSID=120080727e9ae1227dfc7f19865e10ba](http://www.compiz-themes.org/index.php?xcontentmode=6110&PHPSESSID=120080727e9ae1227dfc7f19865e10ba)

---

### Post by Nessa on 2007-07-16
Thanks much! :)

---

### Post by MaximB on 2007-07-16
Thanks

---

### Post by andrewsomething on 2007-07-16
> **MaximB said:**
> 
yes I have ATI 9800 Pro Video card
but I use the property drivers as they perform much better with my card so I can't use this guide : [http://ubuntuforums.org/showthread.php?t=482773&highlight=xgl](http://ubuntuforums.org/showthread.php?t=482773&highlight=xgl)  that Andrew mentioned.

what can I do ?

Have you tried that guide? My understanding was that it is specifically for use with the proprietary driver. 

There are so many conflicting how-to's  out there I know it can be a major pain. I wish people were better about stating up front what card and driver they use when posting how-to's. These forums are amazing, but sometimes sifting through it all to find what you need can be so hard.

---

### Post by kiv on 2007-07-16
> **Nessa said:**
> Worked smoothly. Thanks!

How do you add workspaces? I only have 2...

It's in a sub option somewhere .. called "virtual desktops" or something. It took me about 20 mins to find! eek... I'll have a look for you when i get home.

---

### Post by cookieofdoom on 2007-07-16
It's under CCSM --> General Options --> General Options. If you're using the cube you just adjust the horizontal. If you were using the wall plugin or the desktop plane plugin you'd want to use vertical and horizontal together.

---

### Post by bdtgp on 2007-07-16
@ andrewsomething: I'll make an edit to tell people that im running an nvidia card.  there are different tweaks for different cards and different system configs.

---

### Post by andrewsomething on 2007-07-16
> **bdtgp said:**
> @ andrewsomething: I'll make an edit to tell people that im running an nvidia card.  there are different tweaks for different cards and different system configs.

Thanks! It's a great guide, very simple and straight forward. I imagine it should work for most people with nvidia cards. Things get more complicated with ATI since they haven't opened up their drivers.

 Like I said, there is so much great info in this forum, but it's often hard to sift through every thing to find what applies to you. Maybe someone who has gotten Compiz/Fusion working on multiple setups could compile a list of how-to's that work best for different cards and drivers.

---

### Post by ittiam on 2007-07-16
I already have beryl running using Intel embedded graphics card? Will this tutorial suffice for me in updating to compiz-fusion? Also I am not clear with this one forgive if it is stupid, I dont need to remove beryl if am updating to compiz-fusion right?

---

### Post by bdtgp on 2007-07-16
you shouldnt need to remove beryl but i would recommend it seeing as how compiz-fusion is more recent and stable than beryl.  it also has the same features from what i remember, plus more.  compiz gets updated all the time as well.

as far as this howto goes, people with integrated cards have not had too much trouble using this to my knowledge.  let me know though.

---

### Post by chiklit on 2007-07-16
Worked well for me once I realized I had to get XGL running first. I got emerald running with it too, it seems I have to restart compiz whenever I want to change the emerald theme though. Is this normal, or is there a way around it?

---

### Post by ittiam on 2007-07-16
i did go as said by the tutorial but am not sure whether fusion is working or not. I am running it using emerald since running compiz alone never worked for me. If I just run compiz --replace nothing works, all window borders go away. But if i run compiz --replace -c emerald then at least the window border doesnt go away. The only effect I am able to see is zooming into the screen. Am not sure whether it was already there in beryl, i guess not. But am not able to paint fire on the screen etc etc.

Kindl

---

### Post by ittiam on 2007-07-16
It works fine now! Zen!

---

### Post by ittiam on 2007-07-16
But now am not able to play videos? Did anyone else get the same problem? To be precise I dont get any video in a mplayer under xv driver only sound. However if i change to any other driver say x11 i get the video but I dont get fullscreen.

---

### Post by Gorgo13 on 2007-07-17
Hi there!

Got a problem!! I installed CompizFusion on a brand new Ubuntu install. But I cannot enable the "Desktop effects" in the System>Preferences!! How can I enable the Cube and the Window wobble??

Thanks a lot!

---

### Post by bdtgp on 2007-07-18
go to system>prefs>compizconfig settings manager.  you can enable stuff in there.  if for some reason that doesnt work let me know,  i can help you out with some easy xorg editing.

---

### Post by bdtgp on 2007-07-19
This post is getting a lot of views.  Is there any way to have it be made a Sticky?

---

### Post by Kboss34 on 2007-10-30
:) Thanks for that!

---

