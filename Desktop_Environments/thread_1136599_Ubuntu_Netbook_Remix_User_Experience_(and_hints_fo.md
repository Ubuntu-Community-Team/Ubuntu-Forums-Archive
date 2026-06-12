---
title: "Ubuntu Netbook Remix User Experience (and hints for eeepc 701)"
date: 2009-04-25
forum: Desktop Environments
---

### Post by boom2k1 on 2009-04-25
I installed 9.04 UNR on my Asus eeepc 701 yesterday and just want to share a few hints and comments about it. 

First, I was a bit hesitant to install UNR because on [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

354705 - [Jaunty] Microphone doesn't work at all on Eee 701SD

this bug really bothered me. But anyway, I couldn't resist wiping out my 8.04 for that newest version! (I was positive there must be some fixes out there).

Yes indeed!
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes) 
provided the solution:

```

"For the 700/701 
Edit /etc/modprobe.d/alsa-base and add the line &#8220;options snd-hda-intel model=3stack-dig&#8221; 
Run the following command: 

sudo alsactl store
"

```
. 

2. I noticed a super laggy mouse hovering experience on the application launcher that came with the UNR. I guess it is a strange bug associated with eeepc 701 only... That really destroyed the whole ubuntu experience right from the start. Anyway, as a Ubuntu user for 2 years, I turned to my best friend for solution: Google...  and I located this page

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/)

Yes, this required me to read through this complicated page to know that I could fix it by installing two deb files: the header and the other file. (yes, it was a fix.)
[after installing the deb files, reboot the netbook].

3. Then I tested whether my webcam with the program Cheese worked or not. Nope. But from some online pages, I realized that it had to do with my bios setting. Therefore, I rebooted my computer and pressed F2 when the computer first loaded up to get to the BIOS page, and from there I enabled the webcam.
Fixed!

4. I tried the Desktop Switcher and after a reboot I ended up without a panel (that wouldn't fix itself after subsequent reboots). How annoying! Here I found the solution:
```

http://ubuntuforums.org/showthread.php?t=1115365

```

5. ***ACTUALLY THIS POINT MIGHT NOT BE VALID - I AM ABLE TO BRING UP THE PACKAGE INSTALLER TO INSTALL A DEB FILE BY DOUBLE CLICKING THE DEB FILE FROM THE NAUTILUS FILEMANAGER ... (PERHAPS WHAT DIDN'T WORK WAS THAT FIREFOX DIDN'T RECOGNIZE THE DEB ASSOCIATION SO I COULDN'T JUST DOUBLE CLICK FROM THE FIREFOX DOWNLOADS POPUP WINDOW AFTER THE DOWNLOADS ***
I was also a little bit upset about not being able to DOUBLE CLICK to install the Skype and Adobe Flash deb packages I downloaded off the web to my desktop. It requested me to locate a program on my own to associate to open those .deb files. 
It is not a big deal for me, since I already could get away with using the 
```

sudo dpkg -i FULL_PATH_TO_FILENAME

``` command in terminal to install the stuff. But imagine a new user who is just curious to try out Ubuntu and discovered that he can't just double click to install! (associate that darn .deb extension to that GUI tool please!)
 - on a side note, it seems that firefox didn't associate opening a directory to the nautilus file manager.
 

6. I guess it isn't really a UNR thing, but I have a minor complain about not being able to detect my external monitor at the correct resolution. It only allowed that external monitor to have a maximum resolution of 800 x 600 rather than 1680 x 1050. I wouldn't be able to display my presentations nicely on my school projectors if it can only get to 800x600! (Okay, I admit it is already a HUGE improvement over requiring me to work with the xandr console commands)

Overall, I am very impressed by what the Ubuntu and Linux developers have done over the years. I really wish Ubuntu would recieve more and more attention from netbook manufacturers since it is such a decent OS. 

Let's just fix these annoying bugs so new users will have less excuses to turn away from Ubuntu!

---

### Post by MattMiddleton on 2009-04-25
Thanks very much for the fixes - I just installed UNR 9.04, and ran into the same issues.  Other than these issues, it's working quite a bit better than the Xandros install that came with the laptop.

---

### Post by shadowskyx on 2009-04-25
Thanks for the information.
I have a 701 myself and this will surely help a lot when I install it.

---

### Post by joey-elijah on 2009-04-25
Any chance of letting us know which deb files to install (and links) to fix the laggy clutter launcher? The bug report mentions several so a bit of help would be ace!

---

### Post by boom2k1 on 2009-04-25
Sure!
I used:
 linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb  21-Apr-2009 19:06  670K 
and 
linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb    21-Apr-2009 19:06   24M 

from 
[http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A](http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A)


(check if there are newer versions though)


O... and one of the points I made above about not being able to double click to install might be invalid!I can just double click the files to install from the Nautilus filemanager. (The Package Installer GUI tool would fire up). I guess I was having problem with double clicking from the Downloads windows in Mozilla Firefox only.

---

### Post by boom2k1 on 2009-04-25
I am extremely impressed by this version of Ubuntu.

I also installed the Ubuntu restricted extras.
O, and here is one other tip to configure skype:

In Skype's Options, go to the Sound Devices category
Sound in: HDA Intel (hw:Intel,0)
Sound out: pulse
Ringing: pulse

and after enabling the webcam from bios (or perhaps it would have already been enabled in your system), you should also see that from the Video Devices category, it would detect the 
UVC Camera
and you should have no problem using the webcam.


Feel free to add to this page all you want because we might be able to help more people here.

---

### Post by joey-elijah on 2009-04-25
> **boom2k1 said:**
> Sure!
I used:
 linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb  21-Apr-2009 19:06  670K 
and 
linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb    21-Apr-2009 19:06   24M 

from 
[http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A](http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A)


(check if there are newer versions though)


O... and one of the points I made above about not being able to double click to install might be invalid!I can just double click the files to install from the Nautilus filemanager. (The Package Installer GUI tool would fire up). I guess I was having problem with double clicking from the Downloads windows in Mozilla Firefox only.

Thanks for those. I've installed them but have yet to notice any difference...

---

### Post by boom2k1 on 2009-04-25
Did you reboot?

---

### Post by joey-elijah on 2009-04-25
> **boom2k1 said:**
> Did you reboot?

Haha! Yes i did reboot.

uname tells me i'm running 2.6.28-11 #43 generic (or some such) so i assume the correct headers/image are loading up... 

:confused: hmmm

---

### Post by Rohaq on 2009-04-25
Anyone else missing virtual desktops? I used them a lot in full fat Ubuntu 8.10, and am sad to see that I can't seem to add them in 9.04 NBR, or edit my gnome panel at all.

Any help on re-enabling them?

---

### Post by joey-elijah on 2009-04-25
Tbh - roll on Jolicloud! This netbook-remix version seems to run slower, need more configuration etc than any of the "ubuntu desktop with array kernel and launcher tacked on" versions.

---

### Post by boom2k1 on 2009-04-26
> **Rohaq said:**
> Anyone else missing virtual desktops? I used them a lot in full fat Ubuntu 8.10, and am sad to see that I can't seem to add them in 9.04 NBR, or edit my gnome panel at all.

Any help on re-enabling them?

I guess you mean enabling the workspace switcher and adding workspaces right?

Here is how I do it:
right click the leftmost Ubuntu icon on the taskbar/panel area and uncheck Lock To Panel. Then right click on the Ubuntu icon again to move it to the right a little bit. 
(The purpose is to create a little bit of empty space). 
Then right click on the empty space on the panel(taskbar) to the left of the Ubuntu icon (if it doesn't work, try the right of it -depending on where the maximus now got shoved to).. 

Hopefully, when you right click on that empty space you would see the Add to Panel... option. Click on it, and go to the bottom to locate the Workspace Switcher and click Add. There a new icon (workspace switcher)would be added to the taskbar... right click on it to bring up Preferences.(actually maybe you will see nothing there because the dark panel may be masking the Workspace Switcher item -but try clicking on some dark space to bring up the preferences of it). There you can increase the number of workspaces.)

I guess you can then play around with the positioning of those items on the panel.

 - I know my explanation kind of sucks, and there MUST be better way to enable it.

O.. alternatively, a way easier way is to go to Preference->Switch Desktop Mode. you can switch to the Classic Desktop and then add more workspaces by right clicking on the Workspace switcher icon beside the trash can on the bottom panel. But I would warn that perhaps you would run into that MISSING panel problem next time you reboot if you don't go back to the Ubuntu Netbook Desktop mode after you are done...

---

### Post by Rohaq on 2009-04-26
> **boom2k1 said:**
> I guess you mean enabling the workspace switcher and adding workspaces right?

Here is how I do it:
right click the leftmost Ubuntu icon on the taskbar/panel area and uncheck Lock To Panel. Then right click on the Ubuntu icon again to move it to the right a little bit. 
(The purpose is to create a little bit of empty space). 
Then right click on the empty space on the panel(taskbar) to the left of the Ubuntu icon (if it doesn't work, try the right of it -depending on where the maximus now got shoved to).. 

Hopefully, when you right click on that empty space you would see the Add to Panel... option. Click on it, and go to the bottom to locate the Workspace Switcher and click Add. There a new icon (workspace switcher)would be added to the taskbar... right click on it to bring up Preferences.(actually maybe you will see nothing there because the dark panel may be masking the Workspace Switcher item -but try clicking on some dark space to bring up the preferences of it). There you can increase the number of workspaces.)

I guess you can then play around with the positioning of those items on the panel.

 - I know my explanation kind of sucks, and there MUST be better way to enable it.

O.. alternatively, a way easier way is to go to Preference->Switch Desktop Mode. you can switch to the Classic Desktop and then add more workspaces by right clicking on the Workspace switcher icon beside the trash can on the bottom panel. But I would warn that perhaps you would run into that MISSING panel problem next time you reboot if you don't go back to the Ubuntu Netbook Desktop mode after you are done...The first solution worked, thanks. Seems kind of obvious now, looking back :)

---

### Post by cauemonteiro on 2009-04-27
[LEFT]Hello to all, 
  We also have an Eee PC 701 and installed the UNR and wonders if anyone is having the same problems than me and if someone found a solution! 
1) Slow interface optimized in the Ubuntu Netbook, when I mouse over the icons, he arrives to give a locked, it is very slow, after I open any application it is faster! 
 2) Slow the wireless network, the network cable is very fast, but the wireless network is very slow, my router is a linksys, it will be a BUG? 

 I look forward to in the comments! 
 A hug to all[/LEFT]

---

### Post by Mr_Crimson on 2009-04-27
> **boom2k1 said:**
> O.. alternatively, a way easier way is to go to Preference->Switch Desktop Mode. you can switch to the Classic Desktop and then add more workspaces by right clicking on the Workspace switcher icon beside the trash can on the bottom panel. But I would warn that perhaps you would run into that MISSING panel problem next time you reboot if you don't go back to the Ubuntu Netbook Desktop mode after you are done...

Oh thank God!  I thought I was going crazy.  I installed 3 times today thinking I somehow borked the install.  I suppose I'd be happy with the new fangled optimized desktop if it wasn't so laggy on my 900, but it seems there might be a solution to that.

Now I'm off to search of a way to switch it back, since I've got a relatively useless panel-less desktop.  ugh. :)  Do I hear a 4th reinstall in my future? ;)

-Crim

---

### Post by joey-elijah on 2009-04-28
> **cauemonteiro said:**
> [LEFT]Hello to all, 
  We also have an Eee PC 701 and installed the UNR and wonders if anyone is having the same problems than me and if someone found a solution! 
1) Slow interface optimized in the Ubuntu Netbook, when I mouse over the icons, he arrives to give a locked, it is very slow, after I open any application it is faster! 
 2) Slow the wireless network, the network cable is very fast, but the wireless network is very slow, my router is a linksys, it will be a BUG? 

 I look forward to in the comments! 
 A hug to all[/LEFT]


1. The 'mouse capture' bug is seriously annoying. It's a known bug but there is a workaround! hurrah! :P You need to download andinstall both of these: -

linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb 

and 

linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb    

from 
[http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A]("http://people.ubuntu.com/%7Eapw/lp349314-jaunty/?C=M;O=A")

Reboot and everything should be fine. 

As for the network issue, i have an eee 701 too but i can't say i've noticed it being overly slow. Obviously where you are in relation to the wifi base plays an important role.

Out of curiosity have you installed eee-applet (find it in add/remove) it's a great addition for disabling camera, card reader, over clocking, fan speed and more so you can eek the most out of your battery.

---

### Post by vexorian on 2009-04-28
This is tempting, I am a proud owner for a 4GB 701 eee, and I used ubuntu-eee 8.04 since then, but a jaunty upgrade would be nice if the improved booting time was cool.

I was hesitant to do it because of the wiki page:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701-SD](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701-SD)

First of all, what's up with "netbook remix is made for small screens" but then one of the issues in the wiki is that things are too big? What does "small screen" equal to for netbook remix? What's the new standard for netbooks out there? did it suddenly become bigger than 800x480 ?

The other thing is the atom processor listed as requirement, but It seems that isn't an issue?

Anyway, I've been wondering, anyone that installed jaunty on a 701, what's the boot time?

Also, shouldn't the intel graphics card regression affect the eee?

---

### Post by DocNielsen on 2009-04-29
This is great for you Eee users.

I have a HP 2133 and netbook-launcher is very laggy, using almost 50% CPU when idle, and 100% when i move the mouse over it. Very un-useful.

I did try the kernel above, to no avail. Any suggestions?

---

### Post by j0w on 2009-04-29
> **joey-elijah said:**
> 1. The 'mouse capture' bug is seriously annoying. It's a known bug but there is a workaround! hurrah! :P You need to download andinstall both of these: -

linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb 

and 

linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb    

from 
[http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A]("http://people.ubuntu.com/%7Eapw/lp349314-jaunty/?C=M;O=A")

Reboot and everything should be fine. 

As for the network issue, i have an eee 701 too but i can't say i've noticed it being overly slow. Obviously where you are in relation to the wifi base plays an important role.

Out of curiosity have you installed eee-applet (find it in add/remove) it's a great addition for disabling camera, card reader, over clocking, fan speed and more so you can eek the most out of your battery.

Tnx man for the fix, i have eee900 and i can confirm that this fix works fine on UNR 9.04

X)

---

### Post by joey-elijah on 2009-04-29
> **vexorian said:**
> Anyway, I've been wondering, anyone that installed jaunty on a 701, what's the boot time?

Also, shouldn't the intel graphics card regression affect the eee?

The boot time is notably quicker than with the Eeebuntu NBR i was using before. Takes about 20-25 secs at most from a cold boot to a usable desktop.

---

### Post by vexorian on 2009-04-29
All right then, time to download UNR

---

### Post by BionicSeahorse on 2009-04-29
> **joey-elijah said:**
> 1. The 'mouse capture' bug is seriously annoying. It's a known bug but there is a workaround! hurrah! :P You need to download andinstall both of these: -

linux-headers-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb 

and 

linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386.deb    

from 
[http://people.ubuntu.com/~apw/lp349314-jaunty/?C=M;O=A]("http://people.ubuntu.com/%7Eapw/lp349314-jaunty/?C=M;O=A")

Reboot and everything should be fine. 

As for the network issue, i have an eee 701 too but i can't say i've noticed it being overly slow. Obviously where you are in relation to the wifi base plays an important role.

Out of curiosity have you installed eee-applet (find it in add/remove) it's a great addition for disabling camera, card reader, over clocking, fan speed and more so you can eek the most out of your battery.

The fix works for me unless I switch users, then it gets actually worse (slower and choppier) than before. It will return to normal once I return to the user that was logged on first.

I also notice flash videos are slow and choppy while AVIs play perfectly. I thought the AVIs required a larger video bandwidth to play smoothly? In this case, it's seems to be exactly the opposite. :confused:

I am running UNR 9.04 on an Eee 1000hd.

---

### Post by vexorian on 2009-04-29
It's strange cause to my understanding ubuntu-eee used the same custom kernel, and I noticed a HUGEE slowdown when picking another user, made me decide that multi user is something it is just not made for...

---

### Post by earthtoclinton on 2009-04-30
Although the UNR Jaunty is actually very good, I would recommend Xubuntu 9.04 Jaunty for an eeepc 701. I have one myself, and have Xubuntu 9.04 on it - it runs much much quicker than ubuntu or UNR, as doesn't require anything near that level of tinkering to get things working..In my opinion it's the best and fastest OS for the 701. I will happily lend advice/show pics of my desktop to anyone interested :)

---

### Post by vexorian on 2009-05-01
Ouch, the installer seems to hung up at 82% , I am in a 4GB eee PC 701, not sure what's going on.

Before installing, I made sure to verify the md5sum was all right.

Edit: I reinstalled and it worked.

The boot time is so damn fast, that makes all worth it. Time to fix the other issues.

Imho I think UME-launcher is slow because of the intel regressions, will have to take a look on these regressions.

---

### Post by vexorian on 2009-05-02
Some tips for usual ubuntu users:

Default gnome session is nice, but it is not too small screen friendly. However, you can have the best of both worlds... Instead of changing to default gnome, you might try this, it is a hybrid:

**gnome/netbook-remix  hybrid without the slow launcher**

In startup programs:
* Disable netbook launcher
* Add a startup command for "nautilus --no-default-window

In appearance:
* Change the gtk theme to mist (at least temporarily, this will just make it easier to edit the  panel)

As for the panel:
* unlock the "ubuntu icon" thing, it seems to be just a show desktop button. Remove it, and add the gnome menu button to the panel (use "add to panel")
* You may now add another show destkop button or tweak a keyboard combination to show keyboard (I personally use 'super' for this, super is the eee's home icon)

Run gconf-editor: 
* Go to apps\nautilus\preferences\
* Check "show-desktop".

Now, restart the netbook. You can now place desktop icons (better use this for your favorite launchers and to unmount things)

You may now change the theme back to netbook-human, but I prefer mist as it uses less space. (By the way, I also recommend changing font size to 8 as it is perfectly readable in the 701 eee and then it uses less space)

screenshots:

---

### Post by grindboy on 2009-05-02
Thanks for these tweaks. I was pulling my hair out trying to figure out why the UME launcher was running so slowly on my 900 and my brothers 701.

Personally I love the UME interface and the boot speed with / on the 4GB soldered SSD formated to ext4 is phenomenal (about 28 seconds!)

---

### Post by vexorian on 2009-05-02
It's getting annoying that for Canonical "Designed for small screens" means "We'll **hardcode everything** so it works well ONLY on 1026x600 screens"

Really guys, in ubuntu-eee, evolution, cheese, appearance, all worked just fine in the 800x480 screen, these things were just 'optimized' for 1024x600, which means they won't look good in 800x480 resolutions without tweaks.

Anyway, at least for the important apps of the bunch I noticed with issues, there's a work around, I tried evolution, but it didn't work on it for some reason.

These tweaks will improve resolution support for rhythmbox, totem, cheese and the appearance dialog:

**Install devilspie**
Install the "devilspie"  package, through synaptic or with this command line:
```

sudo apt-get install devilspie

```

**script**
* Create a folder called ".devilspie" inside your /home/user folder. (Without the quotes)
* Inside this folder, create a text file called "eee.ds", give it these contents (change as necessary):

```

(if
    (or
        ; add semicolons before each line in order to disable...
        ; Cheese:
        (is (window_name) "Cheese")
        
        ; Appearance dialog:
        (is (window_class) "Gnome-appearance-properties")

        ; Appearance dialog:
        (is (window_class) "Totem")

        ;Rhythmbox 
        (is (window_class) "Rhythmbox")
        
        ; remove next semicolon if you want to try the tweak on evolution:
        ;(is (window_class) "Evolution") 
        
        ; You may try adding application rules:
        ;(is (window_name) "window title")
        ;(contains (window_name) "window title contents")
        
    )
    (begin
         (wintype "normal")
         (undecorate)
         ; (Change 456 with 480 - (size of panel), subtract twice if you have two panels )
         (geometry "800x456+0-0"  )
         (maximize)
    )
)
```

**Make devilspie start up**
Go to a terminal and type devilspie, now try the apps mentioned, if you want the change, go to the next step, if you don't, then you might try to tweak the script or just do nothing.

**Startup apps**
Go to preferences\ startup apps add this entry:
name: devilspie
command: devilspie
comment: This improves resolution support

**Restart your sesion**
Close your sesion, and enter again, devilspie will now run all the time, fixing these windows' sizes.

---

### Post by joey-elijah on 2009-05-03
> **earthtoclinton said:**
> Although the UNR Jaunty is actually very good, I would recommend Xubuntu 9.04 Jaunty for an eeepc 701. I have one myself, and have Xubuntu 9.04 on it - it runs much much quicker than ubuntu or UNR, as doesn't require anything near that level of tinkering to get things working..In my opinion it's the best and fastest OS for the 701. I will happily lend advice/show pics of my desktop to anyone interested :)

Hmm whislt it would run "faster" i'm not overly fond of XFCE 

Also by your by your argument you make it sound like Ubuntu is too bloated for an eee 701 (which can very happily run windows XP very very well) so what does that say about about Ubuntu?! 

In my expereince Ubuntu runs absolutely fine on a 701.

---

### Post by erdtmann on 2009-05-03
There is another way to (kind of) solve the gui slowness problem, that is use the (experimental) UXA dri2 video acceleration (not used by default because os stability issues). I used it on my 701 with no problem so far. 

For such, you need to add the line on Xorg.conf: 

Option "AccelMethod" "UXA" 

On the device section, this way:

Section "Device"
 Identifier "Configured Video Device"
 Option "AccelMethod" "UXA" 
EndSection

Then restart and profit.

---

### Post by kthdsn on 2009-05-03
I've been wanting to ditch my desktop for a while now but had no luck with using an external monitor on my eeepc 701.  I just wanted to say thank you for this thread as it has solved my problems :)

The new header/image things from page 1 fixed the laggy mouse for me, and as long as I reboot with my monitor plugged in, I am able to use a decent resolution.  All I need now is a USB hub and keyboard, typing on the tiny keyboard isn't going to be fun in the long term.

Thanks guys!

---

### Post by vexorian on 2009-05-04
Finally got the chance to test my new UNR jaunty setup in a real scenario, if you are using a 701 eee and got used to ubuntu-eee just know this: Moving to jaunty's UNR will involve some fixing, but it will be worth it, it boots faster and the interface also feels much more responsive, the new network thingie is going to be your best friend as you can switch premade static network setups without administrative access, and it is much friendlier when missin with wireless connections (It will tell you when one has been detected and whether it was able to connect or not)

---

### Post by earthtoclinton on 2009-05-04
> Hmm whislt it would run "faster" i'm not overly fond of XFCE

Also by your by your argument you make it sound like Ubuntu is too bloated for an eee 701 (which can very happily run windows XP very very well) so what does that say about about Ubuntu?!

In my expereince Ubuntu runs absolutely fine on a 701.

Yes indeed, I have had Ubuntu on my 701 in the past (Intrepid, and recently tried Jaunty and the UNR also) and it is very good. I guess i just prefer Xfce on it for it's speed..Ubuntu is quick but Xubuntu is that much quicker again. On a fairly underpowered netbook like the 701, every little bit of speed counts to me. Combine Xfce with the eee-control [http://greg.geekmind.org/eee-control/]("http://greg.geekmind.org/eee-control/") and it goes like a bullet.
I think UNR is great, and I applaud them for making it, but for me it doesn't really make things any faster - guess I just prefer a more traditional desktop :)

---

### Post by earthtoclinton on 2009-05-05
As in my post above - all 701 users should install the package from here if they haven't already :

[http://greg.geekmind.org/eee-control/]("http://greg.geekmind.org/eee-control/")

It's a must for the 701 - gives you great control and extra processing speed. I've been using it for quite a while through many versions and it's stable, never had any problems with it. Set it to auto start in your panel and your'e set :)

---

### Post by Supergoo on 2009-05-05
I installed the remix on my MSI Wind U100 and it runs great, no lag or install issues, the wireless card is only half workin git can see the networks but it will not connect to them, I use a USB wireless aptr. until this gets worked out, other then that , everything is working , I have not tryed the webcam or skype yet, but will tonight. over all I am impressed, I did have to reinstall , I was playing around with KDE Desktop and it was acting flaky , so I just reinstalled, , KDE alway feels unstable to me, but I am sure thats just me.

:guitar:

---

### Post by earthtoclinton on 2009-05-05
Ive tried KDE before to and had the same opinion, thats why I stick with XFCE, it's rock solid. Gnome is good too. I'm currently trying out Kubuntu 9.04 with the new KDE, and it looks really nice, but for me it's still a tad buggy. I'm wondering if you can tack the UNR interface on top of XFCE rather than Gnome? now there's a thought...

---

### Post by boom2k1 on 2009-05-07
nice suggestions and tweaks!
Thanks!

One question I have is whether there are EASY GUI ways to configure resolution of external monitor to whatever the optimal resolution should be. 

I found it tedious to edit xorg.conf to do this three years ago, and I still think it would be tedious for anybody to mess around those lines with no guarantee the tweak would work for everyone.

Case: I plug my eee701sd to my Samsung 20" monitor. The highest resolution I got was 800x600 (instead of 1680x1050). 

Any hints?

Occassionally I would run into articles/threads where people complain about resolution not set properly and sticking to Windows... Come on, Ubuntu team and xorg, I thought displaying resolution correctly is a pretty basic thing which any computer users would expect!
[Even a lot of us are familiar with using command line, we should not expect another command line solution...]

---

### Post by gstool on 2009-05-07
> **Rohaq said:**
> Anyone else missing virtual desktops? I used them a lot in full fat Ubuntu 8.10, and am sad to see that I can't seem to add them in 9.04 NBR, or edit my gnome panel at all.

Any help on re-enabling them?

Right click the left hand edge of the single desdktop in the lower panel and select Preferences to set the number you want.

---

