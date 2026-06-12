---
title: "The state of Compiz Fusion repositories for Feisty"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by sc00ter on 2007-08-21
Hi, is there any chance of consolidating all the various repos for CF to a single and reliable one.

At present I have 3 repos in my sources.list, one of which appears to be stable, but old.

Here's the three I'm aware of:

Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


Vorian: Extras Repository (GPG key: 22130E65)

deb [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras
deb-src [http://debs.vorian.org/](http://debs.vorian.org/) feisty extras

PPA Dogfood (as featured in the community docs)
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse


Each repo has it's own problems, for example:

1. Vorian:  Appears to be quite old and hasn't been updated for a while. But works (the version I've reverted to).

2. PPA Dogfood: This appears in the ubuntu community docs, but again is old plus also has a problem with the update-manager insisting there is a new version, but the same version is installed. This can be annoying after awhile.

3. Trevino: Was the most reliable until about 2 days ago which (during update-manager) introduced errors with the CCSM and wrecked havoc with trying to change settings/options.

Can some effort be made by LoCo Teams/Leaders to sort this mess out?

I appreciate this is still alpha and is all subject to change, but this is causing some headaches for those who just want to install/upgrade it.

---

### Post by anubhavrocks on 2007-08-21
I just use one of the repos

Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
 
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
 deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Their were some issues yesterday but they seem to be sorted out.

---

### Post by sc00ter on 2007-08-21
The issue with CCSM introduced by those using the Trevino repo does not affect everyone. I am one of the unfortunate ones whom are affected.

The problem was introduced by the CF 0.52 build created by Trevino on 18/19 Aug 2007 (checked [http://download.tuxfamily.org/3v1deb/xtra-debs/compiz-fusion/](http://download.tuxfamily.org/3v1deb/xtra-debs/compiz-fusion/) and [http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/](http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/) respectively).

Neither of these builds fix the problem, either re-installing or completely removing and clean install CF (removing all compiz config files, .config/compiz/compizconfig and ~/.compizconfig) from the Trevino repo resolve the issue.

Hence the plea for a unified and reliable source for CF (during it's alpha life atleast) ...

---

### Post by ThrobbingBrain66 on 2007-08-21
sc00ter:  I sincerely hope you don't have all three CF repos enabled at one time.  If you do, you're just asking for version mismatches, broken packages, etc.  Secondly, you must expect breakage when running a GIT repo (like Trevino's).  The trade-off for being on the bleeding edge is decreased stability.

---

### Post by sc00ter on 2007-08-21
Rest assured, I only have one repo active (Vorian's repo).

Fair comment, it is the price to pay for bleeding edge ... :)

---

### Post by hyperair on 2007-08-21
Are you sure the CCSM problem doesn't affect everyone? Last I checked, it affected everyone, and those who say they have no problems don't realize that it is a problem.

Please refer to this: [http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/](http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/)

That's the reason for the breakages. When they finish making their changes to the Compiz Core, it'll be back to normal. Until then, we have to wait patiently, using the old version or by compiling the 0.5.2 tarball ourselves.

---

### Post by sc00ter on 2007-08-21
hyperair: You may well be right, that everyone is not aware that they have the problem (as it is not inherent in all plugins) maybe I was being slightly optimistic that some not all had been affected.

---

### Post by amadeus266 on 2007-08-22
So, is there an easy way to downgrade 1 version of compiz-core?

---

### Post by reacocard on 2007-08-22
the dogfood repo (amaranth's) updated just yesterday. Lost all my settings in the process (though my computer crashed too, that likely didn't help >.<), but it works great.

---

### Post by psyopper on 2007-08-22
Well, with the breakage of Trevino's repos (the CCSM problem) I'm kind of glad there are other repo's out there with more "stable" versions. reacocard reports that the dogfood repo updated yesterday, and today my update manager tells me that Vorian's repos were updated yesterday too.

With the problems in the Trevino repo, I wonder if it is safe for me to update from the Vorian repo? Does anyone know?

In the meantime, I think cosolidation is unnecessary. CF will be released in it's stable version with Gutsy, supposedly as "desktop effects" but with the ability to download the complete system and CCSM through the Ubuntu repo's. I'm sure (I hope) that within a few weeks after the release of Gutsy CF will be backported into the prior versions repos.

---

### Post by hyperair on 2007-08-22
Well I'm using Vorian's repo, for the moment, although I still find Trevino's repo's Compiz Fusion to run the smoothest. Anyway Vorian's repo has tolerable quality so I guess I'll stick with that for the moment.

EDIT: BLARGH NO NO DONT UPDATE! T_T Now Vorian's repo has problems too. Great! Are we running out of repositories to turn to? And Vorian or Trevino, if you're reading this, can you please explain to me why you did that?

Anyway I'm off to GIT compile mine pfft

---

### Post by jimbo99 on 2007-08-22
There appear to be settings that are stored somewhere besides the typical places.  This is a pure NO-NO.  They must not store settings where they are not obviously identified.

I know this because I removed everything that appeared to have been compiz related yet when I reinstalled my settings were back where they were before--cube transparency and size, various effects, etc.

If config files are hidden and I don't  mean the files beginning with the period (.).  I mean files that are not obviously placed for easy deletion.

I deleted a whole slew of files yet when I reinstalled the settings were as they were before I deleted.

Some serious work needs to be done on this to clean it up.

---

### Post by reacocard on 2007-08-22
> **jimbo99 said:**
> There appear to be settings that are stored somewhere besides the typical places.  This is a pure NO-NO.  They must not store settings where they are not obviously identified.

I know this because I removed everything that appeared to have been compiz related yet when I reinstalled my settings were back where they were before--cube transparency and size, various effects, etc.

If config files are hidden and I don't  mean the files beginning with the period (.).  I mean files that are not obviously placed for easy deletion.

I deleted a whole slew of files yet when I reinstalled the settings were as they were before I deleted.

Some serious work needs to be done on this to clean it up.

settings are either in ~/.compizconfig or in gconf.

---

### Post by ThrobbingBrain66 on 2007-08-22
there are more compiz-related files in ~/.config

---

### Post by jimbo99 on 2007-08-22
In the first release of  compiz-fusion there was a folder with a name something like

.compizfusion

and I believe a file but I can't remember the name.

I did find the .config folder and delete the folder in it related to compiz.

I guess with most recent release they modified the location of some of the files.

I'll  look into that folder (.gconf/apps/compiz) to see what it contains.

---

### Post by psyopper on 2007-08-22
I'll second the not updating Vorian's repo's. Everything works fine but it reset all of my settings. Of particual annoyance is my key bindings, and the new CCSM, while seemingly complete, is missing the "Actions" tab for General settings and EVERY plugin!

Does compiling from git (versus using precompiled .deb's) resolve this ongoing CCSM issue?

---

### Post by bruckwine on 2007-08-22
Just great..just got updated by synaptic and now all I have is wobbly windows and transparent bars..period. No other effect will work despite CCSM looking fine... guess I got screwed by trevino's updates too....

---

### Post by psyopper on 2007-08-23
To be fair, this isn't the fault of Trevino, Amaranth or Vorian. The issue is with Compiz. They have apparently decided to change the method by which CCSM configs and stores configs which is messing with CCSM.

Ahhh... the bleeding edge...

---

### Post by Jeff_From_VA on 2007-08-23
Well I just learned a lesson, I "upgraded" to this crap a few minutes ago against better judgement.   I am now stuck sorting out a half installed, half broken compiz fusion.  

I consider this a very positive experience, because it taught me the hard way what I knew before but ignored.  


[SIZE="7"]
**DONT EVER FOR ANY REASON INSTALL SOMETHING UNSUPPORTED AND NOT STABLE IF YOU HAVE ANY VALUE OF YOUR SYSTEM!!!!!!**[/SIZE]

Seriously, unless you just want to play and could care less how you break your stuff, this is not worth it. Just wait a couple months until it is stable and usable.

---

### Post by GFree678 on 2007-08-23
Trevino's repos have been upgraded; the CCSM now has workable keybindings. Yay!

---

### Post by dannyboy79 on 2007-08-23
can some1 please tell me how to clean out ALL compiz crap so I can start over??? I tried using this stupid bash script to install the latest compiz from git and it doesn't work. I was using Trevino's repo's before but wanted to try this other method because of an issue the cube I was having. ANyway, now that I used the script (also despite trying the scripts uninstall feature) I can' even get compiz working anymore. 

So if anyone can please tell me what ALL files to remove I would appreciate it. 

These are the files I have already removed.
the entire ~/.compizconfig folder
I looked in ~/.config/ BUT there isn't anything related to compiz
I looked in ~/.gconf and there's so much stuff in there I don't know what I can or can not remove. Can I just remove the entire folder named ~/.gconf/apps/compiz/?

Thank you for any help anyone can provide.

These is the result of 
locate compiz*

/etc/X11/xorg.conf_compiz
/var/lib/dpkg/info/compiz-gnome.postinst
/var/lib/dpkg/info/compiz-gtk.list
/var/lib/dpkg/info/compiz-gtk.postrm
/var/lib/dpkg/info/compiz-gnome.md5sums
/var/lib/dpkg/info/compiz-gnome.postrm
/var/lib/dpkg/info/compiz-gnome.prerm
/var/lib/dpkg/info/gnome-compiz-manager.list
/var/lib/dpkg/info/compiz-gnome.list
/var/lib/dpkg/info/gnome-compiz-manager.postrm
/usr/lib/compiz
/usr/lib/compiz/libgconf.so
/usr/lib/libgnome-window-settings1/libcompiz.so
/usr/share/locale-langpack/en_GB/LC_MESSAGES/compiz.mo
/usr/share/compiz
/usr/share/compiz/gconf.xml
/usr/share/gconf/schemas/compiz-video.schemas
/usr/share/gconf/schemas/compiz-water.schemas
/usr/share/gconf/schemas/compiz-blur.schemas
/usr/share/gconf/schemas/compiz-rotate.schemas
/usr/share/gconf/schemas/compiz-cube.schemas
/usr/share/gconf/schemas/compiz-annotate.schemas
/usr/share/gconf/schemas/compiz-fade.schemas
/usr/share/gconf/schemas/compiz-ini.schemas
/usr/share/gconf/schemas/compiz-plane.schemas
/usr/share/gconf/schemas/compiz-dbus.schemas
/usr/share/gconf/schemas/compiz-zoom.schemas
/usr/share/gconf/schemas/compiz-decoration.schemas
/usr/share/gconf/schemas/compiz-minimize.schemas
/usr/share/gconf/schemas/compiz-svg.schemas
/usr/share/gconf/schemas/compiz-switcher.schemas
/usr/share/gconf/schemas/compiz-inotify.schemas
/usr/share/gconf/schemas/compiz-screenshot.schemas
/usr/share/gconf/schemas/compiz-place.schemas
/usr/share/gconf/schemas/compiz-regex.schemas
/usr/share/gconf/schemas/compiz-wobbly.schemas
/usr/share/gconf/schemas/compiz-fs.schemas
/usr/share/gconf/schemas/compiz-resize.schemas
/usr/share/gconf/schemas/compiz-scale.schemas
/usr/share/gconf/schemas/compiz-core.schemas
/usr/share/gconf/schemas/compiz-gconf.schemas
/usr/share/gconf/schemas/compiz-move.schemas
/usr/share/gconf/schemas/compiz-clone.schemas
/usr/share/gconf/schemas/compiz-glib.schemas
/usr/share/gconf/schemas/compiz-png.schemas
/usr/share/gconf/defaults/10_compiz-gnome
/usr/share/gnome/wm-properties/compiz.desktop
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/share/doc/compiz-gnome
/usr/share/doc/compiz-gnome/copyright
/usr/share/doc/compiz-gnome/NEWS.gz
/usr/share/doc/compiz-gnome/changelog.gz
/usr/share/doc/compiz-gnome/AUTHORS
/usr/share/doc/compiz-gnome/README
/usr/share/doc/compiz-gnome/changelog.Debian.gz
/usr/share/doc/compiz-gnome/TODO
/home/daniel/.gconf/apps/compiz
/home/daniel/.gconf/apps/compiz/%gconf.xml
/home/daniel/.gconf/apps/compiz/general
/home/daniel/.gconf/apps/compiz/general/%gconf.xml
/home/daniel/.gconf/apps/compiz/general/allscreens
/home/daniel/.gconf/apps/compiz/general/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/general/allscreens/options
/home/daniel/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/general/screen0
/home/daniel/.gconf/apps/compiz/general/screen0/%gconf.xml
/home/daniel/.gconf/apps/compiz/general/screen0/options
/home/daniel/.gconf/apps/compiz/general/screen0/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins
/home/daniel/.gconf/apps/compiz/plugins/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/decoration
/home/daniel/.gconf/apps/compiz/plugins/decoration/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/decoration/allscreens
/home/daniel/.gconf/apps/compiz/plugins/decoration/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/decoration/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/decoration/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/annotate
/home/daniel/.gconf/apps/compiz/plugins/annotate/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/annotate/allscreens
/home/daniel/.gconf/apps/compiz/plugins/annotate/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/annotate/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/annotate/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/move
/home/daniel/.gconf/apps/compiz/plugins/move/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/move/allscreens
/home/daniel/.gconf/apps/compiz/plugins/move/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/move/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/move/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/scale
/home/daniel/.gconf/apps/compiz/plugins/scale/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/scale/allscreens
/home/daniel/.gconf/apps/compiz/plugins/scale/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/scale/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/scale/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/rotate
/home/daniel/.gconf/apps/compiz/plugins/rotate/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/rotate/allscreens
/home/daniel/.gconf/apps/compiz/plugins/rotate/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/rotate/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/rotate/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/rotate/screen0
/home/daniel/.gconf/apps/compiz/plugins/rotate/screen0/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/rotate/screen0/options
/home/daniel/.gconf/apps/compiz/plugins/rotate/screen0/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/fade
/home/daniel/.gconf/apps/compiz/plugins/fade/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/fade/screen0
/home/daniel/.gconf/apps/compiz/plugins/fade/screen0/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/fade/screen0/options
/home/daniel/.gconf/apps/compiz/plugins/fade/screen0/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/cube
/home/daniel/.gconf/apps/compiz/plugins/cube/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/cube/allscreens
/home/daniel/.gconf/apps/compiz/plugins/cube/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/cube/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/cube/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/cube/screen0
/home/daniel/.gconf/apps/compiz/plugins/cube/screen0/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/cube/screen0/options
/home/daniel/.gconf/apps/compiz/plugins/cube/screen0/options/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/water
/home/daniel/.gconf/apps/compiz/plugins/water/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/water/allscreens
/home/daniel/.gconf/apps/compiz/plugins/water/allscreens/%gconf.xml
/home/daniel/.gconf/apps/compiz/plugins/water/allscreens/options
/home/daniel/.gconf/apps/compiz/plugins/water/allscreens/options/%gconf.xml
/home/daniel/.gconf/apps/gnome-compiz-preferences
/home/daniel/.gconf/apps/gnome-compiz-preferences/%gconf.xml

---

### Post by hyperair on 2007-08-23
Excellent! I've reverted back to Trevino's repositories already. One thing that bugs me is that some of the keybindings are buggy, like the application switcher.

---

### Post by sc00ter on 2007-08-23
Heads up: Some odd plug-in behaviors:

1. Shift Switcher: Shift Switcher no longer functions correctly, opening multiple windows on multiple desktops and use shift switcher to flip between windows (across desktops) will give a nasty re-focus action (seems to get the wrong desktop on re-focus).

2. 3D Cube: Clicking both mouse-buttons no longer initiates the 3D cube. Ctrl+Alt+left-button still works though.

3. Enhanced Zoom Desktop: Cannot invoke.

4. Screen Saver: Cannot manually invoke (I think it used to be Shift+Ctrl+S), but still functions if you let the timer expires to invoke, then it works.

NOTE: This is the same for both Trevino and Vorian GIT builds (as of today).

Closing comment: Great big thanks to Trevino et al for pushing the bleeding edge stuff out for us all to try.

---

### Post by clevin on 2007-08-23
> **bruckwine said:**
> Just great..just got updated by synaptic and now all I have is wobbly windows and transparent bars..period. No other effect will work despite CCSM looking fine... guess I got screwed by trevino's updates too....

is this the update from 0.53 to 0.54? Im holding back fro now.. I noticed update info this morning, but didn't get time to do it.

---

### Post by Inxsible on 2007-08-23
Trevino's repos seem to work now. Re-installed it last night. Like Sc00ter mentioned, the shift plugin and the Enhanced Zoom plugins have issues. Didn't check all the plugins :(

Ctrl + Alt + Left Mouse Button (Dragging) doesn't initiate the cube rotation :(

But its better than what it was  !!

I tried to compile it from source, but on doing a ```
sudo apt-get build-dep compiz
``` it tried to install a bunch of KDE crap like kate and kconfig etc. So I aborted. They say, that compiling CF from source, gives a better performance than a "one size fits all" deb installation. Has this been quantified?

---

### Post by dannyboy79 on 2007-08-23
can anyone tell me how to get back to a smooth start so I can redo the trevino's compiz method. how do I ensure that all remaining compiz stuff is gone so that if I enable trevino's repo it'll work??? refer to post #21 for qustionable things to delete.

---

### Post by Inxsible on 2007-08-23
I uninstalled a bunch of packages. Few I rbr are compiz compiz-core compizconfig-settings-manager libcompizconfig0 compiz-gnome compiz-fusion-backend-gconf and a lot more.

All these should be removed if you do a 

```
sudo apt-get remove --purge compiz* libcompizconfig*
```When you do this, it gives you a list of packages that it selects. Something like,
```
Note, selecting "blah" for regex "compiz*"
```I aborted that uninstall and manually listed all the package names that contained "compiz" in them. I did NOT delete the packages that didnt have compiz in them. I dont know why, I just thought it'd be better not to. Like so
```
 sudo aptitude remove compiz compiz-gnome libcompizconfig0 ......
```After that I removed /home/.compizconfig and /home/.config/compiz folders. I put them on my desktop just in case.

Then i enabled Trevino's repos and re-installed. I was hoping against hope that his repos were rectified. Thankfully they were and everything worked.

I also notice that you have already tried deleting those config folders(post #21). I thought I might just tell you what I did ....and that could help you.

---

### Post by dannyboy79 on 2007-08-23
what about the .gconf/compiz folders?

---

### Post by clevin on 2007-08-23
I just update from trevinos, as of now, it works fine except some switcher problems (alt tab is broken, can't switch to next window, shift switch behaves a little bit chaotic, but still works), I don't have any problems, I still think its slow compare to beryl I have, but its not slower than previous version of compiz-fusion.

---

### Post by Innova on 2007-08-23
I was having the error with ccp and ABI versions (whatever it was).

I just changed to trevino's repository and am getting these errors:

/usr/bin/compiz.real: Couldn't load plugin 'glib'
/usr/bin/compiz.real: Couldn't load plugin 'animation'
/usr/bin/compiz.real: Couldn't load plugin 'imgjpeg'
/usr/bin/compiz.real: Couldn't load plugin 'ring'
/usr/bin/compiz.real: Couldn't load plugin 'text'
/usr/bin/compiz.real: Couldn't load plugin 'blur'
/usr/bin/compiz.real: Couldn't load plugin 'trailfocus'


Also, the configurator doesn't show up in the system->preferences menu.

Any ideas?

---

### Post by Innova on 2007-08-23
Not sure what the difference was, but I just followed these steps and got it working:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by andrewsomething on 2007-08-23
If you want stability you should use amaranth's repo. It's essentially a backport of the stable version shipping with Gutsy, if I recall correctly.  It's not old or out of date, as the original poster says, it is simply the stable version which will update less and doesn't include unsupported developmental plugin-ins.

Trevino's repo is built from the developmental GIT source repository. GIT is the version control system that the compiz-fusion devs use. So when ever there is a big change to the code (in this case CCSM) it will show up in Trevino's debs. It will be bumpy.

---

### Post by isaacj87 on 2007-08-23
I have a question....Whenever I used that CF script, which supposedly installed from GIT, to install compiz some of the animations were different. Such as Magic Lamp. and Trevino's Repo (yes, the newest version 0.5.5) has a different animating magic lamp effect...why is that?

---

### Post by Inxsible on 2007-08-24
> **dannyboy79 said:**
> what about the .gconf/compiz folders?

Check this thread out. I put in a small "howto" (if you can call it that ;) )

[http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---

### Post by Leed on 2007-08-24
I was quite pleased to see a new update on compiz fusion this morning, even more when I saw that the issue with the Command has been fixed. Also the shift-switcher plugin has been improved.

But now I have the problem, that CCSM doesn't save it's settings any more, it's become totally useless. I also tried editing the config files under /home/user/.config/compiz/compizconfig but didn't get anywhere with it. 

I tried uninstalling with purging and then reinstalling, but there seems to be no difference. Anyone else have this Problem?

---

### Post by Shne on 2007-08-24
> **sc00ter said:**
> 2. 3D Cube: Clicking both mouse-buttons no longer initiates the 3D cube. Ctrl+Alt+left-button still works though.

Even though it's unavailable in CCSM you can still edit this binding:

use the Configuration Editor from Applications -> System Tools (right click and edit menus to add it if it's not there already).
in the configuration editor, go to /apps/compiz/plugins/rotate/allscreens/options and you can access and edit the key initiate_button to whatever mouse button you want, with any keyboard modifiers added, like <Ctrl><Alt>Button1 (which is default).

there are probably more CCSM-inaccessable bindings for more plugins you can edit this way.

---

### Post by Zero Prime on 2007-08-24
> **Leed said:**
> I was quite pleased to see a new update on compiz fusion this morning, even more when I saw that the issue with the Command has been fixed. Also the shift-switcher plugin has been improved.

But now I have the problem, that CCSM doesn't save it's settings any more, it's become totally useless. I also tried editing the config files under /home/user/.config/compiz/compizconfig but didn't get anywhere with it. 

I tried uninstalling with purging and then reinstalling, but there seems to be no difference. Anyone else have this Problem?

Same prob here.  I'm hoping this will be something fixed in the updates.  Right now I'm happy that I was able to get Compiz installed and working again.

---

### Post by jcostom on 2007-08-24
For me, Trevino's repository seems to be the best working.  Only one question I've got..

Trevino's debs seem to produce a more responsive system than Amaranth's.  Just my perception there.  However, when I invoked the Benchmark plugin under Amaranth's builds, I get something in the neighborhood of ~ 700 fps, whereas under Trevino's builds, I get ~ 60 fps.

Hardware is good, though I wouldn't call it high-end - C2D 6750, 2GB PC2-8500, Nvidia 8800 GTS 320MB.  Using Nvidia 100.14.11 drivers, which do NOT produce a lockup upon logout with Trevino, unlike Amaranth.

It's really more of a curiosity thing than anything...

Anyone have thoughts on that one?

---

### Post by reacocard on 2007-08-24
> **jcostom said:**
> For me, Trevino's repository seems to be the best working.  Only one question I've got..

Trevino's debs seem to produce a more responsive system than Amaranth's.  Just my perception there.  However, when I invoked the Benchmark plugin under Amaranth's builds, I get something in the neighborhood of ~ 700 fps, whereas under Trevino's builds, I get ~ 60 fps.

Sounds like trev's enable the limiter on benchmark by default, while amaranth's disable it. Just turn off the limiter in CCSM and trev's should show similar numbers.

---

### Post by hyperair on 2007-08-24
Don't forget to turn of Sync to VBlank, otherwise your animations will be choppy.

---

### Post by jigarzon on 2007-08-24
> **Leed said:**
> I was quite pleased to see a new update on compiz fusion this morning, even more when I saw that the issue with the Command has been fixed. Also the shift-switcher plugin has been improved.

But now I have the problem, that CCSM doesn't save it's settings any more, it's become totally useless. I also tried editing the config files under /home/user/.config/compiz/compizconfig but didn't get anywhere with it. 

I tried uninstalling with purging and then reinstalling, but there seems to be no difference. Anyone else have this Problem?

I have the same problem here... is there any fix?

---

### Post by hyperair on 2007-08-25
Yeah. For some reason, the flat-file backend isn't working for CompizConfig Settings Manager. So what you need to do... is remove these folders:
```

rm -r ~/.config/compiz
rm -r ~/.gconf/apps/compiz

```

Then, fully uninstall Compiz Fusion:
```

sudo apt-get autoremove compiz* --purge

```

Then, start up, log into a terminal (Ctrl+Alt+F1), reinstall Compiz Fusion, including the gconf backend:
```

sudo apt-get install compiz compizconfig-settings-manager libcompizconfig-backend-gconf compiz-fusion*

```

Then log in, and you should be good to go =D

When you configure CCSM, make sure you select the Gconf backend.

---

### Post by dannyboy79 on 2007-08-25
> **hyperair said:**
> Yeah. For some reason, the flat-file backend isn't working for CompizConfig Settings Manager. So what you need to do... is remove these folders:
```

rm -r ~/.config/compiz
rm -r ~/.gconf/apps/compiz

```

Then, fully uninstall Compiz Fusion:
```

sudo apt-get autoremove compiz* --purge

```

Then, start up, log into a terminal (Ctrl+Alt+F1), reinstall Compiz Fusion, including the gconf backend:
```

sudo apt-get install compiz compizconfig-settings-manager libcompizconfig-backend-gconf compiz-fusion*

```

Then log in, and you should be good to go =D

When you configure CCSM, make sure you select the Gconf backend.
well the above is ok IF you like using gconf to configure compiz. HOw do I get back my compiz settings manager so it works with flat file?

---

### Post by hyperair on 2007-08-25
"HOw do I get back my compiz settings manager so it works with flat file?" - dannyboy79

Excellent question! As I have said before, the flat file backend is having problem. Hence, you have a few choices here:
1. You wait patiently
2. You join the Compiz Fusion team and fix the flat file backend for them.

Personally, I am doing 1 due to lack of time, but I highly recommend that you do no.2 so that the rest of us will be able to have the flat file backend back =P

---

### Post by Zero Prime on 2007-08-25
Hoora for updates!!!  Compiz is now working perfectly with CCSM working as well!!

---

### Post by vortex_noob on 2007-08-25
I tried trevino's repo on CF 0.5.1 and every option works correctly until the update that mess it all up. Then I tried compiling using ElemonGW's CF_Installer_Updater. Works a bit but can't seem to get scale, switcher and a few other plugin to work correctly. Today after i see trevino's new updates, decide to try it after uninstalling everything related to compiz, including deleting compiz configuration files.

i got this when starting compiz-fusion (newest update from trevino).

No windows decorator, no cube, nothing....

run compiz --replace from the terminal, didn't find any error. Using gconf and flat-file doesn't make any difference

when i run emerald --replace, i got this error:

ferry@ferry-6400via880:~$ emerald --replace

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

Can anyone help me?

---

### Post by Leed on 2007-08-26
Yeah luv it, not only does everything work again, they also made it better...

The World needs more people like the ones involved in this.

---

### Post by hyperair on 2007-08-26
I couldn't agree more.

---

### Post by dannyboy79 on 2007-08-28
> **vortex_noob said:**
> I tried trevino's repo on CF 0.5.1 and every option works correctly until the update that mess it all up. Then I tried compiling using ElemonGW's CF_Installer_Updater. Works a bit but can't seem to get scale, switcher and a few other plugin to work correctly. Today after i see trevino's new updates, decide to try it after uninstalling everything related to compiz, including deleting compiz configuration files.

i got this when starting compiz-fusion (newest update from trevino).

No windows decorator, no cube, nothing....

run compiz --replace from the terminal, didn't find any error. Using gconf and flat-file doesn't make any difference

when i run emerald --replace, i got this error:

ferry@ferry-6400via880:~$ emerald --replace

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

(emerald:20505): Wnck-WARNING **: Unhandled action type (nil)

Can anyone help me?
nevermind

---

### Post by am_pcguy on 2007-08-29
I have one remaining problem.

I had compiz set up so I could initiate the cube, and rotate it by holding my left and right mouse buttons.  I can not seem to get this to work.

When I try to map those buttons they are not accepted, and when I try to type them in manually Button1 Button2, it says those are invalid choices.

Anybody have a solution for this?

Thanks

---

### Post by isaacj87 on 2007-09-04
It got broken...as of today 9/4/07 it works now.

---

### Post by Inxsible on 2007-09-04
> **am_pcguy said:**
> I have one remaining problem.

I had compiz set up so I could initiate the cube, and rotate it by holding my left and right mouse buttons.  I can not seem to get this to work.

When I try to map those buttons they are not accepted, and when I try to type them in manually Button1 Button2, it says those are invalid choices.

Anybody have a solution for this?

Thanks
What plugins do I have to set to get the same effect of initiating my cube with my mouse ?

---

### Post by isaacj87 on 2007-09-05
> **Inxsible said:**
> What plugins do I have to set to get the same effect of initiating my cube with my mouse ?

the plugin is called viewport switcher. It works a little bit differently now. When you press the left and right mouse buttons (or middle click) you have to click to let go.

---

### Post by Inxsible on 2007-09-05
> **isaacj87 said:**
> the plugin is called viewport switcher. It works a little bit differently now. When you press the left and right mouse buttons (or middle click) you have to click to let go.

I got that functionality after the most recent update...the middle click initiation doesn't work but clicking on the left and right buttons at the same time works -- only on the desktop however.

In Beryl, the middle click used to do it even if you were in some app window. Maybe I am just missing something.

---

### Post by isaacj87 on 2007-09-05
Seems to be working for me...but I think a lot of people are having troubles with the latest update...I can't wait for the next one...:)

---

### Post by Inxsible on 2007-09-05
> **isaacj87 said:**
> Seems to be working for me...but I think a lot of people are having troubles with the latest update...I can't wait for the next one...:)
Do you mean the middle click initiation works or the part where you can initiate even if you are in some app window?

---

### Post by isaacj87 on 2007-09-05
> **Inxsible said:**
> Do you mean the middle click initiation works or the part where you can initiate even if you are in some app window?

It doesn't work the same way beryl used to work. You have to middle click on empty space (i.e. desktop), you can't do a middle click in an app window to initiate. :(

---

### Post by Inxsible on 2007-09-05
> **isaacj87 said:**
> It doesn't work the same way beryl used to work. You have to middle click on empty space (i.e. desktop), you can't do a middle click in an app window to initiate. :(
aah !! Ok.

Well, I am glad they at least got the mouse initiation back... I used to miss it sorely ;)

---

### Post by hyperair on 2007-09-06
IF you want you can set a keybinding in the Rotate Cube plugin. I think there's a Initiate for mouse. Just set Button2 and don't add any modifiers. =D

---

### Post by Inxsible on 2007-09-06
> **hyperair said:**
> IF you want you can set a keybinding in the Rotate Cube plugin. I think there's a Initiate for mouse. Just set Button2 and don't add any modifiers. =D

I will try that later today. Thanks :)

---

