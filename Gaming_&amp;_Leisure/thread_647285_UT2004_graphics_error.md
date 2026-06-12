---
title: "UT2004 graphics error"
date: 2007-12-22
forum: Gaming &amp; Leisure
---

### Post by Error1312 on 2007-12-22
I reïnstalled UT2004 yesterday through the linux-installer.sh script. The installation went just fine, but when I start the game and I try to change the resolution it crashes with the error below. I use Ubuntu 7.10. I have installed the latest NVIDIA drivers and glxgears reports around 3200 fps. I used to play this game without problems on Feisty. 

The error:

> 
elegia@amnesiac:~/software/games/ut2004$ ./ut2004 
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error
elegia@amnesiac:~/software/games/ut2004$ 


When I try to play the game in it's default 800x600 resolution, it works well, but it seems some textures and skins are messed up. 

I found a couple of topics about the problem, but none seem to give a working solution. I'm hoping you guys can help me out on this one.

---

### Post by Error1312 on 2007-12-22
Ok, I managed to be able to change the resolution. Turns out I had to set the color depth to 16 bit, the same as my desktop. 

However, I still have strange looking textures (like barcodes with black and white stripes) ingame and the menu backgrounds also look weird.

---

### Post by harvodan on 2007-12-26
I have a similar error in UT2004, under Ubuntu Feisty, some textures, mostly skyboxes and such are incorrectly displayed. Nvidia driver version 169.07. It's affecting quite a lot of the game.

---

### Post by roaldz on 2007-12-26
I´ve had this problem with the new driver too. Just came down to downgrading the driver version. Now I´m using the repository´s driver (nvidia-glx-new). No problems anymore.

---

### Post by Error1312 on 2007-12-26
Thanks. I'll try downgrading my driver and see what it does. :)

---

### Post by harvodan on 2007-12-26
> **roaldz said:**
> I´ve had this problem with the new driver too. Just came down to downgrading the driver version. Now I´m using the repository´s driver (nvidia-glx-new). No problems anymore.

Just out of curiosity, what version of ubuntu are you using? The one in the repositories for Feisty doesn't seem to work with my 8800.

---

### Post by Perfect Storm on 2007-12-26
If you're using feisty - you can download which nvidia driver you want from nivia homepage, just check their archieve. The one in Gutsy is 100.14.19

---

### Post by harvodan on 2007-12-26
> **Artificial Intelligence said:**
> If you're using feisty - you can download which nvidia driver you want from nivia homepage, just check their archieve. The one in Gutsy is 100.14.19

Thanks. UT2004 works fine with earlier versions, but another game I run through wine doesn't work so well with that version. Strange and infuriating. I was hoping for more of a workaround from NVIDIA or something. Hopefully a new version will turn up soon.

---

### Post by JunySan on 2008-01-31
Same error here, some graphics look like bar codes, if you install an older NVIDIA driver UT will work fine (in my case) ,but ET:QW will crash with the older driver.....:(

---

### Post by zoro on 2008-02-03
*bump*
UT2004 in Gutsy is doing this too. Also, when UT2004 is loading, the splashscreen is strangely almost-attempting-to-be-transparent, and the menu screens have a wierd light-blue hue to the backrounds

---

### Post by Perfect Storm on 2008-02-03
Disable compiz will do the trick.

---

### Post by zoro on 2008-02-03
> **Artificial Intelligence said:**
> Disable compiz will do the trick.

Er - compiz is on by default. Disabling something that's installed and enabled for **every** new install simply isn't acceptable.
There has to be a better work around than this.

---

### Post by roaldz on 2008-02-04
> **zoro said:**
> Er - compiz is on by default. Disabling something that's installed and enabled for **every** new install simply isn't acceptable.
There has to be a better work around than this.

Why not? Just create two shortcuts on you desktop, one with "metacity --replace" and one with "compiz --replace". This still is the easiest way to get the most gaming power:)

---

### Post by zoro on 2008-02-04
I'm very comfy in Linux, and I really do want to use Ubuntu on my home desktop, but hacks like this (and lets face it - its a hack) are what really frustrate me when comparing the desktop environment to Windows.

I didnt mean for my post to sound like I was lashing out at A.I. there, I was really lashing out at the fact that this is even neccessary to do something as simple as play a game

---

### Post by zoro on 2008-02-04
I should probably add that "metacity --replace" fixes the transparant-splash-screen-logo problem, but the other problems (ingame) still exist

---

### Post by roaldz on 2008-02-04
> **zoro said:**
> I'm very comfy in Linux, and I really do want to use Ubuntu on my home desktop, but hacks like this (and lets face it - its a hack) are what really frustrate me when comparing the desktop environment to Windows.

I didnt mean for my post to sound like I was lashing out at A.I. there, I was really lashing out at the fact that this is even neccessary to do something as simple as play a game

Then leave compiz on, i've never had difficulties with that.. Only a small performance loss.

---

### Post by Drezliok on 2008-04-18
Same trouble with weird barcode textures. I am however using the soon to be released Hardy Heron.

I have all the eye candy turned off with the "appearance" section of preferences and it still does it. Am I still using Compiz with all the cany off?

---

### Post by zoro on 2008-04-19
> **roaldz said:**
> Then leave compiz on, i've never had difficulties with that.. Only a small performance loss.

Did you even read my post?

---

### Post by Perfect Storm on 2008-04-19
> **Drezliok said:**
> Same trouble with weird barcode textures. I am however using the soon to be released Hardy Heron.

I have all the eye candy turned off with the "appearance" section of preferences and it still does it. Am I still using Compiz with all the cany off?

Install Compiz Fusion Icon app - it makes it all easier (repo in Hardy).

---

### Post by FrozenFox on 2008-04-19
How is an on/off switch for heavily graphic-using software a hack? That's exactly what those commands do, enable compiz (which disables the current non-effects window management, metacity) and enable metacity (which disables the current compiz effects window management).. is it because it's a command instead of a button, or just because you have to do it in the first place? ..and why are you saying that "vs windows" is any different? If it's just because you have to do it in the first place, Xp is a silly comparison as it doesnt have such effects, while vista has comparable performance loss unless you turn effects off manually too from my experience. However, it's not as easy and quick (2-5 seconds to turn off/on) as compiz, especially with the 3-click process of using the compiz fusion icon. In any case, if this bothers you, you can 1) Try the fusion-icon program as suggested  2) Install and run ccsm *compiz config settings manager i think* from the repos, go to general options under the general tab and tick 'unredirect full screen windows' which usually works decently  3) Run your games via scripts that turn that stuff off and on when you load them and quit respectively.

But in any case, the texture issues (with exception to the semitransparent loading splash) are not because of compiz as you've seen, they're nvidia's buggy drivers (a friend told me he had the same issue in the windows versions on opengl games btw, though I couldn't say for sure myself whether that was an isolated incident), as was said several times in the rest of the thread before you. The texture and barcode garbage is present in nvidia drivers > 100.x up to at least the beta before the current one, which ive not tried as the 96xx ones work fine for me. Theyre terrible and glitchy, I had the same bug too. Revert to the 100.x drivers and it will work fine. There is no other solution but to wait for nvidia to fix it and either deal with that bug or revert to older drivers and wait, which is out of ubuntu's control. I -think- the newest -beta- ones on the nvidia site might have fixed it, actually, come to think of it. Check Envy and see if it installs those and look for yourself, it's much easier than installing them manually.

---

### Post by Drezliok on 2008-04-20
Tried EnvyNG first to see if that worked but no it failed to fix the issue. Infact I think it installed the same drivers that I am using albeit installed differently

---

### Post by Perfect Storm on 2008-04-20
Maybe you should try the latest beta driver from nvidia homepage.
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by Drezliok on 2008-04-20
I've never gotten it to install before but that was a few years ago when I was messing with debian. I know more now then when I first tried so I think your right.

I should remove Ubuntu's restricted driver before I start right?

*EDIT
I'll have to try some other day, after readying some of the docs I've decided to do with with atleast 7 hours sleep and no interruptions from my 3 month old.

---

### Post by Perfect Storm on 2008-04-20
uninstall 
linux-restricted-modules (if you have wireless you may not want to do this).
nvidia-kernel-common
nvidia-settings
and ofcause the nvidia driver

Install
build-essential
xserver-xorg-dev

---

### Post by FrozenFox on 2008-04-20
After following Artificial's advice, It's really not as difficult as the docs suggest. Essentially, after his advice, here's what I do and it works fine:

1) Download the newest beta drivers to your Desktop.
2) log out of your desktop back to the login screen
3) ctrl+alt+f2 and log in from the given cmd line
4) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
5) sudo /etc/init.d/gdm stop  (i think that was the cmd)
6) cd /home/YOURNAME/Desktop
7) sudo chmod a+x ./NVIDIA*  [if you have no other nvidia stuff on your desktop. just type the full name of the nvidia drivers if that cmd doesnt work]
8)  sudo ./NVIDIA*  [same comment as #6. note that it may need to be sudo sh ./NVIDIA*, but I don't think so]
9) let it build a module when it doesnt find one on the nvidia site, then at the end say yes, edit xorg.
10) when done, sudo reboot

and there you go. all done, assuming I haven't missed any dumb steps. if it nags that X is still running, there's something not working with step #5, because gdm isnt shutting off. sometimes it will give some other weird nag errors, but it will work correctly anyway. if you reboot OK and you get the nvidia screen, open a terminal and type "glxinfo | grep direct" and check it. if it runs ok and says direct rendering is enabled, try "glxgears". If the gears show up after a second, they should soon post FPS to your console. FPS should be pretty high. if that's ok, you're good to go.

---

### Post by Perfect Storm on 2008-04-20
> 5) sudo /etc/init.d/gdm stop (i think that was the cmd)

correct.

> 7) sudo chmod a+x ./NVIDIA* [if you have no other nvidia stuff on your desktop. just type the full name of the nvidia drivers if that cmd doesnt work]
8) sudo ./NVIDIA* [same comment as #6. note that it may need to be sudo sh ./NVIDIA*, but I don't think so]

7) you can skip if you do sudo sh <filename>.sh

> 9) let it build a module when it doesnt find one on the nvidia site, then at the end say yes, edit xorg.

I don't trust anyone by myself to edit xorg.conf. I suggest saying "no", then manually set the nvidia driver in your xorg.conf

> 10) when done, sudo reboot

**sudo /etc/init.d/gdm start** should be sufficient. ;)

---

### Post by FrozenFox on 2008-04-20
Thank you for the corrections, good sir ;)


BTW: According to the nvidia forums, the newest beta drivers fix the texture corruption issue. Hooray! They no longer completely suck! If you have problems with it still after installing, in nvidia-settings, set your video quality to something higher and it should work ok (if high enough).

---

### Post by Drezliok on 2008-04-21
> **Artificial Intelligence said:**
> 
I don't trust anyone by myself to edit xorg.conf. I suggest saying "no", then manually set the nvidia driver in your xorg.conf




Um, I am unfamiliar with console editing the xorg.conf file. what program do I use? Or am I able to do that with in the GUI before I restart X?

---

### Post by FrozenFox on 2008-04-21
Assuming you're already at the command line, you might as well use nano. sudo nano /etc/X11/xorg.conf, assuming you already made the backup of such in the given steps before. Just note ctrl+x i believe quits and asks you to save.

You could probably boot into the gui and do it that way after installing since xorg hasnt been changed, but why not just get it over with while you're there at cmd line instead of requiring a reboot / reloading x again? 

You may wish to refer to the nvidia documentation for post-installation xorg routines if you want to do it this way as opposed to nvidia-xconfig (Artificial prefers doing it himself for good reason, though I'm too lazy and have personally never had difficulty with that setting it up).

---

### Post by Drezliok on 2008-04-21
Works perfictly. Some last questions though.

What will happen if we have a kernel update. Do I have to reinstall the driver?

---

### Post by Perfect Storm on 2008-04-21
Aye,

---

### Post by Drezliok on 2008-04-22
Awesome.

BTW Artificial, Denmark is where my family came from some 3 generations ago. I've thought about visiting before, I have a half a family over there still. Plus Dirt from the farm. [some how my aunt got it through customs years ago.

It's just neat to meet people from My family came from.

---

### Post by itsguardianjon on 2008-09-02
ive been having the same problem i installed it first and it seemed fine but i didnt install it in "sudo su"  so i uninstalled it and reinstalled now i gotr the barcodes on some of the weapons how did it go from good install to weird install and sometimes when i exit game the sound doesnt work aka perminant mute until restart.

---

### Post by Perfect Storm on 2008-09-03
Sounds like hardware problems more than UT2004 problems.

---

### Post by ashmew2 on 2008-10-11
Thanks Everyone ;)

Using Hardy 32 Bit ..Upgrading to Driver version 177 works like a charm...Thanks!! Now i can finally kick some metal A$$ on UT :D :D :D

---

