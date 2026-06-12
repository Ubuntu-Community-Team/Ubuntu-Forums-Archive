---
title: "Gutsy Compiz and strange XGL message"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by ahood on 2007-10-22
My problem is mentioned in many other posts, but no solution has been found. My system has an Nvidia GeForce 7800 GS video card, AMD Athlon XP 2200+ CPU, and 1 Gb RAM.

**Background**
I upgraded from Feisty Fawn to Gutsy Gibbon over the weekend. To prepare for the upgrade, I uninstalled all applications that were not obtained from the official Ubuntu repositories, which included beryl, miro, and cinelerra. I also removed all third-party repositories. I made sure that Desktop Effects was turned off. During the upgrade, I was notified that Desktop Effects was no longer supported and it was going to be removed. I was okay with that and proceeded.

**The Problem**
After rebooting, I noticed that the Desktop Effects icon was still in the Menu (System --> Preferences). I clicked on System --> Preferences --> Appearance --> Visual Effects and turned on the 3D compositing. 

After turning on the 3D compositing, I noticed that the application title bar was greyed and I could not move the application window.

I was forced to turn off 3D compositing.

**Attempted Fixes**
A. Uninstalled/reinstalled compiz/compiz-fusion plugins. 
> 
compiz 1:0.6.0
compizconfig-settings-manager 0.5.2
compiz-core 1:0.6.0
compiz-fusion-plugins-extra 0.5.2
compiz-fusion-plugins-main 0.5.2
compiz-gnome 1:0.6.0
compiz-plugins 1:0.6.0
gnome-compiz-manager 0.10.3
libcompizconfig0 0.5.2
libcompizconfig-backend-gconf 0.5.2
libgnome-compiz-manager0 0.10.3
python-compizconfig 0.5.2


The problem still persists.

It is not clear to me why all the above packages are needed. I have no clue as to which ones should be removed.

I checked to make sure that I have only gutsy repositories enabled and I do (see below)...

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


B. Tried running this command
> sudo nvidia-xconfig --add-argb-glx-visuals -d 24

No change. The problem persists.

**Clue to the Problem?**
I then decided to turn on compiz at 

> alan@alan-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:00f5 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Hmmm....This message is stating that compiz is looking for XGL, which is strange because my video card is an nvidia GeForce 7600. The video card driver I am using is the nvidia-glx-new 100.14.19+2.6.22.4-14.9 and should be using the AIGLX driver.

**Questions**
Should I be installing XGL?

Do I need to uninstall one of the compiz packages listed above?

Do I need to change video drivers?

[I]Note: I know that the nvidia driver is enabled as I see the nvidia splash screen on shut down and bootup. I also can run 3D games like Nexuiz and Tremulous just fine.
[/I]

Any help or suggestion will be greatly appreciated.

---

### Post by Abetorius on 2007-10-22
I've had similar problems. I've:
1. removed driver completly using synaptic,
2. rebooted,
3. downloaded and instaled driver again,
4. Enabled it in properitary drivers manager
5. rebooted 

and Compiz started to work fine.

---

### Post by ahood on 2007-10-22
> **Abetorius said:**
> I've had similar problems. I've:
1. removed driver completly using synaptic,
2. rebooted,
3. downloaded and instaled driver again,
4. Enabled it in properitary drivers manager
5. rebooted 

and Compiz started to work fine.

Thanks for replying so quickly and making a suggestion on how to fix.

I completely uninstalled the nvidia-glx-new driver and rebooted.

Unfortunately, the problem still persists, see original post above.

Still looking for a solution.

Al

---

### Post by ahood on 2007-10-22
Well..I have installed XGL from the Ubuntu repository, rebooted, verified that XGL was running, and started compiz. The problem described above still remains. I also tried downgrading to nvidia-glx instead of nvidia-glx-new, but this didn't help because nvidia-glx is not compatible with my GeForce 7800 GS video card.

The unfortunate thing is that beryl is no longer available in the repository to use instead of compiz. 

This is a serious dilemma for those of us who had the 3D desktop effects working, want it working, but cannot get it to work.

Unless a suggestion can be made that gets compiz working, the only options I can think of  is to wait for an update by Ubuntu developers or downgrade back to Feisty Fawn. I just might go back to Feisty as I thoroughly enjoyed the 3D effects and will miss having it. For me, the bug that is causing the failure of a working compiz is disappointing to say the least.

Mixed Emotions Here... :( ](*,) :cry: [-o< 

Al

---

### Post by ahood on 2007-10-24
Update....

I have made some progress, but not all is working as it should. 

I no longer have greyed out title bars when I turn on the 3D eye candy in Gutsy.

This was fixed after reading in another post to do the following:

> 
1. Install 'emerald' from the Ubuntu repository
2. Go to System --> Preferences --> Advanced Desktop Effects Settings
3. Filter the list by entering 'window decoration'.
4. Click on Window Decoration
5. Under the General Tabl, enter 'emerald' in the Command line.
6. Make sure the box for Enable Window Decoration is checked.
7. Click on Back button
8. Click on the Close button.


Now, when I start the 3D desktop effects, the application title bar is red. 

This is the output when I run the following command...

> 
alan@alan-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting emerald


**The Problem**
I cannot move the application window. I can minimize and close it, but it is unmovable. Thus, I have to revert back to no desktop effects.

Al

---

### Post by ahood on 2007-10-26
=D>

Okay, I have moving windows when enabling Visual Effects.

The lack of moving windows was a result of a plug-in not enabled under the System --> Preferences --> Advanced Desktop Effects Settings. Enabling the **Place Windows** (under Window Management) plug-in fixed the non-moving windows problem.

Al

---

### Post by ahood on 2007-10-26
[SIZE="4"]**SUMMARY**[/SIZE]
Compiz-Fusion is working and the problems described above were a result of lack of user knowledge on setting up a working Compiz-Fusion. When I started, my expectation was that all I had to do was install Compiz-Fusion and it would work. This was not the case at all and required much more user intervention to get working. Below are what I needed to do to have a functional Compiz-Fusion with little fuss after _upgrading_ from Feisty Fawn.

> **[COLOR="Red"]BEFORE PROCEEDING - be sure that the appropriate 3D graphic driver is installed and operational. I have an Nvidia 7800GS and have the nvidial-glx-new driver installed from the repository. Click on System --> Administration --> Screens and Graphics and be sure that the appropriate card and driver (opensource or proprietary) are selected.[/COLOR]**


[SIZE="4"]**STEP 1. INSTALL PACKAGES FROM UBUNTU REPOSITORIES.**[/SIZE]

Click on System --> Administration --> Synaptic Package Manager.
> 
compiz-core
compiz-plugins
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
compiz-config-settings-manager
libcompizconfig0
libcompizconfig-backend-gconf
python-compizconfig

emerald
libemeraldengine0

xserver-xgl


*Note: If the above packages are not found, then be sure that all repositories are enabled under Settings --> Repositories --> Ubuntu Software (check all 4 boxes). *


[SIZE="4"]**STEP 2. REBOOT THE MACHINE**[/SIZE]

*Note: xserver-xgl should be running automatically.*


[SIZE="4"]**STEP 3. ACTIVATE AND CONFIGURE PLUGINS**[/SIZE]
Click on System --> Preferences --> Advanced Desktop Effects Settings

**[COLOR="Blue"]CATEGORY: GENERAL[/COLOR] [COLOR="Red"]PLUGIN: GENERAL OPTIONS[/COLOR]**
[INDENT]**Desktop Size** tab.[/INDENT]
[INDENT][INDENT]> **Horizontal Virtual Size** should match the number of workspaces.

[/INDENT]
[/INDENT]

[INDENT]**Display Settings** tab.[/INDENT]
[INDENT][INDENT]> In the Output box, change the 800x600+0+0 to the display resolution of your monitor. I changed mine to 1280x1024+0+0.

[/INDENT][/INDENT]

**[COLOR="Blue"]CATEGORY: EFFECTS[/COLOR] [COLOR="Red"]PLUGIN: WINDOW DECORATION[/COLOR]**
> Configure the Window Decoration plugin by clicking on it and typing **emerald** into the Command box.

**[COLOR="Blue"]CATEGORY: WINDOW MANAGEMENT[/COLOR] [COLOR="Red"]PLUGIN: PLACE WINDOW[/COLOR]**

**[COLOR="Blue"]CATEGORY: UNCATEGORIZED[/COLOR] [COLOR="Red"]PLUGIN: RESIZE WINDOW[/COLOR]**

**[COLOR="Blue"]CATEGORY: WINDOW MANAGEMENT[/COLOR] [COLOR="Red"]PLUGIN: MOVE WINDOW[/COLOR]**

**[COLOR="Blue"]CATEGORY: WINDOW MANAGEMENT[/COLOR] [COLOR="Red"]PLUGIN: APPLICATION SWITCHER[/COLOR]**

**[COLOR="Blue"]CATEGORY: WINDOW MANAGEMENT[/COLOR] [COLOR="Red"]PLUGIN: RING SWITCHER[/COLOR]**

**[COLOR="Blue"]CATEGORY: WINDOW MANAGEMENT[/COLOR] [COLOR="Red"]PLUGIN: VIEWPORT SWITCHER[/COLOR]**

[SIZE="4"]**Step 4. ACTIVATE VISUAL EFFECTS**[/SIZE]
Click on System --> Preferences --> Appearance --> Visual Effects --> Custom.

**[SIZE="5"][COLOR="Red"]ENJOY!!![/COLOR][/SIZE]**

Hope this helps others....

---

