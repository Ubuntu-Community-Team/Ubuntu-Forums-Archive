---
title: "HowTo: Xubuntu 7.10 - nVidia - Compiz Fusion Desktop Effects for Newbies"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by BoardDWorld on 2007-11-26
Compositing without Compiz Fusion is like giving a child a lollipopless lollipop stick. With this in mind I hope this helps anyone with nVidia get full compiz fusion desktop effects up and running. As titled this is for nVidia graphics cards. ATI graphics card owners can most likely continue at Step 4 after you have correctly configured your driver. You can search the forums for this. Good Luck All!

[COLOR="Red"]---->PLEASE NOTE THIS TUTORIAL IS SPECIFICALLY FOR NVIDIA AS TITLED<----[/COLOR]

[COLOR="Red"]Step 1:[/COLOR]
Make sure all your updates are applied and that Synaptic Package manager is closed!

[COLOR="Red"]Step 2:[/COLOR]
Install your restricted accelerated graphics driver. Open **Applications ---- Accessories ---- Restricted Drivers Manager**, and Tick the box to enable it.

[COLOR="Red"]Step 3:[/COLOR]
Install Compiz and Emerald. In Terminal Type or Copy & paste the following:
```
sudo aptitude install compiz compizconfig-settings-manager emerald libgl1-mesa-dri libgl1-mesa-glx
```

[COLOR="Red"]Step 4: (IMPORTANT)[/COLOR]
Set Emerald as the Window Decorator. Go to **Applications ---- Settings ---- Advanced Desktop Settings**. Under the **Effects** category click on the **Window Decoration** button. Where it says **Command** Type or Copy & Paste in the following:
```
emerald
```

[COLOR="Red"]Step 5:[/COLOR]
Set Compiz Fusion to start at login. Go to **Applications ---- Settings ---- Autostarted Applications**, click **Add** and in the fields Type or Copy & Paste the following:

Name:
```
Compiz Fusion
```
Description:
```
Desktop Effects
```
Command:
```
compiz --replace --disable-gtk
```

[COLOR="Red"]Step 6:[/COLOR]
You're Done, restart the PC!

[COLOR="Red"]Important Notes:[/COLOR]
* Just in case something goes wrong(Compiz crashes etc) you can re-enable Xfce desktop manager by going to **Applications ---- Settings ---- Autostarted Applications** and untick Compiz Fusion, Log out then log back in and run the following:
```
xfwm4 --replace
```

* Your Window Frame is now controlled by Emerald (**Applications ---- Settings ---- Emerald Theme Manager**). The default Emerald theme is a bit bland, you can find plenty more [COLOR="Blue"][HERE]("http://xfce-look.org/index.php?xcontentmode=102")[/COLOR]
Simply download the file and extract the folder to your /home/your username/.emerald folder and select the frame from within Emerald. Folders/Files with "." in front of them are hidden, to reveal them simply press Ctrl+H from within Thunar.

*  You can change the theme using GTK2+ or Xfce themes from [COLOR="Blue"][HERE]("http://xfce-look.org/index.php?xcontentmode=15x100x420")[/COLOR].
To use them go to /home/your username/ and create a folder named **.themes**. Extract the downloaded theme to the .theme folder and select it from **Applications ---- Settings ---- User Interface Settings**. The same method applies with icons and cursors only they go into /home/your username/.icons folder.

[COLOR="Red"]**Highly Recommended!**[/COLOR]
[This Theme]("http://skiesofazel.deviantart.com/art/imetal-for-gnome-53789181") is one of the most complete, maintained and perfected themes available on Linux. The single download contains everything you need and instructions to help you along. The screenshot used is Xfce.

---

### Post by urinetrouble on 2007-11-26
Thanks! :guitar:

I was wondering how to get compiz to start up in xubuntu on login... It was weird. The way I had it, it was starting up without any window decorations or compiz at all and I had to start compiz manually every time with alt+f2. I'm new to xfce and I couldn't find out how to do it with ~/.xinitrc or whatever I used to use for starting other window managers in other operating systems. It's funny how that "autostarted applications" has been sitting under my nose this entire time without me noticing it, haha :)

---

### Post by BoardDWorld on 2007-11-26
It often works out like that, glad to help!

---

### Post by buntunub on 2007-11-26
Followed your directions explicitly, but direct rending fails. When I run xfwm4 --replace, I get this.

xfwm4 --replace

** (xfwm4:6254): WARNING **: Another Window Manager is already running


how to fix??

---

### Post by BoardDWorld on 2007-11-26
Go to **Applications ---- Settings ---- Autostarted Applications** and untick Compiz Fusion, Log out then log back in and run **xfwm4 --replace** again. Please note you only need to run the command if it fails to actually function, not if it fails to start (you'll know because the window frames remain the same if it didn't start). Compiz rarely but sometimes randomly crashes and you'll be left with windows that can't move and are frameless.

I have adjusted the driver installation step to make it easier, this is what has most likely put you wrong.

---

### Post by Brian96 on 2007-11-27
Thanks for your help, but it didn't work for me. And when I try to run it from a terminal I still get the following error output:

> 
brian@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


Compiz works fine on this system with a full Ubuntu install, but I don't want anything that heavy. Any ideas what the problem is here?

---

### Post by hencethus on 2007-11-27
What if I don't want to use Emerald? I like the default xfwm window decorations.

---

### Post by BoardDWorld on 2007-11-28
@ Brian96, Either your restricted nVidia driver isn't installed for what ever reason or you didn't restart your PC. Also if you're going to enable compiz enable it with:
```
compiz --replace --disable-gtk
```

@ hencethus, I'm sorry but I only had Xubuntu for the day as I wanted to get a taste of Xfce. I never actually got around to trying to use xfwm4. It's now removed and I'm back on Ubuntu.

---

### Post by Brian96 on 2007-11-28
> **BoardDWorld said:**
> @ Brian96, Either your restricted nVidia driver isn't installed for what ever reason or you didn't restart your PC. Also if you're going to enable compiz enable it with:
```
compiz --replace --disable-gtk
```

@ hencethus, I'm sorry but I only had Xubuntu for the day as I wanted to get a taste of Xfce. I never actually got around to trying to use xfwm4. It's now removed and I'm back on Ubuntu.

I have an intel graphics card, so I don't need the nvidia driver. Also, I did try the compiz --replace --disable-gtk command as well.

What confuses me is that my Xorg file is identical now to what it was with the full Ubuntu 7.10 install in which the Compiz effects worked on this system. :confused:

---

### Post by cheaptrick on 2007-11-29
my desktop disappeared, i did xfwm4 --replace , but it is still the same, 
i went into desktop settings checked the 'allow xfce to manage desktop', still nothing changed,
then i uninstalled compiz and advance windows settings manager, it didnt help either, My desktop is gone.

---

### Post by cheaptrick on 2007-11-30
help?

---

### Post by BoardDWorld on 2007-11-30
> **cheaptrick said:**
> my desktop disappeared, i did xfwm4 --replace , but it is still the same, 
i went into desktop settings checked the 'allow xfce to manage desktop', still nothing changed,
then i uninstalled compiz and advance windows settings manager, it didnt help either, My desktop is gone.

Did you log out then log back in as described in post 5. If you did, log in in safe mode from the log in window and disable it under autostart and run xfwm4 --replace again.

---

### Post by pcjunkie on 2007-11-30
I could not get it to function and it did cause some corruption of XFE. Now I guess I should find a way to remove what has been done in this thread and try something else...

I hope this can help, something is missing? 

> quartz@quartz-desktop:~$ compiz --replace -c emerald &
[1] 5752
quartz@quartz-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:5826): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

(emerald:5826): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8




using command to start...
quartz@quartz-desktop:~$ compiz --replace -c emerald &

---

### Post by jpkotta on 2007-12-01
Do you really need to restart?  This isn't Windows.  A CTRL-ALT-Backspace should suffice.  

(I cheated.  I used startx to start a new X session to try this out.)
```
startx /usr/bin/xfce4-session -- :1
```

---

### Post by BoardDWorld on 2007-12-01
> **jpkotta said:**
> Do you really need to restart?  This isn't Windows.  A CTRL-ALT-Backspace should suffice.  

(I cheated.  I used startx to start a new X session to try this out.)
```
startx /usr/bin/xfce4-session -- :1
```

If you're installing the video driver it's recommended you restart your system, though everyone unto their own :)

---

### Post by IsraeliHawk on 2007-12-01
i did everything you said - and nothing happens... :/

now, before i begin - i installed xubuntu from gnome (since my system is pretty old.. and i figured i have an alternative only a day ago..) and messed up things by trying to enable the effects myself . 
so, i have 2 Q's:
first, will it help if i delete xubuntu from gnome, restart, and reinstall it, and then try installing the Deffects again? 
second, can i fix this without deleting?

thanks in advance.. :)

---

### Post by tak1150 on 2007-12-04
For those of you that have the same problem as I.
I couldn't get my CF to work in a fresh install of Xubuntu.
I did:
glxinfo | grep direct
and it said that I didn't have direct rendering.

The cause was that I was missing **libgl1-mesa-dri** (see [http://ubuntuforums.org/showthread.php?t=588735]("http://ubuntuforums.org/showthread.php?t=588735")).
Once you install that package, it should work as the original post said.

Blessings,
Tak

---

### Post by BoardDWorld on 2007-12-04
> **tak1150 said:**
> For those of you that have the same problem as I.
I couldn't get my CF to work in a fresh install of Xubuntu.
I did:
glxinfo | grep direct
and it said that I didn't have direct rendering.

The cause was that I was missing **libgl1-mesa-dri** (see [http://ubuntuforums.org/showthread.php?t=588735]("http://ubuntuforums.org/showthread.php?t=588735")).
Once you install that package, it should work as the original post said.

Blessings,
Tak

Thanks for letting us know, to make it simple on others I'll add it to the guide. It's interesting that this didn't affect me as mine was a fresh install as well, only updates applied...

---

### Post by dethredic on 2007-12-04
I don't have a "Settings" Menu In my Applications menu. Whats wrong?

---

### Post by IsraeliHawk on 2007-12-04
> **tak1150 said:**
> For those of you that have the same problem as I.
I couldn't get my CF to work in a fresh install of Xubuntu.
I did:
glxinfo | grep direct
and it said that I didn't have direct rendering.

The cause was that I was missing **libgl1-mesa-dri** (see [http://ubuntuforums.org/showthread.php?t=588735]("http://ubuntuforums.org/showthread.php?t=588735")).
Once you install that package, it should work as the original post said.

Blessings,
Tak

i followed your thread and it didn't work .. :(

any ideas? if you have any i would be more than happy if you'll answer in my thread..

[http://ubuntuforums.org/showthread.php?t=630542](http://ubuntuforums.org/showthread.php?t=630542)

thanks again :)

---

### Post by Odd-rationale on 2007-12-05
oops...

---

### Post by Brian96 on 2007-12-06
> **tak1150 said:**
> For those of you that have the same problem as I.
I couldn't get my CF to work in a fresh install of Xubuntu.
I did:
glxinfo | grep direct
and it said that I didn't have direct rendering.

The cause was that I was missing **libgl1-mesa-dri** (see [http://ubuntuforums.org/showthread.php?t=588735]("http://ubuntuforums.org/showthread.php?t=588735")).
Once you install that package, it should work as the original post said.

Blessings,
Tak

Thanks for that. I installed the packages recommended in that link. Now when I run compiz --replace from the terminal I get no error messages, but it otherwise does the same thing (basically gives me no window manager functions at all). I will have to keep looking around.

glxingo | grep direct now gives me a "yes" answer instead of no, so this seems to be on the right track.

---

### Post by ctrlf5 on 2007-12-09
Works for me. The [other one by Forlong]("http://ubuntuforums.org/showthread.php?t=567792") didn't.

---

### Post by tak1150 on 2007-12-09
> **Brian96 said:**
> Thanks for that. I installed the packages recommended in that link. Now when I run compiz --replace from the terminal I get no error messages, but it otherwise does the same thing (basically gives me no window manager functions at all). I will have to keep looking around.

glxingo | grep direct now gives me a "yes" answer instead of no, so this seems to be on the right track.

Your problem is most likely because the actual window manager needed (emerald) is not enabled when Compiz turns on. First you can tell if this is the case by doing the following from "Alt+F2"
```

emerald --replace

```
If this works, the lack of emerald enabling is the cause. Just follow the part where you type in "emerald" into Compiz manager in the original post.

tak

---

### Post by Brian96 on 2007-12-10
> **tak1150 said:**
> For those of you that have the same problem as I.
I couldn't get my CF to work in a fresh install of Xubuntu.
I did:
glxinfo | grep direct
and it said that I didn't have direct rendering.

The cause was that I was missing **libgl1-mesa-dri** (see [http://ubuntuforums.org/showthread.php?t=588735]("http://ubuntuforums.org/showthread.php?t=588735")).
Once you install that package, it should work as the original post said.

Blessings,
Tak

That did it for me. (I installed the dri and glx packages.) Thanks!

---

### Post by Brian96 on 2007-12-11
Not sure if this is relevant, but when I run cairo-clock it launches as just a white square. Anybody know what's going on?

---

### Post by BoardDWorld on 2007-12-12
This simply means Compiz isn't running.

---

### Post by Brian96 on 2007-12-13
> **Brian96 said:**
> Not sure if this is relevant, but when I run cairo-clock it launches as just a white square. Anybody know what's going on?

Finally found a solution on this thread: [http://ubuntuforums.org/showthread.php?t=492238](http://ubuntuforums.org/showthread.php?t=492238)

---

### Post by pinkwick on 2007-12-14
Hi, I followed this guide step by step, but Compuz doesn't work: there are no effects, and I can't see the windows border.

I have an nVida board, and I'm sure that drivers are ok because with gnome everything works fine (but slow! =P ).

What should I do? ^^;

---

### Post by tad1073 on 2007-12-14
I can't get to step four. (Set Emerald as the Window Decorator. Go to Applications ---- Settings ---- Advanced Desktop Settings.)  There is no settings option under the applications menu. The closest thing I see is Apps>sys.tools>Beryl Settings Manager and under System>Prefrences>Emerald Theme Manager. thanks in advanced for the help.:guitar:

by the way i think I have Ubuntu 7.10, how do I check the version? Also it is a wubi install.

finally got beryl working, now just need to learn how to configure it

---

### Post by Gigamo on 2008-01-01
Try getting 

```

sudo apt-get install compizconfig-settings-manager
```

I'm not entirely sure, it could also be named compiz-config-settings-manager.

After that is done, simply type "ccsm" in the terminal to run it.

---

### Post by mikexgough on 2008-01-01
All works good on my dad's pc.........clean install of 7.10, on 80g Ubuntu drive and one 20gb for back ups (used to be on windoze) 256MB XFX AGP Nvidia GeForce 6200  graphics, AMD xp2000 processor, 512mb ram..........the 6200 was a Christmas gift and father was on 6.06, so to use the card fully it was upped to 7.10 and way to go..........great Compiz effects and it's like a new pc........yay

---

### Post by Smashing Pumpkin on 2008-01-28
This thread is the best post I've found on getting Compiz to work. I've re-installed Xubuntu a number of times and each time I just follow these instructions and I'm sorted.

Cheers fella :)

---

### Post by ericveldhuizen on 2008-01-28
I have the compiz working etc but my screen font/resolution still looks very poor. I had it working ok, but it is very intermittent. See below my PC hardware details:
MSI Motherboard
AMD Processor
Serial HDD 320Gb
MSI NVIDIA GeForce 7300 videocard - 256Mb ( i have the restricted drivers loaded and activated)
Philips LCD widescreen monitor 20inch (model 200WS)
Screen resolution is set as 1680x1050

Not sure how to fix this so ubuntu will become readable with it's fonts. I have Unbuntu 7.10

Many thanks for your help in advance.

Cheers
Eric

---

### Post by kittiphanh on 2008-03-25
deleted

---

