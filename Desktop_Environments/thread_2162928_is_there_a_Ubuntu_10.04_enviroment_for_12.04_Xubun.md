---
title: "is there a Ubuntu 10.04 enviroment for 12.04 Xubuntu?"
date: 2013-07-16
forum: Desktop Environments
---

### Post by eival on 2013-07-16
ive been checking all the different settings so far since upgrading to Xubuntu 12 cause i didnt like the 10.10+ Ubuntu enviroments. but theres also alot of other simple things that dont seem to be availible or easily changed, like the fact my Alsa mixer has no minimize button, also the folder sizes on the desktop wont increase when i change their size in the settings but the font size works fine.. and the only 2 window styles that have a scroll bar i can actualy see but its either in purple or blue, i just want the different shades of brown/grey from Ubuntu, or at the very least manually set each section to a color of my choice and the "GNOME" style they do have isnt anything close to the one in 10.04U

and why for the love of god am i not able to just click "Move" on a toolbar icon and place it anywhere on the entire length of the 1920x1080 size bar and have it stay there!? it just all crams up together to the left, unless i add a bunch of "spaces" to the toolbar between everything or make a bunch of seperate mini bars for each icon so i can put the sign out button and time on the right..i cant even click and drag icons to make them launches on the toolbar either, i have manually "add launcher" and choose the app..

if 10.04 wasnt litterally broken and slow and still worked like it always did i wouldnt of never upgraded, but i would think ?-buntu distros would ATLEAST have theses basic functions across all versions, since they're supposed to be the most user friendly versions of linux

would it be better to just switch to Ubuntu 12.04 and make changes to that layout instead? will the install disk give me the option to just switch it over, like when i was able to switch from 10.04U to 12.04X without formating?

---

### Post by snowpine on 2013-07-16
Every version of Ubuntu is different than the previous version. This is a fact. :) If you don't like constant change then stick with the LTS (long term support) releases, which are supported 5 years.

---

### Post by Frogs Hair on 2013-07-16
1. 10.04 used Gnome 2 which Gnome no longer supports . 
2. Xubuntu uses Xfwm4 window manager. 
3. The gnome-session-fall back is available on 12.04 and is most like Gnome 2 in appearance, but lacks many of its features.   
4. The Mate desktop environment is a Gnome 2 fork and can installed on 12.04  and is an option on Mint.  [http://mate-desktop.org/](http://mate-desktop.org/) 
5. The lack of features in Gnome 3 are a result of Gnome's new direction .

---

### Post by buzzingrobot on 2013-07-16
10.04 was based on Gnome 2.  The Gnome project stopped working on Gnome 2 more than 2 years ago.  It's dead code, out to pasture.

MATE is a fork of Gnome 2 that is actively maintained.  From a user's point of view, it is essentially the same as the 10.04 interface (theming aside).  Component names have been changed in many cases to avoid conflict with Gnome 3 software that continues to use the old names. 

If the 10.04 environment is what you are looking for, your best bet is to install MATE per the instructions at mate-desktop.org.  I know from personal use that it installs and runs fine on Ubuntu 12.04 LTS and 13.04.  I would guess it would install and run fine on Xubuntu, but I'd certainly research that before taking the plunge.

---

### Post by grahammechanical on 2013-07-16
It is called a distribution for a reason. The Ubuntu/Xubuntu developers rely on the work of other developers. If the developers of the Xfce desktop environment improve/change things then the Xubuntu developers have to keep up. This is true with Ubuntu and all the flavours. Ubuntu has gone a bit further by having its own user interface, Unity.

If you think that Ubuntu 10.04 was just right for you, then do not install Ubuntu 12.04. You will not like it.

I think that you have reached the stage in your experience of Linux where you should bring out your very own distribution. Then you can have everything exactly the way you want it.

---

### Post by eival on 2013-07-16
i dont like the screen shots of Mate looking too much like WIndows XP with everything on the bottom toolbar.

im gonna try the Gnome enviroment i found in the package manager and see if that makes any improvments

---

### Post by eival on 2013-07-16
just finished installing, the classic gnome option with no frills is pretty much what i wanted and i like how it gives you the option when you log in which enviroment to use, not that im ever going to use those other ones. it has the newer left-side pannel version of Gnome as well, i might fool around with it since its already installed.

so when im in the Gnome envirment am i technically using Ubuntu 12.04? like if i had any issues or bugs, would that make a difference when explaining the issue?

---

### Post by buzzingrobot on 2013-07-16
> **eival said:**
> i dont like the screen shots of Mate looking too much like WIndows XP with everything on the bottom toolbar.



The panel can be moved to any one of the four sides of the screen, and new panels can be added.  Right-click on the panel and explore the options.

The contents of the panel -- the applets that you want to move -- is also controllable by the user.

---

### Post by ibjsb4 on 2013-07-16
Has this been mention?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by eival on 2013-07-16
> **ibjsb4 said:**
> Has this been mention?

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

i installed that earlier, but it didnt come with the metacity theme so thanks for that.

how ever, is there away to edit the top and bottom toolbars? i cant actually right click on any of them and when i click and drag an icon too them theres no way to actually move them to a specific spot on the bar and theres no way to add new bars.

i want to be able to put the trash on the bottom and get rid of the "show desktop" and "workspace" icons as well

---

### Post by cmcanulty on 2013-07-16
to move items or add toolbars use alt+rt cl or sometimes alt+rt cl+super key

---

### Post by ibjsb4 on 2013-07-16
> **cmcanulty said:**
> to move items or add toolbars use alt+rt cl or sometimes alt+rt cl+super key

Yep that should work.  Alt + right click on the panel (or an icon) for metacity.

Window key + Alt + right click for compiz.

---

### Post by eival on 2013-07-18
this is just rediculous, everything keeps crashing, its rediculous that i have to hold down alt keys just to do minor things, not to mention this Gnome classic isnt the final version before Unity, cause 10.04 looked alot different, this is more like 8.04

im going back to 10.04 clean install, it was starting to get buggy and i wont be able to use the latest version of chrome, but atleast i can do things like add a friggen time icon to my top toolbar and actually change the time right from its preferences, not running terminal codes... and not have everything crash every 10 seconds...oh and i can simply CLICK AND DRAG to any point on the bar and not have it snapping to one side or the next...

what happen to canonacle making a user friendly OS?

the funniest part is that they have built in windows 95 or 98 era themes 12.04...but not the Gnome 10.04...what is this Microsoft Windows now? you either upgrade and accept our forced changes or be stuck with no more support on the version that you can actually use and not have to install a knock-off UI that doesnt work or have any of the same features.

---

### Post by Lewis Balentine on 2013-07-18
What I fail to understand is the various distributions are jumping on the bandwagon to emulate the Windows 8 Metro style interface.
I could be wrong but I think most people moving to UBUNTU from windows are doing so to get away from Microsoft's constantly changing UI and the personnel retraining required. In other words if they wanted METRO then they would probably stick with MS Windows 8 instead of Ubuntu or some other flavor of Linux. Personally I am not a fan of the Metro UI and that goes double for Unity and the new GNOME Unity clone as well.

---

### Post by cmcanulty on 2013-07-18
you have it backwards unity was first win 8 is imitating ubuntu, that said both are huge time and click wasters

---

### Post by eival on 2013-07-18
i actually gave Ub12.04, clean install a chance and ...its actually not that bad, much better than Xu for sure. getting used to the File/Edit/Tools...ect placement in the top toolbar didnt take that long to adjust to

but for whatever reason when i unchecked "download updates" during the install it still did, resulting in taking litterally hours cause of whatever default server it chooses. why cant they put the server test inside the installer if they're going to mandate updates? it takes litterally 30 seconds and would save people alot of time, especially when you're apparently trying to help speed up the process by doing it during install

i almost pulled the ethernet cord out when i saw the very first "downloading packages" text pop up and it said 40+ minutes....i got Fios 80/35..are you kidding me, stop trying to download from Uganda at 25kb/s and just install the OS and then let me download everything from the USF college mirror 1 hour from my house.

how ever on my other machine the UI never loaded and the monitor was flicking like crazy, which was the same when i loaded Xu12 too but atleast the UI loaded and i could find my way to the 3rd party hardware install option, im guessing ill need to do that from the command prompt in Ub12, is that even possible?

---

### Post by buzzingrobot on 2013-07-18
If  you lament the loss of the Gnome 2 interface delilvered in 10.04, I am at a loss to understand why you don't want to give MATE a try.  It is, after all, a recompilation of the Gnome 2 source.

---

### Post by BBQdave on 2013-07-18
> **eival said:**
> i actually gave Ub12.04, clean install a chance and ...its actually not that bad...

As far as Ubuntu Unity 12.04LTS, I humbly offer that it is a well done *next step* in the evolution of Gnome - beyond Gnome 2. For me, Gnome 3 is still trying to find it's way.

If you really dig the work flow of Gnome 2, and want an up to date LTS of Gnome 2 - give Linux Mint Maya 13LTS with MATE a try :D

---

### Post by eival on 2013-07-19
i dont have any +700mb discs, and thus i cant install any version of Mint, nor can i even install Debian, outside of the "standard" version which didnt even have a GUI and for whatever reason i couldnt even sign in as sudo even tho it clear as day had me set up the root password during the install process, so that was out of the bag of possabilities as well.

after doing some research on both Xu and Ku 12.04's i found out they arent even fully supported as Ubuntu interms of finance and availability of apps, i thought Canonacle made all of them and just simply reskinned for different audiences but apparently thats not the case, atleast anymore.

and for one last gasp i fresh installed10.04 but its just so broken and unstable its impossible to use now, especially since alot of stuff isnt even availible to redownload and all the apps are out of date and clearly 12.04 makes a huge difference

only real pain so far is every time i open GIMP its toolbars are under the top system bar so i cant actually click and drag and move them around, im guessing i have to change something in compiz settings, i saw something about telling it to open things at certani areas of the screen, maybe bottom right would be the safest, as long as the top is free to be grabbed...then again maybe if the top system bar was set to auto-hide that might fix it...idk that just seems like a really bad and buggy design choice, i dont know how they're QA team tested that and said "yeah this is totally easy to use" and Unity started back in 10.10 didnt it? this is supposed to be the STABLE version

does 13.04/10 have a better UI with less glitches? i might acually upgrade from the LTS if they're not going to ever update 12's UI and merely make security updates for the next 3 years


i would actually prefer to keep that left bar but go back to having each window keeping the menu bar on its window, is there an option for that in compiz settings? im afraid to make any changes cause it'll just screw everything up, not to mention ive heard you can actually break the OS entirely if Unity is changed too much


also i want to get rid of the 4 desktop icon which is locked, the only time it actually comes in handy is when i have that issue with GIMP or others where the top of the window is covered by the top bar, but its Menu options won appear, unless i open up the 4 desktop quick and close it so the UI fixes itself.


also is there anyone working on an updated flash varient for firefox? like Google has done for Chrome with Pepperflash? itm surprised 11.2 still works, im wondering why google hasnt updated their youtube players to basically require 11.3+ archetecture to play, that would cause someone to get off their butt and actually work on it, either on Firefox or Linux's side

---

### Post by r_avital on 2013-07-19
eival,

I'm in the same boat as you with 12.04 and the user interface and instability.  For one thing, 13.04 is "a little" more stable and worth a try.  And I really, really recommend you give MATE a try.  No need for large disks or installing all of mint, just install MATE under 13.04, and when you log in, you will have a choice to pick MATE as your desktop environment, AFTER you put in your user name, but BEFORE you enter the password and log in.

You can download by following the instructions here:
[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)

It looks and behaves just like a gnome session under 10.04 Lucid.

If you're on 12.04 right now, and you want to go to 13.04, keep this in mind;  The release notes for 13.04 state that you should first upgrade to 12.10, then to 13.04.  I did that, and in the end, there were so many glitches with lost or mis-configured applications, that I gave up and started a fresh install of 13.04.  

I wish I had found out about MATE under Raring 13.04 a month ago.  That's a month out of my life I'll never get back.

You also mentioned something about 700 Mb disks -- maybe you know this, maybe you don't, but you don't need them.  If you download an ISO of any distribution you want to try, you can use your own current install of Ubuntu (even 10.04) and create a boot-up image of the distro (any version of mint, any version of ubuntu, kubuntu etc.) with your Startup Disk Creator (should be under your Administration menu if you're using 10.04).  Surely, any cheap 1-Gb usb stick should be more than good enough for this.  That way you can try it before you install it, and you can install it from the same usb disk if you like it.

Hope that helps :)

---

### Post by eival on 2013-07-20
is there a way to set the side scroll bar from white to an actual color, without changing the entire theme?

i like the default, but i just want to make the white bar, is there a hidden config file where it has html color code for that bar (#FFFFFF - white) and i can change it to another color of my choice?

---

