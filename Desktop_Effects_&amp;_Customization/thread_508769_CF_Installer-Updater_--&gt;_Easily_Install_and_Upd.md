---
title: "CF Installer-Updater --&gt; Easily Install and Update Compiz Fusion"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by ElemonGW on 2007-07-24
[B]DO NOT USE IT! The current version is not really good. Use [Git4CF Automator]("http://elemongw.exofire.net/projects/linux/git4cf_auto") instead. Git4CF Automator (also created by me) is the result of CF Installer-Updater 's rewrite and it is by far better from it. Here is the download link for [Git4CF Automator version 0.1.5]("http://elemongw.exofire.net/download/git4cf_auto") (current version) .

Now, here is the original post fro CF Installer-Updater.
```
***Targeted to Ubuntu, may also work in other Debian-based distros.***

**About**

CF Installer-Updater will automatically install and update Compiz Fusion to its very latest version (from its git). I created this because I couldn't find a fast (and good) way of doing this. Compiz Fusion 's files are sometimes changed even every hour so there is not possible to have the latest available files without compiling by yourself (.deb packages and repositories are always not up-to-date with the latest Compiz Fusion version (which between always fixes some problems and adds functionalities, so it is good to have the latest one) and this is normal because creating a new package every few hours that a new Compiz Fusion revision comes out would not be possible). With this tool you will have the freedom to choose when to update Compiz Fusion (the more frequently the better).
***Note: It has been reported (and from personal experience too) that by following this way (either using my script or compiling by yourself) Compiz Fusion responses much better and it is way faster, comparing with installing it through repositories/.deb packages.***

[Download CF Installer-Updater Version 3]("http://elemongw.exofire.net/down_cf_i-u")

**Downloads Archive** (old versions and other versions that they no longer exist, as they have been merged), (between, only their latest revisions of old releases are available)

[Download CF Installer-Updater Version 2 rev.1]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2_rev.1.sh")
[Download CF Installer-Updater Version 2 Final]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2.sh")
[Download CF Installer-Updater Version 2 Beta]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2_beta.sh")
[Download CF Installer-Updater for Gnome Version 1 rev.6]("http://elemongw.googlepages.com/CFInstaller-Updater.sh")
[Download CF Installer-Updater for KDE Version 1 rev.4]("http://elemongw.googlepages.com/CFInstaller-Updater_kde_.sh")
[Download Installation Script Version 0.1]("http://elemongw.googlepages.com/fusion-install.sh")
[Download Installation Script (Alternative) Version 0.1]("http://elemongw.googlepages.com/fusion-installalt.sh")
[Download Update script Version 0.1]("http://elemongw.googlepages.com/fusion-update.sh")

**Running CF Installer-Updater**

Just run

[code]bash CF_Installer-Updater_v.X.sh
```
in terminal or
```
chmod +x CF_Installer-Updater_v.X.sh
```

to make it executable and then run it. After that, everything is explained and easily understood within the script so you should not have any problems using it. If you however do have, feel free to post.

**Credits**
# Fyda for creating [this]("http://forum.compiz-fusion.org/showthread.php?t=1985") guide.
# glezos for the help he provided me.

**Changelog**

**23-8-2007** Version 3
# You can now choose the download directory.
# Script dialogs are now in bold to avoid confusion ( & for eye candy purposes ;) )
# If you enter an invalid answer in one of the questions that the script makes, it will exit instead of skipping that step.
# Uninstalling ccsm now works.
# Fixed permission denied errors when trying to remove some files.
# Download Urls Changed
# Option to compile CF from source instead of git.
# Availability of all the currently existing plugins.
# Code Cleanup.

**8-8-2007** Version 2 rev.1
# Tags removed.
# An xcb-enabled version of libX11 will be compiled as the latest Compiz Fusion revisions need it.

**2-8-2007** Version 2 Final
# Added KDE support (probably will work now).
# Added Uninstallation ability.
# Syntax completely changed.
# Lots of minor changes (many changed and added dialogs, added tips etc.).
# And probably many more that I can't remember right now...

**29-7-2007** Version 2 Beta
# You can now choose which components to install.
# Changes on how the program installs Compiz Fusion and its components.
# Probably more, but I can't remember them right now ;) .

**26-7-2007** Version 1 rev.6
# Fixed a problem at ccms 's installation (it would probably be installed multiple times :) )

**26-7-2007** Version 1 rev.5
# Changed how ccsm is installed because of some changes at the latest version.
# Minor changes

**26-7-2007** Version 1 rev.4
# Some things tuned to be more clear

**25-7-2007** Version 1 rev.3
# Fixed a syntax error that I accidentally did after the last changes (Sorry!)

**25-7-2007** Version 1 rev.2
# Some things tuned

**25-7-2007** Version 1 rev.1
# Some things tuned

**25-7-2007** Version 1
# Installation Script, Installation Script Alternative & Update script merged under the name CF Installer-Updater

**25-7-2007** Version 0.1
# Alternative script added to face some problems in certain cases

**24-7-2007** Version 0.1
# First Public Release of Installation Script & Update script

[***Homepage***]("http://elemongw.exofire.net/projects/linux/cf_i-u")[/code]

---

### Post by benx009 on 2007-07-24
i hope these scripts work well because i am getting a new video card soon (my current one cannot support compiz) and i can't wait to try out compiz fusion!  thanks for taking the time to make the scripts though.  i have saved both of them to my drive for future use.

---

### Post by ElemonGW on 2007-07-25
EDIT: Post deleted, as I updated the first post. View that instead.

---

### Post by doomster on 2007-07-25
very good work. thanx Elemon  for these scripts :)

---

### Post by ElemonGW on 2007-07-25
Thnx doomster ;-) . Oh, and a request. If a mod could change the thread's title with the one that the first post now has I would be really greatfull.

---

### Post by ElemonGW on 2007-07-25
I just uploaded a version with a few changes, you are recommended to re-download the script.
**EDIT: Just updated the files one more time, you may re-download them.**

---

### Post by treadwayms on 2007-07-25
I keep getting this error 
Do you want to install Compiz Fusion or update it?(i/u)i
CFInstaller-Updater.sh: 150: Syntax error: "(" unexpected (expecting "}")

What am I doing wrong ?

---

### Post by ElemonGW on 2007-07-25
No you are not doing sth wrong. After the latest changes it seems that I messed up the code a bit. I will upload the correct one very soon. Sorry!
**EDIT: OK, I found what was wrong, it is supposed to be fixed now. Re-download it and try again. Thank you for reporting it!**

---

### Post by Frak on 2007-07-25
Is there a reason why it installs KDE crap?

---

### Post by ElemonGW on 2007-07-25
When it asks you if you have any KDE modules you should have answered yes. I assume that you have some KDE modules installed and so it tries to install all the KDE modules,

---

### Post by llln30lll on 2007-07-25
this is my first post on the forum :D

testing the script now

---

### Post by Frak on 2007-07-25
> **ElemonGW said:**
> When it asks you if you have any KDE modules you should have answered yes. I assume that you have some KDE modules installed and so it tries to install all the KDE modules,
Are they a dependency of Compiz Fusion?

---

### Post by Traldan on 2007-07-25
Will this work with 64-bit feisty too?

---

### Post by ElemonGW on 2007-07-25
> **Frak said:**
> Are they a dependency of Compiz Fusion?

No, but if you have some KDE modules it will try to install many more. This is a problem of build-dep. I don't know why this happens. I might release a new version which will not use build-dep command and only install the known dependencies. Knowing that problem, I had decided to leave it for those who do not have any kde modules installed, so that they will be completely safe that everything required will be installed. When the script asks you if you have any kde modules installed, if you press yes it will install all the known dependencies and if you press no it will use build-dep to install the dependencies. As I said before I might change that and install the known dependencies and not use build-dep at all.

> **Traldan said:**
> Will this work with 64-bit feisty too?

I am not sure if it will. Just try it and tell us. I don't think that if it doesn't work it will harm your computer...

---

### Post by Frak on 2007-07-25
From what I've seen, I like it alot :)

---

### Post by X3n0n on 2007-07-25
Well, it seems that ccsm is not working and I get the "Not using Gettext" warning during compilation.
That's what it says when I run ccsm:

```
ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 29, in <module>
    gettext.bindtextdomain("ccsm", DataDir + "/locale")
NameError: name 'DataDir' is not defined
```

---

### Post by ElemonGW on 2007-07-25
ccsm is compiz config settings manager. Have you tried launching it from system-->preferences? I don't think that this will fix anything but ok :) just try it :)
EDIT: You might also try removing DataDir at the line where it is referred (although this can be risky). Finally, I don't think that this is a problem of the script but it is a problem of ccsm

---

### Post by Traldan on 2007-07-25
Seems to have worked for me, thank you!

---

### Post by Tokhra on 2007-07-25
I'm getting the following error for a clean install of Feisty.

Installing ccsm...
./CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory

Any ideas what I'm missing?

---

### Post by tagrace on 2007-07-25
Trying your script and it gets all the way through but no joy when it comes to starting the Icon.

I get the following message on the terminal:

checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I get a number of similar messages with different file names such as "libxslt"

What am I doing wrong?

Thanks
Ted

---

### Post by Frak on 2007-07-25
When it says "Do you have KDE modules" or whatever installed, hit **n**.
Those, as I found out, are KDE packages.

---

### Post by ElemonGW on 2007-07-25
> **Tokhra said:**
> I'm getting the following error for a clean install of Feisty.

Installing ccsm...
./CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory

Any ideas what I'm missing?

I assume you have cd to the directory you have CFInstaller-Updater.sh. You shouldn't have done that as it may mess up the things a bit. try just running
```
sh /path/to/file/CFInstaller-Updater.sh
```
and tell me what happens (btw. from the error you get it seems that for some reason it didn't downloaded ccsm, well try what I told you and we will see...)

> **tagrace said:**
> Trying your script and it gets all the way through but no joy when it comes to starting the Icon.

I get the following message on the terminal:

checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I get a number of similar messages with different file names such as "libxslt"

What am I doing wrong?

Thanks
Ted

Try running
```
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
```
in terminal. This should have run by the script but I can't think of anything else. In order to help you more, please tell me which OS you use.

---

### Post by ElemonGW on 2007-07-25
> **Frak said:**
> When it says "Do you have KDE modules" or whatever installed, hit **n**.
Those, as I found out, are KDE packages.

Well, OK :) , English are not my native language so some things wrongly referred should be expected.

---

### Post by ElemonGW on 2007-07-25
Just tuned some things to be more clear, I uploaded an updated version.

---

### Post by Tokhra on 2007-07-25
That fixed it, it now installs thanks.

But im getting an issue with window borders not showing. I've selected the Emerald Window Decorator and tried restarting but it doesnt fix it.

---

### Post by Frak on 2007-07-25
How about pressing Alt+F2 and entering
```
compiz --replace -c emerald &
```

And an easier way to start the script is to right click on the script, click properties, go to permissions, check "Allow executing file as program", double click on the script, then click "Run in Terminal".

---

### Post by simosx on 2007-07-25
You get the error "No package 'compiz' found" when the compiz compilation has failed.

Check the error message when compiling compiz itself. I had an issue with the FUSE development library, so I uninstalled the system package "libfuse-dev" and installed the one from upstream.

I got a problem with running "ccsm", though it appears that it is being worked on right now,
[http://gitweb.opencompositing.org/?p=fusion/compizconfig/ccsm;a=summary](http://gitweb.opencompositing.org/?p=fusion/compizconfig/ccsm;a=summary)
I think it has a serious issue with installation.

Apart from that, compiz fusion is working, though I cannot configure the details.. ;-)

---

### Post by simosx on 2007-07-25
I managed to find why ccsm failed to run on my system. Apparently, it is required to have python 2.5. Now it works for me, Ubuntu 6.10 ;-)

---

### Post by ElemonGW on 2007-07-25
> **simosx said:**
> You get the error "No package 'compiz' found" when the compiz compilation has failed.

Yes, I suppose that this is what matters.

> **simosx said:**
> Check the error message when compiling compiz itself.

Btw., that is the reason why I have added so many times the message "Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).", in order people to be able to examine the terminal's messages and look for errors.

> **Frak said:**
> And an easier way to start the script is to right click on the script, click properties, go to permissions, check "Allow executing file as program", double click on the script, then click "Run in Terminal".

I wouldn't recommend that as in case of errors the terminal would close and the user wouldn't be able to examine them.

> **Frak said:**
> How about pressing Alt+F2 and entering
```
compiz --replace -c emerald &
```

And an easier way to start the script is to right click on the script, click properties, go to permissions, check "Allow executing file as program", double click on the script, then click "Run in Terminal".

I don't think that this could really help, as this is probably what Compiz Fusion Icon runs. Anyway, you might want to try it (you don't have anything to lose, right?).

> **Tokhra said:**
> But im getting an issue with window borders not showing. I've selected the Emerald Window Decorator and tried restarting but it doesnt fix it.

This is certainly not a problem of the script :) . That saying, you might want to try doing that:

enter
```
sudo nano /etc/X11/xorg.conf
```
in terminal, scroll down until you see the section labeled 'Section "Device"' and there add this line:
```
Option "AddARGBGLXVisuals" "True"
```
Restart Compiz Fusion and Emerald and see what happens. Btw., do you have a nvidia graphics card? If yes, I suppose you ignored the message that the script displayed about nvidia graphics cards. So, run
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
in terminal. And, people, please don't ignore the messages that the script displays, it would save you and us lots of time.

---

### Post by Frak on 2007-07-25
> **ElemonGW said:**
> I wouldn't recommend that as in case of errors the terminal would close and the user wouldn't be able to examine them.

That would explain alot for my problems... :lolflag:
I get to the NVidia xconfig and everything goes haywire.

---

### Post by Frak on 2007-07-25
> **ElemonGW said:**
> Just tuned some things to be more clear, I uploaded an updated version.
In this new version did you disable those "Press enter if you want to continue" things?
Because I found it much easier to deal with, without them.

---

### Post by tagrace on 2007-07-25
Hi,

Still getting the NO PACKAGE COMPIZ FOUND error during the script

Also, If I run fusion-icon in a terminal I get the following:

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

Running Fiesty

Any Ideas?

---

### Post by unusedusername on 2007-07-25
First, Thank you for the script ElemonGW. :)

Second, I'm getting the same error like tagrace.

Installed everything, but couldn't launch it. Then i type fusion-icon in terminal and get
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

I'm using Edgy.  Help please.
btw, i'm a newb. :)

---

### Post by fictivetoast on 2007-07-26
INCREDIBLE!  Thank you!
It worked wonderfully on my HPnc6000 laptop with an ATI MOBILITY RADEON 9600 !

---

### Post by ElemonGW on 2007-07-26
> **Frak said:**
> In this new version did you disable those "Press enter if you want to continue" things?
Because I found it much easier to deal with, without them.

No I didn't and I don't think I will ever do that. I think that by removing them people won't know what's their problem is and more messages about problems will start popping up saying "I did everything correct but I don't know why it doesn't work.
PS: However, I am thinking of making available a version which will have them removed, but both versions (with & without it) will be available.

> **tagrace said:**
> Hi,

Still getting the NO PACKAGE COMPIZ FOUND error during the script

Also, If I run fusion-icon in a terminal I get the following:

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

Running Fiesty

Any Ideas?

> **unusedusername said:**
> First, Thank you for the script ElemonGW. :)

Second, I'm getting the same error like tagrace.

Installed everything, but couldn't launch it. Then i type fusion-icon in terminal and get
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

I'm using Edgy.  Help please.
btw, i'm a newb. :)

Well, probably both of you didn't did something correctly. Either you cd to the directory that you have CF Installer-Updater (you must not do this) or you ignored some messages. Btw., pressing y is not the same as pressing enter. It tells which choices you have when. Also, try updating because if you downloaded the files correctly this might save you lots of time.

---

### Post by ElemonGW on 2007-07-26
**Guys, is there everyone who can check if this script works under KDE (the version of KDE) so that I can merge it with the Gnome version if it works or completely remove it if it doesn't?**

---

### Post by llln30lll on 2007-07-26
all installed fine for me :D

---

### Post by llln30lll on 2007-07-26
*edit* scrap that, Compiz icon appears in the corner, theme manager works but not the settings manager

---

### Post by Happy_Man on 2007-07-26
> **ElemonGW said:**
> **Guys, is there everyone who can check if this script works under KDE (the version of KDE) so that I can merge it with the Gnome version if it works or completely remove it if it doesn't?**
Here, I'll test it for you. Hold on a few minutes....
:
Right, here's the deal for me, using Kubuntu Feisty, fully updated as of  8:21 AM EDT. Fusion was installed at about 9:45 AM EDT. 

It works, but I'm noticing more jerkiness in the wobbly, more jumpiness in all animations, along with a host of other things. That's not the script's fault, though. The installer also asked me to get every single development package in existence for GNOME (or so it seemed), but I'm running pure KDE and can't' fathom a use for them. Trevino's Fusion packages did not ask for all these dev libraries. I also had to use the "install" function, as the "upgrade" function threw errors along the lines of "could not find autogen.sh." However, looking through the script, it seems that doing an install removes all previous versions anyway, so no harm done. All in all, though, it does work.... if you know what to do. Your script is very good. I remember when I first tried to compile the git version back in the day, when there was only one thread about Fusion in the entire forum. *reminisces* It didn't work. Your script does, and for that it is good. Kudos for a job well done. :D

---

### Post by tagrace on 2007-07-26
Ok, maybe this is my mistake.

I downloaded the CFInstaller Updater to my Desktop and ran it from a terminal. Is this the problem? Where should the Installer Updater be put?

Ted

---

### Post by tagrace on 2007-07-26
Ok,

Apparently there was something missing on my system and / or from the script that is required for this to work.

I looked at the instructions on OpenCompositing site and found these two commands.

This one loades the Python pyrex which is required to compile css-python.
> sudo apt-get install git-core automake build-essential intltool libtool python-pyrex python2.5-dev

This one loads the build dependencies required for compiz 
> sudo apt-get build-dep compiz

Running the script now worked and it appears to be working.

Ted

---

### Post by Swarms on 2007-07-26
If I already got Compiz Fusion installed from someone others reps, what should I do before?

---

### Post by babygoose on 2007-07-26
did all that stuff detailed in first post, the way i installed it was right click on that .sh file and give it permissions to run as an executable then selected run in terminal, everything worked okay afaik, but, now when i turn on that emerald thing, every window i load has no top bar with the "x" and the minimize etc--and i cant get the settings manager to open up! should i just reinstall the whole thing or what?

---

### Post by ElemonGW on 2007-07-26
> **tagrace said:**
> Ok,

Apparently there was something missing on my system and / or from the script that is required for this to work.

I looked at the instructions on OpenCompositing site and found these two commands.

This one loades the Python pyrex which is required to compile css-python.


This one loads the build dependencies required for compiz 


Running the script now worked and it appears to be working.

Ted

Well, both commands DO run by the script so I don't know why it didn't worked for you from the beginning. The first command runs always will the second runs if you answer no when it asks you about if you have any kde packages installed. When running the second command, which packages it installed to your system. You could provide great help if you remember them.

> **Happy_Man said:**
> Here, I'll test it for you. Hold on a few minutes....
:
Right, here's the deal for me, using Kubuntu Feisty, fully updated as of  8:21 AM EDT. Fusion was installed at about 9:45 AM EDT. 

It works, but I'm noticing more jerkiness in the wobbly, more jumpiness in all animations, along with a host of other things. That's not the script's fault, though. The installer also asked me to get every single development package in existence for GNOME (or so it seemed), but I'm running pure KDE and can't' fathom a use for them. Trevino's Fusion packages did not ask for all these dev libraries. I also had to use the "install" function, as the "upgrade" function threw errors along the lines of "could not find autogen.sh." However, looking through the script, it seems that doing an install removes all previous versions anyway, so no harm done. All in all, though, it does work.... if you know what to do. Your script is very good. I remember when I first tried to compile the git version back in the day, when there was only one thread about Fusion in the entire forum. *reminisces* It didn't work. Your script does, and for that it is good. Kudos for a job well done. :D

Lots of thanks for testing it. As of the fact that it tried to install lots of gnome packages: You used the test version for KDE, right (I assume yes, but just to be safe :) ). Do you have any Gnome packages already installed? If yes, that's the reason why it happened. The script uses build-dep to install the dependencies for compiz, which seems to try to install: in Gnome lots of KDE packages if you have some installed and vise-versa. I was wondering if you could try from a fresh installation of Kubuntu (running it from a live cd will do the same gob too) running
```
sudo apt-get build-dep compiz
```
and listing here all of the dependencies that it tells it requires. This could help me solve the problem.

PS: Reading your post, I can understand why I failed in the examination for the certificate of proficiency in English ;) .

---

### Post by ElemonGW on 2007-07-26
> **Swarms said:**
> If I already got Compiz Fusion installed from someone others reps, what should I do before?

Nothing, just run the script. It will automatically uninstall all the previous versions of compiz, emerald and everything around them.

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> did all that stuff detailed in first post, the way i installed it was right click on that .sh file and give it permissions to run as an executable then selected run in terminal, everything worked okay afaik, but, now when i turn on that emerald thing, every window i load has no top bar with the "x" and the minimize etc--and i cant get the settings manager to open up! should i just reinstall the whole thing or what?

Do you have a NVidia Graphics Card???

---

### Post by babygoose on 2007-07-26
yessir 
geforce go 7800 gtx

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> yessir 
geforce go 7800 gtx

In one of the steps at the script it asked if you have a nvidia graphics card. I assume you pressed no. Well, to fix it now run
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
in terminal.

---

### Post by babygoose on 2007-07-26
actually, i hit yes at that prompt :)

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> actually, i hit yes at that prompt :)

So running the command told you didn't solved the problem (I suppose yes) ? Then you might want to try doing that:

enter
```
sudo nano /etc/X11/xorg.conf
```
in terminal, scroll down until you see the section labeled 'Section "Device"' and there add this line:
```
Option "AddARGBGLXVisuals" "True"
```
Restart Compiz Fusion and Emerald and see what happens. You might also be able to find more help elsewhere, to threads specific for problems like that.

---

### Post by babygoose on 2007-07-26
i ran the script anyways, but it still doesnt do anything, i cant click on any themes to get them to work either..how do i uninstall compiz fusion? i will try a clean install of it, see if that helps, maybe i missed something in the install process?

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> i ran the script anyways, but it still doesnt do anything, i cant click on any themes to get them to work either..how do i uninstall compiz fusion? i will try a clean install of it, see if that helps, maybe i missed something in the install process?

Have you tried what I told you before? Have you tried right-clicking Compiz Fusion Icon at your system tray and going to select window decorator-->emerald, as one of the tips at the script says?

---

### Post by babygoose on 2007-07-26
> **ElemonGW said:**
> Have you tried what I told you before? Have you tried right-clicking Compiz Fusion Icon at your system tray and going to select window decorator-->emerald, as one of the tips at the script says?
yup, heres what i got right now:
window manager: metacity (only one that actually shows the top window bar with the "x" etc
window decorator: emerald

i can get into the emerald settings manager, but i cant change anything
and the settings manager still does not open

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> yup, heres what i got right now:
window manager: metacity (only one that actually shows the top window bar with the "x" etc
window decorator: emerald

i can get into the emerald settings manager, but i cant change anything
and the settings manager still does not open

If you don't have Compiz activated Emerald doesn't work...

---

### Post by babygoose on 2007-07-26
makes sense, 
okay! i got compiz enabled rather that metacity--no i have no top bar on my windows and all that, still cant enable themes or get into settings manager...
how do i uninstall compiz-fusion in order to reinstall?

---

### Post by ElemonGW on 2007-07-26
> **babygoose said:**
> makes sense, 
okay! i got compiz enabled rather that metacity--no i have no top bar on my windows and all that, still cant enable themes or get into settings manager...
how do i uninstall compiz-fusion in order to reinstall?

```
cd ~/compiz/bcop
sudo make uninstall
cd ~/compiz/ccsm
sudo make uninstall
cd ~/compiz/compiz
sudo make uninstall
cd ~/compiz/compizconfig-python
sudo make uninstall
cd ~/compiz/emerald
sudo make uninstall
cd ~/compiz/emerald-themes
sudo make uninstall
cd ~/compiz/fusion-icon
sudo make uninstall
cd ~/compiz/libcompizconfig
sudo make uninstall
cd ~/compiz/plugins-extra
sudo make uninstall
cd ~/compiz/plugins-main
sudo make uninstall
cd ~/compiz/plugins-unsupported
sudo make uninstall
```

I may incorporate in the script at the feature. Still, I don't think that this will solve your problem (if in fact exists).

---

### Post by tagrace on 2007-07-26
The second package loaded a lot of K type stuff. When running your script I always answered Y to the KDE question. Did I miss something or was I supposed to answer N?

Also, I guess I spoke too soon about it working properly. I can not start the Settings Manager from the Icon.

---

### Post by fictivetoast on 2007-07-26
Hey, I too can't get the settings manager to launch.  It doesn't even *appear* in the system prefs menu, and trying CCSM in the terminal yields "command not found" !  For some reason it seems not to be installed at all... I've tried rerunning the script again to reinstall all, but have had the same result.

When I run Update, I get: 

Would you like to update ccsm?(y/n)y
/home/brandon/Desktop/CFInstaller-Updater.sh: 260: ./autogen.sh: not found
Already up-to-date.


Curious......... any suggestions?

---

### Post by Happy_Man on 2007-07-26
> **ElemonGW said:**
> Lots of thanks for testing it. As of the fact that it tried to install lots of gnome packages: You used the test version for KDE, right (I assume yes, but just to be safe :) ). Do you have any Gnome packages already installed? If yes, that's the reason why it happened. The script uses build-dep to install the dependencies for compiz, which seems to try to install: in Gnome lots of KDE packages if you have some installed and vise-versa. I was wondering if you could try from a fresh installation of Kubuntu (running it from a live cd will do the same gob too) running
```
sudo apt-get build-dep compiz
```
and listing here all of the dependencies that it tells it requires. This could help me solve the problem.

PS: Reading your post, I can understand why I failed in the examination for the certificate of proficiency in English ;) .

Ah... that would explain it. I do keep a couple GNOME packages around for experimental purposes. I'm sure that if I weren't, all these packages would not have been installed. I will try to get a live session running to get that info. 

And besides, your English is better than most of the native English speakers I know. ;) Somehow, everybody's good at English, except Americans. Never ceases to amaze me.

---

### Post by tagrace on 2007-07-26
Got Settings Manager to work by following the instruction in the INSTALL file in /compiz/ccsm

Ted

---

### Post by ryandamartini on 2007-07-26
> **Tokhra said:**
> I'm getting the following error for a clean install of Feisty.

Installing ccsm...
./CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory

Any ideas what I'm missing?

I used /home/ryandamartini/CFInstaller-Updater.sh and it ran fine. Double check your path, I messed mine up 5 times and couldnt understand why it wouldnt work, haha :lolflag: 


<---- Newb

But so far I am loving linux for my needs as an engineering student and with other schoolwork, etc...

---

### Post by ElemonGW on 2007-07-26
OK, they have changed the way that ccsm is installed, I will release a new version changing the way it installs it.
**EDIT: I want to change really lots of things @ the script, as the guide at which this script is based doesn't seem to be very good written. Also I want to do some changes at the questions this script asks etc. Also I hope that from the feedback of  Happy_Man I will make CF Installer-Updater work perfectly under KDE. Well, now that I wrote them down they seem  to be many :) . Anyway, don't expect it to be released today (well this is eysily understood :) ) but it will probably be tomorrow (I won't do anything tomorrow until I finish the new version :) .**

---

### Post by ElemonGW on 2007-07-26
File updated, fixing the ccsm error, adding some dependencies that might be needed, adding a reminder about repos and changing the location from where compiz (only compiz) is downloaded. This is the last version before the "big" release with lots of changes.
EDIT: Just did a small change, you might want to download the updated version.
**NOTICE: Only the version for Gnome was updated. The KDE version will be updated as soon as I gather some informations I need and I merge it with the Gnome version.**

---

### Post by ElemonGW on 2007-07-27
I did a mistake witht the yesterday release and during the installation of ccsm it would be installed multiple times :) . It has been fixed now.

---

### Post by luckylarry on 2007-07-27
i'm giving the scripts a go now, so lets see how it does..

I've had no luck with compiz working properly so far, so maybe this'll do it - fingers crossed!

---

### Post by Chazall1 on 2007-07-27
I downloaded the script a couple of hours ago, I have an updated feisty, using only Gnome. When the script asks, "If I have any KDE modlues" I do not, so I answered no. What is with all the KDE stuff!  I do not want all the KDE Stuff. I do not think it is necessary. Is their any way, using your scripts, to have compiz fusion without all the KDE CRAP??????
Could you please advise!

Thanks:confused:

---

### Post by luckylarry on 2007-07-27
bugger, still didn't fix my issues :/

I may just forget about compiz for now...

---

### Post by tagrace on 2007-07-27
I used the latest script on my other Feisty machine and had a bunch of trouble.

I lost all window decorations, even on Metacity.

Quite a struggle but I did a metacity --replace and everything started working. I'm now spinning cubes and it looks good on this high end dual SLI nvidia system.

Seems like the script is close to being perfect but there must be some pre-requisites that must be interfering with the manager. The condition of the system prior to the running of the script seems to be important. Maybe it was because I was running Beryl before running the script. Maybe I should have switch back to metacity before running the script.

Anyway, keep up the good work. I'll get brave over the weekend and try it on my Laptop which is also a Feisty with Beryl running right now.

TAG

---

### Post by ElemonGW on 2007-07-27
> **luckylarry said:**
> bugger, still didn't fix my issues :/

I may just forget about compiz for now...

Well, waht's your problem????

> **Chazall1 said:**
> I downloaded the script a couple of hours ago, I have an updated feisty, using only Gnome. When the script asks, "If I have any KDE modlues" I do not, so I answered no. What is with all the KDE stuff!  I do not want all the KDE Stuff. I do not think it is necessary. Is their any way, using your scripts, to have compiz fusion without all the KDE CRAP??????
Could you please advise!

Thanks:confused:

So it tried to install KDE packages? If yes, then you DO already have some installed, so it tried to install many more. So, when it asks you if you have any KDE packages installed, answer yes.

> **tagrace said:**
> I used the latest script on my other Feisty machine and had a bunch of trouble.

I lost all window decorations, even on Metacity.

Quite a struggle but I did a metacity --replace and everything started working. I'm now spinning cubes and it looks good on this high end dual SLI nvidia system.

Seems like the script is close to being perfect but there must be some pre-requisites that must be interfering with the manager. The condition of the system prior to the running of the script seems to be important. Maybe it was because I was running Beryl before running the script. Maybe I should have switch back to metacity before running the script.

Anyway, keep up the good work. I'll get brave over the weekend and try it on my Laptop which is also a Feisty with Beryl running right now.

TAG

First, you must uninstall Beryl first (Compiz, previous versions of Compiz Fusion and Emerald are automatically being uninstalled from the script, in the next version I will make it to also uninstall beryl). Now, as of the fact you don't have any windows borders. Did you select from Fusion Icon Compiz as window manager and Emerald as window decorator? When it asked you if you have a NVidia graphics card did you answer yes?

---

### Post by tagrace on 2007-07-27
Like I said in my post, all is working. I have no issues at the moment.

As for the install, I did remove beryl using the package manager but does that close down the running beryl? Probably should have removed it and then re-logged before running the script.

TED

---

### Post by dingleberry420 on 2007-07-27
I am on a fresh install of ubuntu 7.04.  The only thing I did before trying the script was enable the nvidia driver and do a complete update on the system.  I checked my sources.list and it appeared to already have the multiverse and universe repositories enabled.

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse 

that is at the bottom of sources.list.  So I downloaded the script and ran it per your instructions 

> eric@eric-ubuntu:~$ sh ~/CFInstaller-Updater.sh

It appears I get an error

> E: You must put some 'source' URIs in your sources.list
..snip..
E: Couldn't find package emerald*


When it asks "Did you get a message about gitfm?(y/n)" I answer no, thought I don't know wtf gitfm is, but I didn't see it any where in the terminal.

This is where stuff seems to go into the pooper..

I see a lot of these messages scrolling by..

> configure.ac:21: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:154: warning: macro `AM_GCONF_SOURCE_2' not found in library


at the next prompt I see this..

> autoreconf: automake failed with exit status: 1
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).read: 262: arg count
Do you use a NVidia graphics card? If you press yes, a command will be executed (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) which might be needed to make window decorations work.(y/n)


I just contrl-c at this point to stop the process as there is definitely something wrong going on..

Any ideas?

---

### Post by Espreon on 2007-07-27
How do I uninstall Compiz Fusion compiled from this script since the one from this script did not work as well as  Trevinho's. So how do I uninstall? Cause I am missing features like the 3-D windows,lightning and the fish. The only reason I used this was because when I had 3D windows enabled the AltTab function was not working properly.

---

### Post by Frak on 2007-07-27
Did you try
```
sudo make uninstall
```

---

### Post by Espreon on 2007-07-27
> **Frak said:**
> Did you try
```
sudo make uninstall
```

I got this: make: *** No rule to make target `uninstall'.  Stop.

---

### Post by Frak on 2007-07-27
How about doing a checkinstall on Compiz Fusion then making Synaptic uninstall it...

---

### Post by ElemonGW on 2007-07-28
> **Espreon said:**
> How do I uninstall Compiz Fusion compiled from this script since the one from this script did not work as well as  Trevinho's. So how do I uninstall? Cause I am missing features like the 3-D windows,lightning and the fish. The only reason I used this was because when I had 3D windows enabled the AltTab function was not working properly.

If you want to uninstall it run this in terminal.

```
cd ~/compiz/bcop
sudo make uninstall
cd ~/compiz/ccsm
sudo make uninstall
cd ~/compiz/compiz
sudo make uninstall
cd ~/compiz/compizconfig-python
sudo make uninstall
cd ~/compiz/emerald
sudo make uninstall
cd ~/compiz/emerald-themes
sudo make uninstall
cd ~/compiz/fusion-icon
sudo make uninstall
cd ~/compiz/libcompizconfig
sudo make uninstall
cd ~/compiz/plugins-extra
sudo make uninstall
cd ~/compiz/plugins-main
sudo make uninstall
cd ~/compiz/plugins-unsupported
sudo make uninstall
```

Ans as of the plugins that you say, these and many more are coming with the next version...

---

### Post by gamefreak863 on 2007-07-28
not to be rude or anything....but I have no idea what this file just did to my computer..

I had compiz installed...sort of..but I had no frames around my windows..

well, now I can't sign into a GNOME session..but all of the sudden I have KDE (which I thank you for...I think...since I wanted to try it out anyway...)

but uhh...yea...lil help here?

---

### Post by gamefreak863 on 2007-07-28
not to mention, now none of my compiz settings are there anymore...water && snow effects don't work..no cube effects..

---

### Post by Espreon on 2007-07-28
> **ElemonGW said:**
> If you want to uninstall it run this in terminal.

```
cd ~/compiz/bcop
sudo make uninstall
cd ~/compiz/ccsm
sudo make uninstall
cd ~/compiz/compiz
sudo make uninstall
cd ~/compiz/compizconfig-python
sudo make uninstall
cd ~/compiz/emerald
sudo make uninstall
cd ~/compiz/emerald-themes
sudo make uninstall
cd ~/compiz/fusion-icon
sudo make uninstall
cd ~/compiz/libcompizconfig
sudo make uninstall
cd ~/compiz/plugins-extra
sudo make uninstall
cd ~/compiz/plugins-main
sudo make uninstall
cd ~/compiz/plugins-unsupported
sudo make uninstall
```

Ans as of the plugins that you say, these and many more are coming with the next version...

Thank you!

---

### Post by X3n0n on 2007-07-28
Well, with the new version uploaded I managed to get ccsm working but the output of the command "compiz --replace -c emerald &" is as below
```
 compiz --replace -c emerald &
[1] 6205
****@****-****:~$ compiz (core) - Warn: Unknown option '-c'

compiz (core) - Error: Couldn't load plugin 'emerald'

[1]+  Done                    compiz --replace -c emerald
```

and nothing happens except that metacity loses it's borders whatever I do with compiz icon.

---

### Post by upthelum on 2007-07-28
I ran the script but it didnt work.
I ran
sh /path/to/file/CF Installer-Updater.sh
which asked me if i want to install or update which i chose to install, here's the rest:

root@linuxhomepc:/home/don/Desktop# sh /home/don/Desktop/CFInstaller-Updater.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Do you have any KDE packages installed?(y/n)y
Reading package lists... Done
Building dependency tree... Done
autoconf is already the newest version.
autotools-dev is already the newest version.
build-essential is already the newest version.
debhelper is already the newest version.
dpkg-dev is already the newest version.
g++ is already the newest version.
E: Couldn't find package g++-4.1
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex 'emerald*'
E: Couldn't find package emerald*
mkdir: cannot create directory `/root/compiz': File exists
Downloading Compiz Fusion and everything else required...
/home/don/Desktop/CFInstaller-Updater.sh: line 32: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 33: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 34: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 35: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 36: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 37: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 38: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 39: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 40: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 41: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 42: git: command not found
Did you get a message about gitfm?(y/n)n
Continuing...
Installing Compiz...
/home/don/Desktop/CFInstaller-Updater.sh: line 65: cd: /root/compiz/compiz: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 66: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing bcop...
/home/don/Desktop/CFInstaller-Updater.sh: line 74: cd: /root/compiz/bcop: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 75: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing libcompizconfig...
/home/don/Desktop/CFInstaller-Updater.sh: line 81: cd: /root/compiz/libcompizconfig: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 82: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing compizconfig-python...
/home/don/Desktop/CFInstaller-Updater.sh: line 88: cd: /root/compiz/compizconfig-python: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 89: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing ccsm...
/home/don/Desktop/CFInstaller-Updater.sh: line 95: cd: /root/compiz/ccsm: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-main...
/home/don/Desktop/CFInstaller-Updater.sh: line 102: cd: /root/compiz/plugins-main: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 103: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald...
/home/don/Desktop/CFInstaller-Updater.sh: line 109: cd: /root/compiz/emerald: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 110: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald-Themes...
/home/don/Desktop/CFInstaller-Updater.sh: line 116: cd: /root/compiz/emerald-themes: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 117: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-extra...
/home/don/Desktop/CFInstaller-Updater.sh: line 123: cd: /root/compiz/plugins-extra: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 124: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-unsupported...
/home/don/Desktop/CFInstaller-Updater.sh: line 130: cd: /root/compiz/plugins-unsupported: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 131: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Do you use a NVidia graphics card? If you press yes, a command will be executed (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) which might be needed to make window decorations work.(y/n)n
Skipping...
Installing Compiz Fusion Icon...
/home/don/Desktop/CFInstaller-Updater.sh: line 144: cd: /root/compiz/fusion-icon: No such file or directory
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Completed
Warning: Do not delete the files that this script downloaded to your home folder. If you do so, update will not be possible.
Tip: In order to launch Compiz Fusion and everything else needed, launch Compiz Fusion Icon (at Gnome it is located at Applications-->System Tools).
Tip: In order to launch Compiz Fusion during startup go to System-->Preferences-->Sessios and at the startup tab click new. At the name field add whatever you want (ex. Compiz Fusion Icon) and at the command field add fusion-icon
Tip: If your windows have no borders, right click at fusion-icon (at your system tray) and go to select window decorator and then select Emerald.
Created by ElemonGW. For more visit [http://elemongw.awardspace.com/](http://elemongw.awardspace.com/)
root@linuxhomepc:/home/don/Desktop#

Whenever it said:
(Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
I pressed enter and it asked again for each line until i hit enter and it finished...

Any suggestions...

---

### Post by ElemonGW on 2007-07-28
> **X3n0n said:**
> Well, with the new version uploaded I managed to get ccsm working but the output of the command "compiz --replace -c emerald &" is as below
```
 compiz --replace -c emerald &
[1] 6205
****@****-****:~$ compiz (core) - Warn: Unknown option '-c'

compiz (core) - Error: Couldn't load plugin 'emerald'

[1]+  Done                    compiz --replace -c emerald
```

and nothing happens except that metacity loses it's borders whatever I do with compiz icon.

Who told you to run that command? Didn't you read the tips at the end of the script? The one you must run is fusion-icon. From there you can activate emerald & compiz (right click on it, it is located at your system tray after you execute it).

---

### Post by ElemonGW on 2007-07-28
> **upthelum said:**
> I ran the script but it didnt work.
I ran
sh /path/to/file/CF Installer-Updater.sh
which asked me if i want to install or update which i chose to install, here's the rest:

root@linuxhomepc:/home/don/Desktop# sh /home/don/Desktop/CFInstaller-Updater.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Do you have any KDE packages installed?(y/n)y
Reading package lists... Done
Building dependency tree... Done
autoconf is already the newest version.
autotools-dev is already the newest version.
build-essential is already the newest version.
debhelper is already the newest version.
dpkg-dev is already the newest version.
g++ is already the newest version.
E: Couldn't find package g++-4.1
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex 'emerald*'
E: Couldn't find package emerald*
mkdir: cannot create directory `/root/compiz': File exists
Downloading Compiz Fusion and everything else required...
/home/don/Desktop/CFInstaller-Updater.sh: line 32: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 33: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 34: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 35: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 36: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 37: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 38: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 39: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 40: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 41: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 42: git: command not found
Did you get a message about gitfm?(y/n)n
Continuing...
Installing Compiz...
/home/don/Desktop/CFInstaller-Updater.sh: line 65: cd: /root/compiz/compiz: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 66: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing bcop...
/home/don/Desktop/CFInstaller-Updater.sh: line 74: cd: /root/compiz/bcop: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 75: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing libcompizconfig...
/home/don/Desktop/CFInstaller-Updater.sh: line 81: cd: /root/compiz/libcompizconfig: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 82: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing compizconfig-python...
/home/don/Desktop/CFInstaller-Updater.sh: line 88: cd: /root/compiz/compizconfig-python: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 89: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing ccsm...
/home/don/Desktop/CFInstaller-Updater.sh: line 95: cd: /root/compiz/ccsm: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-main...
/home/don/Desktop/CFInstaller-Updater.sh: line 102: cd: /root/compiz/plugins-main: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 103: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald...
/home/don/Desktop/CFInstaller-Updater.sh: line 109: cd: /root/compiz/emerald: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 110: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald-Themes...
/home/don/Desktop/CFInstaller-Updater.sh: line 116: cd: /root/compiz/emerald-themes: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 117: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-extra...
/home/don/Desktop/CFInstaller-Updater.sh: line 123: cd: /root/compiz/plugins-extra: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 124: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-unsupported...
/home/don/Desktop/CFInstaller-Updater.sh: line 130: cd: /root/compiz/plugins-unsupported: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 131: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Do you use a NVidia graphics card? If you press yes, a command will be executed (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) which might be needed to make window decorations work.(y/n)n
Skipping...
Installing Compiz Fusion Icon...
/home/don/Desktop/CFInstaller-Updater.sh: line 144: cd: /root/compiz/fusion-icon: No such file or directory
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Completed
Warning: Do not delete the files that this script downloaded to your home folder. If you do so, update will not be possible.
Tip: In order to launch Compiz Fusion and everything else needed, launch Compiz Fusion Icon (at Gnome it is located at Applications-->System Tools).
Tip: In order to launch Compiz Fusion during startup go to System-->Preferences-->Sessios and at the startup tab click new. At the name field add whatever you want (ex. Compiz Fusion Icon) and at the command field add fusion-icon
Tip: If your windows have no borders, right click at fusion-icon (at your system tray) and go to select window decorator and then select Emerald.
Created by ElemonGW. For more visit [http://elemongw.awardspace.com/](http://elemongw.awardspace.com/)
root@linuxhomepc:/home/don/Desktop#

Whenever it said:
(Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
I pressed enter and it asked again for each line until i hit enter and it finished...

Any suggestions...

First: Do not run it as root. Your root password will be requested when needed. Second, you might wanna try installing git-core. Third, do you have universe and multiverse repositories enabled? Finally,  what's your distro (version etc.).

---

### Post by chris-miami on 2007-07-28
I hated it. How do i uninstall it?

---

### Post by Oen386 on 2007-07-29
I ran the install... I get...

```
fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!

```

I can't get the fusion icon to come up. I had compiz working about 3-4 days ago. Then my themes (window decorations) disappeared. So I gave this a try, and now nothing. :(

---

### Post by ElemonGW on 2007-07-29
A testing version of CF Installer-Updater is available for download. You may download it from [here]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2_beta.sh"). The final version will include a bunch of fixes to any problems that might occur, complete support for KDE and build-in the ability to uninstall it.

---

### Post by mandavi on 2007-07-29
hi, when i run the script, i get the following at the compiz section:

```
make  all-recursive
make[1]: Betrete Verzeichnis '/home/butze/compiz/compiz'
Making all in include
make[2]: Betrete Verzeichnis '/home/butze/compiz/compiz/include'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/butze/compiz/compiz/include'
Making all in src
make[2]: Betrete Verzeichnis '/home/butze/compiz/compiz/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -export-dynamic  -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE -lxslt -lm -lxml2 -lstartup-notification-1   -lGL -lm 
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Fehler 1
make[2]: Verlasse Verzeichnis '/home/butze/compiz/compiz/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/butze/compiz/compiz'
make: *** [all] Fehler 2

```

"Fehler" meaning error and "Verlasse Verzeichnis" leaving directory...

---

### Post by Oen386 on 2007-07-29
I get this with the new script you posted.. during install....

```
configure: Using PKG_CONFIG_PATH=NONE/lib/pkgconfig
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements (compiz) were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Jan Eppo Jonker on 2007-07-29
The script worked for me, but only after I modified the installation of ccsm: ccsm has an install.py script
I had a lot of unrelated errors, so I also added "sudo ldconfig" whenever libraries have been modified. I'm not sure this is really necessary.

My entry for ccsm in the script is like this:

cd ~/compiz/ccsm
git-pull
read -p "Would you like to update ccsm?(y/n)" answer;
if [ $answer = y ] ; then
##  skip this ## ./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install
sudo python setup.py install --prefix=/usr/local && sudo ldconfig
else
echo "Skipping..."
fi

My platform is Asus P5B Vista 4 GB, GeForce 8800GTS 340 MB,
Acer AL2223W 1680x1050 widescreen
Gutsy x86_64, MemTotal:  4036800 kB
Kernel version: 2.6.22-8-generic
X Window System Version 1.3.0
NVidia: lrm disabled, install script NVIDIA-Linux-x86_64-100.14.11-pkg2.run

---

### Post by Jan Eppo Jonker on 2007-07-29
The script worked for me, but only after I modified the entry for fusion icon: fusion-icon doesn't need configuring or building, only "make install". My entry for fusion-icon is:

cd ~/compiz/fusion-icon
git-pull
read -p "Would you like to update fusion-icon?(y/n)" answer;
if [ $answer = y ] ; then
## skip this ## ./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install
sudo make install
else
echo "Skipping..."
fi

(;--)

---

### Post by tadada on 2007-07-29
ok I want to try this but when I was looking the one at the front ([http://elemongw.googlepages.com/CFInstaller-Updater.sh](http://elemongw.googlepages.com/CFInstaller-Updater.sh))  and the one here in the back ([http://elemongw.googlepages.com/CF_Installer-Updater_v.2_beta.sh](http://elemongw.googlepages.com/CF_Installer-Updater_v.2_beta.sh)) have a slight difference. the second one has some colons the the first doesn't have. which one should I use?

---

### Post by upthelum on 2007-07-29
Right i'm not sure how to add the post this is addressed to though this is it:

                     Originally Posted by **upthelum**                     [[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=3096127#post3096127")                 
                 [I]I ran the script but it didnt work.
I ran
sh /path/to/file/CF Installer-Updater.sh
which asked me if i want to install or update which i chose to install, here's the rest:

root@linuxhomepc:/home/don/Desktop# sh /home/don/Desktop/CFInstaller-Updater.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Do you have any KDE packages installed?(y/n)y
Reading package lists... Done
Building dependency tree... Done
autoconf is already the newest version.
autotools-dev is already the newest version.
build-essential is already the newest version.
debhelper is already the newest version.
dpkg-dev is already the newest version.
g++ is already the newest version.
E: Couldn't find package g++-4.1
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex 'emerald*'
E: Couldn't find package emerald*
mkdir: cannot create directory `/root/compiz': File exists
Downloading Compiz Fusion and everything else required...
/home/don/Desktop/CFInstaller-Updater.sh: line 32: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 33: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 34: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 35: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 36: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 37: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 38: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 39: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 40: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 41: git: command not found
/home/don/Desktop/CFInstaller-Updater.sh: line 42: git: command not found
Did you get a message about gitfm?(y/n)n
Continuing...
Installing Compiz...
/home/don/Desktop/CFInstaller-Updater.sh: line 65: cd: /root/compiz/compiz: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 66: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing bcop...
/home/don/Desktop/CFInstaller-Updater.sh: line 74: cd: /root/compiz/bcop: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 75: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing libcompizconfig...
/home/don/Desktop/CFInstaller-Updater.sh: line 81: cd: /root/compiz/libcompizconfig: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 82: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing compizconfig-python...
/home/don/Desktop/CFInstaller-Updater.sh: line 88: cd: /root/compiz/compizconfig-python: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 89: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing ccsm...
/home/don/Desktop/CFInstaller-Updater.sh: line 95: cd: /root/compiz/ccsm: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-main...
/home/don/Desktop/CFInstaller-Updater.sh: line 102: cd: /root/compiz/plugins-main: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 103: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald...
/home/don/Desktop/CFInstaller-Updater.sh: line 109: cd: /root/compiz/emerald: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 110: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing Emerald-Themes...
/home/don/Desktop/CFInstaller-Updater.sh: line 116: cd: /root/compiz/emerald-themes: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 117: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-extra...
/home/don/Desktop/CFInstaller-Updater.sh: line 123: cd: /root/compiz/plugins-extra: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 124: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Installing plugins-unsupported...
/home/don/Desktop/CFInstaller-Updater.sh: line 130: cd: /root/compiz/plugins-unsupported: No such file or directory
/home/don/Desktop/CFInstaller-Updater.sh: line 131: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
Do you use a NVidia graphics card? If you press yes, a command will be executed (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) which might be needed to make window decorations work.(y/n)n
Skipping...
Installing Compiz Fusion Icon...
/home/don/Desktop/CFInstaller-Updater.sh: line 144: cd: /root/compiz/fusion-icon: No such file or directory
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Completed
Warning: Do not delete the files that this script downloaded to your home folder. If you do so, update will not be possible.
Tip: In order to launch Compiz Fusion and everything else needed, launch Compiz Fusion Icon (at Gnome it is located at Applications-->System Tools).
Tip: In order to launch Compiz Fusion during startup go to System-->Preferences-->Sessios and at the startup tab click new. At the name field add whatever you want (ex. Compiz Fusion Icon) and at the command field add fusion-icon
Tip: If your windows have no borders, right click at fusion-icon (at your system tray) and go to select window decorator and then select Emerald.
Created by ElemonGW. For more visit [http://elemongw.awardspace.com/](http://elemongw.awardspace.com/)
root@linuxhomepc:/home/don/Desktop#

Whenever it said:
(Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
I pressed enter and it asked again for each line until i hit enter and it finished...

Any suggestions...[/I]
                                 First: Do not run it as root. Your root password will be requested when needed. Second, you might wanna try installing git-core. Third, do you have universe and multiverse repositories enabled? Finally, what's your distro (version etc.).

I re-installed the os and ran it again but got this output:

root@linuxhomepc:/home# sh /home/CFInstaller-Updater_kde_.sh

It then collected the packages and finished with this:

Setting up build-essential (11.1) ...
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex 'emerald*'
E: Couldn't find package emerald*
Downloading Compiz Fusion and everything else required...
/home/CFInstaller-Updater_kde_.sh: line 27: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 28: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 29: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 30: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 31: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 32: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 33: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 34: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 35: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 36: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 37: git: command not found
Installing Compiz...
/home/CFInstaller-Updater_kde_.sh: line 41: cd: /root/compiz/compiz: No such file or directory
/home/CFInstaller-Updater_kde_.sh: line 42: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).

What next then?

---

### Post by chiinox on 2007-07-29
Script ran with some errors on PC, in the end got the fusion-icon and such was able to launch.  CPU would spike up big time and would loose all borders and such.  I got it to work after uninstalling the desktop effects that come installed with Ubuntu.

sudo apt-get remove compiz-core desktop-effects

After that everything works pretty good.  I definitely like compiz fusion, still have some quirks to work out like the bottom cap of the cube can't get it to show a pic. still messing around with all the other plugins.  Now having a hard time with Laptop and Radeon Mobility x1400.  So far have tried Trevinos but no go, unless I log in with XGL session.  Will give this script a try on laptop as well.  Hope this helps someone.

Forgot to thank Elemon for a cool script, probably needs some tweaking just like everything else.  Will leave that to the experts!!

---

### Post by neoplasticity on 2007-07-29
I just tried the script and it seemed to install fine.

However, when I went to activate compiz, i lost all my windows borders.  No problem I thought, i'll select emerald as the window decorator like the script says to do.  That did nothing.

I went to the emerald theme manager option and i click it.  nothing happens.

I go into synaptics and notice that emerald is not installed.  So i go ahead and install it.

Now the theme manager works.  I choose a theme but it doesn't seem to change anything.

So whenever i choose compiz, I get no borders and it seems that compiz is not working because I dont get the cube effect or any of the other effects.  So basically.. as far as i can tell, the only thing that compiz does with the way i've installed this script is to make me lose my windows borders.  does not add any compiz effects at all.  

any clue to where i might have gone wrong?  I did this on a fresh install of 7.10 Alpha3.  I run the amd64 version and i have a 64x2 with geforce 7600gs.  I said no to KDE, no to gitfm, and yes to nvidia.

---

### Post by weblordpepe on 2007-07-30
How can I uninstall what this script did?? My compiz is a total mess.

---

### Post by mandavi on 2007-07-30
> How can I uninstall what this script did?? My compiz is a total mess.
It was explained twice already in this thread.

---

### Post by mandavi on 2007-07-30
> **mandavi said:**
> hi, when i run the script, i get the following at the compiz section:

```
make  all-recursive
make[1]: Betrete Verzeichnis '/home/butze/compiz/compiz'
Making all in include
make[2]: Betrete Verzeichnis '/home/butze/compiz/compiz/include'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/butze/compiz/compiz/include'
Making all in src
make[2]: Betrete Verzeichnis '/home/butze/compiz/compiz/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -export-dynamic  -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE -lxslt -lm -lxml2 -lstartup-notification-1   -lGL -lm 
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Fehler 1
make[2]: Verlasse Verzeichnis '/home/butze/compiz/compiz/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/butze/compiz/compiz'
make: *** [all] Fehler 2

```

"Fehler" meaning error and "Verlasse Verzeichnis" leaving directory...

I don't know why, but when i ran the script today in the morning again, all compiled just fine and it's working. First my window-boarders weren't there, because it was set to GTK Windows Decoration, but after switching to Emerald and a new X-server start all is working just fine. Thanks for the great script and good luck for all the ones which are still struggling.

---

### Post by johannes_ on 2007-07-30
Does this script work with 64bit versions?

---

### Post by mandavi on 2007-07-30
> **johannes_ said:**
> Does this script work with 64bit versions?

[http://ubuntuforums.org/showthread.php?p=3079486&highlight=64-bit#post3079486](http://ubuntuforums.org/showthread.php?p=3079486&highlight=64-bit#post3079486)

you could have searched the thread by yourself though... ;)

---

### Post by gula on 2007-07-30
Nice Script. Thanks a lot

Installed without problems on 64bit Feisty. Ati X800XT with community "ati" xorg driver. Everything just works. This compiz is really nice. Ring Switcher beats vistas flip3d hands down. Gotta love that eyecandy.

---

### Post by Happy_Man on 2007-07-30
> **neoplasticity said:**
> I just tried the script and it seemed to install fine.

However, when I went to activate compiz, i lost all my windows borders.  No problem I thought, i'll select emerald as the window decorator like the script says to do.  That did nothing.

I went to the emerald theme manager option and i click it.  nothing happens.

I go into synaptics and notice that emerald is not installed.  So i go ahead and install it.

Now the theme manager works.  I choose a theme but it doesn't seem to change anything.

So whenever i choose compiz, I get no borders and it seems that compiz is not working because I dont get the cube effect or any of the other effects.  So basically.. as far as i can tell, the only thing that compiz does with the way i've installed this script is to make me lose my windows borders.  does not add any compiz effects at all.  

any clue to where i might have gone wrong?  I did this on a fresh install of 7.10 Alpha3.  I run the amd64 version and i have a 64x2 with geforce 7600gs.  I said no to KDE, no to gitfm, and yes to nvidia.
You shouldn't use this script on Gutsy, as Compiz Fusion is already in the repos.

---

### Post by upthelum on 2007-07-30
Ok this is what i get now after a re-install of my os.

don@linuxhomepc:/$ sudo sh /home/CFInstaller-Updater_kde_.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 for regex ‘automake’
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex ‘emerald*’
E: Couldn't find package emerald*
Downloading Compiz Fusion and everything else required...
/home/CFInstaller-Updater_kde_.sh: line 27: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 28: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 29: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 30: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 31: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 32: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 33: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 34: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 35: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 36: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 37: git: command not found
Installing Compiz...
/home/CFInstaller-Updater_kde_.sh: line 41: cd: /home/don/compiz/compiz: No such file or d irectory
/home/CFInstaller-Updater_kde_.sh: line 42: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).

I cant do anything in Terminal except close the window, or keep pressing enter until it goes through each line that has an error, at which point it will tell me another error but i dont want to continue the installation at this point as there is obviously something wrong at this point. Also it says "E: Couldn't find package emerald*"

Is this a repository problem?

Here's my sources.list

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Please help as i'm anxious to get compiz running, if indeed i can. 

I use an athlon 64 with onboard vga and gig ram.

Thanks...

---

### Post by upthelum on 2007-07-30
Ok i tried this:


Quote:
Originally Posted by Tokhra View Post
I'm getting the following error for a clean install of Feisty.

Installing ccsm...
./CFInstaller-Updater.sh: line 96: ./autogen.sh: No such file or directory

Any ideas what I'm missing?
I assume you have cd to the directory you have CFInstaller-Updater.sh. You shouldn't have done that as it may mess up the things a bit. try just running
Code:

sh /path/to/file/CFInstaller-Updater.sh

But i get the same message it cant find emerald and then the rigmoroll i posted earlier...

PS How do you add a previous post?

---

### Post by ny_NEx on 2007-07-31
Hi guys, i have a little problem and need your help... i search everywhere but seems i cant fix this...  

PLEASE HELP!

I have Intel GM 915 Graphics Card

When i use compiz i have no boarders, and when i use emerald nothing happens, even when i star emerald theme manager i cant do anything...

I try emerald --replace...

This is what i get when use compiz --replace

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Frak on 2007-07-31
> **ny_NEx said:**
> Hi guys, i have a little problem and need your help... i search everywhere but seems i cant fix this...  

PLEASE HELP!

I have Intel GM 915 Graphics Card

When i use compiz i have no boarders, and when i use emerald nothing happens, even when i star emerald theme manager i cant do anything...

I try emerald --replace...

This is what i get when use compiz --replace

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Does Beryl or regular Compiz run on your system?

---

### Post by ny_NEx on 2007-08-01
I dont know which composit menager is it but default effect in Feisty is working fine, but i think i found solution

Every thing seems to work when started with following command 

LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp

But there is problem if compiz icon is started after the command.... so is there any way of importing that particular command in Compiz Fusion Icon ??

THX !!!

---

### Post by ElemonGW on 2007-08-01
> **ny_NEx said:**
> I dont know which composit menager is it but default effect in Feisty is working fine, but i think i found solution

Every thing seems to work when started with following command 

LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp

But there is problem if compiz icon is started after the command.... so is there any way of importing that particular command in Compiz Fusion Icon ??

THX !!!

You can achieve that by doing the appropriate changes in the libfusionicon.py file. If you can't make it, just contact me and I will tell you how ;) .

---

### Post by ElemonGW on 2007-08-01
[B]EVERYBODY READ!!!
To all those who had an error about libcairo.so.2. This is Mono 's blame. For some reason it does changes that it shouldn't do (at least when you install the latest version with the installer). You will get this error even when you try running Firefox (try running it from the terminal and you will see). So, what you have to do is uninstall Mono you will no more get that error. Also, as of the next version, you may have noticed that it was supposed to be released a few days go. but steel nothing. Please just be patient. It will be released as soon as it is finished.[/B]

---

### Post by ny_NEx on 2007-08-01
> **ElemonGW said:**
> You can achieve that by doing the appropriate changes in the libfusionicon.py file. If you can't make it, just contact me and I will tell you how ;) .

Hi thanks very much for your help 

but i have one more question :) 

Im not 100% sure what exactly i have to change in this python script, i try something but nothing happens, nothing good by the way :) 

So help me out, 

I have attached my libfusionicon.py 

Thanks one more time for your effort :D

---

### Post by ElemonGW on 2007-08-01
Here is it.

---

### Post by ny_NEx on 2007-08-01
> **ElemonGW said:**
> Here is it.

:( its not working.... 

Only solution for now is to manually enter in shell....

But thx anyway!!! :)

---

### Post by ElemonGW on 2007-08-01
Hrm, I just noticed that I didn't edit the file as I should (i wrote the command with which works for you with wrong order ;) ) . This one should work fine. Otherwise, you are out of luck from my side. OH, and btw., what you did when I gave you the changed file? I mean where you put it etc.
Btw: From what I can see, this will not work either. Sorry that I wasn't able to help :( . It seems that more files need to be edited than I expected and I don't have the time of doing it right now. Sorry again :( .

---

### Post by upthelum on 2007-08-02
> **upthelum said:**
> Ok this is what i get now after a re-install of my os.

don@linuxhomepc:/$ sudo sh /home/CFInstaller-Updater_kde_.sh

This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Do you want to install Compiz Fusion or update it?(i/u)i
Welcome to Compiz Fusion Installation Script.
Installing required dependencies to build...
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 for regex ‘automake’
automake1.4 is already the newest version.
build-essential is already the newest version.
E: Couldn't find package python2.5-dev
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Removing any previous installations of Compiz and Emerald...
Reading package lists... Done
Building dependency tree... Done
Note, selecting xemeraldia for regex ‘emerald*’
E: Couldn't find package emerald*
Downloading Compiz Fusion and everything else required...
/home/CFInstaller-Updater_kde_.sh: line 27: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 28: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 29: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 30: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 31: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 32: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 33: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 34: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 35: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 36: git: command not found
/home/CFInstaller-Updater_kde_.sh: line 37: git: command not found
Installing Compiz...
/home/CFInstaller-Updater_kde_.sh: line 41: cd: /home/don/compiz/compiz: No such file or d irectory
/home/CFInstaller-Updater_kde_.sh: line 42: ./autogen.sh: No such file or directory
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).

I cant do anything in Terminal except close the window, or keep pressing enter until it goes through each line that has an error, at which point it will tell me another error but i dont want to continue the installation at this point as there is obviously something wrong at this point. Also it says "E: Couldn't find package emerald*"

Is this a repository problem?

Here's my sources.list

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Please help as i'm anxious to get compiz running, if indeed i can. 

I use an athlon 64 with onboard vga and gig ram.

Thanks...

Can anyone verify for me if my sources.list file has the correct repositories please or tell me what to try next?

---

### Post by ElemonGW on 2007-08-02
Version 2 of CF Installer-Updater is out. It is not yet official (few minor changes may be made at the final version). You may download it from [here]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2.sh"). Really lots of changes, changelog will come with the final release.

---

### Post by ElemonGW on 2007-08-02
> **upthelum said:**
> Can anyone verify for me if my sources.list file has the correct repositories please or tell me what to try next?

It is because you have dapper. Why don't you upgrade?

You might however try adding these lines in you sources.list file:
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by upthelum on 2007-08-02
Hey thanks, do i upgrade by sudo apt-get updrade. And do i apt-get update first?

---

### Post by weblordpepe on 2007-08-02
update first, that will update all your information about the repositories.

then do the dist-upgrade or whatever it is.

---

### Post by Frak on 2007-08-02
Before you do anything else, it is **not** recommended to upgrade from Dapper to Feisty, there is a very high chance your system will break. If you upgrade, upgrade to edgy, then to feisty.
Run
```
gksu "update-manager -c"
```
Then once your upgraded to Edgy, go to
System -> Administration -> Update Manager
[IMG]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager.png[/IMG]
Then you should see this
[IMG]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager-upgrade.png[/IMG]
Then just click upgrade!

---

### Post by upthelum on 2007-08-02
Thanks. 
This is my desktop at the moment but i would love to get compiz running, do i have to upgrade? Can you tell me the proper list of commands i need to do it right, as i upgraded before on a previous install and things started to go towards the sky. I am wary of upgrading now because of that but if know how to do it correctly it would be a great help...

---

### Post by Frak on 2007-08-02
> **upthelum said:**
> Thanks. 
This is my desktop at the moment but i would love to get compiz running, do i have to upgrade? Can you tell me the proper list of commands i need to do it right, as i upgraded before on a previous install and things started to go towards the sky. I am wary of upgrading now because of that but if know how to do it correctly it would be a great help...
Just follow what I posted above. It should work just fine.

---

### Post by upthelum on 2007-08-02
Do i have to include the quotation marks Thanks.

---

### Post by Frak on 2007-08-02
> **upthelum said:**
> Do i have to include the quotation marks Thanks.
Yes.

---

### Post by upthelum on 2007-08-02
> **Frak said:**
> Before you do anything else, it is **not** recommended to upgrade from Dapper to Feisty, there is a very high chance your system will break. If you upgrade, upgrade to edgy, then to feisty.
Run
```
gksu "update-manager -c"
```
Then once your upgraded to Edgy, go to
System -> Administration -> Update Manager
[IMG]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager.png[/IMG]
Then you should see this
[IMG]https://help.ubuntu.com/community/FeistyUpgrades?action=AttachFile&do=get&target=update-manager-upgrade.png[/IMG]
Then just click upgrade!

I tried this and got this error box from the update manager:

Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

This is the terminal output of gksu "update-manager -c"

don@linuxhomepc:/home/splash$ sudo gksu "update-manager -c"
Password:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmp4WJiTV/edgy.tar.gz'
authenticate '/tmp/tmp4WJiTV/edgy.tar.gz' against '/tmp/tmp4WJiTV/edgy.tar.gz.gpg'
/tmp/tmp4WJiTV/DistUpgradeViewGtk.py:360: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
  self._term.realize()
don@linuxhomepc:/home/splash$ sudo gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmp0Ky5CU/edgy.tar.gz'
authenticate '/tmp/tmp0Ky5CU/edgy.tar.gz' against '/tmp/tmp0Ky5CU/edgy.tar.gz.gpg'
/tmp/tmp0Ky5CU/DistUpgradeViewGtk.py:360: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
  self._term.realize()
don@linuxhomepc:/home/splash$

I think this may be related to my sources.list file:

#
deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

For some reason it cant get the cdrom updates, perhaps im wrong but if you or anyone can shed some light on it that would be great as i get this error with other updates and installations. Thanks again...

---

### Post by Frak on 2007-08-02
Try this instead
```
gksu "update-manager -c -d"
```
And run the code as it is, **don't add [B]sudo**[/B] to the beggining of it.

---

### Post by upthelum on 2007-08-02
The same error:

Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

I already tried apt-cdrom but it didnt work.

---

### Post by Frak on 2007-08-02
Is there any CD in your drive at the moment.

---

### Post by upthelum on 2007-08-02
Yes the disc i used to install.

---

### Post by Frak on 2007-08-02
> **upthelum said:**
> Yes the disc i used to install.
Eject it, at the moment since it contains Ubuntu packages, Apt has mounted it as it thinks its ready to install more packages.
Thats probably why it isn't working.

---

### Post by upthelum on 2007-08-02
I did that but still the same error...

---

### Post by Frak on 2007-08-02
Go to synaptic, Edit->Repositories, and make sure CD-ROM is unchecked.

---

### Post by upthelum on 2007-08-02
Thats helped a little as there are only two error lines now instead of four though it's still not working.

---

### Post by Frak on 2007-08-02
Log out, log back in, and then try it.

---

### Post by upthelum on 2007-08-02
Ok i did a hard reboot and get the same error on two lines.

sources.list file:

#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

I have a hunch that there's something wrong here. Should i comment out the first line and alter the next or not? Help...

---

### Post by Frak on 2007-08-02
were it says
> deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
Change it to
> # deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

---

### Post by superbungalow on 2007-08-02
when i run this scrip in the command line (from the first post) is it meant to take about 1 hour?

---

### Post by upthelum on 2007-08-02
Firstly i got this message:

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or with synaptic.

Seems i have roughly two hours till the upgrade finishes so i think it'll be starbucks in the morning for a wake up call. 
Thanks for your help i'll have another go at installing compiz tomorrow....

---

### Post by upthelum on 2007-08-02
> **superbungalow said:**
> when i run this scrip in the command line (from the first post) is it meant to take about 1 hour?

Do you have broadband? Whats your machine spec?

---

### Post by Frak on 2007-08-02
> **superbungalow said:**
> when i run this scrip in the command line (from the first post) is it meant to take about 1 hour?
It does take awhile to build packages from source, so give it time.

---

### Post by superbungalow on 2007-08-02
yes, umm, it finished and said I have the fusion icon thing, and to click it, so I did, and I also logged out and back in a started it again, and it appears to doo absolultey nothing, like its there but not really doing anything. any advice?

---

### Post by st33med on 2007-08-02
> **superbungalow said:**
> yes, umm, it finished and said I have the fusion icon thing, and to click it, so I did, and I also logged out and back in a started it again, and it appears to doo absolultey nothing, like its there but not really doing anything. any advice?

Having the same problem too, it does nothing.

---

### Post by superbungalow on 2007-08-02
umm, I reloaded the wondow manager and played around in the right click menu of the icon, and now my windows have no border???

---

### Post by upthelum on 2007-08-02
I hear of that problem a lot but i haven't been fortunate enough to have to try and fix it myself YET lol, but at least your making progress. :confused:

---

### Post by st33med on 2007-08-02
```
andrew@andrew-laptop:~$ fusion-icon
* Using the GTK Interface
* libcompizconfig.so.0: cannot open shared object file: No such file or directory
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

So where is this interface?

---

### Post by superbungalow on 2007-08-02
OK, latest update, after playing around, it seems, that none of the emerald themes do anything, and whichever windows decorator you use has no effect. However, my windows suddenly have borders if I change my windows manager to kwin or metacity (both of which look different, but kwin has 4 workspaces). Um,, so there is somethign wrong with the compiz windows manager?

---

### Post by superbungalow on 2007-08-02
Also, I get this if I run it from the terminal:

```

leon@ubuntu:~$ fusion-icon
* Using the GTK Interface
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Active WM is already running

```

---

### Post by upthelum on 2007-08-02
> **superbungalow said:**
> Also, I get this if I run it from the terminal:

```

leon@ubuntu:~$ fusion-icon
* Using the GTK Interface
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Active WM is already running

```

Someone correct me if i'm wrong but does that mean Active "window management" is already running?

---

### Post by superbungalow on 2007-08-02
I really don;t know, I'm a n00b, all I know is that I have 2 new ways of making my windows look different and nothing else works! I'm going to reboot.

---

### Post by st33med on 2007-08-03
Ok. I now have fusion-icon running... HOWEVER: none of the effects work (not even 3d Desktop), and the borders are missing. The only fix for the borders is to switch to the metacity windows manager. What do I do?

EDIT: this is what happens in terminal.
```
 * Using the GTK Interface
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/bin/compiz.real
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Intel found, exporting: INTEL_BATCH=1
* No GLX_EXT_texture_from_pixmap present with direct rendering context
... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* Executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: Couldn't load plugin 'ccp'

```

---

### Post by X3n0n on 2007-08-03
> **ElemonGW said:**
> Who told you to run that command? Didn't you read the tips at the end of the script? The one you must run is fusion-icon. From there you can activate emerald & compiz (right click on it, it is located at your system tray after you execute it).


Well I tried that way but compiz-icon runs the old compiz, not the compiz-fusion one...

---

### Post by Digitallysick on 2007-08-03
it works for me, but the compiz settings manager is not there/doesn't work, how do i fix this??

---

### Post by upthelum on 2007-08-03
> **ElemonGW said:**
> [CENTER]***_I will update this post soon, until then you may visit its homepage (scroll down to the end of the post to find it) (btw., If you experience any problems accessing its homepage and my site in general, I would be really glad if you contact me and report it)._***



***About***[/CENTER]

I present you another script I made, this time for automatically installing and updating Compiz Fusion to its very latest version (from gitweb). I created this script because I couldn't find a fast way of doing this and Trevino 's repository didn't have the latest files available. Compiz Fusion files are changes sometimes even every hour so this is not even possible. With this script you will have the freedom to chose when to update Compiz Fusion. Also, it has been reported from people who where using the files from Trevino's repository and then tried this script that Compiz Fusion then started being faster (probably because that this script downloads and installs files that are newer, and enchantments have been made comparing with the older versions). Finally, for creating this script I was based on [this]("http://forums.opencompositing.org/viewtopic.php?f=51&t=758") guide.

[Download CF Installer-Updater for Gnome]("http://elemongw.googlepages.com/CFInstaller-Updater.sh")
[Download CF Installer-Updater for KDE (verified to work, but not really well, use it at your own risk!)]("http://elemongw.googlepages.com/CFInstaller-Updater_kde_.sh")

[CENTER]***Downloads Archive***
(There is no reason for using them, as I have merged them all in the current version and I have done lots of enchantments)[/CENTER]

[Download Installation Script]("http://elemongw.googlepages.com/fusion-install.sh")
[Download Installation Script (Alternative)]("http://elemongw.googlepages.com/fusion-installalt.sh")
[Download Update script]("http://elemongw.googlepages.com/fusion-update.sh")

[CENTER]***Running CF Installer-Updater***[/CENTER]

Just run

```
sh /path/to/file/CF Installer-Updater.sh
```

Everything is explained within the script so you should not have any problems. If you however do have, feel free to post. Also, a thanks would be good :) .

[CENTER]***Changelog***[/CENTER]

**26-7-2007** Some things tuned to be more clear
**25-7-2007** Fixed a syntax error that I accidentally did after the last changes (Sorry!)
**25-7-2007** Some other things tuned
**25-7-2007** Some things tuned
**25-7-2007** Installation Script, Installation Script Alternative & Update script merged under the name CF Installer-Updater
**25-7-2007** Alternative script added to face some problems in certain cases
**24-7-2007** First Public Release of Installation Script & Update script


[***Homepage***]("http://elemongw.awardspace.com/?q=node/19")

***Note: It has been reported (and from personal experience too) that by following this way (either using my script or compiling by yourself) Compiz Fusion responses much better and it is way faster, comparing with installing it through repositories/deb packages.***

Ok i just upgraded to Feisty and installed compiz, i have it in my Kmenu but when i start it, it just hangs loading on the taskbar for maybe 7-10 seconds and then stops. I cant go to system > preferences as i dont have System > preferences. 
Is there an easy way to get compiz up and running from here?

---

### Post by greppi on 2007-08-03
I've installed this pack, and all seemed OK, but after installation when I go to _Applications->System tools-> compiz fusion icon_ or _System->preferences->CompizConfig Setting Manager_ nothing follows, no action, no setting window show ...
What's wrong ?

---

### Post by upthelum on 2007-08-03
Wish i could help but im still chasing answers too.

---

### Post by upthelum on 2007-08-04
Hey i hate to bring the thread up with the same question but does anyone know why compiz wont start for me. I click the icon on the taskbar and it starts loading and keeps loading for about 20 seconds, and then just quits. This is really annoying as it took me some time to get installing it right, now its installed but wont work.
I have kubuntu server with kde, asus board, onboard vga and gig ram.

---

### Post by ElemonGW on 2007-08-06
**The current version doesn't work as it should. You are highly recommended to use a previous version. However, if you already installed CF and you plan to use CF Installer-Updater only to update, then you can use the current version, as the problem with the current version is located at the installation part. I will release a version fixing it as soon as I have time and will to do it.**

---

### Post by Ub1476 on 2007-08-06
Hey, I get this when installing:

```
kasper@FeistyFawn:~$ sh /home/kasper/Compiz_Fusion/CFInstaller-Updater.sh
This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).
Do you want to install Compiz Fusion or update it?(i/u)u
Welcome to Compiz Fusion Update Script.
cd: 262: can't cd to /home/kasper/compiz/bcop
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update bcop?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/ccsm
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update ccsm?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/compiz
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update compiz?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/compizconfig-python
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update compizconfig-python?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/emerald
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update emerald?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/emerald-themes
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update emerald-themes?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/fusion-icon
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update fusion-icon?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/libcompizconfig
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update libcompizconfig?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-extra
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-extra?(y/n)y 
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-main
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-main?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-unsupported
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-unsupported?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
Created by ElemonGW. For more visit http://elemongw.awardspace.com/

```

What's wrong? I got both files located in home/user/Compiz_Fusion.. Btw, you need to remove the space between CF and Installer-Updater.sh:p

---

### Post by upthelum on 2007-08-06
> **ElemonGW said:**
> **The current version doesn't work as it should. You are highly recommended to use a previous version. However, if you already installed CF and you plan to use CF Installer-Updater only to update, then you can use the current version, as the problem with the current version is located at the installation part. I will release a version fixing it as soon as I have time and will to do it.**

Hi there, sorry for hassling you but is there any sign of the latest version, i have managed to install but when i start it, it just loads for about 20 seconds then stops?

Many thanks.

---

### Post by Kosimo on 2007-08-06
> **ElemonGW said:**
> If you want to uninstall it run this in terminal.

```
cd ~/compiz/bcop
sudo make uninstall
cd ~/compiz/ccsm
sudo make uninstall
cd ~/compiz/compiz
sudo make uninstall
cd ~/compiz/compizconfig-python
sudo make uninstall
cd ~/compiz/emerald
sudo make uninstall
cd ~/compiz/emerald-themes
sudo make uninstall
cd ~/compiz/fusion-icon
sudo make uninstall
cd ~/compiz/libcompizconfig
sudo make uninstall
cd ~/compiz/plugins-extra
sudo make uninstall
cd ~/compiz/plugins-main
sudo make uninstall
cd ~/compiz/plugins-unsupported
sudo make uninstall
```

Ans as of the plugins that you say, these and many more are coming with the next version...

I did it...

But it says:

> /compiz/bcop$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.


What can I do?

---

### Post by mrbandersnatch on 2007-08-07
> **Digitallysick said:**
> it works for me, but the compiz settings manager is not there/doesn't work, how do i fix this??

Likewise Im having an issue with ccsm.

It looks like Im missing a package on build now (formally was fully working) x11-xcb? Is this a new dependency which isny being installed by the update script&#65311;

BTW I wish this thread was stickied - I can usually get a working compositing manager with this when the ubuntu version has issues. Very helpfull and thanks to the OP :)

---

### Post by PaulFXH on 2007-08-07
I used the v.2 Final installer to install Compiz-Fusion in Ubuntu Feisty and it worked perfectly, first time.
That's a great script -- thanks a lot.

However, I then tried to install it in Linux Mint 2.8 (which is very similar --indeed almost indistinguishable from -- Ubuntu).
Again, I used the v.2 Final installer and no errors popped up and everything seemed fine.
But, unfortunately it doesn't seem to work.
Thus, although I've included "fusion-icon" in the StartUp Sessions, it doesn't start.
If I type "fusion-icon" in a terminal, I get this error:
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```
I saw an earlier post in this thread refer to the same error (but in Ubuntu) and the response was that this issue should be resolved by the Final version of the installer. However, I am using the final version and no go.
Although CompizConfig Settings Manager appears in System>Preferences, it doesn't do anything when left-clicked. Also, Compiz Fusion Icon appears in Applications.System Tools. But again, nothing happens when this is clicked.
Would be grateful for any advice?
Thanks
Paul

---

### Post by ElemonGW on 2007-08-07
Damn, [more problems]("http://forums.opencompositing.org/viewtopic.php?f=12&t=1776"). The current versions will not work at all. Stay tuned for next release...

---

### Post by ElemonGW on 2007-08-07
> **ElemonGW said:**
> **The current version doesn't work as it should [...]**

Well, how should I begin?!?! It seems that this was my pc's problem and nothing was wrong with the script ;) . Anyway, after fixing my pc and re-installing Compiz Fusion I noticed that one more problem exists with the latest Compiz Fusion 's revisions (more @ my previous post) (thanks fly to bernardo for pointing the solution @ the thread I posted previously). So, after fixing that and removing the tags from dialogs (optional, required etc.) (most were not correct anyway :) ) a new version is here. I can't find any bugs write now. Now I start collecting problems. You may report the problem you have here, with all the required informations (CF Installer-Updater version, when you build Compiz Fusion, your OS, your DM etc.) and with no wining etc. Otherwise they will be ignored. Also, you may want to start your post by writing the word problem with bold. Also, please triple-check if the solution has already be posted before. Why I want all these??? First I don't have enough time. Second, you can't imagine how much spam I receive with questions for my script, providing me no information. That's all for now.

**PS: To grab the latest release, you may go to my website because I haven't updated the first post (I might update it tomorrow).**

---

### Post by ElemonGW on 2007-08-07
> **Ub1476 said:**
> Hey, I get this when installing:

```
kasper@FeistyFawn:~$ sh /home/kasper/Compiz_Fusion/CFInstaller-Updater.sh
This script is targeted to Ubuntu and it may also work to other Debian-based distros.
Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).
Do you want to install Compiz Fusion or update it?(i/u)u
Welcome to Compiz Fusion Update Script.
cd: 262: can't cd to /home/kasper/compiz/bcop
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update bcop?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/ccsm
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update ccsm?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/compiz
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update compiz?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/compizconfig-python
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update compizconfig-python?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/emerald
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update emerald?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/emerald-themes
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update emerald-themes?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/fusion-icon
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update fusion-icon?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/libcompizconfig
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update libcompizconfig?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-extra
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-extra?(y/n)y 
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-main
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-main?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
cd: 262: can't cd to /home/kasper/compiz/plugins-unsupported
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: git-pull: not found
Would you like to update plugins-unsupported?(y/n)y
/home/kasper/Compiz_Fusion/CFInstaller-Updater.sh: 262: ./autogen.sh: not found
Created by ElemonGW. For more visit http://elemongw.awardspace.com/

```

What's wrong? I got both files located in home/user/Compiz_Fusion.. Btw, you need to remove the space between CF and Installer-Updater.sh:p

The wrong thing is that you chose to update it and not to install it :P . Also, I there is no space between CF and Installer-Updater because of restrictions of allowed characters at the place I host the files.

---

### Post by Digitallysick on 2007-08-07
im having problem trying to update

CF Installer-Updater.

Targeted to Ubuntu, may also work in other Debian-based distros.

Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).

Warning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).

Do you use Gnome or KDE?(g/k):g

Do you want to (un)install Compiz Fusion or update it?(i/u):u
cd: 676: can't cd to /home/adam/compiz/compiz
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion?(y/n):




then it just gives me the same error "fatal not a git repository"

---

### Post by rainwalker on 2007-08-07
Okay, so if I understand this correctly:
1. It will uninstall the Compiz Fusion I installed following the guide at [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
2. It doesn't use Trevino's repo
3. I need to uninstall Beryl before I run it

Am I right?

---

### Post by Frak on 2007-08-07
Exept for the Beryl part, your right.

---

### Post by Oen386 on 2007-08-08
> **ElemonGW said:**
> [CENTER]***_I will update this post soon, until then you may visit its homepage (scroll down to the end of the post to find it) (btw., If you experience any problems accessing its homepage and my site in general, I would be really glad if you contact me and report it)._***

It isn't working. Please post the script here, I hate jumping through hoops like going to another website, finding the download section, finding the script, making sure it is the right one etc...

Can't you just post it here, or direct link. Instead of "go to my homepage"?

Thanks.

---

### Post by Frak on 2007-08-08
[http://elemongw.googlepages.com/fusion-install.sh](http://elemongw.googlepages.com/fusion-install.sh)
He has a link on the first page of this thread with a direct link to the script. i.e. the one above.

---

### Post by ElemonGW on 2007-08-08
> **Digitallysick said:**
> im having problem trying to update

CF Installer-Updater.

Targeted to Ubuntu, may also work in other Debian-based distros.

Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).

Warning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).

Do you use Gnome or KDE?(g/k):g

Do you want to (un)install Compiz Fusion or update it?(i/u):u
cd: 676: can't cd to /home/adam/compiz/compiz
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion?(y/n):




then it just gives me the same error "fatal not a git repository"

So, you have already installed Compiz Fusion with this script and now you can't update? If yes, then you probably deleted the compiz folder which was created at your home directory. If you installed Compiz Fusion with another way and now you just want to update it, then I have to inform you that this is not possible. You have to install Compiz Fusion again with this way.

> **rainwalker said:**
> Okay, so if I understand this correctly:
1. It will uninstall the Compiz Fusion I installed following the guide at [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
2. It doesn't use Trevino's repo
3. I need to uninstall Beryl before I run it

Am I right?

Completely right ;) .

> **Frak said:**
> Exept for the Beryl part, your right.

No, the newer versions also remove Beryl, because it could conflict with Compiz Fusion.

> **Oen386 said:**
> It isn't working. Please post the script here, I hate jumping through hoops like going to another website, finding the download section, finding the script, making sure it is the right one etc...

Can't you just post it here, or direct link. Instead of "go to my homepage"?

Thanks.

Well, is it so hard for you to go to the link that I posted at the first post?? The link sends you immediately to the page from where you can download the latest version of Compiz Fusion. Anyway, I will update the first post, I just haven't yet found the time to do it.

> **Frak said:**
> [http://elemongw.googlepages.com/fusion-install.sh](http://elemongw.googlepages.com/fusion-install.sh)
He has a link on the first page of this thread with a direct link to the script. i.e. the one above.

This is an older version ;)

---

### Post by ElemonGW on 2007-08-08
I was wondering, if you are happy with the current collection of plugins.... I told you at the past that with version 2 more plugins for Compiz Fusion were about to come... However, I didn't did that. Why? Because new plugins are constantly added at the main etc. packages so it could cause problems if I did so. However, I was wondering which is your opinion to that. I may create a poll to have clearest results...

---

### Post by ElemonGW on 2007-08-08
One more thing. It seems that my current hoster is... hrm.... anyway. So my homepage is currently down. I had a bad filing on this last night :( . Anyway, I hope that after a few hours (?) it will back up within no problems....
PS: The download links are valid, as the files were hosted elsewhere.

---

### Post by ben55 on 2007-08-08
Hi. I need a little help. i am new to Linux. Since last night. Please be gentle if this is a "n00b" question.
Anyway. I ran the script. Everything goes fine up until this:

```
Did you get a message about gitfm?(y/n)n
Continuing...
Installing Compiz...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: running: /usr/bin/autoconf
configure.ac:39: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:192: error: possibly undefined macro: AM_GCONF_SOURCE_2
autoreconf: /usr/bin/autoconf failed with exit status: 1
Would you like to continue? (Press enter to continue or close the window to stop (this is probably what you want if any errors occured).
```

I didn't see any message about gitfm (i don't even know what to look for) so i said No.
Also, earlier on i pressed No to KDE.
I am using the fglrx driver on an ATI Radeon X700. I have updated to the latest driver using Envy.
Any idea what the problem is??

Thanks.

---

### Post by Ub1476 on 2007-08-08
[B]checking for COMPIZ... configure: error: Package requirements (compiz) were not met:

No package 'compiz' found[/B]

What to do?

---

### Post by Oen386 on 2007-08-08
> **Frak said:**
> [http://elemongw.googlepages.com/fusion-install.sh](http://elemongw.googlepages.com/fusion-install.sh)
He has a link on the first page of this thread with a direct link to the script. i.e. the one above.

That is the older one? So where is the valid link to the newest since the site is down?

---

### Post by ElemonGW on 2007-08-08
> **Oen386 said:**
> That is the older one? So where is the valid link to the newest since the site is down?

It is up and running now. Here is the link anyway: [http://elemongw.googlepages.com/CF_Installer-Updater_v.2_rev.1.sh]("http://elemongw.googlepages.com/CF_Installer-Updater_v.2_rev.1.sh")

---

### Post by ElemonGW on 2007-08-08
[B]With the newest version, CF Installer-Updater will install libx11 with xcb support, as it is required by Compiz Fusion 's latest revisions. Here is a warning, stated by Jupiter at Compiz Fusion's forums:
[I]libX11 is a core system library, and replacing
it with an xcb-enabled version may lead to any number of problems such
as breaking java.[/I]
I had no problems installing it with xcb support, but as I found it I wanted to share it with you, so that you will be warned in case of any problems.[/B]

---

### Post by ben55 on 2007-08-08
No worries about my problem guys.
I just reformatted and followed this tutorial:
[How To : Compiz Fusion for ATI cards + Xgl in Feisty]("http://ubuntuforums.org/showthread.php?t=488385")

All running fine now. :D

---

### Post by Stealth on 2007-08-08
I'm getting this error:

> 
checking for XPROTO... configure: error: Package requirements (xproto >= 7.0.6) were not met:
No package 'xproto' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XPROTO_CFLAGS
and XPROTO_LIBS to avoid the need to call pkg-config.

See the pkg-config man page for more details.

make: *** [build-stamp] Error 1
dpkg: status database area is locked by another process
rm: cannot remove `libx11*deb': No such file or directory
rm: cannot remove `libX11-1.1.3/obj-i486-linux-gnu/config.log': Permission denied
rm: cannot remove `libX11-1.1.3/obj-i486-linux-gnu/libtool': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/genscripts': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/prepare': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patches/.version': Permission denied
rm: cannot remove directory `libX11-1.1.3/stampdir/log': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patch': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/stampdir': Permission denied



and continuing is just spitting out a bunch of other stuff about unmet dependencies or something. :(

---

### Post by ElemonGW on 2007-08-08
> **Stealth said:**
> I'm getting this error:



and continuing is just spitting out a bunch of other stuff about unmet dependencies or something. :(

You didn't provided the informations that I have asked for for any problem you encounter (distro etc.). Anyway, download and install [this]("http://xorg.freedesktop.org/releases/individual/proto/xproto-7.0.10.tar.bz2") and tell me if it doesn't solve your problem.

---

### Post by rainwalker on 2007-08-08
So what are the advantages of using this script over waiting for Trevino to update his repo?

---

### Post by isaacj87 on 2007-08-08
Well, besides the fact that Trevino is supposedly on vacation...you're receiving the the latest and greatest version of compiz fusion. Whereas with Trevino we have to wait till he puts up new debs in order to receive an update.

Anywho, I have a question as well, the script is running fine, but it doesn't seem to properly install libx11-xcb because when it tries to install compiz it can't (says it's missing that dependency)

Can you tell me where I can find it to compile and install myself?

---

### Post by ElemonGW on 2007-08-08
> **rainwalker said:**
> So what are the advantages of using this script over waiting for Trevino to update his repo?

Already stated...

---

### Post by ElemonGW on 2007-08-08
> **isaacj87 said:**
> Well, besides the fact that Trevino is supposedly on vacation...you're receiving the the latest and greatest version of compiz fusion. Whereas with Trevino we have to wait till he puts up new debs in order to receive an update.

Anywho, I have a question as well, the script is running fine, but it doesn't seem to properly install libx11-xcb because when it tries to install compiz it can't (says it's missing that dependency)

Can you tell me where I can find it to compile and install myself?

[http://forums.opencompositing.org/viewtopic.php?f=12&t=1776&st=0&sk=t&sd=a#p11969](http://forums.opencompositing.org/viewtopic.php?f=12&t=1776&st=0&sk=t&sd=a#p11969)

---

### Post by celafon on 2007-08-08
Cool that you have taken time to incorporate this in a script. I have one sugestion: add a variable for the directory you are working in (i.e. ~/compiz). Some may prefer to use different one.

Also I thought that while most of the commands are repeated wouldnt it be easier to create a loop that executes some sort of array of commands? Just a thought.

Thanks,
Bartek

---

### Post by Frak on 2007-08-08
> **rainwalker said:**
> So what are the advantages of using this script over waiting for Trevino to update his repo?
Bleeding Edge. Right now, no having to wait.

---

### Post by st33med on 2007-08-09
Now, I reinstalled CF with the current script. However, I switched the windows manager to compiz, but it gave me an error message:
```
andrew@andrew-laptop:~$ fusion-icon
* Using the GTK Interface
ini init, size 0
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Intel found, exporting: INTEL_BATCH=1
* No GLX_EXT_texture_from_pixmap present with direct rendering context
... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* Executing: LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp --indirect-rendering
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
  File "/usr/share/fusion-icon/interface_gtk.py", line 22, in <module>
    from libfusionicon import *
  File "/usr/share/fusion-icon/libfusionicon.py", line 339, in <module>
    start_wm()
  File "/usr/share/fusion-icon/libfusionicon.py", line 163, in start_wm
    start_compiz()
  File "/usr/share/fusion-icon/libfusionicon.py", line 183, in start_compiz
    subprocess.Popen(compiz_command)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```
What is happening?

EDIT: Oh, yeah. Running Ubuntu Feisty 7.04 on a Dell Inspiron E1505 with an Intel 945GM integrated card.

---

### Post by dwegner on 2007-08-09
Running GNOME and Fesity 7.04 on a GeForce FX5200 and everything went very smoothly. Script took a long time to process but everything seems to be working.

Well done!

---

### Post by Dark Star on 2007-08-09
Will try this. .Thanks :) Nice work :)

---

### Post by adam_r on 2007-08-09
if i have compiz fusion installed and updating from synaptic you reccommend to remove it and reinstall it with your script?

---

### Post by Frak on 2007-08-09
Compilations are slightly faster, but if you don't want to mess with cryptic error messages (if and when they do happen), then you should stay with the Debian version, but this one is up to date and bleeding edge.

---

### Post by Oen386 on 2007-08-09
Error:

```
checking pkg-config is at least version 0.9.0... yes
checking for LIBXSLT... configure: error: Package requirements (libxslt) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXSLT_CFLAGS
and LIBXSLT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Would you like to install the Settings Library for Plugins?(y/n):y

```

```
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

```

checking pkg-config is at least version 0.9.0... yes
checking for EMERALD... configure: error: Package requirements ( xrender >= 0.8.4                   gtk+-2.0 >= 2.8.0               libwnck-1.0                 libdecoration                    pangocairo) were not met:

No package 'libdecoration' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMERALD_CFLAGS
and EMERALD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by ElemonGW on 2007-08-09
> **Oen386 said:**
> Error:

```
checking pkg-config is at least version 0.9.0... yes
checking for LIBXSLT... configure: error: Package requirements (libxslt) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXSLT_CFLAGS
and LIBXSLT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Would you like to install the Settings Library for Plugins?(y/n):y

```

```
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

```

checking pkg-config is at least version 0.9.0... yes
checking for EMERALD... configure: error: Package requirements ( xrender >= 0.8.4                   gtk+-2.0 >= 2.8.0               libwnck-1.0                 libdecoration                    pangocairo) were not met:

No package 'libdecoration' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMERALD_CFLAGS
and EMERALD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Install the package libxslt (including the development kit). You may also need to install the package libdecoration...

---

### Post by ElemonGW on 2007-08-10
> **celafon said:**
> I have one sugestion: add a variable for the directory you are working in (i.e. ~/compiz). Some may prefer to use different one.

That's a good idea. I had never thought that ;) .

> **celafon said:**
> Also I thought that while most of the commands are repeated wouldnt it be easier to create a loop that executes some sort of array of commands? Just a thought.

And finally somebody makes that question. I waited for it since the day that I released version 2. It is not exactly that most of the commands are repeated. Until the middle everything is as it should. However, after that, everything is repeated with some minor changes. These minor changes are to make it work under KDE. This was caused after the merge of the KDE and Gnome scripts. The fact is, that this is not one of my priorities, as it doesn 't heart anything (the size is quite small, and there is not any other disadvantage with the way that it is right now.
Btw., are you sure it can be done with loops???

---

### Post by Oen386 on 2007-08-10
Why do I get compiz not found error to? Do I need to install that also separately?

---

### Post by ElemonGW on 2007-08-10
> **Oen386 said:**
> Why do I get compiz not found error to? Do I need to install that also separately?

Because you do something wrong or something goes wrong. When you report a problem (like now) be sure to provide more information in order to be helped. Also, please make sure that you press the y button when you want to answer yes at the question that the script makes, and not just press enter (even if it is referred within the script, lots of ***** (I don't want to say the word, also sorry to be "rude" but I have told that thousands of times) keep on pressing enter and not answering the question, so the script skips that step).

---

### Post by maduranga on 2007-08-10
i think i got it installed. can someone tell me how to run Compiz Fusion????????????

---

### Post by eagzor on 2007-08-10
is it possible for you to alter the CF installer script to implement a choice weather i have x86 or amd64, making it to compile with for example --march=amd64?

---

### Post by Frak on 2007-08-10
> **eagzor said:**
> is it possible for you to alter the CF installer script to implement a choice weather i have x86 or amd64, making it to compile with for example --march=amd64?
the compiler will compile to whatever the Kernel says your arch is.
i.e., if you installed for x86, gcc will compiler will compile for x86, x86_64 for x86_64, etc.
But you can create a dchroot environment to compile for a different arch.

---

### Post by Oen386 on 2007-08-10
> **ElemonGW said:**
> Install the package libxslt (including the development kit). You may also need to install the package libdecoration...

```
sudo apt-get install libxslt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxslt

```

---

### Post by ElemonGW on 2007-08-10
> **Oen386 said:**
> ```
sudo apt-get install libxslt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxslt

```

Well you could at least take the time to look at synaptic, to find out that the packages 's name has also the version number in its name. So, what you must run is
```
sudo apt-get install libxslt1.1 libxslt1-dev
```.

---

### Post by maduranga on 2007-08-10
I tried your script on my newly installed ubuntu installation after trying the .deb installation mentioned in some other guide in ubuntuforums. i thought i have completely removed packages that are installed by the guide I have followed before. Anyway, after running your script, i didn't able to run compiz fusion by clicking on the compiz-icon or by giving the command "compiz --replace" anyway, i just reinstalled ubuntu and then installed Nvidia. after that i just installed Compiz Fusion and now it is working fine...  okk.... thanks.. great job....!!!!


----Maduranga----

---

### Post by Oen386 on 2007-08-10
Nice!

Finally.. it was all probably because of that one package. :(

---

### Post by Stealth on 2007-08-10
> **ElemonGW said:**
> You didn't provided the informations that I have asked for for any problem you encounter (distro etc.). Anyway, download and install [this]("http://xorg.freedesktop.org/releases/individual/proto/xproto-7.0.10.tar.bz2") and tell me if it doesn't solve your problem.

Sorry 'bout that. I am running Ubuntu Feisty, on a laptop with a GeforceGo 6800 and an Intel Pentium M. Is taht the info you need? Currently running off the Trevino packages.

I installed the package (./conifgure && make && sudo make install) but I still get the error:

> checking for XPROTO... yes
checking for X11... configure: error: Package requirements (xextproto xtrans xcb-xlib >= 0.9.92) were not met:

No package 'xextproto' found
No package 'xtrans' found
No package 'xcb-xlib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** [build-stamp] Error 1
dpkg: error processing libx11*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libx11*deb
rm: cannot remove `libx11*deb': No such file or directory
rm: cannot remove `libX11-1.1.3/obj-i486-linux-gnu/config.log': Permission denied
rm: cannot remove `libX11-1.1.3/obj-i486-linux-gnu/libtool': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/genscripts': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/prepare': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patches/.version': Permission denied
rm: cannot remove directory `libX11-1.1.3/stampdir/log': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patch': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/stampdir': Permission denied


After that, it'll ask if I have any KDE packages installed. I have K3B, does that count? I ctrl-c right after I get the above error, but was just wondering about that option once this works...

---

### Post by st33med on 2007-08-10
> **st33med said:**
> Now, I reinstalled CF with the current script. However, I switched the windows manager to compiz, but it gave me an error message:
```
andrew@andrew-laptop:~$ fusion-icon
* Using the GTK Interface
ini init, size 0
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Intel found, exporting: INTEL_BATCH=1
* No GLX_EXT_texture_from_pixmap present with direct rendering context
... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* Executing: LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp --indirect-rendering
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
  File "/usr/share/fusion-icon/interface_gtk.py", line 22, in <module>
    from libfusionicon import *
  File "/usr/share/fusion-icon/libfusionicon.py", line 339, in <module>
    start_wm()
  File "/usr/share/fusion-icon/libfusionicon.py", line 163, in start_wm
    start_compiz()
  File "/usr/share/fusion-icon/libfusionicon.py", line 183, in start_compiz
    subprocess.Popen(compiz_command)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```
What is happening?

EDIT: Oh, yeah. Running Ubuntu Feisty 7.04 on a Dell Inspiron E1505 with an Intel 945GM integrated card.

More problems. 
If I highlight text in Firefox and drag it somewhere inside Firefox, it crashes, not just Firefox itself, but everything. I have to do a hard shutdown.
My taskbars, scrollbars, highlights, and other stuff still has my Metacity theme.

---

### Post by maduranga on 2007-08-11
I got CF installed successfully. But now I see some files in my home folder. Are these files needed for future activities? If yes, are there any method to hide them or something like that to keep my home folder clean? 

And my other question is, are there any method to change the image on the desktop cube? (images in the top and the bottom of the cube?) thanks

---

### Post by Gifty85 on 2007-08-11
Hi guys!

I ran the script and now there's no windows borders. I also cannot run ccsm and there's no compiz icon too.

This is the output I get when i tried to run ccsm:

```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig
```

I'm running Gutsy! :rolleyes:

Should I run the script again?

Btw, i'm using a nvidia card.

Edit: I ran the script again and i notice this:

```
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Frak on 2007-08-11
@Gifty85
```
sudo aptitude install compiz-dev
```
That should fix it.

---

### Post by Gifty85 on 2007-08-11
> **Frak said:**
> @Gifty85
```
sudo aptitude install compiz-dev
```
That should fix it.

It didn't work... :(

---

### Post by Frak on 2007-08-11
I also tried it, not only did it not let me choose KDE modules (script error), but I was getting errors for
```
No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

And errors like the above, exept about libdecorations. Oh well, doing it the manual way never hurt anybody :)
[http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion](http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion) for anybody wanting to manually compile it.

---

### Post by ElemonGW on 2007-08-11
> **Frak said:**
> I also tried it, not only did it not let me choose KDE modules (script error), but I was getting errors for
```
No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

And errors like the above, exept about libdecorations. Oh well, doing it the manual way never hurt anybody :)
[http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion](http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion) for anybody wanting to manually compile it.

1. Script error? Where? How? Are you sure? I don't think so...
2. The guide where you point at no longer works, due to the recent major changes.
PS: Will answer to everybody else tomorrow, I am of to bed now ;) .

---

### Post by Frak on 2007-08-11
Where it says
```
echo ""
					read -p "Do you have any KDE packages installed?(y/n):" answer;
					if [ $answer = y ] ; then
```
I get a script error and it just goes installing KDE Packages.

---

### Post by ASPCartman on 2007-08-11
Do you want to (un)install Compiz Fusion or update it?(i/u):u
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 243: cd: /home/aspcartman/compiz/compiz: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion?(y/n):y
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 247: ./autogen.sh: No such file or directory
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 252: cd: /home/aspcartman/compiz/bcop: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion Option Code Generator?(y/n):



WTF? Im running compiz now..... :lolflag:

---

### Post by Happy_Man on 2007-08-11
> **maduranga said:**
> I got CF installed successfully. But now I see some files in my home folder. Are these files needed for future activities? If yes, are there any method to hide them or something like that to keep my home folder clean? 

And my other question is, are there any method to change the image on the desktop cube? (images in the top and the bottom of the cube?) thanks
If you are OK with the version of Fusion you have, delete the folders. But if you'd like to update every now and then, keep the folder so that you can.

---

### Post by ElemonGW on 2007-08-12
> **Frak said:**
> Where it says
```
echo ""
					read -p "Do you have any KDE packages installed?(y/n):" answer;
					if [ $answer = y ] ; then
```
I get a script error and it just goes installing KDE Packages.

When you say that you get a script error? What you answer at the question? What's the error that it gives you?

> **ASPCartman said:**
> Do you want to (un)install Compiz Fusion or update it?(i/u):u
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 243: cd: /home/aspcartman/compiz/compiz: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion?(y/n):y
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 247: ./autogen.sh: No such file or directory
/home/aspcartman/Desktop/CF_Installer-Updater_v.2_rev.1.sh: line 252: cd: /home/aspcartman/compiz/bcop: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion Option Code Generator?(y/n):



WTF? Im running compiz now..... :lolflag:

Even if you already have Compiz Fusion installed with another way (from deb packages or anything else) you should again install it using this script. All the previous version will automatically be rermoved.

> **Happy_Man said:**
> If you are OK with the version of Fusion you have, delete the folders. But if you'd like to update every now and then, keep the folder so that you can.

Exactly! Just a note, you 'ld better keep them, in the next version I will change the place where the files are downloaded. They will be downloaded in another folder, which will be hidden. So you will just need to rename the folder and it will be hidden + you will not need to manually do any changes to the script. (I don't know if you understand what I wrote here, I couldn't express it very clear, just don't delete the files and w8 for the next version ;) ).

> **st33med said:**
> More problems. 
If I highlight text in Firefox and drag it somewhere inside Firefox, it crashes, not just Firefox itself, but everything. I have to do a hard shutdown.
My taskbars, scrollbars, highlights, and other stuff still has my Metacity theme.

You may wanna try running
```
You LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp
```
in terminal. See if it works and CF runs as it should and tell me.

> **Gifty85 said:**
> Hi guys!

I ran the script and now there's no windows borders. I also cannot run ccsm and there's no compiz icon too.

This is the output I get when i tried to run ccsm:

```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig
```

I'm running Gutsy! :rolleyes:

Should I run the script again?

Btw, i'm using a nvidia card.

Edit: I ran the script again and i notice this:

```
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Something wrong went through the installation and compiz was not installed at all. Re-run the installation script and make sure you answer what you should at the questions. Also, watch for errors and post them here.

> **Stealth said:**
> Sorry 'bout that. I am running Ubuntu Feisty, on a laptop with a GeforceGo 6800 and an Intel Pentium M. Is taht the info you need? Currently running off the Trevino packages.

I installed the package (./conifgure && make && sudo make install) but I still get the error:



After that, it'll ask if I have any KDE packages installed. I have K3B, does that count? I ctrl-c right after I get the above error, but was just wondering about that option once this works...

1. Just keep on installing the required dependencies. Search for them at Synaptic and, if you don't find them there, then google them. When you manage to satisfy all the dependencies, please tell me which they where so I can add them to CF Installer-Updater.
2. In order to have K3B installed you need some KDE core libraries so, yes, it counts.

---

### Post by Gifty85 on 2007-08-12
I answered 'yes' to the question "Do you have any KDE packages installed?(y/n):" and now I don't get the error saying compiz package is not found and it seams to be working perfectly! ;)

Thanks for the support.

---

### Post by rausuar on 2007-08-12
Hi have tried the script, but i keep getting the error: 

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I am using Ubuntu 7.04, Gnome, and not using Nvidia card.  Thanks for any help...

---

### Post by Frak on 2007-08-12
> **ElemonGW said:**
> When you say that you get a script error? What you answer at the question? What's the error that it gives you?

I reinstalled Ubuntu, again for various reasons, but if I get it again I'll try to get it. Last time I couldn't because the terminal randomly cleared every 5 minutes and kept compiling.
But, as I recall, it output something like "script error, (some text) not defined"

---

### Post by maduranga on 2007-08-13
I answered no when it ask about kde packages. but now I can see some new apps (Konsole, KSysGuard) in my menu. do i need to keep those packages? if no, can someone tell me how to find all of those kde packages and remove? is there any easy method or can someone at least give me the list of kde packages the script install?

---

### Post by st33med on 2007-08-13
> **ElemonGW said:**
> 
You may wanna try running
```
You LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp
```
in terminal. See if it works and CF runs as it should and tell me.

Right now, I'm away from my computer.  That is the way I usually run compiz (except without the 'You'... was I supposed to put that in there?). I also left out that my window borders appear with the Emerald theme I selected, but nothing else follows the theme. Example? My Emerald theme is a glassy theme. The border looks like glass, however, my scrollbar still has the purple bar from my Metacity theme.

---

### Post by Happy_Man on 2007-08-13
Yes, that is normal. Emerald only changes the outside of the window, not what is in it. To change scrollbars, highlight colors, and such, you need to go into System --> Preferences --> Theme and change it manually.

---

### Post by dysonsphere23 on 2007-08-13
Thanks for the script.

A problem I am getting is that there are no window borders.

I get the following messages during the install:

No package 'xcb-xlib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** [build-stamp] Error 1
dpkg: error processing libx11*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libx11*deb
rm: cannot remove `libx11*deb': No such file or directory

Package libxslt was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxslt.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxslt', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CCS_CFLAGS
and CCS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Package libxslt was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxslt.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxslt', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Package libxslt was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxslt.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxslt', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Package libxslt was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxslt.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxslt', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.  

Perhaps there is something there that will fix it?

Thanks

---

### Post by petit.padavoine on 2007-08-13
Everything compiles and works fine except for all the compiz fusion plugins, which is kinda annoying...
When running the configure script for the plugins, it checks for BCOP, and tells me I have too old a version of BCOP...
I tried sudo apt-get install bcop, which told me that bcop was deprecated and now called compiz-bcop, so I tried sudo apt-get install compiz-bcop, ran the script again, but it still gave me the same error when checking for BCOP.

EDIT: I removed Trevino's reps from my sources.list and then it worked...

---

### Post by dysonsphere23 on 2007-08-13
Quick question:

Should I uninstall the current "desktop effects" with the package manager or should that be installed before running the script?

---

### Post by glope on 2007-08-13
I have the same problem as dysonsphere described above. When i install Compiz Fusion as part of the Gnome install process i get the following error

checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found
No package 'libxslt' found

Now i know i could install some of these manually and see if that fixes it but have i missed something critical and obvious that just needs to be selected on the install?

Any idea's on what i need to do?

Thanks
Myles

---

### Post by Frak on 2007-08-13
Just a suggestion, but instead of installing all of the dependencies seperately, (well exept for git-core, automake, build-essential, intltool, libtool, python-pyrex, and python2.5-dev).
Why don't you just build-dep compiz to install all of the needed dependencies. And then just ask otherwise whether or not they are using Ubuntu or Kubuntu?
This may not be that clear, but its an idea.

EDIT
Also, versions past 0.5.2 don't currently work with Feisty Fawn.

---

### Post by st33med on 2007-08-13
Thanks, Happy_Man! Once I get back, I shall change my Metacity theme to match.

And, I have also considered that the Firefox crash I described might be a new bug I discovered. Could someone try to highlight text in Firefox and click and drag it inside the window?

I still can't get fusion-icon to launch, but, as long as I can get compiz-fusion started up at login, it's no hair off my back.

(Wait, what hair:confused:)

---

### Post by Ubumby on 2007-08-13
I am having the same problem petit.padavoine had. My BCOP is 0.1.4 and I tried removing trevinos reps but it still does not want to update. should I just reinstall it? :confused:

---

### Post by zakalwe_ukuk on 2007-08-14
So did anyone figure out how to get the settings manager working?

---

### Post by jk_warrior on 2007-08-14
> **glope said:**
> I have the same problem as dysonsphere described above. When i install Compiz Fusion as part of the Gnome install process i get the following error

checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found
No package 'libxslt' found

Now i know i could install some of these manually and see if that fixes it but have i missed something critical and obvious that just needs to be selected on the install?

Any idea's on what i need to do?

Thanks
Myles

This is exactly the error I'm getting. I suppose something is wrong with the script. I hope the TS can fix it soon.

---

### Post by dmacdonald111 on 2007-08-14
I get the following error after choosing gnome and then update;

CF_Installer-Updater_v.2_rev.1.sh: line 243: cd: /home/me/compiz/compiz: No such file or directory
fatal: Not a git repository

It still asks me if I would like to update compiz, but don´t particularly want to incase something goes wrong. Would appreciate the help. TIA

---

### Post by chiinox on 2007-08-14
in CCSM under the "Extras" a buddy says he has a ScreenSaver plugin I think he used Trevinos repos.  Any idea how to get that?  What does the do?

Thanks

---

### Post by Frak on 2007-08-14
Add this to your /etc/apt/sources.list if you have a 32 bit processor.
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Or if your 64 bit.

```
# Treviño&#8217;s Ubuntu Deisty EyeCandy Repository (GPG key: 81836EBF)
# Many eyecandy 3D apps: Beryl, Compiz, Fusion, AWN and kiba-dock
# built by jbs using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
```

Then

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Next

```
sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
```
```
sudo apt-get install compizconfig-settings-manager # libcompizconfig-backends-* ?!
```
```
sudo apt-get install compiz-fusion-*
```
```
compiz --replace
```

Taken from [Compiz-Fusion.org]("http://forum.compiz-fusion.org/showthread.php?t=1012")

---

### Post by dweez on 2007-08-14
Check out this post in this thread to see what the installer developer said regarding this error.

[http://ubuntuforums.org/showpost.php?p=3176148&postcount=214](http://ubuntuforums.org/showpost.php?p=3176148&postcount=214)

I was having the same issue.  Selecting to install seems to have resolved it (halfway through the install now with now errors).

---

### Post by TheOtherLinuxFreak on 2007-08-14
sweet script! I couldn't get compiz-fusion working before I used it. Now even emerald works. thanks!

---

### Post by ElemonGW on 2007-08-14
> **Frak said:**
> Add this to your /etc/apt/sources.list if you have a 32 bit processor.[..]

Doing that he will install Compiz Fusion through Trevino 's repo, which i believe that it is something that he doesn't want (as he used that script). So, just wait for the next version (i don't know when it will come), i will add the ability to install lots of other plugins

---

### Post by chiinox on 2007-08-14
> **ElemonGW said:**
> Doing that he will install Compiz Fusion through Trevino 's repo, which i believe that it is something that he doesn't want (as he used that script). So, just wait for the next version (i don't know when it will come), i will add the ability to install lots of other plugins

Yes you are right, I did have trouble using Trevinos Repo's and this script has worked good.  Just wanted the extra plug-ins with out Trevinos.  Thanks ElemonGW, I am patient will wait till the other plug-ins are included.

---

### Post by dmacdonald111 on 2007-08-14
> **dweez said:**
> Check out this post in this thread to see what the installer developer said regarding this error.

[http://ubuntuforums.org/showpost.php?p=3176148&postcount=214](http://ubuntuforums.org/showpost.php?p=3176148&postcount=214)

I was having the same issue.  Selecting to install seems to have resolved it (halfway through the install now with now errors).

Thanks. Using that worked a charm! This has to be the best utility ever!

---

### Post by GokuH12 on 2007-08-14
hi, i have a big problm here :S, hope u can help me a litle, btw, great job with the script :D
well, when i'm compiling the compiz part i get this error

```
/lib/libkdecorations.so -ldbus-qt-1
decorator.o: In function `KWinInterface':
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~Decorator':
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
decorator.o:/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: more undefined references to `vtable for KWD::Decorator' follow
decorator.o: In function `~KWinInterface':
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `~Decorator':
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/gokuh/compiz/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
window.o: In function `Window':
/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
window.o: In function `~Window':
/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:132: undefined reference to `vtable for KWD::Window'
/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:132: undefined reference to `vtable for KWD::Window'
window.o:/home/gokuh/compiz/compiz/kde/window-decorator/window.cpp:132: more undefined references to `vtable for KWD::Window' follow
collect2: ld returned 1 exit status
make[3]: *** [kde-window-decorator] Error 1
make[3]: se sale del directorio `/home/gokuh/compiz/compiz/kde/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/gokuh/compiz/compiz/kde'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/gokuh/compiz/compiz'
make: *** [all] Error 2


```

i dont have idea of what i am missing :S, i tried installed a lot of dev packages but no one seem to do the job, im using kubuntu gutsy 64, i googled  too but whit out luck :(

---

### Post by techstop on 2007-08-14
I am getting lots of errors, this one in particular;

```
patching file src/xlibi18n/Makefile.in
patching file src/Makefile.in
patching file mkinstalldirs
if ! [ `which quilt` ]; then \
                echo "Couldn't find quilt. Please install it or add it to the build-depends for this package."; \
                exit 1; \
        fi; \
        if quilt --quiltrc /dev/null next >/dev/null 2>&1; then \
          echo -n "Applying patches..."; \
          if quilt --quiltrc /dev/null push -a -v >stampdir/log/patch 2>&1; then \
            cat stampdir/log/patch; \
            echo "successful."; \
          else \
            cat stampdir/log/patch; \
            echo "failed! (check stampdir/log/patch for details)"; \
            exit 1; \
          fi; \
        else \
          echo "No patches to apply"; \
        fi; \
        >stampdir/patch
No patches to apply
dh_testdir
make: dh_testdir: Command not found
make: *** [build-stamp] Error 127
dpkg: error processing libx11*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libx11*deb
rm: cannot remove `libx11*deb': No such file or directory
rm: cannot remove `libX11-1.1.3/stampdir/genscripts': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/stampdir': Permission denied
rm: cannot remove directory `libX11-1.1.3/stampdir/log': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patch': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patches/.version': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/prepare': Permission denied

Do you have any KDE packages installed?(y/n):
```

I did a sudo apt-get install quilt, but this error keeps coming up. Here are the rest of my errors from the start;

```
patching file mkinstalldirs
dh_testdir
make: dh_testdir: Command not found
make: *** [build-stamp] Error 127
dpkg: error processing libx11*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libx11*deb
rm: cannot remove `libx11*deb': No such file or directory
rm: cannot remove `libX11-1.1.3/stampdir/genscripts': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/stampdir': Permission denied
rm: cannot remove directory `libX11-1.1.3/stampdir/log': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patch': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patches/.version': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/prepare': Permission denied

Do you have any KDE packages installed?(y/n):

```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
```

Note: here is my sources.list;

```
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ feisty main restricted universe multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ feisty-updates main restricted universe multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ feisty-security main restricted universe multiverse
```

```
Would you like to install Compiz Fusion?(y/n):y
destination directory 'compiz' already exists.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:49: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL
metadata/Makefile.am:39: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:39: (probably a GNU make extension)
metadata/Makefile.am:42: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:43: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:43: (probably a GNU make extension)
autoreconf: automake failed with exit status: 1

```

```
checking for LIBXSLT... configure: error: Package requirements (libxslt) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXSLT_CFLAGS
and LIBXSLT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Would you like to install the Settings Library for Plugins?(y/n):
```

```
checking for COMPIZ... configure: error: Package requirements ("compiz") were not met:

No package 'compiz' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Would you like to install CompizConfig-Python?(y/n):

```

```
checking for CCS... configure: error: Package requirements (libcompizconfig >= 0.5.2 glib-2.0 >= 2.6 ) were not met:

No package 'libcompizconfig' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CCS_CFLAGS
and CCS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Would you like to install CompizConfig Settings Manager?(y/n):
```

And so on and so on....It seems lots of people are having this error, there is something wrong in the script...I have tried uninstalling and installing many times, the errors do not go away...Please help.

---

### Post by Ubumby on 2007-08-15
I re-ran the script and reinstalled compiz-fusion however I still get this BCOP error:

"Requested 'bcop >= 0.5.2' but version of bcop is 0.1.4

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BCOP_CFLAGS
and BCOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

---

### Post by icecoldmilk on 2007-08-15
thx so much for the great script!!!

everything works fine but the shift switcher and the Application Switcher,

everytime i hit Super+Tab the ring switcher comes up eventhough i disable the ring Swithcer. 

and when i hit Alt+Tab nothing happen while my Application Switcher is ticked!

any ideas how to fix this or make it to work!!?? :confused:

Shift Switcher is everything i WANTED! plz help^^:popcorn::popcorn:

---

### Post by baixinhu on 2007-08-15
ok just finished installing, i click on the icon and ... nothing happens, reeboot, click on the icon and :-D .... :confused: nothing happens :S 
what to do?

Now an GUI to make this just perfect :D ;)

---

### Post by baixinhu on 2007-08-15
ok this is my output from terminal : 

brito@britoPC:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
brito@britoPC:~$ 


what did i do wrong

---

### Post by icecoldmilk on 2007-08-15
> **icecoldmilk said:**
> thx so much for the great script!!!

everything works fine but the shift switcher and the Application Switcher,

everytime i hit Super+Tab the ring switcher comes up eventhough i disable the ring Swithcer. 

and when i hit Alt+Tab nothing happen while my Application Switcher is ticked!

any ideas how to fix this or make it to work!!?? :confused:

Shift Switcher is everything i WANTED! plz help^^:popcorn::popcorn:

WOOT!! got it fixed and Shift switcher is working hella good now 

Lovin' IT!!!

ps: FIXED by uninstall C.F. using this script and then Uninstalled the old one 

THEN install again using this COOL script!!! :popcorn::popcorn::popcorn:

---

### Post by icecoldmilk on 2007-08-15
> **baixinhu said:**
> ok just finished installing, i click on the icon and ... nothing happens, reeboot, click on the icon and :-D .... :confused: nothing happens :S 
what to do?

Now an GUI to make this just perfect :D ;)

u see the Compiz Fusion icon on the top right of ur panel?

RIght click it and reload window manager:lolflag:

---

### Post by maduranga on 2007-08-15
is dis a normal thing? i get those when I run the script. but CF works fine. 
[B]
rm: cannot remove `libx11*deb': No such file or directory
rm: cannot remove `libX11-1.1.3/stampdir/genscripts': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/stampdir': Permission denied
rm: cannot remove directory `libX11-1.1.3/stampdir/log': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patch': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/patches/.version': Permission denied
rm: cannot remove `libX11-1.1.3/stampdir/prepare': Permission denied[/B

same prob is described in #238 post. so i'm not gonna post all of my terminal output. any idea?

---

### Post by RideP2 on 2007-08-15
> **baixinhu said:**
> ok this is my output from terminal : 

brito@britoPC:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
brito@britoPC:~$ 


what did i do wrong

I'm getting the exact same problem.

---

### Post by midtown on 2007-08-15
Thanks, this worked very well and was really easy!

Though, it installed a whole bunch of KDE stuff for some reason, even though I selected that I was using Gnome.

---

### Post by CoreyDS on 2007-08-15
> **baixinhu said:**
> ok just finished installing, i click on the icon and ... nothing happens, reeboot, click on the icon and :-D .... :confused: nothing happens :S 
what to do?

Now an GUI to make this just perfect :D ;)

If you mean your going to Applications > System Tools > Compiz Fusion Icon, clicking that and nothing happens ...the same thing is happening with me. 

System > Preferences > Compiz Config Settings Manager does nothing as well.

---

### Post by st33med on 2007-08-15
> **techstop said:**
> I am getting lots of errors, this one in particular;

I did a sudo apt-get install quilt, but this error keeps coming up. Here are the rest of my errors from the start;

And so on and so on....It seems lots of people are having this error, there is something wrong in the script...I have tried uninstalling and installing many times, the errors do not go away...Please help.
Try sudoing it.
```
sudo sh /path/to/CF_Installer-Updater
```

---

### Post by Solvax on 2007-08-15
> **CoreyDS said:**
> If you mean your going to Applications > System Tools > Compiz Fusion Icon, clicking that and nothing happens ...the same thing is happening with me. 

System > Preferences > Compiz Config Settings Manager does nothing as well.

Echo :confused: I got the same problem.
I hope someone has a solution for this?

Greetings

~ Solvax

PS: this is what i get when trying to configure compiz fusion (i installed everything (which means i pressed Y each time except for the nvidia video card)
The compiz file is in my personal file and all files are there... (i guess) /home/christoph/compiz/...

[IMG]http://img529.imageshack.us/img529/4718/schermafdruklc6.png[/IMG]

---

### Post by Scotty562 on 2007-08-15
Mine isn't updating to the newly released stable release. Am I doing something wrong?

---

### Post by isaacj87 on 2007-08-15
WOW! 

I re-tried the script and it works perfectly for me now...thanks alot!

Now I'm going to see if the updating part works!

---

### Post by baixinhu on 2007-08-15
> **baixinhu said:**
> ok this is my output from terminal : 

brito@britoPC:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
brito@britoPC:~$ 


what did i do wrong

> **RideP2 said:**
> I'm getting the exact same problem.

can anyone help us with this problem?

---

### Post by baixinhu on 2007-08-15
> **CoreyDS said:**
> If you mean your going to Applications > System Tools > Compiz Fusion Icon, clicking that and nothing happens ...the same thing is happening with me. 

System > Preferences > Compiz Config Settings Manager does nothing as well.

try, in the terminal $ fusion-icon and se the output probably it will be the same i get :P

---

### Post by CoreyDS on 2007-08-15
I get this....

```
corey@corey-desktop:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

---

### Post by Solvax on 2007-08-15
this is what i get

```
christoph@Solvaxonline38a1:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named compizconfig
... Trying another interface
* Using the Qt3 Interface
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
RuntimeError: the qt and PyQt4.QtCore modules both wrap the QObject class
christoph@Solvaxonline38a1:~$ 

```

---

### Post by tekkenlord on 2007-08-15
Very nice script. However, I get the exact same error as Solvax.

Patrida, voitheia!!!

---

### Post by Solvax on 2007-08-16
It looks like me, CoreyDS, baixinhu and tekkenlord are having the same problem.
Probably other people too...
I hope anyone can bring some light in our mystery :)

Greetings

~ solvax

---

### Post by realvz on 2007-08-16
thankx for making this...its a great help:guitar:

---

### Post by RizSilverthorn on 2007-08-16
Same issue here on two separate systems (both AMD 64 running Ubuntu Fiesty i386) one 3800+ with AGP Geforce 6600, one 4800+ DC with PCI-Express 7950GT, both on nvidia chipset motherboards. But I uninstalled, re-installed using the script and they are both working.

The 3800+ took 3 attempts but is finally running as expected. I chose gnome at beginning, but said yes to KDE stuff on the last install. But then again I could have said no to KDE then it worked...

Short version - uninstall, and try alternate options when asking if you have KDE installed. Ohhh, a restart of X didn't help, had to do a full reboot. I thought I had left full-reboots (except when upgrading the kernel) behind when I switched to Linux.

---

### Post by Frak on 2007-08-16
Did you run compiz --replace ?
Also, I don't quite see how a reboot would help, it has nothing to do with your hardware or Kernel, so rebooting really isn't necessary.

---

### Post by RizSilverthorn on 2007-08-16
TBH, neither do I see how a reboot helped. All I know is that on the 3800+ what didn't work  did afterwards, so I thought it might help someone who had the same issues. Don't *think* I ran compize-replace, just hit the icon. Maybe I ought to stop using Ubuntu - I cut my teeth on Slackware '95 (in '96)and had fun getting X working on a Cirrus Logic graphics card. Maybe I should stick Debian or even  Gentoo on this box to get the old feeling of accomplishment back and stop being lazy...

---

### Post by CoreyDS on 2007-08-16
Yes to compiz --replace after install before clicking the icon...

Uninstalled / reinstalled but said no to KDE. It installed KDE packages. I ran the program and Compiz Fusion started up fine... except I have no window borders.

---

### Post by Solvax on 2007-08-16
yeh i got compiz working now aswell...
though my cssm doesn't work...
I get the following error:

```
christoph@Solvaxonline38a1:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : gconf
Integration : true
Profile     : default
Adding plugin svg (Svg)
Adding plugin png (Png)
Adding plugin minimize (Minimize Effect)
Adding plugin inotify (Inotify)
Adding plugin snap (Snapping Windows)
Adding plugin scaleaddon (Scale Addons)
Adding plugin expo (Expo)
Adding plugin animation (Animations)
Adding plugin screenshot (Screenshot)
Adding plugin fadedesktop (Fade to Desktop)
Adding plugin splash (Splash)
Adding plugin addhelper (ADD Helper)
Adding plugin clone (Clone Output)
Adding core settings (General Options)
Adding plugin dbus (Dbus)
Adding plugin extrawm (Extra WM Actions)
Adding plugin fade (Fading Windows)
Adding plugin water (Water Effect)
Adding plugin place (Place Windows)
Adding plugin mblur (Motion blur)
Adding plugin cubereflex (Cube Reflection)
Adding plugin resize (Resize Window)
Adding plugin ring (Ring Switcher)
Adding plugin group (Group and Tab Windows)
Adding plugin rotate (Rotate Cube)
Adding plugin switcher (Application Switcher)
Adding plugin fs (Userspace File System)
Adding plugin wobbly (Wobbly Windows)
Adding plugin regex (Regex Matching)
Adding plugin blur (Blur Windows)
Adding plugin neg (Negative)
Adding plugin zoom (Zoom Desktop)
Adding plugin bench (Benchmark)
Adding plugin crashhandler (Crash handler)
Adding plugin firepaint (Paint fire on the screen)
Adding plugin cube (Desktop Cube)
Adding plugin annotate (Annotate)
Adding plugin trailfocus (Trailfocus)
Adding plugin move (Move Window)
Adding plugin video (Video Playback)
Adding plugin opacify (Opacify)
Adding plugin showdesktop (Show desktop)
Adding plugin decoration (Window Decoration)
Adding plugin vpswitch (Viewport mouse switch)
Adding plugin imgjpeg (JPEG)
Adding plugin scale (Scale)
Adding plugin reflex (Reflection)
Adding plugin thumbnail (Window Previews)
Adding plugin put (Put)
Adding plugin text (Text)
Adding plugin wall (Desktop Wall)
Adding plugin winrules (Window Rules)
Adding plugin plane (Desktop Plane)
Adding plugin glib (GLib)
Adding plugin resizeinfo (Resize Info)
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 84, in __init__
    self.ResetMainWidgets()
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 178, in ResetMainWidgets
    self.BuildTable(pluginsVPort)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 230, in BuildTable
    pluginEnable.set_sensitive(self.Context.AutoSort)
AttributeError: 'compizconfig.Context' object has no attribute 'AutoSort'
christoph@Solvaxonline38a1:~$ 

```

---

### Post by Nigmah on 2007-08-16
[COLOR=DarkOrange]**installed 3 times couldn't get it to work, though now i have kde installed on ubuntu.**[/COLOR]

---

### Post by s_spiff on 2007-08-18
Got same error as a few others here. I'm on Fiesty AMD64 and 6150 onboard nvidia graphic card, which used to run beryl with no trouble at all. Heres the out put when i run compiz-fusion in the terminal ( as the menu icons don't work )
```
spiff@spiffed:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
spiff@spiffed:~$ 

```

---

### Post by Lordmarshal on 2007-08-18
when i do the compiz "--replace -c -emerald &" in terminal i end up getting this

josh@Reaper:~$ compiz --replace -c emerald &
[1] 6644
josh@Reaper:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'

im running ubuntu 7.04 with an nvidia graphics card. and this is the second time i have installed this CF installer thing. so if someone could help out that would be great.

---

### Post by tekkenlord on 2007-08-18
> **Lordmarshal said:**
> when i do the compiz "--replace -c -emerald &" in terminal i end up getting this

josh@Reaper:~$ compiz --replace -c emerald &
[1] 6644
josh@Reaper:~$ Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'

im running ubuntu 7.04 with an nvidia graphics card. and this is the second time i have installed this CF installer thing. so if someone could help out that would be great.

Are you sure you have installed emerald? If so, then try to run compiz --replace and then emerald --replace.

---

### Post by unimatrix on 2007-08-18
I got this strangest error:
> 
Installing compiz...

Executing make
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qjpunicode.h:82: warning: &#8216;class QJpUnicodeConv&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qpolygonscanner.h:48: warning: &#8216;class QPolygonScanner&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qsqldatabase.h:63: warning: &#8216;class QSqlDriverCreatorBase&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:224: warning: &#8216;class QXmlReader&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:407: warning: &#8216;class QXmlContentHandler&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:424: warning: &#8216;class QXmlErrorHandler&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:433: warning: &#8216;class QXmlDTDHandler&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:441: warning: &#8216;class QXmlEntityResolver&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:448: warning: &#8216;class QXmlLexicalHandler&#8217; has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:461: warning: &#8216;class QXmlDeclHandler&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: &#8216;class KDecorationProvides&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration_p.h:62: warning: &#8216;class KDecorationBridge&#8217; has virtual functions but non-virtual destructor
make[2]: *** No rule to make target `compiz-core.kcfg', needed by `compizrc'.  Stop.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2


Anyone has a clue to WTF that means? There is no such file as a 'compiz-core.kcfg' anywhere in the source.

---

### Post by isaacj87 on 2007-08-18
To the creator of the script or to anyone who knows about GIT:

Compiz Fusion installed correctly, and everything is working fine, but whenever I do an update...how do I know if it is *actually* updating?
If I say "yes", then it will compile and the say "Already up to date." And if I say "no", then sometimes it says either "Already up to date" or appears to be downloading something. Then I go back and say "yes" to the ones that appeared to be downloading something and it compiles and say "Already up to date." Seems like it isn't really updating??

---

### Post by isaacj87 on 2007-08-18
> **unimatrix said:**
> I got this strangest error:


Anyone has a clue to WTF that means? There is no such file as a 'compiz-core.kcfg' anywhere in the source.

Does it install okay...can you run Compiz-Fusion? I think those are errors for KDE...if you're using GNOME, I wouldn't worry about it.

---

### Post by unimatrix on 2007-08-18
Unfortunately it does not install OK. The compiz component fails to fully compile and then so do all the components that rely on it...
I'm running KDE though.
PS: I've edited my previous post - it includes exactly what the compilation does.

---

### Post by isaacj87 on 2007-08-18
I'm assuming that your chose "K" whenever the script asked you if you were using either GNOME or KDE?
and did you say "yes" to the KDE packages question? I'm guessing your missing a dependency...

EDIT: I went back and looked at your post...I don't really know how much help I could be, I've never really played around with KDE...Sorry.

---

### Post by unimatrix on 2007-08-18
OK I just found out I was using a script written by someone else lol...
Anyway, now I've tried it with your script, but the result is the same. It doesn't compile compiz.

Basically the same error:
> 
<cut: lots of output>
Making all in metadata
make[2]: Entering directory `/home/andrej/compiz/compiz/metadata'
make[2]: *** No rule to make target `compiz-core.kcfg', needed by `compizrc'.  Stop.
make[2]: Leaving directory `/home/andrej/compiz/compiz/metadata'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrej/compiz/compiz'
make: *** [all] Error 2

Would you like to install Compiz Fusion Option Code Generator?(y/n):


It might be a good idea to ask about this on the CompizFusion forums. Sorry to bother you.

---

### Post by Meneldir on 2007-08-18
Hmm. sounds interesting to download and try it... As always, I asume I'll do something wrong and post it here :P. If not, I'll post anyway, al least, saying thanks...

---

### Post by isaacj87 on 2007-08-18
> **unimatrix said:**
> OK I just found out I was using a script written by someone else lol...
Anyway, now I've tried it with your script, but the result is the same. It doesn't compile compiz.

Basically the same error:


It might be a good idea to ask about this on the CompizFusion forums. Sorry to bother you.

With the new script...can you post your complete output...even if I haven't played around with KDE, I'd like to see if I could figure it out...and help a fellow ubuntu/kubuntu user! :)

---

### Post by Meneldir on 2007-08-18
> **Meneldir said:**
> Hmm. sounds interesting to download and try it... As always, I asume I'll do something wrong and post it here :P. If not, I'll post anyway, al least, saying thanks...

I've tryed, but I get this:
> Would you like to install Compiz Fusion?(y/n):y

git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm


And it will never Install.. or so it seems.
Can the script be used in Feisty Fawn 7.04 64bits UBUNTU?

---

### Post by unimatrix on 2007-08-18
> 
With the new script...can you post your complete output...even if I haven't played around with KDE, I'd like to see if I could figure it out...and help a fellow ubuntu/kubuntu user!

Thank you for your concern, but I really don't think there is much you can do about it. There may actually be something wrong with the git source. I've tried compiling the officially released 0.5.2 version from the tarball and it works nicely.

---

### Post by st33med on 2007-08-18
Wow. I had stuff screwed up when I installed CF (No fusion-icon, dragging stuff into firefox crashes it) so I decided to reinstall it.

And, now, I seem to get every one of your errors wrapped into a tortilla! It doesn't taste good. :(

Fusion-icon will not start (the same as you guys), LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp comes up with an error saying their is no ccp plugin, no plugins were installed because it said I didn't have compiz (when I DID!!!), doesn't change my libX11 thing because 'Permission Denied'.

And, to top it off, none of the others worked as well as yours (used to) work.

What is wrong?

---

### Post by tekkenlord on 2007-08-19
> **st33med said:**
> Wow. I had stuff screwed up when I installed CF (No fusion-icon, dragging stuff into firefox crashes it) so I decided to reinstall it.

And, now, I seem to get every one of your errors wrapped into a tortilla! It doesn't taste good. :(

Fusion-icon will not start (the same as you guys), LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp comes up with an error saying their is no ccp plugin, no plugins were installed because it said I didn't have compiz (when I DID!!!), doesn't change my libX11 thing because 'Permission Denied'.

And, to top it off, none of the others worked as well as yours (used to) work.

What is wrong?

Well, it seems like the install script needs a hardcore revision! For the time being I use Amaranth's repos and everything works fine. Either way, do not expect big differences between installing from source and repos.

---

### Post by dweez on 2007-08-19
> **Meneldir said:**
> I've tryed, but I get this:


And it will never Install.. or so it seems.
Can the script be used in Feisty Fawn 7.04 64bits UBUNTU?


I used it with 64bit Feisty.  If you've ever tried to install compiz before with some other method, when you use this script initially, it seems you have to select to uninstall compiz first, then run it again to install it.

---

### Post by eeeeepuk on 2007-08-19
Thanks for the script. I've used it previously on Feisty and its worked perfectly. However, on my clean install compz is refusing to compile, giving the follwoing errors:

> kconfig.cpp:20:21: error: kglobal.h: No such file or directory
kconfig.cpp:21:27: error: kstandarddirs.h: No such file or directory
kconfig.cpp:22:26: error: kapplication.h: No such file or directory
kconfig.cpp:23:27: error: ksimpleconfig.h: No such file or directory
kconfig.cpp:24:19: error: qfile.h: No such file or directory
kconfig.cpp:30: error: expected initializer before '*' token
kconfig.cpp:43: error: ISO C++ forbids declaration of 'KConfig' with no type
kconfig.cpp:43: error: expected ';' before '*' token
kconfig.cpp: In function 'int kconfigRcSync(void*)':
kconfig.cpp:80: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp: At global scope:
kconfig.cpp:103: error: 'QString' does not name a type
kconfig.cpp: In function 'void kconfigSetOption(CompDisplay*, CompOption*, const char*, const char*)':
kconfig.cpp:186: error: 'QString' was not declared in this scope
kconfig.cpp:186: error: expected `;' before 'group'
kconfig.cpp:190: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:190: error: 'group' was not declared in this scope
kconfig.cpp:195: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:199: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:202: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:210: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:211: error: 'kconfigValueToString' was not declared in this scope
kconfig.cpp:218: error: 'QValueList' was not declared in this scope
kconfig.cpp:218: error: expected primary-expression before 'int'
kconfig.cpp:218: error: expected `;' before 'int'
kconfig.cpp:221: error: 'list' was not declared in this scope
kconfig.cpp:223: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:223: error: 'list' was not declared in this scope
kconfig.cpp:234: error: 'QStringList' was not declared in this scope
kconfig.cpp:234: error: expected `;' before 'list'
kconfig.cpp:237: error: 'list' was not declared in this scope
kconfig.cpp:241: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:241: error: 'list' was not declared in this scope
kconfig.cpp: At global scope:
kconfig.cpp:258: error: 'QString' has not been declared
kconfig.cpp: In function 'int kconfigStringToValue(CompDisplay*, int, CompOptionType, CompOptionValue*)':
kconfig.cpp:264: error: request for member 'toInt' in 'str', which is of non-class type 'int'
kconfig.cpp:267: error: request for member 'toFloat' in 'str', which is of non-class type 'int'
kconfig.cpp:270: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp:270: error: 'strdup' was not declared in this scope
kconfig.cpp:275: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp:279: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp:282: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp:285: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp:288: error: request for member 'toInt' in 'str', which is of non-class type 'int'
kconfig.cpp:292: error: request for member 'ascii' in 'str', which is of non-class type 'int'
kconfig.cpp: At global scope:
kconfig.cpp:319: error: 'KConfig' has not been declared
kconfig.cpp: In function 'int kconfigReadOptionValue(CompDisplay*, int*, CompOption*, CompOptionValue*)':
kconfig.cpp:328: error: request for member 'readBoolEntry' in '* config', which is of non-class type 'int'
kconfig.cpp:331: error: request for member 'readNumEntry' in '* config', which is of non-class type 'int'
kconfig.cpp:334: error: request for member 'readDoubleNumEntry' in '* config', which is of non-class type 'int'
kconfig.cpp:342: error: request for member 'readEntry' in '* config', which is of non-class type 'int'
kconfig.cpp:355: error: 'QValueList' was not declared in this scope
kconfig.cpp:355: error: expected primary-expression before 'int'
kconfig.cpp:355: error: expected `;' before 'int'
kconfig.cpp:357: error: 'list' was not declared in this scope
kconfig.cpp:357: error: request for member 'readIntListEntry' in '* config', which is of non-class type 'int'
kconfig.cpp:382: error: 'QStringList' was not declared in this scope
kconfig.cpp:382: error: expected `;' before 'list'
kconfig.cpp:384: error: 'list' was not declared in this scope
kconfig.cpp:384: error: request for member 'readListEntry' in '* config', which is of non-class type 'int'
kconfig.cpp: In function 'void kconfigGetDisplayOption(CompDisplay*, CompOption*, const char*)':
kconfig.cpp:430: error: 'QString' was not declared in this scope
kconfig.cpp:430: error: expected `;' before 'group'
kconfig.cpp:431: error: 'QString' does not name a type
kconfig.cpp:435: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:435: error: 'group' was not declared in this scope
kconfig.cpp:437: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:437: error: 'name' was not declared in this scope
kconfig.cpp:441: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:443: error: 'strcmp' was not declared in this scope
kconfig.cpp: In function 'void kconfigGetScreenOption(CompScreen*, CompOption*, const char*, const char*)':
kconfig.cpp:463: error: 'QString' was not declared in this scope
kconfig.cpp:463: error: expected `;' before 'group'
kconfig.cpp:464: error: 'QString' does not name a type
kconfig.cpp:468: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:468: error: 'group' was not declared in this scope
kconfig.cpp:470: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:470: error: 'name' was not declared in this scope
kconfig.cpp:474: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:476: error: 'strcmp' was not declared in this scope
kconfig.cpp: In function 'int kconfigRcReload(void*)':
kconfig.cpp:501: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:519: error: 'QString' was not declared in this scope
kconfig.cpp:519: error: expected `;' before 'screen'
kconfig.cpp:523: error: 'screen' was not declared in this scope
kconfig.cpp:533: error: 'screen' was not declared in this scope
kconfig.cpp: In function 'void kconfigRcChanged(const char*, void*)':
kconfig.cpp:550: error: 'strcmp' was not declared in this scope
kconfig.cpp: In function 'int kconfigSetScreenOption(CompScreen*, const char*, CompOptionValue*)':
kconfig.cpp:639: error: 'QString' was not declared in this scope
kconfig.cpp:639: error: expected `;' before 'screen'
kconfig.cpp:641: error: 'screen' was not declared in this scope
kconfig.cpp:641: error: 'QString' is not a class or namespace
kconfig.cpp: In function 'int kconfigSetScreenOptionForPlugin(CompScreen*, const char*, const char*, CompOptionValue*)':
kconfig.cpp:680: error: 'QString' was not declared in this scope
kconfig.cpp:680: error: expected `;' before 'screen'
kconfig.cpp:682: error: 'screen' was not declared in this scope
kconfig.cpp:682: error: 'QString' is not a class or namespace
kconfig.cpp: In function 'int kconfigInitPluginForScreen(CompPlugin*, CompScreen*)':
kconfig.cpp:737: error: 'QString' was not declared in this scope
kconfig.cpp:737: error: expected `;' before 'screen'
kconfig.cpp:739: error: 'screen' was not declared in this scope
kconfig.cpp:739: error: 'QString' is not a class or namespace
kconfig.cpp: In function 'int kconfigInitDisplay(CompPlugin*, CompDisplay*)':
kconfig.cpp:755: error: 'QString' was not declared in this scope
kconfig.cpp:755: error: expected `;' before 'dir'
kconfig.cpp:761: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:761: error: expected type-specifier before 'KConfig'
kconfig.cpp:761: error: expected `;' before 'KConfig'
kconfig.cpp:762: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:771: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp:780: error: 'dir' was not declared in this scope
kconfig.cpp:780: error: 'KGlobal' has not been declared
kconfig.cpp:780: error: 'QString' is not a class or namespace
kconfig.cpp:782: error: 'QFile' has not been declared
kconfig.cpp: In function 'void kconfigFiniDisplay(CompPlugin*, CompDisplay*)':
kconfig.cpp:826: error: 'struct _KconfigDisplay' has no member named 'config'
kconfig.cpp: In function 'int kconfigInit(CompPlugin*)':
kconfig.cpp:878: error: 'kInstance' was not declared in this scope
kconfig.cpp:878: error: expected type-specifier before 'KInstance'
kconfig.cpp:878: error: expected `;' before 'KInstance'
kconfig.cpp: In function 'void kconfigFini(CompPlugin*)':
kconfig.cpp:894: error: 'kInstance' was not declared in this scope
make[2]: *** [kconfig.lo] Error 1
make[2]: Leaving directory `/home/atm/compiz/compiz/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/atm/compiz/compiz'
make: *** [all] Error 2


As far as I can tell it's failing to build a plugin for KDE, but I'm using (and have told the script so) Gnome. Can anynoe shed any light on this?

---

### Post by PatheticMoFo on 2007-08-19
Try the following, it worked for me for compling from source "by hand" (I didn't use this script):
> 
export QTDIR=/usr/share/qt3
export KDEDIR=/usr/lib/kde3

See if that makes it work.

---

### Post by eeeeepuk on 2007-08-19
Thanks for the suggestion, but I'm still getting the same errors.

---

### Post by PatheticMoFo on 2007-08-19
Oh, you know what? Maybe this script does not install all the dependencies for the kde-window-decorator. Try doing:
sudo apt-get install kde-devel

Since this will install a metapackage with a bunch of, not only headers, but some other KDE development tools, you might not want it all, so here's the stuff it installs individually:
sudo apt-get install kde-core kdesdk libartsc0-dev libarts1-dev kdelibs4-dev kdebase-dev libkonq4-dev qt3-designer

And I guess leave out the stuff you don't think you need. (like qt3-designer).

---

### Post by eeeeepuk on 2007-08-19
Thanks - that worked perfectly :)

---

### Post by st33med on 2007-08-19
This is funny...

I now have beryl installed (I was installing emerald), and... no problems. Not even no GLX_from_pixmap error. It is a bit slower, but...

I think it is time to update the script.

---

### Post by isaacj87 on 2007-08-19
Okay...now I'm confused...

I tried the script and it worked perfectly, but then Trevino came back and updated his repo...so I had to try it. I uninstalled compiz fusion using the script and now it won't install/compile correctly. It appears to be..when it tries to install other packages such as the BCOP, the script says compiz isn't installed??? :confused:

---

### Post by isaacj87 on 2007-08-19
> **PatheticMoFo said:**
> Oh, you know what? Maybe this script does not install all the dependencies for the kde-window-decorator. Try doing:
sudo apt-get install kde-devel

Since this will install a metapackage with a bunch of, not only headers, but some other KDE development tools, you might not want it all, so here's the stuff it installs individually:
sudo apt-get install kde-core kdesdk libartsc0-dev libarts1-dev kdelibs4-dev kdebase-dev libkonq4-dev qt3-designer

And I guess leave out the stuff you don't think you need. (like qt3-designer).

I apologize for double-posting...but when I do what you suggested..apt-get wants to install 69 (!!) packages...is this normal?

---

### Post by Frak on 2007-08-19
> **isaacj87 said:**
> I apologize for double-posting...but when I do what you suggested..apt-get wants to install 69 (!!) packages...is this normal?
Sounds normal to me.

---

### Post by Crinos512 on 2007-08-20
**_One Suggestion:_**
on the lines near the beginning which read:
```
wget http://ftp.debian.org/debian/pool/main/libx/libx11/libx11_1.1.3.orig.tar.gz
wget http://ftp.debian.org/debian/pool/main/libx/libx11/libx11_1.1.3-1.diff.gz
```

...would it be possible to do a version check to see if the latest version is already installed, then a "if exists" to see if the tarballs are already present in the target download directory. I realize this is a negligable amount of time spent downloading over dsl or cable, but this takes a painful 20-30 minutes over dialup, ...especially when I have to hack away at the *apt-get* dependencies and *git* downloads in chunks. 

Without checking this downloads every time the script is run. :(

---

### Post by Parms on 2007-08-20
OK I installed the newest version. And install went fine. I have the icon and tried to launch it.
I see a outline expanding to my computer, then that is it.

I tried to use CCSM and this is what i got...

parms@parms-laptop:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig
parms@parms-laptop:~$ 

I've also opened the emerald themes and can see hem, but can't figure out how to boot them on my computer. 

7.04 64bit

---

### Post by Meneldir on 2007-08-20
Nope, still doent's work. And it also tries to install KDE stuff, when I told it that I run GNOME...

---

### Post by hyrcan on 2007-08-20
I'm getting this same error on my Latitude D810.    running CCSM gets a trackback, that also indicates no module named compizconfig.  looking deeper, will report back when I can.


> **s_spiff said:**
> Got same error as a few others here. I'm on Fiesty AMD64 and 6150 onboard nvidia graphic card, which used to run beryl with no trouble at all. Heres the out put when i run compiz-fusion in the terminal ( as the menu icons don't work )
```
spiff@spiffed:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
spiff@spiffed:~$ 

```

---

### Post by PatheticMoFo on 2007-08-20
I think that what's going on here is that the script is now either a little too out dated, or isn't doing everything the OP intended it to do. It didn't work for me either, so for anyone who is interested in installing compiz-fusion from GIT, I found this nice guide on the compiz-fusion forums. Not as nice as an automated script, but it should give you more freedom:

[http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

Note that this method is more GNOME oriented, and if you want to use it for KDE/Kubuntu, you're gonna haveta make a few changes (if anyone's interested, I'll post the modifications I made to it here). Mostly, it involves changing the configure/autoconf options and what dependencies to install (as well as leaving out emerald, if you want)

---

### Post by g2g591 on 2007-08-20
doesn't work here either (on gutsy)

---

### Post by hyrcan on 2007-08-20
Digging deeper on this...

> **hyrcan said:**
> I'm getting this same error on my Latitude D810.    running CCSM gets a trackback, that also indicates no module named compizconfig.  looking deeper, will report back when I can.

I discovered that when the script attempts to compile Compiz Fusion (the compiz portion of the install)  it fails with a exit status:1.  Will clear out everything and try again to explore the error. If only has any words of wisdom I'd love to hear them.

```
Would you like to install Compiz Fusion?(y/n):y
destination directory 'compiz' already exists.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
configure.ac:192: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:76: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL
metadata/Makefile.am:40: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:40: (probably a GNU make extension)
metadata/Makefile.am:43: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:44: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:44: (probably a GNU make extension)
metadata/Makefile.am:52: patsubst %.xml.in,compiz-%.kcfg,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:52: (probably a GNU make extension)
metadata/Makefile.am:56: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:57: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:57: (probably a GNU make extension)
autoreconf: automake failed with exit status: 1
```

---

### Post by PatheticMoFo on 2007-08-20
> I discovered that when the script attempts to compile Compiz Fusion (the compiz portion of the install) it fails with a exit status:1. Will clear out everything and try again to explore the error. If only has any words of wisdom I'd love to hear them.

Make sure you are using automake-1.9 (1.10 I think works too)

> sudo update-alternatives --config automake

---

### Post by Eion on 2007-08-20
I've seen this problem reported several times before in this thread and I have yet to see an answer.  The installer went off without a problem, and i've got window borders and all, but no compiz.  The fusion-icon dosn't work and the settings dosn't launch either.  I've got no cube, wobbly windows, ect.  Any ideas?  Or am I a n00b and I just missed the answer?

---

### Post by peitschie on 2007-08-20
This may help other people:

I had issues compiling the compiz version found in git.  It seemed that the file headers (for compiz.h: CompizAction specifically) were meant for a different version than libcompizconfig expected.  This lead to a compile error during the install script (libcompizconfig would fail to compile complaining about CompizAction missing an edgeButton property).  Everything beyond here would fail in interesting ways...

To fix this I downloaded the official release code found at [http://xorg.freedesktop.org/archive/individual/app/compiz-0.5.2.tar.gz]("http://xorg.freedesktop.org/archive/individual/app/compiz-0.5.2.tar.gz") (0.5.2 when last checked), and replaced the existing ~/compiz/compiz directory **KEEPING THE autogen.sh file found in the existing compiz folder**, and commenting out the line in the install script where it goes off and downloads the latest compiz source from git.

I figured I will wait a few days and then uncomment this out and try again...

If you have already deleted the autogen.sh, download the one found at [http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh]("http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh")

---

### Post by Druke on 2007-08-20
I get errors asking about "undefined symbol: ccsEdgesToStringList" at the start of fusion-icon(making it then stop trying to run gnome stuff and run KDE instead), and when i try to run ccsm.

---

### Post by Druke on 2007-08-20
> **peitschie said:**
> This may help other people:

I had issues compiling the compiz version found in git.  It seemed that the file headers (for compiz.h: CompizAction specifically) were meant for a different version than libcompizconfig expected.  This lead to a compile error during the install script (libcompizconfig would fail to compile complaining about CompizAction missing an edgeButton property).  Everything beyond here would fail in interesting ways...

To fix this I downloaded the official release code found at [http://xorg.freedesktop.org/archive/individual/app/compiz-0.5.2.tar.gz]("http://xorg.freedesktop.org/archive/individual/app/compiz-0.5.2.tar.gz") (0.5.2 when last checked), and replaced the existing ~/compiz/compiz directory, and commenting out the line in the install script where it goes off and downloads the latest compiz source from git.

I figured I will wait a few days and then uncomment this out and try again...




read -p "Would you like to install Compiz Fusion?(y/n):" answer;
					if [ $answer = y ] ; then
						cd ~/compiz
						#git clone git://anongit.opencompositing.org/compiz
						cd ~/compiz/compiz
						./autogen.sh --disable-kde && make && sudo make install
					else
						echo "Skipping..."
					fi

when i download from your link, there is no autogen, I tried ./configure myself but that didn't make it either, got any tips?

---

### Post by peitschie on 2007-08-20
Whups... forgot that step :oops:

You can copy autogen.sh file from the git-downloaded source into the downloaded compiz source. If you have already deleted the autogen.sh, download the one found at [http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh]("http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh")

 In the mean time, you can manually compile & install this part with the following commands:
> cd ~/compiz/compiz
./configure && make && sudo make install

---

### Post by Druke on 2007-08-20
thats done, not noticing any changes though, fusion-icon still doesn't work nor does 'compiz --replace' or 'compiz --replace &emerald'

edit- to be more specific what doesn't work are window borders, and no ccsm to change options either

perhaps my probelm still goes back to-

> druke@druke-desktop:~$ fusion-icon
* Using the GTK Interface
* /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
druke@druke-desktop:~$ 

---

### Post by peitschie on 2007-08-20
> **Druke said:**
> thats done, not noticing any changes though, fusion-icon still doesn't work nor does 'compiz --replace' or 'compiz --replace &emerald'

edit- to be more specific what doesn't work are window borders, and no ccsm to change options either


I'm not sure from reading your post, but after you build & install the compiz source that you downloaded by hand, are you re-running the CF Installer script? 

**Update:** If you have already deleted the autogen.sh, download the one found at [http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh]("http://gitweb.freedesktop.org/?p=xorg/app/compiz.git;a=blob_plain;h=e7513cd93e5f4eda31b58570f237036955a0c567;f=autogen.sh") and place it in the ~/compiz/compiz directory and re-run the CF Installer script

As compiz initially fails to compile, most of the other modules will not successfully compile either, including the compizconfig, emerald, etc.

---

### Post by Druke on 2007-08-20
was running it with the autogen before... same errors arg, i'd imagine it will be fixxed in a matter of days :/

---

### Post by Eion on 2007-08-20
Just wanted to post the error message that went with what I said earlier.  When I try to open the fusion-icon nothing happens, when I try to load in the terminal

```
mcadams@mcadams-desktop:~$ fusion-icon
* Using the GTK Interface
* /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList
... Trying another interface
* Error: All interfaces failed, aborting!
mcadams@mcadams-desktop:~$ 

```

---

### Post by peitschie on 2007-08-20
Hi Eion,

**Update:**  Never mind... Have just tried it myself and it won't fix it...

Please try the instructions listed in my earlier here: [http://ubuntuforums.org/showpost.php?p=3224188&postcount=300]("http://ubuntuforums.org/showpost.php?p=3224188&postcount=300")
 and let me know if it fixes your problem

---

### Post by peitschie on 2007-08-20
> **Druke said:**
> was running it with the autogen before... same errors arg, i'd imagine it will be fixxed in a matter of days :/

Yes... i would agree.  Looking at changelogs on the git browser, they are in the middle of melding in some new stuff.  The script is pulling from the development branch after all...

---

### Post by spartan777 on 2007-08-20
I run in gnome, and when it asked me if I have any kde packages installed, I chose yes becuase I have amarok installed. was this the right course of action?

---

### Post by Eion on 2007-08-20
> **peitschie said:**
> Hi Eion,

**Update:**  Never mind... Have just tried it myself and it won't fix it...

Please try the instructions listed in my earlier here: [http://ubuntuforums.org/showpost.php?p=3224188&postcount=300]("http://ubuntuforums.org/showpost.php?p=3224188&postcount=300")
 and let me know if it fixes your problem


Hey, thanks for trying tho!:)  Hopefully we'll get it figured out!

---

### Post by copyrightake on 2007-08-20
I'm having problems compiling compiz using this script, i'm getting the following error and I can't find any body having the same problem.


```
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so -L/usr/lib /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm  
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Error 1
make[2]: Leaving directory `/home/steph/compiz/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steph/compiz/compiz'
make: *** [all] Error 2

```

any ideas?

---

### Post by Druke on 2007-08-20
> **spartan777 said:**
> I run in gnome, and when it asked me if I have any kde packages installed, I chose yes becuase I have amarok installed. was this the right course of action?

either wya you end up with more :/

---

### Post by Druke on 2007-08-20
> **copyrightake said:**
> I'm having problems compiling compiz using this script, i'm getting the following error and I can't find any body having the same problem.


```
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so -L/usr/lib /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm  
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Error 1
make[2]: Leaving directory `/home/steph/compiz/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steph/compiz/compiz'
make: *** [all] Error 2

```

any ideas?

its not finding -lgl which is the openGL lib

are ypou sure you have your 3d card enabled?

---

### Post by joshuachad on 2007-08-20
Dude pls tell me im retarded and missed something but your script seems to leave out a core package called 'compiz' lol. Please tell me i messed up and dont know what i am talking about..Cheers

---

### Post by st33med on 2007-08-20
> **joshuachad said:**
> Dude pls tell me im retarded and missed something but your script seems to leave out a core package called 'compiz' lol. Please tell me i messed up and dont know what i am talking about..Cheers

Don't worry. Currently, it is very buggy. I am having the same problems to.

---

### Post by brucewagner on 2007-08-20
I am a brand new Ubuntu user...   And I ran this script...

I finally made it through...  Although I had to GUESS at a lot of the questions...

Now, I have an icon for Compiz Fusion...  which does NOTHING.

Also, the Desktop Effects that was on the System-->Preferences menu before...  is Gone.

Help!

Do I need to reinstall Ubuntu in order to get back to where I started?

---

### Post by copyrightake on 2007-08-20
> **Druke said:**
> its not finding -lgl which is the openGL lib

are ypou sure you have your 3d card enabled?


Yes I have my nvidia driver installed and its working fine, I used Envy to install the latest nvidia driver, is there some package I need to install for this to work?

I'm running Ubuntu 7.04

---

### Post by Eion on 2007-08-20
> **brucewagner said:**
> I am a brand new Ubuntu user...   And I ran this script...

I finally made it through...  Although I had to GUESS at a lot of the questions...

Now, I have an icon for Compiz Fusion...  which does NOTHING.

Also, the Desktop Effects that was on the System-->Preferences menu before...  is Gone.

Help!

Do I need to reinstall Ubuntu in order to get back to where I started?

This is what im experiencing.  But I REALLY don't want to reinstall Ubuntu!

---

### Post by derba on 2007-08-21
> **Eion said:**
> This is what im experiencing.  But I REALLY don't want to reinstall Ubuntu!

I am also experiencing this problem, I registered just to comment about said problem.

I too updated to the latest NVidia driver and am running Ubuntu 7.04 x64.

When I click on the Compfiz Icon nothing happens.

When I select CompfizConfig Settings Manager nothing happens.

Please Help!

---

### Post by Eion on 2007-08-21
I think we have an epidemic on our hands!   :shock:  Quick, somebody invent a cure!:lolflag:

---

### Post by joshuachad on 2007-08-21
i think ur right

---

### Post by Druke on 2007-08-21
ok then your all teh same as I, run fusion-icon in a term and see if your output is the same as mine a few pages back

---

### Post by Analord on 2007-08-21
Folks, if you have problems with script, it has an uninstall option at start.

Run it, chose uninstall and that's it. You don't have to reinstall OS ! :lolflag:

Then get compiz via vorian's repositories or wait for Trevino to fix his.

---

### Post by garnie on 2007-08-21
I sit behind a proxy, so git won't work, any work around to that ?

---

### Post by melado on 2007-08-21
Same problem here... :confused:

```
martin@tatil:~$ fusion-icon
* Using the GTK Interface
* /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

---

### Post by tiki28 on 2007-08-21
When I try config thru the icon, I get:

"Could not launch application" with the following message

"/home/artie/.compizconfig/config" (Permission denied)


I assume it expects me to be the "root", but with Ubuntu I don't know how to become the root.


Thanks
Artie

---

### Post by profjohn on 2007-08-21
It doesn't sound like it wants to be root, instead it sounds like it's not executable, you can try:

chmod +x /home/artie/.compizconfig/config

Also if you want to do something as root just put sudo in front of the command in a terminal.  Most GUI programs that require you to be root, such as Synaptic, will ask you for your password when they need it. :)

---

### Post by profjohn on 2007-08-21
> **garnie said:**
> I sit behind a proxy, so git won't work, any work around to that ?
I'm behind a proxy too and I have no problem connecting to git, maybe you have a firewall blocking you.

---

### Post by garnie on 2007-08-21
> **profjohn said:**
> I'm behind a proxy too and I have no problem connecting to git, maybe you have a firewall blocking you.

Perhaps so, but i looked through the git documentation but i can't seem to find a port number anywhere in it or anything related to network documentation.

---

### Post by profjohn on 2007-08-21
> **garnie said:**
> Perhaps so, but i looked through the git documentation but i can't seem to find a port number anywhere in it or anything related to network documentation.
The "DEFAULT_GIT_PORT" is 9418, at least that's what git daemon listens on, I'm not sure if that's the one git will be using on your machine but it could be worth checking it out.

---

### Post by raycosm on 2007-08-21
> **derba said:**
> I am also experiencing this problem, I registered just to comment about said problem.

I too updated to the latest NVidia driver and am running Ubuntu 7.04 x64.

When I click on the Compfiz Icon nothing happens.

When I select CompfizConfig Settings Manager nothing happens.

Please Help!

Got the same problem, except running Kubuntu 7.04 using Wubi, and using an Intel 945GM Express Graphics Controller (whatever that is, I'm a noob). I click the Compiz Icon/CompizConfig Settings Manager, it shows it as loading in my taskbar, but then it just disappears. Installation with the script went fine, I'm pretty sure I answered all questions correctly.

---

### Post by ElemonGW on 2007-08-21
@ Everybody: Please just be patient. I am currenlty coding the next version...

---

### Post by Eion on 2007-08-21
Nice, good luck with the coding!

---

### Post by st33med on 2007-08-21
> **ElemonGW said:**
> @ Everybody: Please just be patient. I am currenlty coding the next version...

Yes! I really miss the compile script. It made installing plugins and updating a breeze!
Now, I patiently wait...

---

### Post by Eion on 2007-08-21
Any updates?:confused:

---

### Post by spintel on 2007-08-21
Thanks for the script, it ran great.

For anyone that cares Compiz-Fusion is working fine on a laptop with 1gig ram, intel gma 950 and intel centrino duo.

[SIZE="2"]Does anyone know of a website that has all the commands for using the various plugins?[/SIZE]

---

### Post by Eion on 2007-08-22
So, does this mean its working?  I just had to do a new reinstall to set up my Dual-Boot thing, and ummm. . . . . :p   Anybody else wanna try before me?

---

### Post by michaelramm on 2007-08-22
I just used the script to install Compiz Fusion on my system and it ran like a champ.

I am missing my window borders if anyone know how to get them back. I tried 

```
compiz --replace -c emerald &
```

at one time and it worked, but everytime I do it now, it crashes CF and I have to log out of my session.

Thanks,
Michael

---

### Post by joshuachad on 2007-08-22
hmmm Ill I had to do to fix the script on my box was change the first git clone line to:"git clone git://git.freedesktop.org/git/xorg/app/compiz" under all the sudo's.

---

### Post by joshuachad on 2007-08-22
wow now i know why ppl go through the trouble of compiling. I have never had compiz run this awesome. And ive tried a many of times from repos.

Thanks for the script.

Cheers

---

### Post by ElemonGW on 2007-08-22
For those who like to be up-to-date with what is currently happening...
**Changelog:**
[I]Script dialogs are now in bold so that they will not be confused with anything else
Dialogs added and changed.
If you enter an invalid answer in one of the questions that the script makes, it will exit instead of skipping that step.
Code Cleanup.
Option to compile CF from source instead of git.
Ability to choose download directory.
Changed download urls.[/I]
**TODO:**
*Ability to install all available plugins.*
And the list keeps on becoming bigger as I review the code....

---

### Post by Dark Star on 2007-08-22
> **ElemonGW said:**
> For those who like to be up-to-date with what is currently happening...
**Changelog:**
[I]Script dialogs are now in bold so that they will not be confused with anything else
Dialogs added and changed.
If you enter an invalid answer in one of the questions that the script makes, it will exit instead of skipping that step.
Code Cleanup.
Option to compile CF from source instead of git.
Ability to choose download directory.
Changed download urls.[/I]
**TODO:**
*Ability to install all available plugins.*
And the list keeps on becoming bigger as I review the code....
Thanks again man :D CF is really very good and you installed makes easy for newbies out there ;)

---

### Post by maupin42 on 2007-08-22
Thank you.. I have been looking for something like this for a while. I have upgraded to the Ubuntu64 and was scared of all the incompatibilities (I didn't care still better than vista). Clean code by the way.

---

### Post by spintel on 2007-08-22
> **ElemonGW said:**
> For those who like to be up-to-date with what is currently happening...
**Changelog:**
[I]Script dialogs are now in bold so that they will not be confused with anything else
Dialogs added and changed.
If you enter an invalid answer in one of the questions that the script makes, it will exit instead of skipping that step.
Code Cleanup.
Option to compile CF from source instead of git.
Ability to choose download directory.
Changed download urls.[/I]
**TODO:**
*Ability to install all available plugins.*
And the list keeps on becoming bigger as I review the code....

Do you know where I can find a list of the commands that will allow me to use the plugins?

ie - I know that Alt+Ctrl will let me drag the cube and Super+E does Expose but how do I use the other plugins.

Also, does anyone know how well this works under UbuntuStudio?

---

### Post by Tiftof on 2007-08-22
> **spintel said:**
> Do you know where I can find a list of the commands that will allow me to use the plugins?

ie - I know that Alt+Ctrl will let me drag the cube and Super+E does Expose but how do I use the other plugins.


Just activate the plugins that you want in ccsm. Every plugin has a tab with shortcuts concerning the plugin, you can view the key combinations there for each plugin, or you can change them to whatever you want.

---

### Post by Eion on 2007-08-22
When I launched the script it asked if I had "universe" and "multi verse" on?  How do I make sure that I have these?  I'm running a fresh install btw

---

### Post by Eion on 2007-08-22
Anybody?  I'm itching to get this installed, but I don't want to mess something up again. . .

---

### Post by spintel on 2007-08-22
> **Eion said:**
> When I launched the script it asked if I had "universe" and "multi verse" on?  How do I make sure that I have these?  I'm running a fresh install btw

In the Synaptic Package Manager, go to preferences and you can set which respositories you want.  You will see which ones are universe, multiverse, etc.  They all have to be checked to work.

---

### Post by Eion on 2007-08-22
Thanks!

---

### Post by Eion on 2007-08-22
Wait, which repositories am I supposed to have?  I don't have any right now.

---

### Post by vortex_noob on 2007-08-22
Thanks for the script, dude.... I managed to install CF. Looks stable enough than the ones from the three  repos' at the current alpha situation. However, there's no 3D windows on the cube *plus* Scale-effect and Shift + Super + Alt don't display all windows, just the ones from the current screen.

What should I change in compizconfig, or do i have to uninstall and re-run the install script?

Using Script Version 2 Rev.1

Thanks....Any suggestion is appreciated :)

---

### Post by Amarth on 2007-08-22
Doesn't seem to work here. Running Kubuntu.

First, there was a problem with xsltproc not being available. No idea what it is, but it was quickly installed - you might want toadd it somewhere though. Now, it errors while building compiz/kde/window-decorator. Seems to assume moc is in /bin/moc, but it's in /usr/bin/moc. Not too sure how to fix that - shouldn't some configure script take care of that?

---

### Post by stinkinrich88 on 2007-08-22
$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

---

### Post by st33med on 2007-08-22
> **stinkinrich88 said:**
> $ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

This is a bug, currently. He will fix it in the next script.

---

### Post by spintel on 2007-08-22
> **Eion said:**
> Wait, which repositories am I supposed to have?  I don't have any right now.

When you start the script it should tell you which repositories you need.

---

### Post by stinkinrich88 on 2007-08-22
> **stinkinrich88 said:**
> $ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

actually I sorted it, 
semantic this: libxslt1-dev

and then I sudo 'ed the script. Not sure if that helped.

Thanks! it's sexy!

---

### Post by moochm on 2007-08-22
> **Amarth said:**
> Doesn't seem to work here. Running Kubuntu.

First, there was a problem with xsltproc not being available. No idea what it is, but it was quickly installed - you might want toadd it somewhere though. Now, it errors while building compiz/kde/window-decorator. Seems to assume moc is in /bin/moc, but it's in /usr/bin/moc. Not too sure how to fix that - shouldn't some configure script take care of that?

Same here, I started with Ubuntu Feisty Server install CD, added KDE to that. First time i tried the Compiz installer (sudo), I selected kde and told the script to install every feature, but clicking the fusion-icon would just hang. I tried it from console and it said "All Interfaces Failed". Tried it a few more times.. then I saw Amarth's post and installed xsltproc and make a link to /usr/bin/moc in /bin. I just tried the install again but I got some g++ errors about constructors/destructors like:
window.o: In function `Window':
/home/moochm/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/home/moochm/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/home/moochm/compiz/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'

Also, For some reason when I ran the script the second time, the install option seemed to skip a lot of the compilation, while each subsequent run rebuilt everything :???:

---

### Post by st33med on 2007-08-22
> **vortex_noob said:**
> Thanks for the script, dude.... I managed to install CF. Looks stable enough than the ones from the three  repos' at the current alpha situation. However, there's no 3D windows on the cube *plus* Scale-effect and Shift + Super + Alt don't display all windows, just the ones from the current screen.

What should I change in compizconfig, or do i have to uninstall and re-run the install script?

Using Script Version 2 Rev.1

Thanks....Any suggestion is appreciated :)

I have heard that 3D Desktop has memory leaks. Best not to get it.
I have modified my buttons in ccsm to have the 'Home' button make everything on the current desktop appear and 'Pause' displays everything on every desktop. A bit more simple than a button combo (though, the home button might interfere with a browser, but not me!).

---

### Post by moochm on 2007-08-22
I got Compiz installed. My machine locked up 2 minutes later when I started playing around with the effects and enabled "Reflection".... lol

---

### Post by dannyboy79 on 2007-08-22
I am getting tons of Permission denied errors when the script is trying to remove directories or files. libX11-1.1.3/debian/libx11-data/ etc etc. Was I suppose to run this with sudo or logged in as root? The guide doesn't say that.
Will things get meesed up if I have installed compiz-fusion previously from Trevino's Repo's? Should I remove them from my sources.list? Should I remove and purge all compiz before running this? Thank you for your help and also, I think it'd be wise to include these answers within the guide on sheet 1 as possible snags. It's still running in the background, it wanted to install like 112 things so I said yes. It also asked if I wanted to remove these files that were write protected or soemthign or other and I just said yes. hope that was right?

UPDATE: Can I please have an undo script! This thing installed konqueror and a ton of KDE stuff when I explicitely told it I had no KDE modules installed.
Also, I am gettings errros the whole way:
/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
CF_Installer-Updater_v.2_rev.1.sh: line 102: cd: /home/daniel/compiz/compizconfig-python: No such file or directory
CF_Installer-Updater_v.2_rev.1.sh: line 103: ./autogen.sh: No such file or directory

most likely because not run as root. Man, why wouldn't the guide have said that?????

---

### Post by ElemonGW on 2007-08-22
> **st33med said:**
> This is a bug, currently. He will fix it in the next script.

It is not a bug. This and similar errors happen when something is not correctly installed.

---

### Post by ElemonGW on 2007-08-22
> **dannyboy79 said:**
> I am getting tons of Permission denied errors when the script is trying to remove directories or files. libX11-1.1.3/debian/libx11-data/ etc etc. Was I suppose to run this with sudo or logged in as root? The guide doesn't say that.
You were not supposed to run the script as root. This will not cause any problem however. Anyway, it is going to be fixed in the upcoming release.

> **dannyboy79 said:**
> Will things get meesed up if I have installed compiz-fusion previously from Trevino's Repo's?
Yes, but you don't have to do anything. The script will automatically uninstall them.

> **dannyboy79 said:**
> Should I remove them from my sources.list?
I don't know if leaving them will cause errors. I don't think so but...

> **dannyboy79 said:**
> UPDATE: This thing installed konqueror and a ton of KDE stuff when I explicitely told it I had no KDE modules installed.
Obviously however it seems that you DO have some KDE libraries installed.


> **dannyboy79 said:**
> Also, I am gettings errros the whole way:
/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
CF_Installer-Updater_v.2_rev.1.sh: line 102: cd: /home/daniel/compiz/compizconfig-python: No such file or directory
CF_Installer-Updater_v.2_rev.1.sh: line 103: ./autogen.sh: No such file or directory

most likely because not run as root. Man, why wouldn't the guide have said that?????
Seems that errors happened and nothing was downloaded. Search for errors that previously appeared (there should be some.

---

### Post by ElemonGW on 2007-08-22
And with my 100 post comes the new release :) . View more [here]("http://elemongw.awardspace.com/?q=node/28") (everybody that already uses my script should read that). Download it from [here]("http://elemongw.awardspace.com/?q=down_cf_i-u").
**EDIT: Fixed a bug caused by a typo I did and added link from where you can view a copy of the license under which this script is licensed. Please re-download.**

---

### Post by bn127 on 2007-08-22
It worked quite well with Feisty X86 but I can't succeed installing with Gutsy AMD64 which makes me think that it doesn't work with this last Tribe-4 release. Am I right?

---

### Post by RideP2 on 2007-08-22
I'm still getting the same error as the last version of the script.

zachary@ubuntu-zach:~/downloads$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!

---

### Post by michaelramm on 2007-08-22
> **Tiftof said:**
> Just activate the plugins that you want in ccsm. Every plugin has a tab with shortcuts concerning the plugin, you can view the key combinations there for each plugin, or you can change them to whatever you want.

I don't seem to have a tab for shortcuts. Any idea what could be wrong?

I ran the script on a fresh FF install. It also seems that there are some other anomolies in my XGL session. I could not add Desktop icons (had to do that in a regular session), keybord cmd don't work (like Alt-F2 for the Run dialog) and now the fact that the Commands tab is missing from ALL of the CCSM plugins.

Any thoughts would be helpful.

Michael

---

### Post by Kujen on 2007-08-22
...ignore this post.

---

### Post by dannyboy79 on 2007-08-22
> **ElemonGW said:**
> You were not supposed to run the script as root. This will not cause any problem however. Anyway, it is going to be fixed in the upcoming release.


Yes, but you don't have to do anything. The script will automatically uninstall them.


I don't know if leaving them will cause errors. I don't think so but...


Obviously however it seems that you DO have some KDE libraries installed.



Seems that errors happened and nothing was downloaded. Search for errors that previously appeared (there should be some.
how  can a script be run that should download somethign and store it to /usr/bin if the command is not run as root? why I am getting tons of errors? the script did NOT uninstall the compiz-fusion from the trevino's repos. i had to do that manually. now what do I do since it doesn't work at all???

here's just some of the errors ecen when running with sudo: [http://www.pastebin.org/966](http://www.pastebin.org/966)

---

### Post by Kujen on 2007-08-22
This script completely failed me. Compiz refuses to run.

Also, why did it give me a full install of KDE? That is NOT what I wanted, and now it's just there taking up space.

---

### Post by vortex_noob on 2007-08-23
Reinstall compiz using CF_Updater v.3. Scale still only display windows from current desktop *not* from ALL windows. What's seems to be the problem. Script run completely though.

Btw, using v3 rather than v2 rev1, i lost the ring switcher. 

When i want to uninstall, do i use the script again or just use:

> 
Code:
cd ~/compiz/bcop
sudo make uninstall
cd ~/compiz/ccsm
sudo make uninstall
cd ~/compiz/compiz
sudo make uninstall
cd ~/compiz/compizconfig-python
sudo make uninstall
cd ~/compiz/emerald
sudo make uninstall
cd ~/compiz/emerald-themes
sudo make uninstall
cd ~/compiz/fusion-icon
sudo make uninstall
cd ~/compiz/libcompizconfig
sudo make uninstall
cd ~/compiz/plugins-extra
sudo make uninstall
cd ~/compiz/plugins-main
sudo make uninstall
cd ~/compiz/plugins-unsupported
sudo make uninstall 

How do i uninstall the libx11-xcb though? Any thoughts?

Thanks for the script, man. It let me taste the progress of desktop linux without having to resort to Vista.

---

### Post by blueeyesmike on 2007-08-23
Wow this script is great!! just found it thanks to trevino's repo's sucking at the moment, thank goodness for that. Only thing that doesn't seem to work is that I can't figure out how to assign the mouse buttons for anything?? the default options work (eg ctrl +alt +button1 to spin cube) but don't know how to change that.

Also Scale is working fine with all windows for me

---

### Post by ethan961 on 2007-08-23
I have lost the shift AND the ring switchers, the two I actually use, at Super+Tab and Alt+Tab respectively.  This happened after uninstalling with v2rev1 and installing with v3. I love this script, and have used everything else (compile by hand, Trevino Eyecandy, the script Trevino uses to make his packages) but chose this in the end! (Things aren't cross-contaminated, trust me.) Love the changes in v3, although thumbnails failed to compile and several plugins are missing, including the enhanced zoom not working.
Hope someone knows what is going on,
Ethan


**UPDATE**
All of a sudden, all the checkboxes in ccsm are greyed out!!!
Should I uninstall and go back to v2rev1???

---

### Post by open2linux on 2007-08-23
After running the script and finish the instalation, I click in the Compiz Fusion Icon and nothing happens. Am I missing something?

---

### Post by dillanlaughlin on 2007-08-23
Sorry if I'm an idiot, I've been searching the forum for a concise answer without luck.

Am I missing something major here? I have run the script saying matching all the Gnome and Nvidia stuff that applies to my system and the whenever it asks to install something I let it.
Tried installing with git, uninstalled when it wasn't working, tried stable version.
After that it drops a nice little Compiz Fusion Icon in my applications menu... fantastic, almost....

Clicking on the icon seems to do nothing. No dialog box, no wobbly windows, nada.
Attempts to load the CCSM do nothing also.

Any recommendations? Thanks in advance!

---

### Post by number3pencil on 2007-08-23
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```

I had Fusion installed fine before I uninstalled it with this script.  I've tried using the script multiple times and I always get this error when running fusion-icon from the terminal I made sure I wasn't root and that I didn't cd to the scripts location, I even removed Treveno's repos so I don't know what to do.  Also, compizconfig doesn't do anything either.

---

### Post by stinkinrich88 on 2007-08-23
> **number3pencil said:**
> ```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```

I had Fusion installed fine before I uninstalled it with this script.  I've tried using the script multiple times and I always get this error when running fusion-icon from the terminal I made sure I wasn't root and that I didn't cd to the scripts location, I even removed Treveno's repos so I don't know what to do.  Also, compizconfig doesn't do anything either.


Anyone who is getting this error, run

```
sudo apt-get install libxslt1-dev
```

before running the script.

And to the dude who doesn't know why his icon isn't working, open a terminal and type the command compiz-icon or whatever the command is

---

### Post by ElemonGW on 2007-08-23
> **dannyboy79 said:**
> how  can a script be run that should download somethign and store it to /usr/bin if the command is not run as root? why I am getting tons of errors? the script did NOT uninstall the compiz-fusion from the trevino's repos. i had to do that manually. now what do I do since it doesn't work at all???

here's just some of the errors ecen when running with sudo: [http://www.pastebin.org/966](http://www.pastebin.org/966)

It is self explained. Just run ```
 sudo update-alternatives --config git 
``` .

---

### Post by dannyboy79 on 2007-08-23
> **ElemonGW said:**
> It is self explained. Just run ```
 sudo update-alternatives --config git 
``` .

i suppose this is "self explained" also????

sudo update-alternatives --config git

There are 2 alternatives which provide `git'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/git.transition
          2    /usr/bin/git-scm

I mean come on, how can you create a script and just say, it does eveything you need it to get compiz installed from git. What about people like myself who are fairly new to linux and don't know what git is. You expect people to know this kind of stuff?? It might help as gotcha in your guide. So basically I have been trying for a total of 6 hours to use your script to install compiz because it was supposedly "better" than the one in trevino's repo's or ubuntu repo's. So I lost compiz and haven't had it since. Hopefully this will work. I chose the default from the command you told me to use, was that correct???? Any more help would be appreciated.

---

### Post by ElemonGW on 2007-08-23
> **dannyboy79 said:**
> i suppose this is "self explained" also????

sudo update-alternatives --config git

There are 2 alternatives which provide `git'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/git.transition
          2    /usr/bin/git-scm

I mean come on, how can you create a script and just say, it does eveything you need it to get compiz installed from git. What about people like myself who are fairly new to linux and don't know what git is. You expect people to know this kind of stuff?? It might help as gotcha in your guide. So basically I have been trying for a total of 6 hours to use your script to install compiz because it was supposedly "better" than the one in trevino's repo's or ubuntu repo's. So I lost compiz and haven't had it since. Hopefully this will work. I chose the default from the command you told me to use, was that correct???? Any more help would be appreciated.

First of all, don't be rude!  Second, you should probably choose the second one. If it still displays you the same error, choose the first. Have you ever heard of trial and error.... ??
PS:This was handled by previous versions of CF Installer-Updater but I removed it because nobody seemed to have that problem. As it seems that some people do have it, i will re-add it.

---

### Post by dannyboy79 on 2007-08-23
I apologize if you felt that I was being rude BUT you don't realize that your comment, "self-explained" was very rude to start it all out. My frustration lies in the fact that you claim that the script does something and it doesn't. If I could only capture my entire xterm session I would show you slew of error's about not being able to chdir, about not being able to remove files, about not finding files, it seemed like it was error after error. Like I said that was the first time, when I didn't run it as root. Now that I am running it as root, I am getting less errors but still no compiz. 

I tried your newest version just now, I already get error's trying to make sure I remove everything:

Uninstalling CompizConfig Settings Manager...
Desktop/CF_Installer-Updater_v.3.sh: line 335: cd: /home/daniel/.cf_i-u/ccsm: No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory
Have you instaled Compiz Fusion version 0.5.2 or the latest one from git?(git/stable):

So what do I pick, git or stable???? I am guessing git but then I get these errors:

Uninstalling Compiz Fusion Option Code Generator...
Desktop/CF_Installer-Updater_v.3.sh: line 331: cd: /home/daniel/.cf_i-u/bcop: No such file or direc                               tory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling CompizConfig Settings Manager...
Desktop/CF_Installer-Updater_v.3.sh: line 335: cd: /home/daniel/.cf_i-u/ccsm: No such file or direc                               tory
python: can't open file 'setup.py': [Errno 2] No such file or directory
Have you instaled Compiz Fusion version 0.5.2 or the latest one from git?(git/stable):
git
Uninstalling Compiz Fusion...
Desktop/CF_Installer-Updater_v.3.sh: line 341: cd: /home/daniel/.cf_i-u/compiz-0.5.2: No such file                                or directory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling CompizConfig-Python...
Desktop/CF_Installer-Updater_v.3.sh: line 353: cd: /home/daniel/.cf_i-u/compizconfig-python: No suc                               h file or directory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling Emerald...
Desktop/CF_Installer-Updater_v.3.sh: line 357: cd: /home/daniel/.cf_i-u/emerald: No such file or di                               rectory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling the Package of Themes for Emerald...
Desktop/CF_Installer-Updater_v.3.sh: line 361: cd: /home/daniel/.cf_i-u/emerald-themes: No such fil                               e or directory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling Compiz Fusion Icon...
Desktop/CF_Installer-Updater_v.3.sh: line 365: cd: /home/daniel/.cf_i-u/fusion-icon: No such file o                               r directory
make: *** No rule to make target `uninstall'.  Stop.
Uninstalling the Settings Library for Plugins...
Desktop/CF_Installer-Updater_v.3.sh: line 369: cd: /home/daniel/.cf_i-u/libcompizconfig: No such fi                               le or directory
make: *** No rule to make target `uninstall'.  Stop.
Have you installed all the available plugins for Compiz Fusion or you have chosen which according t                               o where they are classified?(all/choose):

Then i chose all, and I get these errors:
Uninstalling all Compiz Fusion Plugins...
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/3d: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/addhelper: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/animation: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/atlantis: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/bench: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/colorfilter: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/compiz-scheme: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/crashhandler: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/cubecaps: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/cubereflex: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/expo: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/extrawm: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/ezoom: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/fadedesktop: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/fakeargb: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/firepaint: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/gears: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/group: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/jpeg: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/mblur: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/mswitch: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/neg: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/opacify: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/put: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/reflex: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/resizeinfo: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/ring: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/scaleaddon: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/scalefilter: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/screencasting: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/shift: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/showdesktop: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/snap: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/snow: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/splash: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/text: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/thumbnail: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/tile: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/trailfocus: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/vpswitch: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/wall: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/wallpaper: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/widget: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/winrules: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
Desktop/CF_Installer-Updater_v.3.sh: line 376: cd: /home/daniel/.cf_i-u/plugins/workarounds: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.


and it's no different I chose stable?????
Thanks for the attempt at writing a script for the community but I'll stick with Trevino's repos. Good luck

---

### Post by dillanlaughlin on 2007-08-23
```
user@computer:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

I tried uninstalling everything and then:
```
sudo apt-get install libxslt1-dev
```
before re-running the script. Is there any other dependencies that I need to run before being able to use this script?

Thanks for the help!

---

### Post by peitschie on 2007-08-23
> **dillanlaughlin said:**
> ```
user@computer:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

I tried uninstalling everything and then:
```
sudo apt-get install libxslt1-dev
```
before re-running the script. Is there any other dependencies that I need to run before being able to use this script?

Thanks for the help!

Hiya dillanlaughlin,

There will have been some errors generated during the compile and install process (i.e., before it attempted to run compiz fusion.  Are you able to find these?  We are primarily interested in the first few errors that occured.

Just an idea ElemonGW, would it be possible to make the script dump a debug.log file or similar that holds a copy of all the output the script produces?  Then the people having trouble could simply attach the file... make some of these a little less of a shot in the dark...  You're doing good work though.  Keep it up!

Cheers,

A Satisfied Script User

---

### Post by unabatedshagie on 2007-08-23
I've just downloaded and tried v3 of the installer but I guess there is something wrong on my end because compiz-fusion doesn't work when it's finished.

```
alex@MysteryMachine:~/Misc/Compiz Git$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```As you can see I have as suggested in a few posts above got **libxslt1-dev** installed.
```
alex@MysteryMachine:~/Misc/Compiz Git$ sudo apt-get install libxslt1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxslt1-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libmp4v2-0 libfuse2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Anyone have any ideas?

---

### Post by ArtF10 on 2007-08-23
Hello, I am a new Ubuntu user and have a quick question about your installer.  When you say "Just run bash /path/to/file/file_name.sh in terminal."  I am a bit confused about what I should enter.:confused:  I can download the file to my desktop and then move it to my home folder in Places.  If the file name is xyz, should I enter this:

bash /home/xyz.sh

Your help would be greatly appreciated as I am not getting anything to run.

---

### Post by Tiftof on 2007-08-23
> **ArtF10 said:**
> Hello, I am a new Ubuntu user and have a quick question about your installer.  When you say "Just run bash /path/to/file/file_name.sh in terminal."  I am a bit confused about what I should enter.:confused:  I can download the file to my desktop and then move it to my home folder in Places.  If the file name is xyz, should I enter this:

bash /home/xyz.sh

Your help would be greatly appreciated as I am not getting anything to run.

if you move the file to you home folder, you hae to run it by entering: "bash /home/USERNAME/xyz.sh"
But depending on how new you are, you'd better try compiz first from repositories. Installing is way easier and less risk of screwing things up.

---

### Post by ArtF10 on 2007-08-23
1.  By that  do you mean following these instructions:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

I thought that Compiz was already installed in Ubuntu 7.04?

2.  Do I need to install XGL and be logged into an XGL session BEFORE running the above commands?
XGL installation:  [http://ubuntuforums.org/showthread.php?t=527479&highlight=desktop+effects](http://ubuntuforums.org/showthread.php?t=527479&highlight=desktop+effects)

---

### Post by Tiftof on 2007-08-23
Those instructions will work. I prefer these [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) . The repository used in that one is very good. You don't need to do anything else. Just be sure you have drivers installed for your video card.

---

### Post by ArtF10 on 2007-08-23
Thanks a lot.  Will post back.

---

### Post by ArtF10 on 2007-08-23
> **Tiftof said:**
> Those instructions will work. I prefer these [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) . The repository used in that one is very good. You don't need to do anything else. Just be sure you have drivers installed for your video card.

Hmm..tried it and have it installed.  But when I Run, it simpy does nothing.  The only thing I did differently was install the video card drivers using a different method. i.e. not hte Envy script but instead another method by the same person who wrote Envy.

 Do I have to be in Gnome or some other session?  I did not install XGL.

---

### Post by Tiftof on 2007-08-23
Gnome will do. Better open up a new topic to keep this topic only for this script. In a new topic,post the output you get when running compiz from a terminal.

---

### Post by JonD25 on 2007-08-23
I finally got everything installed, but now when I go to CCSM and make some changes, nothing happens. If I close it and open it up again, all my changes are gone. I tried reloading everything, but it doesn't work. Everything still goes back to the default. How do I fix this?

---

### Post by st33med on 2007-08-23
OK, so I get this error message:
```
* Using the GTK Interface
* libcompizconfig.so.0: cannot open shared object file: No such file or directory
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* libcompizconfig.so.0: cannot open shared object file: No such file or directory
... Trying another interface
* Error: All interfaces failed, aborting!

```

I know where my libcompizconfig.so.0 lies, but where do i put it? Then there is emerald:
```
emerald: error while loading shared libraries: libemeraldengine.so.0: cannot open shared object file: No such file or directory

```
I also know where this is, but where do I put it?

Thanks.

---

### Post by open2linux on 2007-08-23
I have a laptop with Ubuntu and my graphic card is
Intel 82852/855GM Integrated Graphics Device

Is it possible to run Compiz Fusion with this card?
Anybody got it working?

After installing the script without error messages, when I chick the Compiz Fusio Icon just 
nothing happens, nothing opens. Same with CompizConfig Settings Manager, it doesn do anything at all.

Is there anything more I should do after installing with the script, before running Compiz?

Thanks

---

### Post by Crinos512 on 2007-08-23
:guitar:

Awesome, I finally got it working... oh man. how awesome.

This script deserves  :KS :KS :KS :KS :KS

---

### Post by st33med on 2007-08-23
The script for compiling Compiz-settings Manager in stable version is not working. I get errors, and I can't install libcompizconfig, which is needed for installing python-compizconfig.

The errors are:
```
ccp.c: In function 'ccpSameType':

ccp.c:392: error: 'CompOptionTypeKey' undeclared (first use in this function)

ccp.c:392: error: (Each undeclared identifier is reported only once

ccp.c:392: error: for each function it appears in.)

ccp.c:394: error: 'CompOptionTypeButton' undeclared (first use in this function)

ccp.c:396: error: 'CompOptionTypeEdge' undeclared (first use in this function)

ccp.c:398: error: 'CompOptionTypeBell' undeclared (first use in this function)

ccp.c: In function 'ccpSetOptionFromContext':

ccp.c:441: warning: passing argument 1 of 'findActivePlugin' discards qualifiers from pointer target type

ccp.c:488: warning: passing argument 3 of 'compFindOption' discards qualifiers from pointer target type

ccp.c:509: warning: passing argument 2 of 's->setScreenOptionForPlugin' discards qualifiers from pointer target type

ccp.c:509: warning: passing argument 3 of 's->setScreenOptionForPlugin' discards qualifiers from pointer target type

ccp.c:511: warning: passing argument 2 of 'd->setDisplayOptionForPlugin' discards qualifiers from pointer target type

ccp.c:511: warning: passing argument 3 of 'd->setDisplayOptionForPlugin' discards qualifiers from pointer target type

ccp.c:516: warning: passing argument 2 of 's->setScreenOption' discards qualifiers from pointer target type

ccp.c:518: warning: passing argument 2 of 'd->setDisplayOption' discards qualifiers from pointer target type

ccp.c: In function 'ccpSetContextFromOption':

ccp.c:543: warning: passing argument 1 of 'findActivePlugin' discards qualifiers from pointer target type

ccp.c:590: warning: passing argument 3 of 'compFindOption' discards qualifiers from pointer target type

ccp.c: In function 'ccpSetDisplayOption':

ccp.c:619: warning: passing argument 2 of 'd->setDisplayOption' discards qualifiers from pointer target type

ccp.c:620: warning: assignment from incompatible pointer type

ccp.c: In function 'ccpSetDisplayOptionForPlugin':

ccp.c:641: warning: passing argument 2 of 'd->setDisplayOptionForPlugin' discards qualifiers from pointer target type

ccp.c:641: warning: passing argument 3 of 'd->setDisplayOptionForPlugin' discards qualifiers from pointer target type

ccp.c:642: warning: assignment from incompatible pointer type

ccp.c: In function 'ccpSetScreenOption':

ccp.c:662: warning: passing argument 2 of 's->setScreenOption' discards qualifiers from pointer target type

ccp.c:663: warning: assignment from incompatible pointer type

ccp.c: In function 'ccpSetScreenOptionForPlugin':

ccp.c:688: warning: passing argument 2 of 's->setScreenOptionForPlugin' discards qualifiers from pointer target type

ccp.c:688: warning: passing argument 3 of 's->setScreenOptionForPlugin' discards qualifiers from pointer target type

ccp.c:689: warning: assignment from incompatible pointer type

ccp.c: In function 'ccpInitDisplay':

ccp.c:825: warning: assignment from incompatible pointer type

ccp.c:826: warning: assignment from incompatible pointer type

ccp.c: In function 'ccpInitScreen':

ccp.c:907: warning: assignment from incompatible pointer type

ccp.c:908: warning: assignment from incompatible pointer type

make[2]: *** [ccp.lo] Error 1

make[2]: Leaving directory `/home/andrew/.cf_i-u/libcompizconfig/plugin'

make[1]: *** [all-recursive] Error 1

make[1]: Leaving directory `/home/andrew/.cf_i-u/libcompizconfig'

make: *** [all] Error 2


#This next part is when I install Python-CompizConfig

checking for CCS... configure: error: Package requirements (libcompizconfig >= 0.5.2 glib-2.0 >= 2.6 ) were not met:



No package 'libcompizconfig' found



Consider adjusting the PKG_CONFIG_PATH environment variable if you

installed software in a non-standard prefix.



Alternatively, you may set the environment variables CCS_CFLAGS

and CCS_LIBS to avoid the need to call pkg-config.

See the pkg-config man page for more details.

```

---

### Post by rozen on 2007-08-23
Just tried using CF Installer on Kubuntu Fiesty on a Dell XPS 410 with an 256MB nVidia Geforce 7300LE.  

It didn't work for me.  There were several error messages that I was confused about:

FIrst batch:

dh_testdir
make: dh_testdir: Command not found
make: *** [build-stamp] Error 127
dpkg: error processing libx11*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libx11*deb
rm: cannot remove `libx11*deb': No such file or directory

I answered yes to question whether I had gnome packages installed.

The next error messages were:

E: Couldn't find package beryl-*

followed by:

E: Couldn't find package beryl*

In response to configure messages, I installed xcomposite, xdamage, libxslt and/or the associated -dev packages.   Then I seemed to get stuck at the message:

No package 'x11-xcb' found

I couldn't figure which package was needed.  I did try installing libxcbl1-dev but that didn't satisfy the dependency.

At that, it didn't seem worthwhile going on.

If I knew what package corresponded to 'x11-xcb' maybe I could go on.  Also, is it correct to ignore the earlier messages?

A couple of small points:

1: I tried using tee to get an install log, but then it seemed to miss the first gnome/kde question. It would be great to preserve a log.

2: I ran the script several times and each time it spent a minute downloading libx11_1.1.3.orig.tar.gz.  How about awaiting successful installation to erase it.  I may change the script to remove the appropriate 'rm commands'.

I will certainly appreciate any suggestions that will enable me to go on.

Thanks in Advance,
Don

---

### Post by st33med on 2007-08-23
AHA! Found the solution to my own problem. When I compile from git and launched fusion-icon, it would tell me:
```
** libcompizconfig.so.0: cannot open shared object file: No such file or directory 
```

And I thought, how can that be? It's a fresh install!
Searched for the file... found it, and realized, then, it was a shared library right then (I never went into depth of that error message ;D)
Anyways, I tried to find where to put it. /usr/local/lib/python2.5? Nope.

However, I found a whole bunch of files in the same format as libcompizconig.so.0 in /usr/lib.
I put it there, and, what do you know, it launched! Then I put a file for emerald there, and Emerald worked!

Yea! I'm so happy!!! Gnarly effects. Thanks for the puzzle and the script.

I still have that bug from last time (where I drag and drop anything into firefox and everything crashes :() though, I have a hunch that it's Emerald's doing. I have had problems with Emerald before. On another repository, whenever I logged out and had Emerald on, their were flashing monochromatic boxes and It hung.

---

### Post by st33med on 2007-08-23
OK, now I realized that, since Emerald doesn't crash it, it is the libx11 package. I remember the script said that libx11 can crash Java... Well, Java is integrated into Firefox, so, yeah.

But, I'm not reinstalling, not even to the stable version. I love these plugins!\\:D/
And, I'll avoid dragging and dropping the best I can.

Thanks again!

---

### Post by rozen on 2007-08-23
I apologize.  I have now downloaded todays version of the script and things seem to get a lot further.  I still have a message about libcompizcong not found.

When it gets to the bottom and try to launch Compiz Fusion Icon nothing seems to happen.

I will go back and see what i can find out about the missing lib.

Don

---

### Post by Kent_Geek on 2007-08-23
Great script - it's been working for me for a couple of weeks. A couple of days ago, I found that the key bindings were no longer in the settings manager tool.  In the interest of having the cleanest and most orderly install, I uninstalled this afternoon, cleaned up, downloaded the latest installer script and re-installed.  Since I read a post in this thread that indicated "sudo" is not necessary, I installed without it.
 Now, my key bindings are still gone from the manager, but also, it appears that the checkboxes that enable/disable features are themselves disabled, so I cannot change any of them.  
 Has anyone else seen this behavior?

---

### Post by st33med on 2007-08-23
> **rozen said:**
> I apologize.  I have now downloaded todays version of the script and things seem to get a lot further.  I still have a message about libcompizcong not found.

When it gets to the bottom and try to launch Compiz Fusion Icon nothing seems to happen.

I will go back and see what i can find out about the missing lib.

Don

Hey, try what I did. Find the libcompizconfig.so.0, sudo nautilus there, open another root nautilus, navigate to /usr/lib, drag and drop libcompizconfig.so.0 and libcompizconfig.0.0.0 to /usr/lib. These are shared libraries, so you need them both.

Once that is done, go ahead and launch fusion-icon!

EDIT: Sorry, you were talking about the script. You might want to use the git repository. I have had trouble with stable version as well.

> **Kent_Geek said:**
> Great script - it's been working for me for a couple of weeks. A couple of days ago, I found that the key bindings were no longer in the settings manager tool.  In the interest of having the cleanest and most orderly install, I uninstalled this afternoon, cleaned up, downloaded the latest installer script and re-installed.  Since I read a post in this thread that indicated "sudo" is not necessary, I installed without it.
 Now, my key bindings are still gone from the manager, but also, it appears that the checkboxes that enable/disable features are themselves disabled, so I cannot change any of them.  
 Has anyone else seen this behavior?

You might want to do this:
```
fusion-icon --reset
```

If that still doesn't fix it:
```
sudo chmod 644 /home/<your_usr_name>/.config/fusion-icon
```
Where <your_usr_name> is your user name.

Don't sudo everytime. When a program writes something while sudoed, it will make a file accessible only by root. In this case, you sudoed fusion-icon, reinstalled compiz (this doesn't remove configuration files) and locked your configuration file in.

---

### Post by stinkinrich88 on 2007-08-24
for the people who installed libxslt1-dev and it still isn't working:

don't forget: don't cd to the directory of the script

run the script and install compiz-fusion, but just before answering each question take a look at all the terminal text. Scroll up and see if you can find any errors that occured due to a missing dependancy. See one? install it (semantic) then try, try, try again

---

### Post by dannyboy79 on 2007-08-24
the thread subject should be changed to exlude the word "easily"! This caused compiz havoc on my machine. The author says it does eveything but doesn't. he also didn't mention (maybe has added it now) that people who have Trevino's repo enabled, there will be unresolvable problems as I have!!!! What's with not being able to cd to the directory, I've ever seen a script like that before??

Good luck to anyone who tries this out.......

---

### Post by glaze0101 on 2007-08-24
> **stinkinrich88 said:**
> Anyone who is getting this error, run

```
sudo apt-get install libxslt1-dev
```

before running the script.

And to the dude who doesn't know why his icon isn't working, open a terminal and type the command compiz-icon or whatever the command is
I am having the same error message I ran ```
sudo apt-get install libxslt1-dev
``` and then re-ran the script choosing "update" - should I choose a new install?  Thanks!

---

### Post by shantzg001 on 2007-08-24
@Elemon: Thnx for the script: A cpl of questions:
1) In the script, you are setting opdeskenv to kde if answer is g and to gnome is answer is k. Is that intentional? I think this is the reason why it installs so much kde stuff even on selecting gnome.
2) Does the script work for amd64 as well or only for 32 bit..

---

### Post by bricksen on 2007-08-24
That explains why my update come up with alot of kde stuff after trying to install after the CF_Installer-Updater_v.3 :(
anyway to totally remove everything this script did....

---

### Post by dannyboy79 on 2007-08-24
> **shantzg001 said:**
> @Elemon: Thnx for the script: A cpl of questions:
1) In the script, you are setting opdeskenv to kde if answer is g and to gnome is answer is k. Is that intentional? I think this is the reason why it installs so much kde stuff even on selecting gnome.
2) Does the script work for amd64 as well or only for 32 bit..
WOW, another downside to running this script. If this is true anyway, i can't read code but when I told the author that this script installed a bunch of KDE crap like Konqueror and other stuff, he said, "well you must have had previous kde modules installed and that's why it did that" Despite me answering no, to the question it asks about having kde modules installed.

Now I get to selectively go thru and try to remove all this crap that was installed that I didn't even want.

---

### Post by joshuachad on 2007-08-24
this script worked fantastic for me doing the latest git install.

Cheers

---

### Post by glaze0101 on 2007-08-24
[LEFT]Still having porblems.  I have done everything mentioned, inc.

> Hey, try what I did. Find the libcompizconfig.so.0, sudo nautilus there, open another root nautilus, navigate to /usr/lib, drag and drop libcompizconfig.so.0 and libcompizconfig.0.0.0 to /usr/lib. These are shared libraries, so you need them both.

  I still get the following when I type in fusion-icon
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

```[/LEFT]

I am running with an Intel Integrated graphics card.  Please help.  Thanks!

---

### Post by crazyhunk on 2007-08-24
hey there....

I really like ur script.... true to ur word it is really fast than the repos....good work man... :)

I just have a small problem though tI just saw your latest script and i download it and before using it... i uninstalled the previous install from your last script.... i used the git install rather than the stable install evrything went well and it runs perfectly as well except that now i do not have the ring switcher or the shift switcher and a few others too.... so i was wondering is it tht the git dows not have these or, sorry to say,  is there a glitch in the script ...'coz i even tried to update it and i do not see these ...

other than tht great script works awesome and most of all thanx a million... :D

---

### Post by crazyhunk on 2007-08-24
> **glaze0101 said:**
> [LEFT]Still having porblems.  I have done everything mentioned, inc.



  I still get the following when I type in fusion-icon
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

```[/LEFT]

I am running with an Intel Integrated graphics card.  Please help.  Thanks!

BTW did you do this before install

```
sudo apt-get build-dep compiz
```

if no uninstall do this and then install and do not forget to say 'no' if the script asks you if u have any KDE stuff installed... 

:D

---

### Post by blueeyesmike on 2007-08-24
For those missing certain plugins (ring switcher, thumbnail previews and some others I think) It is because the new script attempts to compile each one individually from git rather than the packages (main, extra and unsupported) A good way to fix this is to install again, and when installing plugins use 'choose' instead of 'all' then just say yes to all the packages. No need to uninstall the 'all' install as there are some plugins that are not in the packages (eg 3d windows). So to get all plugins properly you really need to do both. Doing this I now have all plugins (except compiz-scheme which  appears to be a work in progress). Hope this helps.

---

### Post by amadeus266 on 2007-08-24
> **crazyhunk said:**
> BTW did you do this before install

```
sudo apt-get build-dep compiz
```

if no uninstall do this and then install and do not forget to say 'no' if the script asks you if u have any KDE stuff installed... 

:D


Quote:
Originally Posted by glaze0101 View Post
Still having porblems. I have done everything mentioned, inc.



I still get the following when I type in fusion-icon
Code:

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!


I am running with an Intel Integrated graphics card. Please help. Thanks!
BTW did you do this before install

Code:

sudo apt-get build-dep compiz

if no uninstall do this and then install and do not forget to say 'no' if the script asks you if u have any KDE stuff installed...



Didn't work for me. got the same response.

---

### Post by snsoneee on 2007-08-25
it doesn't work.help i'm noob.i open the program, but it doesn't do anything

---

### Post by adam.tropics on 2007-08-25
All good, thanks, but has anyone using this got the Shift plugin? I may well be blind...can't find it! If its not included, any chance of including it?

---

### Post by crazyhunk on 2007-08-25
> **amadeus266 said:**
> Quote:
Originally Posted by glaze0101 View Post
Still having porblems. I have done everything mentioned, inc.



I still get the following when I type in fusion-icon
Code:

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!


I am running with an Intel Integrated graphics card. Please help. Thanks!
BTW did you do this before install

Code:

sudo apt-get build-dep compiz

if no uninstall do this and then install and do not forget to say 'no' if the script asks you if u have any KDE stuff installed...



Didn't work for me. got the same response.

Ok did you uninstall compiz fusion... did the command i told you and then installed compiz fusion again...?

coz i had the same problem and this worked for me....

---

### Post by amadeus266 on 2007-08-25
Earlier today I completely removed all of compiz and everything related to it. I downloaded and ran your script - awesome by the way. I even did the step to install all the depencies first.  I installed the stable version and got the response I posted eariler. I have decided that since I don't have anything important on this machine to go ahead and do a complete reinstall from scratch and try again. I'll post again when I'm finished.

---

### Post by gelicide on 2007-08-25
> 
Quote:
Originally Posted by amadeus266 View Post
Quote:
Originally Posted by glaze0101 View Post
Still having porblems. I have done everything mentioned, inc.



I still get the following when I type in fusion-icon
Code:

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!


I am running with an Intel Integrated graphics card. Please help. Thanks!
BTW did you do this before install

Code:

sudo apt-get build-dep compiz

if no uninstall do this and then install and do not forget to say 'no' if the script asks you if u have any KDE stuff installed...



Didn't work for me. got the same response.
Ok did you uninstall compiz fusion... did the command i told you and then installed compiz fusion again...?

coz i had the same problem and this worked for me....


I'm getting that same error.  I uninstalled, ran the build-dep compiz command, and re-installed.  Still get the same error message.  Any suggestions?

---

### Post by akiratheoni on 2007-08-25
> **unabatedshagie said:**
> I've just downloaded and tried v3 of the installer but I guess there is something wrong on my end because compiz-fusion doesn't work when it's finished.

```
alex@MysteryMachine:~/Misc/Compiz Git$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```As you can see I have as suggested in a few posts above got **libxslt1-dev** installed.
```
alex@MysteryMachine:~/Misc/Compiz Git$ sudo apt-get install libxslt1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxslt1-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libmp4v2-0 libfuse2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Anyone have any ideas?

Same error here... Anyone else have a solution?

---

### Post by BRILLtheTHRILL on 2007-08-25
> **gelicide said:**
> I'm getting that same error.  I uninstalled, ran the build-dep compiz command, and re-installed.  Still get the same error message.  Any suggestions?

yup i'm gettin the same thing too.
lemme build the depo and see if it works this time.

---

### Post by amadeus266 on 2007-08-25
Just finished a fresh install of Feisty, ran the apt-get build-dep compiz command, then the script and still getting the same error
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!

```

Edit: I figured I would add my system specs, if it makes any difference.

AMD Athlon 64
ATI AIW 9200
256MB Ram
(2) 40G IDE HDD
MSI 7142 (K8VMM) Motherboard

Compiz-Fusion ran almost flawlessly before the 0.5.2 core update. Couldn't run the Water, Blur, Motion Blur, Cheat sheet and Wallpaper plugins but everything else worked.

---

### Post by BRILLtheTHRILL on 2007-08-25
seems like the installer is having some problems.
i would have no idea though :|

---

### Post by shantzg001 on 2007-08-25
I'd suggest all the users to tread with caution before Elecom replies to what I asked a few posts earlier cuz I think there is a MAJOR bug in the script (Am sorry if its not a bug and is intentionally put there) because it "appears" that the script installs kde stuff if u choose gnome and gnome stuff if u choose kde as a wrong variable is set in the beginning of the script....

---

### Post by amadeus266 on 2007-08-25
This is interesting... after I posted earlier, I reinstalled the default desktop effects and got everything working by editing gconf. I was very pleased to say the least. However, I decided to plug in my second cd drive so I turned my system off, plugged in the drive, and restarted. the drive works fine. But now the desktop effect don't!!! When run in terminal I get this:
```
me@me-desktop:~$ desktop-effects
nvidia hardware not available
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```


WTF does connecting a cd drive have to do with visual effects?????????????

---

### Post by Tiftof on 2007-08-25
> **amadeus266 said:**
> WTF does connecting a cd drive have to do with visual effects?????????????

I don't think it has anything to do with connecting a cd drive, but more likely it is connected to rebooting your pc and thus restarting X. I think your xorg.conf has been altered. Check it and maybe see if there are backups in the same folder.

---

### Post by amadeus266 on 2007-08-25
> **Tiftof said:**
> I don't think it has anything to do with connecting a cd drive, but more likely it is connected to rebooting your pc and thus restarting X. I think your xorg.conf has been altered. Check it and maybe see if there are backups in the same folder.

I don't have an xorg.conf any more!!!!! This doesn't make any sense whatsoever! X starts and I can see the desktop and everything!

---

### Post by Tiftof on 2007-08-25
> **amadeus266 said:**
> I don't have an xorg.conf any more!!!!! This doesn't make any sense whatsoever! X starts and I can see the desktop and everything!

Seems like a little error happened somewhere. Don't know why it still can boot into X though... When you run "sudo dpkg-reconfigure xserver-xorg", you can make a new xorg.conf.

---

### Post by amadeus266 on 2007-08-25
> **Tiftof said:**
> Seems like a little error happened somewhere. Don't know why it still can boot into X though... When you run "sudo dpkg-reconfigure xserver-xorg", you can make a new xorg.conf.

I was about to ask what that command was, thanks. I have run that command and am going to restart the system.

---

### Post by amadeus266 on 2007-08-25
Well, no luck. After a reboot, the screen resolution was correct but when I tried to enable desktop effects, the xserver froze. I am going to reinstall again and be smart enough to make a backup of the default xorg.conf!!! Getting late here so I'll post again tomorrow.:mad:

---

### Post by BoogieKnight on 2007-08-25
just want to chime in and say thanks for an amazing script !
got Compiz 0.5.5 and Emerald running smooth on my Ubuntu 7.04 (64bit).

---

### Post by holodad on 2007-08-25
Excellent!!
Finally got it to work... 
XCB and all effects are working fine with this script.
The previous version of the script was not working for me. XCB was not functioning... with fglrx 8.24... and previous version of script.
After installing the latest ATI driver with Envy and building CF with this script, everything is running smoothly!!!
Thanks a lot for your wonderful work
Cheers

---

### Post by nest on 2007-08-25
who has this problem:
```

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```

do this:

```
sudo apt-get remove compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager
```

it should fix the problem. worked for me :D

actually, i have another problem, my f***** ATI Raden Xpress 1250. but that is another sh*t.

---

### Post by glaze0101 on 2007-08-25
ok, so I FINALLY got this up and running!  The trick?  I ran install like normal, but when I got to the question about all or choose plugins I chose "choose" this time then installed them all.  This was the trick!  YEA.  Thanks.

That was the only thing I did other then running the script.  If you are getting errors (like I was) just try this slight modification.

---

### Post by bronze on 2007-08-25
Finally did it with some trouble (had to install CCSM and Emerald from repos), but I don't have any window borders/decorations. It's just like when you install beryl without that "addrgbxvalue" thingy in xorg.conf (which I do). Every other effect seems to be working. Does anyone know what might be wrong?

My xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Samsung SyncMaster 997MB"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7900GTX"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7900GTX"
    Monitor        "Samsung SyncMaster 997MB"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by aantn on 2007-08-25
Are there any benefits to using this instead of Trevinho's Make Debs script? His script downloads the latest code from git (including all the extra plugins), compiles everything, and packages it into debs. Does this script just do the same thing?

---

### Post by amadeus266 on 2007-08-26
After yet another reinstall, I got the defaut compiz working again and got most of the settings I actually use working through editing gconf. This will have to do until Gutsy comes out.

---

### Post by unabatedshagie on 2007-08-26
> **nest said:**
> who has this problem:
```

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
```

do this:

```
sudo apt-get remove compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager
```

it should fix the problem. worked for me :D

actually, i have another problem, my f***** ATI Raden Xpress 1250. but that is another sh*t.Thanks, that kind of worked for me, although it said I didn't have ccsm installed :confused: so I apt-getted it and compiz-fusion now works.

Also the emerald theme manager wasn't installed or most of the plugins.

I also don't have window borders.

Apart from that everythings working fine :lolflag:

It is running a lot smoother than trevino's repo one for me anyway.

---

### Post by ozzyprv on 2007-08-26
Did everything and no error. 

But I do not have Compiz running, do not have CCSM working either....

Any help?

Thanks.

---

### Post by sultanoswing on 2007-08-26
Thanks for the script.

Initially had problems with ccsm not working, but by apt-get remove / purge ALL previous instances or part instances or remnants of Beryl / Emerald / Desktop Effects & any and all Repo versions of Compiz-Fusion, it finally worked. Actually, the stable version (0.52) didn't cube rotate, but the git version has everything running sweetly (using emerald themes)!

Feisty 7.04
NVIDIA 6600GT w/97.55

---

### Post by Dark Star on 2007-08-26
Now I download ver 1 .sh file how can I install Cf via that file.. I had removed Amarnath repo.. Cf :)

---

### Post by Nossie on 2007-08-26
why didnt you download the latest version instead?
 
you run the script from a terminal with ./ in front



Can anyone tell my if some of the plugins should be missing?
I just tried this and installed it with max bloat... BUT
I cant seem to get the cube to rotate on mouse wheel AND I'm missing the tabs plugin and various other little things.... have I missed something or just not kept up with whats going on?

---

### Post by ElemonGW on 2007-08-26
> **shantzg001 said:**
> 1) In the script, you are setting opdeskenv to kde if answer is g and to gnome is answer is k. Is that intentional? I think this is the reason why it installs so much kde stuff even on selecting gnome.
IT is intentional. And the script will not try to install any kde stuff if you don't have any already installed, and in case you do have you should answer yes at the corresponding question (which is obviously something that many people don't do).

> **shantzg001 said:**
> 2) Does the script work for amd64 as well or only for 32 bit..
Probably it does work (I can't find any reason why it shouldn't work...)

> **crazyhunk said:**
> I just have a small problem though tI just saw your latest script and i download it and before using it... i uninstalled the previous install from your last script.... i used the git install rather than the stable install evrything went well and it runs perfectly as well except that now i do not have the ring switcher or the shift switcher and a few others too.... so i was wondering is it tht the git dows not have these or, sorry to say,  is there a glitch in the script ...'coz i even tried to update it and i do not see these ...
When the script questions you which plugins you want to install you should answer all. Then re-run the script and reach the step where it asks you about the plugins again (you may skip the previous steps). Now answer by packages and install them all. You will now have all the available plugins in your system. In the next revision this will be fixed but until then this is what you should do.

EDIT : Just show that [blueeyesmike has already answered]("http://ubuntuforums.org/showpost.php?p=3248817&postcount=413") ;) .

---

### Post by ozzyprv on 2007-08-26
> **amadeus266 said:**
> This is interesting... after I posted earlier, I reinstalled the default desktop effects and got everything working by editing gconf.....

How do you reinstall the default Desktop Effect?

Thank you.

---

### Post by Nossie on 2007-08-26
Elmon, I'm having the same problem... and I did answer all :-| missing viewport switching, tabs and a few others...

---

### Post by Nossie on 2007-08-26
I went back through it all... uninstalled re-installed... etc 

and now I'm still missing tabs and 3d windows (I had 3d windows before but not view port mouse switching) :-Z

anyone got any ideas?

---

### Post by ElemonGW on 2007-08-26
> **amadeus266 said:**
> This is interesting... after I posted earlier, I reinstalled the default desktop effects and got everything working by editing gconf. I was very pleased to say the least. However, I decided to plug in my second cd drive so I turned my system off, plugged in the drive, and restarted. the drive works fine. But now the desktop effect don't!!! When run in terminal I get this:
```
me@me-desktop:~$ desktop-effects
nvidia hardware not available
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```


WTF does connecting a cd drive have to do with visual effects?????????????

When launching it with desktop-effects it is for sure that it will not work. Launch it with fusion icon or with one of the commands posted [here]("http://forum.compiz-fusion.org/showpost.php?p=16632&postcount=6") (which one you should use depends on your situation).

---

### Post by arashiko28 on 2007-08-26
After i installed everything, I could not find the compiz fusion icon, found it on applications and system tools folder, where i used to have beryl manager, but the button does not start the compiz fusion, and on system, preferences, the compizconfig settings manager does not start the tettings manager. I ctrl+alt+backspace and its the same. And now my video player (vlc) do not respond and lost audio. Have force quit the programs of video and audio to close them:confused::confused::confused::confused::confused::confused: where did i messed up?:confused::confused:

---

### Post by ozzyprv on 2007-08-26
> **arashiko28 said:**
> After i installed everything, I could not find the compiz fusion icon, found it on applications and system tools folder, where i used to have beryl manager, but the button does not start the compiz fusion, and on system, preferences, the compizconfig settings manager does not start the tettings manager. I ctrl+alt+backspace and its the same. And now my video player (vlc) do not respond and lost audio. Have force quit the programs of video and audio to close them:confused::confused::confused::confused::confused::confused: where did i messed up?:confused::confused:

I had exactly the same problem arashiko28. So far no luck. 

I was so frustrated that I did a clean reinstall of Ubuntu. I am re-installing the latest Nvidia driver now.

If you get it to work please let me know.

---

### Post by RobNyc on 2007-08-26
Will this work good with both kde and gnome ?

---

### Post by Nossie on 2007-08-26
ok can someone tell me why everytime I reinstall this script ... some plugins get disabled and others become enabled?

1st time  I had 3d windows, reflections but no viewport switchng
2nd time I had view port switching, no 3d windows.. no tabs, no reflections
3rd time I have tabs, viewport switching, scale extras, reflections   but dont have scale, 3d windows etc

No offence but am I doing something wrong or is this script pick and mix? I follow the same procedure everytime and each time I recieve different results :-|

---

### Post by amadeus266 on 2007-08-26
> **ozzyprv said:**
> How do you reinstall the default Desktop Effect?

Thank you.

I did it by removing the version installed by the script and then reinstalling desktop-effect using synaptec. worked fine for me.

---

### Post by ozzyprv on 2007-08-26
> **amadeus266 said:**
> .. then reinstalling desktop-effect using synaptec. worked fine for me.

Do you remember the name of the package by any chance?

---

### Post by ElemonGW on 2007-08-27
> **amadeus266 said:**
> I did it by removing the version installed by the script[..]
CF Installer-Updater doesn't install any other version of desktop effects. It just removes it if you have it installed.

---

### Post by Dark Star on 2007-08-27
Can you tell me how install Snow plugin in Cf.. I updated my Cf using your updater :)

---

### Post by MrGreen on 2007-08-27
Could not get anything to work so ran fusion-icon in a terminal got

```
 fusion-icon 
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named compizconfig
... Trying another interface
* Using the Qt3 Interface
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
RuntimeError: the qt and PyQt4.QtCore modules both wrap the QObject class

```

I use Gnome do I need to have qt installed ? used version 3 is that correct? I do have some KDE stuff installed konq etc...

MrG

---

### Post by dannyboy79 on 2007-08-27
> **MrGreen said:**
> Could not get anything to work so ran fusion-icon in a terminal got

```
 fusion-icon 
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named compizconfig
... Trying another interface
* Using the Qt3 Interface
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
RuntimeError: the qt and PyQt4.QtCore modules both wrap the QObject class

```

I use Gnome do I need to have qt installed ? used version 3 is that correct? I do have some KDE stuff installed konq etc...

MrG

Just a suggestion, give up on this script and go with Trevino's Repo. This script caused hell on my machine and installed a bunch of KDE crap and I could never get it to work either running it as root or as my normal user. It's not like it provides anything better as Trevino's is from git as well!!!!!

---

### Post by dannyboy79 on 2007-08-27
> **ozzyprv said:**
> I had exactly the same problem arashiko28. So far no luck. 

I was so frustrated that I did a clean reinstall of Ubuntu. I am re-installing the latest Nvidia driver now.

If you get it to work please let me know.
exactly, this script as far as MY OPINION is NOT good at all!!!!! I never got it to work, it installed a bunch of KDE crap I didn't even want. Trevion's Repo is just as good as it's from git as well!!!

---

### Post by dannyboy79 on 2007-08-27
> **amadeus266 said:**
> Earlier today I completely removed all of compiz and everything related to it. I downloaded and ran your script - awesome by the way. I even did the step to install all the depencies first.  I installed the stable version and got the response I posted eariler. I have decided that since I don't have anything important on this machine to go ahead and do a complete reinstall from scratch and try again. I'll post again when I'm finished.

sounds to me like installing bleeding edge compiz-fusion using this script and NOT having it work then resulting in having to do a reinstall makes for a script that I would STRONGLY discourage users from using!

FYI=Trevino's Repo's packages are created from git as well so what's the point of installing using this script which will install a bunch of KDE crap (Kate, Konqueror and others even if you only had  1 KDE app installed) and NOT even work.

JUST MY OPINION :)

---

### Post by MrGreen on 2007-08-27
point me to this repo I will give it a shot..... bit concerned about the stuff being loaded while script was running

---

### Post by dannyboy79 on 2007-08-27
> **MrGreen said:**
> point me to this repo I will give it a shot..... bit concerned about the stuff being loaded while script was running

[http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

---

### Post by number3pencil on 2007-08-27
I finally got the script to work after trying MANY different things.  the thing that worked was purging EVERY last remenance of beryl, compiz, and emerald then using the script.  Compiz runs so much faster and more smooth with the script, its almost unbelievable.  I'm glad I got it working.

---

### Post by Jeff_From_VA on 2007-08-27
> **number3pencil said:**
> I finally got the script to work after trying MANY different things.  the thing that worked was purging EVERY last remenance of beryl, compiz, and emerald then using the script.  Compiz runs so much faster and more smooth with the script, its almost unbelievable.  I'm glad I got it working.


Congrats to you, I spent the last hour trying to get this script to work....

Would you please detail what commands one needs to run to purge every last remnant of beryl, compiz, and emerald so this script will work?  I could use some serious help here - LOL

---

### Post by Schleeb on 2007-08-27
I admit, I've only skimmed through this thread....so if someone's already stated this, my apologies.

I attempted to install this script earlier this morning, and thought it odd the number of KDE things it installed in the process.

Turns out it's because of this:

echo -e "\033[1mDo you use Gnome or KDE?(g/k):\033[0m" ; read answer
if [ $answer = g ] ; then
	opdeskenv=kde
elif [ $answer = k ] ; then
	opdeskenv=gnome
else
	echo -e "\033[1mInvalid answer\033[0m"
	exit


Gnome, one would think, would be represented by g, and KDE by k, but if I'm reading this correctly, someone got the two mixed up.

Things appear to have run much smoother when I then chose k, for Gnome, but I haven't had a chance to verify it yet....

Anyway, am I reading that mistake right, or am I being stupid?

---

### Post by MrGreen on 2007-08-27
which script is that from ? v1 or v3?

---

### Post by Jeff_From_VA on 2007-08-27
Thanks for the tip on choosing kde over gnome, now it does not try to install KDE for me...

I get this error on just about everything "Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix."

I need to read back through the thread and see if it's been addressed before.

---

### Post by Jeff_From_VA on 2007-08-27
OK, I decided to go ahead and let it install all of KDE - now the script will let most of it compile but crashes during the compile of the addons.   

I think I am going to give up on this one for now, and look into my options for ubuntu ultimate which has this working and also a ton of useful apps that I would install anyway right out of the box.  

Thanks much for your efforts on this script!!!!  I will be keeping an eye out for a more stable future release once you have had time to improve on this.

---

### Post by ElemonGW on 2007-08-27
> **Jeff_From_VA said:**
> Thanks for the tip on choosing kde over gnome, now it does not try to install KDE for me...

I get this error on just about everything "Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix."

I need to read back through the thread and see if it's been addressed before.

Look [here]("http://ubuntuforums.org/showpost.php?p=3256453&postcount=443")

> **Jeff_From_VA said:**
> OK, I decided to go ahead and let it install all of KDE - now the script will let most of it compile but crashes during the compile of the addons.   

I think I am going to give up on this one for now, and look into my options for ubuntu ultimate which has this working and also a ton of useful apps that I would install anyway right out of the box.  

Thanks much for your efforts on this script!!!!  I will be keeping an eye out for a more stable future release once you have had time to improve on this.

Crashes? Really? This is the first time I hear that. What error it gives you? When? (addons??? - you mean plugins?)

----------------
Now playing: [Green Day - Boulevard Of Broken Dreams](http://www.foxytunes.com/artist/green+day/track/boulevard+of+broken+dreams)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by mzmiric5 on 2007-08-27
Hi people, i'm new to linux and i need help with cf!!!
I have  Ubuntu 7.04 x64 running on Core 2 Duo and 2x8600GT(is there any possibility of enabling SLI?).
I have tried this script for a few times(i select gnome, install everything from git, and i answer y to nvidia q(before using this script i installed nvidia drivers for Linux AMD64/EM64T because my 8600s are not supported by ubuntu integrated drivers). After script is over i get my compiz running and i lose my windows borders and titlebar. After reboot compiz doesn't start although i have added cf icon to session startup. After going trough all options in compiz configurator i have decided to reinstall my cf. I run the script and selected (un)install i then u. After that according to script my compiz is uninstalled. I reboot and start the script again. Installation finishes and i try running compiz, nothing happens, try alt+f2 then compiz --replace, nothing happens, i try restart, shutdown, logoff, reboot, ubuntu crashes. So now i'm wipeing my disk. And before i try one more time any suggestion that could help me. :confused::confused:

Thanks in advance

---

### Post by number3pencil on 2007-08-27
> **Jeff_From_VA said:**
> Congrats to you, I spent the last hour trying to get this script to work....

Would you please detail what commands one needs to run to purge every last remnant of beryl, compiz, and emerald so this script will work?  I could use some serious help here - LOL

All I did was go to synaptic and search for beryl, compiz, and emerald than I right clicked everything and selected completely remove.  There may have been an easier way, but thats what I did.

---

### Post by Taragudrig on 2007-08-27
I've been trying to get this to work for an hour now. Every thing compiles fine, but when the script tries to install compiz, it tells me that libxslt. I've tried to install it through apt-get, but it only show up the package libxslt1 and when I try to install it nothing happens. Any help would be very much appreciated, thanks in advance.

---

### Post by Vorian on 2007-08-27
> **dannyboy79 said:**
> 
JUST MY OPINION :)
We've heard your opinion over and over again, I don't think we need to hear it again.

---

### Post by Jeff_From_VA on 2007-08-28
> **ElemonGW said:**
> 
Crashes? Really? This is the first time I hear that. What error it gives you? When? (addons??? - you mean plugins?)


Yes I mean the script crashed, as in the error messages from something that went wrong, were injected into bash, and bash complained about command not found, the command it complained about I no longer have, but it was an error from previous failed commands in the script, that tried to run as a command. 


I have been fighting this all day.

I broke down and installed ubuntu ultimate, and kept that for 30 minutes or so.  I only abandoned that because it does not yet support a few things I need (software raid via alternate disk, and 64 bit), the second it does support those things, I am going back, it is everything I want, all rolled up into an easy to keep up with package.

Once I abandoned ultimate, I reinstalled feisty from alternate.  Fresh formatted partions, all I did was use febe in firefox to get firefox back to the way I like it, I installed via envy the driver I need for my 8400gs card (only because ubuntu does not yet have a late enough driver to support my card), then I went off on a quest to make CF work.

I chose to start at the beginning, and end at the end.  I don't just mean "start over in running this script from a fresh install way". I mean in a choose to read up on "my options for getting CF, weighing those options against my ultimate goals, and forming a plan accordingly" kind of way.  

I chose to go with Amarath's repo.  The reason I chose this was simple for me.  While I like the idea of bleeding edge, and the benefits that do come with it.  I also would like the ability to build a somewhat stable box, with some bleeding edge type features, and still have the ability to upgrade to gutsy when that becomes available, in a somewhat seamless fashion.  

I had some issues today after the upgrade.  CF was installed but did not seem to do anything at all.  That was resolved by a post on the compiz forum I came across that instructed me to 

```
(CCSM &#8594; Preferences &#8594; Backend)

Ubuntu uses gconf by default, that might act weird sometimes.
```

That fixed all but the cube being two sided... Even though I had 4 workspaces in gnome in the bottom right corner.  I found the answer to this on this forum.  

```
ccsm->general->general options->desktop size  horizontal = 4 ---  vertical = 1----- number of desktops = 1
```

So far after that, all seems to be working fine.   My CF will not be near as nice as the people that find success from this thread, but it does allow me to make a seamless upgrade to gutsy in a couple months, and it ensures a stable version of CF. Two things I value more then the advantages offered by this wonderful script.   

I am fully sure that now that I better understand this script, I would have been able to get it working on my clean install.  When I tried this at first, I was on a somewhat hosed box, that had tried and failed many attempts, and paths to CF.  I am sure that left me in a working, but not even close to right, situation.

I thank the author of this script for his/her attempts, and all the work they put into this.  It's easy for any of us to get frustrated, pissed off, and start in on a rant about how the fix they get does not work etc.  -- I started down that same path today, and would like to apologize to the author of this for that.  I truly do realize that you are just a guy, with a life, a family, a job, etc, same as me, and that by providing this in your free time, you make many happy.   I hope you did not take offence to my terse and frustrated attitude when I could not make it work.

---

### Post by ElemonGW on 2007-08-28
> **Vorian said:**
> We've heard your opinion over and over again, I don't think we need to hear it again.

[img]http://www.thesmilies.com/smilies/happy/applause.gif[/img]		[img]http://www.thesmilies.com/smilies/happy/thumbsup.gif[/img]		[img]http://www.thesmilies.com/smilies/happy/yes.gif[/img]

---

### Post by galv on 2007-08-28
Hello,
I've search but I've not found the answer :(
Does this script works with XFCE?

Thanks

---

### Post by 0ziris on 2007-08-28
I have installed compiz on a freshly installed ubuntu  with this script and when I select compiz window manager I have no window borders (no minimize, maximize,... etc).  I have attached my xorg.conf.  Can anyone tell me what am I doing wrong? :(

---

### Post by ElemonGW on 2007-08-28
> **0ziris said:**
> I have installed compiz on a freshly installed ubuntu  with this script and when I select compiz window manager I have no window borders (no minimize, maximize,... etc).  I have attached my xorg.conf.  Can anyone tell me what am I doing wrong? :(
You should also select emerald as your window manager.

---

### Post by ElemonGW on 2007-08-28
> **galv said:**
> Hello,
I've search but I've not found the answer :(
Does this script works with XFCE?

Thanks
Unfortunately, I don't think that it will work.

---

### Post by mzmiric5 on 2007-08-28
ok, as no1 responded to my post, i decided to give cf 1 more try. and i was succesful. everything was working fine, and i was browsing in ff and suddenly my screen goes blanc and ubuntu chrashes.  Afrer reboot compiz render just the top left part of the screen. what should i do to fix this?

thanks in advanced

---

### Post by dannyboy79 on 2007-08-28
> **Vorian said:**
> We've heard your opinion over and over again, I don't think we need to hear it again.

user's aren't going to read all the pages in the middle so if I'd like to warn people of problems on each page I am entitled to do so. I don't believe there's anything in the COC that states it's ok for mods to tell me how many times I can post my opinion.

---

### Post by mzmiric5 on 2007-08-28
ok, tnx, it didnt installed any of kde s*** for me. i fixed it. was something with my xorg and graphics drivers. BTW is compiz in any way related for problems like: my mouse stops working randomly, my keybord freezes, etc.

Does anybody knows how to enable sli on nvidias linux drivers, cos it says it is supported

---

### Post by 0ziris on 2007-08-28
> **ElemonGW said:**
> You should also select emerald as your window manager.

Well, I finally figured out what was wrong. Of course I selected emerald, however it didn't work. And  what I found out was that my settings set in Settings manager were not saved. Each time I press reload everything is reset. What is wrong?

---

### Post by arashiko28 on 2007-08-28
:evil::evil:](*,)[-(  I GIVE UP!!!! 15 attempts have had it!!! nothing works!!! as a i said on a previous post, at first it was the window borders, then the window insides, then audio and video, and now it just does nothing, not at startup, not at selecting it from the menu, nothing!!!! I'll wait until it comes installed or see if I can install ubuntu ultimate. I have read this thread a 150 times, combined new outcomes, tryouts alone, nothing!!! good luck to you all!](*,)](*,)](*,)](*,)

---

### Post by st33med on 2007-08-28
What repo you choose is fine, however, I have found the git repo in this script works just fine. I have problems with installing stable.

---

### Post by joshuachad on 2007-08-28
dannyboy, No offense but i think you are confused cuz you dont have any idea what you talking about. All packages and I mean all have to be built from some source git or whatever. So when you say that Trevinos repo is built from git thats the say as say gstreamer in ubuntu's repo is built from source so it should work just as good. Sorry but thats not always the case. And the people are not saying that if you build from git with this script that 100% of the time for all people it will work better. It didnt work for you so its almost as if you dont want others to use it cuz you couldnt manage to make it work. At any rate, personal expirience over multiple installs on multiple systems this installing compiz using this script choosing git source compiz runs at least 25% faster and less buggy.

---

### Post by Frak on 2007-08-28
Yes, but in many ways debs are better because most of the installation bugs can, and probably are already worked out.

---

### Post by chiinox on 2007-08-28
Any one know how to remove all the KDE stuff that was installed by one of the earlier scripts.  I pressed NO to KDE but still got the desktop installed along with all the apps.  I tried "sudo aptitude remove kde-core" but no glory also tried "sudo aptititude remove kubuntu-desktop" and nothing.  I had forgotten that the earlier script installed KDE but just got a bunch of updates for it and want to get rid of it to free up harddrive space.

Thanks

---

### Post by brucewagner on 2007-08-29
Is this information old now...?

I am a brand new user of Ubuntu, and I attempted to install Compiz-Fusion...  using this automated script...

It was supposed to be completely automated and simple.

But it was NOT.

It asked a lot of questions I had no idea how to answer....

And when it was finally finished running...

I see nothing different...  Except that I now see, under System-->Preferences,  a "CompizConfig Settings Manager"...   But it does nothing.

Also, I now no longer have "Desktop Effects"...

I have no idea what went wrong...  or if I should have even attempted to install  Compiz-Fusion... 

I really wanted to keep my installation of Ubuntu very safe and secure and "official"...  and STABLE....

I'm now thinking that maybe I should just back up my data, and reinstall Ubuntu from the CD again from scratch...

Thoughts?

Bruce Wagner
[http://brucewagner.com](http://brucewagner.com)
[email]bruce@brucewagner.com[/email]

---

### Post by spartacus13b on 2007-08-29
I installed everything and when I click on the icon to launch the program nothing happens....

can anyone help

---

### Post by MrGreen on 2007-08-29
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Just tried this method and it worked.... :)

HTH

MrG

---

### Post by dannyboy79 on 2007-08-29
> **MrGreen said:**
> [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Just tried this method and it worked.... :)

HTH

MrG
just so you're aware. this post will get jailed. I have been suggesting to people that they should try out trevino's repo if they have issues with this script because I had nothing but problems with it and like the poster above mentiioned, it installed all this KDE stuff that I didn't even want. Apparently, according to kwinz and 2 other admin's, people can't suggest methods other than the original thread or it gets jailed because "it's off topic"..... i was even given a disciplnary point against my account for it. if you think that's unfair please post here why: [http://ubuntuforums.org/showthread.php?t=537081](http://ubuntuforums.org/showthread.php?t=537081)

---

### Post by bapoumba on 2007-08-29
> **dannyboy79 said:**
> just so you're aware. this post will get jailed. I have been suggesting to people that they should try out trevino's repo if they have issues with this script because I had nothing but problems with it and like the poster above mentiioned, it installed all this KDE stuff that I didn't even want. Apparently, according to kwinz and 2 other admin's, people can't suggest methods other than the original thread or it gets jailed because "it's off topic"..... i was even given a disciplnary point against my account for it. if you think that's unfair please post here why: [http://ubuntuforums.org/showthread.php?t=537081](http://ubuntuforums.org/showthread.php?t=537081)
Dannyboy, let it go. I'm answering here, and I have not problem to have my post moved out of the way because it is OT. My point is, in the Resolution Center, only the OP and admins can post. So please do not ask other members to post there, it's useless. Thanks.

---

### Post by Nossie on 2007-08-29
Dannyboy, let it go... whether this script works or not you've said your piece

give 5 reasons why this script sucks and leave, find something that does work for you

---

### Post by brucewagner on 2007-08-29
Ok.

I posted a question in this thread yesterday, and someone else posted another one after me...

Yet neither was even Acknoledged by anyone...

Is this forum "read only", or "a helpful community"...?

---

### Post by MrGreen on 2007-08-29
I am very sorry for my post, I read that some users were having problems thought I would try to help please remove my post 

It will not happen again 

MrG

---

### Post by dannyboy79 on 2007-08-29
> **Nossie said:**
> Dannyboy, let it go... whether this script works or not you've said your piece

give 5 reasons why this script sucks and leave, find something that does work for you

i never said the script sucks.
5 reasons why it's not good

1. only 1 person is here to support it and when I needed help I didn't get answers to my issues.

2. it installs KDE APPLICATIONS (not only libs) and does NOT ask you to do so.

3. the guide does not tell you what it will ask and how to answer the questions.

4. trevino's repo is built fetches the latest git snapshot, and builds it with some patches and configuration ennhancements which this bash script claims to do, how can this one be any different?

5. the obvious one, I couldn't get it to work even spending 3+ hours trying.

---

### Post by cptjaben on 2007-08-29
After completing the install using the script, I get this message when I run compiz in the terminal.

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

Does anyone know how to fix this problem? I have an ATI X1700 with 3d acceleration. Thanks

---

### Post by Nossie on 2007-08-29
> **brucewagner said:**
> Ok.

I posted a question in this thread yesterday, and someone else posted another one after me...

Yet neither was even Acknoledged by anyone...

Is this forum "read only", or "a helpful community"...?

I think I've asked a question 3 - 4 times in here and haven't had them even remotely noticed (until danny replied hehe)  I wouldn't say it was the community, I've had some fantastic support and insight on this forum.  I do think however that this thread is undermanned... and the guy that is writing the code whose English is not native is having a problem keeping up.  If it wasn't for the fact he seems unable to give details on the script I would have suggested the compiz forum would help you better in this situation.  Atleast if you use the git repo's debs then you'll have more of a leg to stand on asking in their forum.

I've managed to fix most of my problems but I cant tell if the lack of the 3d window plugin is something to do with git or this script :-|  try what danny has suggested to see if you get better results from that, I switched to this one because no matter how hard I tried I couldnt get the control panel to work with trevinos packages.


> **dannyboy79 said:**
> i never said the script sucks.
5 reasons why it's not good

1. only 1 person is here to support it and when I needed help I didn't get answers to my issues.

2. it installs KDE APPLICATIONS (not only libs) and does NOT ask you to do so.

3. the guide does not tell you what it will ask and how to answer the questions.

4. trevino's repo is built fetches the latest git snapshot, and builds it with some patches and configuration ennhancements which this bash script claims to do, how can this one be any different?

5. the obvious one, I couldn't get it to work even spending 3+ hours trying.


1. Thats right, only one person, on a 50 post thread... and he has made what? 3 - 4 revisions?
2.  It asked me if I had KDE installed when the script ran, did you get that or nothing at all? sounds like a bug he OR, someone else that knows how, should please look into
3.  The script I thought was quite logical, apart from the bit where 'i' meant install or uninstall when 'u' meant upgrade... no its not a perfect script by any means, but I cant write a better one... can you? I read earlier in the thread that you sometimes you get better results with plugins if you choose 'choose' rather than all.


4. Trevino's builds are built from the nightly releases and so (I believe) are always a few days or up to a week older than the WIP in git.  It also means that more people have had a chance to test the code and can be reasonably satisfied they will work.

This script pulls the raw code from the up to the minute git and compiles from scratch... like CVS builds, git is not always stable... I'm using this as a last resort because of my problem detailed above... but it also means you get the latest features... and the latest bugs.  I know there is a 'stable' option in the script... but funnily enough I had more luck with the git version..

This guy (and I'm too lazy to find the poor mans name) put in the effort to write the script for the benefit of the community, nothing more, nothing less..   Obviously some people are finding this thread useful and if you look on google Trevino's packages sometimes get warned off also.  I just think you've made your point and everyone is well aware of your opinion  :(  I just dont think you should carry the chip on the shoulder just because you've had a problem when some people atleast have found this script a saving grace.

So its not that I... or I believe any of us feel that your wrong, just that your starting to troll your point a little when really its a 'suck it and see' issue to begin with :-|

take care,
Ian.

---

### Post by ElemonGW on 2007-08-29
> **dannyboy79 said:**
> just so you're aware. this post will get jailed. I have been suggesting to people that they should try out trevino's repo if they have issues with this script because I had nothing but problems with it and like the poster above mentiioned, it installed all this KDE stuff that I didn't even want. Apparently, according to kwinz and 2 other admin's, people can't suggest methods other than the original thread or it gets jailed because "it's off topic"..... i was even given a disciplnary point against my account for it. if you think that's unfair please post here why: [http://ubuntuforums.org/showthread.php?t=537081](http://ubuntuforums.org/showthread.php?t=537081)

You know, it is not always what you say but the way you say it and when you say it. First you were really rude and 2. you proposed to others to install CF from repos when the problem they had made it clear that it would definetely not resolved that way.

> **dannyboy79 said:**
> 1. only 1 person is here to support it and when I needed help I didn't get answers to my issues.
I tried to help you. However you were rude and you didn't answered to my questions. Indeed you kept on saying your things and flaming.


> **dannyboy79 said:**
> 2. it installs KDE APPLICATIONS (not only libs) and does NOT ask you to do so.
First it doesn't unless you "tell" it to do so (i explained that at a previous post). Furthermore, apt-get informs you which packages is going to install so everything related to kde is not installed unless YOU approve it.

> **dannyboy79 said:**
> 3. the guide does not tell you what it will ask and how to answer the questions.

> **dannyboy79 said:**
> 4. trevino's repo is built fetches the latest git snapshot, and builds it with some patches and configuration ennhancements which this bash script claims to do, how can this one be any different?.
Because compiling from source is (almost?) always better than installing from packages (at least from personal experience...).

> **dannyboy79 said:**
> 5. the obvious one, I couldn't get it to work even spending 3+ hours trying.
I haven't ever heard of something working for everybody. And we might be able to get around your problems if you were cooperative...

> **cptjaben said:**
> After completing the install using the script, I get this message when I run compiz in the terminal.

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

Does anyone know how to fix this problem? I have an ATI X1700 with 3d acceleration. Thanks

How you tried to launch it? I assume with compiz --replace .this is not the right way. You should do so from Compiz Fusion Icon.

---

### Post by ElemonGW on 2007-08-29
> **brucewagner said:**
> It was supposed to be completely automated and simple.

But it was NOT.
1. Who told that it was supposed to be completely automated?
2. I consider replying to questions simple...

> **brucewagner said:**
> Also, I now no longer have "Desktop Effects"...
This is normal. This is done to avoid conflicts.

Now, as mentioned also at the script when it finished, you should launch Compiz Fusion Icon and from there select Compiz & Emerald.

---

### Post by Frak on 2007-08-29
> **dannyboy79 said:**
> 1. only 1 person is here to support it and when I needed help I didn't get answers to my issues.

So are many Linux distro's.
You don't see me going to other people and saying "well 'X' sucks because there is no support, you should use Ubuntu"

Get over it.

---

### Post by dannyboy79 on 2007-08-29
> **ElemonGW said:**
> 
First it doesn't unless you "tell" it to do so (i explained that at a previous post). Furthermore, apt-get informs you which packages is going to install so everything related to kde is not installed unless YOU approve it..
I would like to address these statements.
You state that I was rude? I was only rude back to you when I pointed out an error in post number 369 and you tell me the answer is "self explained".  Not all of us know what to do when we read something like what you say is "self explained":

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
CF_Installer-Updater_v.2_rev.1.sh: line 69: cd: /root/compiz/compiz: No such file or directory
CF_Installer-Updater_v.2_rev.1.sh: line 70: ./autogen.sh: No such file or directory
Would you like to install Compiz Fusion Option Code Generator?(y/n):y
git, the filemanager with GNU Interactive Tools, is now called gitfm.
If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).#
This transition script will be removed in the debian stable
release after etch.
If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git
Press RETURN to run gitfm 

ALso, a new questions arises from running the command, can you help?
There are 2 alternatives which provide `git'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/git.transition
          2    /usr/bin/git-scm

Press enter to keep the default[*], or type selection number: 

What do I pick?

How would a normal user not experienced with git (this is myself and I am sure other's) know that they want to "transition early" and are suppose to in fact run the command that you say is self explained? I don't understand how hard it would be to update your guide or thread to put "gotcha's" in it.

Also, your script does not at any point (the lat version 3 that I tried) ask the user if they want to install KDE apps, it asks about modules or was it libraries, NOT Applications. Despite me hitting NO, it still installed them without my approval. So whe you say, I told apt to install them, that's just false and I don't why you can't see that.

Thats all I have to say. I would also like to point out that if this script was written well enough along with a guide that explained what's going to occur and common issues, there certainly wouldn't be 500+ posts.

Don't get me wrong here, it's a great idea, I just think there are some issues and that's all I have been trying to inform other users of.

---

### Post by Nossie on 2007-08-29
Danny,

I certainly never got those errors... I'm not sure if its his script or a lack of dependencies? I take it you've tried installing git from the deb repository?  when I ran the script I just had yes no answers, nothing about installing git with default settings etc.... Elemon only has control over his script.. not git, not the compiz git source, just the way to grab it, compile it and fit it into ubuntu

It certainly sounds like a bug regarding your KDE apps I have both gnome and kde installed so I just typed yes to that.

See in all honesty Danny? I think your a alright guy thats probably taken the authors comments the wrong way.  Elemons first language is not English,  I know people with many european backgrounds and they find it difficult to use their English vocabulary to the best use.  Not speaking for Elemon directly, I feel that his vocabulary is reasonably limited and he uses the words he does know to the best use he can.  If say you spoke a little German, and were asked a question that you might not have fully understood in German but understood enough that prerson might have overlooked something (rightly or not) rather than saying ' oh you need to go back through and look at this part...' its simply easier, less frustrating (and lets him answer more questions)

to say 'self explained' OR
Read the instructions given,
RTFA
GTFO ! (if your a regular of /. or digg)

I'm not saying he's right and the answer is there...  I'm not saying your wrong and either of you were cheeky.  But POSSIBLY. there was a little x-language misunderstanding that tipped the powder keg of your temper

*shrugs* thats giving Elemon the benifit of the doubt.

---

### Post by dannyboy79 on 2007-08-29
ok, I solved it by chosing each thing and it errored again when I chose the default, so I chose the number 2 and it appears to get farther. BUT, now it's telling me this when I tell it to install Emerald, should I do all this?

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

---

### Post by number3pencil on 2007-08-29
I have a very weird problem I hope someone can help me remedy.  After installing fusion using the script, I got this error
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```
so I installed compizconfig-settings-manager.  Now everything runs very well except that many plugins don't work.  For example when I try to enable the animations plugin, it doesn't work and the checkbox next to the plugin always unchecks itself, as though I never enabled it.  It happens for many other plugins like ADD Helper, 3D Windows, etc.  What can I do?

---

### Post by X3n0n on 2007-08-30
> **number3pencil said:**
> I have a very weird problem I hope someone can help me remedy.  After installing fusion using the script, I got this error
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```
so I installed compizconfig-settings-manager.  Now everything runs very well except that many plugins don't work.  For example when I try to enable the animations plugin, it doesn't work and the checkbox next to the plugin always unchecks itself, as though I never enabled it.  It happens for many other plugins like ADD Helper, 3D Windows, etc.  What can I do?

I have the same problem with you and can't figure out how to solve it...

---

### Post by ElemonGW on 2007-08-30
> **dannyboy79 said:**
> I would like to address these statements.
You state that I was rude? I was only rude back to you when I pointed out an error in post number 369 and you tell me the answer is "self explained".  Not all of us know what to do when we read something like what you say is "self explained":

/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.
CF_Installer-Updater_v.2_rev.1.sh: line 69: cd: /root/compiz/compiz: No such file or directory
CF_Installer-Updater_v.2_rev.1.sh: line 70: ./autogen.sh: No such file or directory
Would you like to install Compiz Fusion Option Code Generator?(y/n):y
git, the filemanager with GNU Interactive Tools, is now called gitfm.
If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).#
This transition script will be removed in the debian stable
release after etch.
If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git
Press RETURN to run gitfm 

ALso, a new questions arises from running the command, can you help?
There are 2 alternatives which provide `git'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/git.transition
          2    /usr/bin/git-scm

Press enter to keep the default[*], or type selection number: 

What do I pick?

How would a normal user not experienced with git (this is myself and I am sure other's) know that they want to "transition early" and are suppose to in fact run the command that you say is self explained? I don't understand how hard it would be to update your guide or thread to put "gotcha's" in it.
Isn't it self-explained when it tells you what you should run? Anyway, from what i remember, i had told you what you should do....


> **dannyboy79 said:**
> Also, your script does not at any point (the lat version 3 that I tried) ask the user if they want to install KDE apps, it asks about modules or was it libraries, NOT Applications. Despite me hitting NO, it still installed them without my approval. So whe you say, I told apt to install them, that's just false and I don't why you can't see that.
1. It doesn't ask you if you want to install them. It asks you if you have any already installed.
2. apt-get asks you for confirmation of what it is going to install. So, without you agreeing and choosing y at apt nothing will happen.


@ everyone having this error:
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```
This error (from what it says) seems to appear because compizconfig wasn't successfully installed. You may anyway want to ignore this and try installing python-qt4 and python-qt4-dev. The problem will be probably fixed then.


> **dannyboy79 said:**
> ok, I solved it by chosing each thing and it errored again when I chose the default, so I chose the number 2 and it appears to get farther. BUT, now it's telling me this when I tell it to install Emerald, should I do all this?

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Just ignore it....

---

### Post by X3n0n on 2007-08-30
> **number3pencil said:**
> Now everything runs very well except that many plugins don't work.  For example when I try to enable the animations plugin, it doesn't work and the checkbox next to the plugin always unchecks itself, as though I never enabled it.  It happens for many other plugins like ADD Helper, 3D Windows, etc.  What can I do?

What about this problem? any solution yet?

---

### Post by sultanoswing on 2007-08-30
> **X3n0n said:**
> What about this problem? any solution yet?

Solved for me by uninstalling EVERYTHING via the script's uninstaller and also manually deleting .compiz and .cf_i-u and .emerrald folders from /home/user and reinstalling (I use the git version).

---

### Post by Tiftof on 2007-08-30
Hi everyone,

I've been following this thread for a while now. I've been messing around with the last two releases of this script. Yesterday I finally got it working almost completely (some plugins still won't run). I thought I would post the things I did to get it running:

- before running the script, do "**sudo apt-get build-dep compiz**". This will install all the packages needed compile compiz. Some of them aren't being installed by the script. This command will also install a couple of kde packages. I think it's allright to leave those out though.

- To get fusion-icon running: before compiling it try installing the **python-qt4-dev** or python-qt-dev.

- Fusion-icon wouldn't run either because of libcompizconfig.so.0 not being in /usr/lib/. I solved this with "**sudo ln -s /usr/local/lib/libcompizconfig.so.0 /usr/lib/libcompizconfig.so.0**". Making a link is better than just copying. If there is an update for libcompizconfig you won't have to copy the file again.

- Last problem I had was with emerald. It wouldn't fin libemeraldengine.so.0. Solved it with a similar command as in the previous step: "**sudo ln -s /usr/local/lib/libemeraldengine.so.0 /usr/lib/libemeraldengine.so.0**"

- I also had to **run the script more than once**. Running it once didn't do everything: a lot of plugins wouldn't load. I ran the install script again (but then choosing to choose witch plugins to install instead of telling it to install them all, and the confirm every plugin one by one) and after that I also did an update.

These might fix some of your problems. I do hope so. But after all these steps I still hae plugins that won't load because of some version mismatch.
For now I gave up on this script though. I compiled it myself without using the script. I followed these instructions: [http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985) . It's a lot to do by hand but everything worked from the first time.
Thanks ElemonGW for the script though. For those who can run it without problems, it's really great to compile compiz so easily. Hopefully you can fix it so it'll run for everyone.

---

### Post by X3n0n on 2007-08-30
> **sultanoswing said:**
> Solved for me by uninstalling EVERYTHING via the script's uninstaller and also manually deleting .compiz and .cf_i-u and .emerrald folders from /home/user and reinstalling (I use the git version).

Thanks you! I'll try and post later.


EDIT: Well I couldn't fix it...Maybe the problem lies somewhere else...

---

### Post by dannyboy79 on 2007-08-30
> **ElemonGW said:**
> 1. It doesn't ask you if you want to install them. It asks you if you have any already installed.
2. apt-get asks you for confirmation of what it is going to install. So, without you agreeing and choosing y at apt nothing will happen.


@ everyone having this error:
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```
This error (from what it says) seems to appear because compizconfig wasn't successfully installed. You may anyway want to ignore this and try installing. The problem will be probably fixed then.




Just ignore it....
thank you for the help. I seem to have it working finally. It must have been the update-alternatives thingy the whole time. I wonder why they got rid of the ring switcher, that was awesome. Also, when it asks if I have any KDE apps installed, you're saying that I should have answered yes originally (i have k3b)  and it wouldn't have installed Konqueror, Kate and others? Also, I don't know of any way to tell apt to only install what I want it to  versus what it wants to install based on the script running, can you answer this?

One last thing, I run a dual head gfx card with 2 seperate screens. for whatever reason, screen 0 has horrible lag with ALL drop down menus. I am talking like almost 3 seconds. I tried to record my desktop but was unsuccessful with this weird app I found on the net that started with a "B". So my question is, does anyone else have this issue, if so how do I resolve it? Is it an xorg bug, a compiz bug or I have even read that this doesn't occur with kde but only gnome (gtk). Can anyone comment? THe only other issue but it's not as serious, is that the rotate desktop does NOT work on screen 0 if I try to rotate it while looking at the desktop, I hold ctrl-alt and push the mouse button and it just creates a box for highlighting purposes. BUT, heres the weird thing, If I have a window open, If I hover my mouse cursor over the top bar of any window, then try to rotate the cube, it works. HUH?

Here's my post about this horrible menu drop down lag problem as well as the cube rotate issue if anyone would like to comment:
[http://ubuntuforums.org/showthread.php?t=512894](http://ubuntuforums.org/showthread.php?t=512894)

---

### Post by ElemonGW on 2007-08-30
> **dannyboy79 said:**
> I wonder why they got rid of the ring switcher, that was awesome.
They didn't. It is a problem with the script. Until the next version comes out, here is a workaround:
When you reach the step about installing plugins choose all. Then run again the script from the beggining, go to the plugins installation step and type choose. Then install all the available packages.


> **dannyboy79 said:**
> Also, when it asks if I have any KDE apps installed, you're saying that I should have answered yes originally (i have k3b)  and it wouldn't have installed Konqueror, Kate and others?
Right!!!


> **dannyboy79 said:**
> Also, I don't know of any way to tell apt to only install what I want it to  versus what it wants to install based on the script running, can you answer this?.
There is no such a way. But it asked you and you told yes, right? That's what I told you before.

---

### Post by dannyboy79 on 2007-08-30
> **ElemonGW said:**
> 
There is no such a way. But it asked you and you told yes, right? That's what I told you before.

so why is apt run to begin with? are you saying that apt isn't run to install compiz stuff based on instructions from your script? if apt doesn't have to run for your script than why is it run asking me to install kde stuff IF I answer no the question about me having any KDE libraries installed, that's my only point here.

great job on the script itself, if you had a little bit better information regarding gotchas and possible scenarios and how to answer certain questions on the first page of this thread it would make the entire thing an excellent guide for getting compiz from git.

I'd also like to apologize for my behavior. I know it was deemed as trolling by the admins but my intentions were good and were only for ensuring other's didn't have to go through what I went through.

---

### Post by amadeus266 on 2007-08-30
> **ozzyprv said:**
> Do you remember the name of the package by any chance?


Quite simply...desktop-effects

---

### Post by firecat53 on 2007-08-30
Right before the script gets to asking about installing the Compiz Fusion Code generator, it fails with the following error:

blur.c:34:20: error: GL/glu.h: No such file or directory
blur.c: In function 'projectVertices':
blur.c:1294: warning: implicit declaration of function 'gluProject'
blur.c:1294: warning: nested extern declaration of 'gluProject'
make[2]: *** [blur.lo] Error 1

Compiling on AMD-64 w/ a 2.6.21 self-compiled kernel.

Great script! Any thoughts?

Thanks, Scott

---

### Post by frotzed on 2007-08-30
> **ElemonGW said:**
> 
@ everyone having this error:
```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```
This error (from what it says) seems to appear because compizconfig wasn't successfully installed. You may anyway want to ignore this and try installing python-qt4 and python-qt4-dev. The problem will be probably fixed then.


I was getting that error, then I installed python-qt4 and python-qt4-dev.  Now when I run fusion-icon in terminal I get this error:

```

* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named compizconfig
... Trying another interface
* Using the Qt3 Interface
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
RuntimeError: the qt and PyQt4.QtCore modules both wrap the QObject class


```

---

### Post by Ganseki on 2007-08-30
> **firecat53 said:**
> Right before the script gets to asking about installing the Compiz Fusion Code generator, it fails with the following error:

blur.c:34:20: error: GL/glu.h: No such file or directory
blur.c: In function 'projectVertices':
blur.c:1294: warning: implicit declaration of function 'gluProject'
blur.c:1294: warning: nested extern declaration of 'gluProject'
make[2]: *** [blur.lo] Error 1

Compiling on AMD-64 w/ a 2.6.21 self-compiled kernel.

Great script! Any thoughts?

Thanks, Scott

Install libglu1-mesa-dev

Peter

---

### Post by Ganseki on 2007-08-30
As of now It needs the libcompizconf library.
You can find in the git, fusion/compizconfig

Peter

---

### Post by firecat53 on 2007-08-31
> **Ganseki said:**
> Install libglu1-mesa-dev

Peter

Thanks!!  Worked great.

The only other issue was having to Choose plugins instead of installing all, because there were errors during the install all plugins. Just selecting choose and yes for each one worked perfectly!!

Thanks very much,   Scott

---

### Post by CryptiniteDemon on 2007-08-31
So I ran this script and it executed through just fine, but when i actually go click the compiz-fusion icon in the applications menu, nothing happens at all.  Or when I try it in the preferences menu, still nothing happens.

So what's up?

---

### Post by Nigmah on 2007-08-31
[COLOR=DarkOrange][B]worked first try on gutsy.
 [/B][/COLOR]

---

### Post by Opeth115 on 2007-08-31
Ok well i jsut did a reinstall and am running 64 bit feisty fawn.  whenever i try to run this and install form git i get this error when it tried to compile compiz

make[2]: *** No rule to make target `object.o', needed by `compiz'.  Stop.
make[2]: Leaving directory `/home/matt/.cf_i-u/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/.cf_i-u/compiz'
make: *** [all] Error 2


any ideas?

---

### Post by docdagger on 2007-08-31
Hi,

I tried to use the CF Installer-Updater to install compiz-fusion.  It shows the icon and the manager and all other programs you would expect are there.  The manager will not launch for me.  I can't open any of the control options except for emerald.

What suggestions do you have for me?

Thanks in advance.

---

### Post by bwakkie on 2007-09-01
I know conpiz-fusion works on my system. But when I started fiddeling with xinerama settings I lost the possibility. I have no clue how to set it back:

dell d620 intel dualcore and intel graphic card. The CF_install went without problems I think and after the command fusion-icon I get the following error:

```
~/Desktop# fusion-icon &
[1] 29238
:~/Desktop# * Using the GTK Interface
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Intel found, exporting: INTEL_BATCH=1
* Executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

I end up in a windowless gui system and after clicking in reload window manager I get metacity back.

here is my corg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath "/usr/share/X11/fonts/misc"
        FontPath "/usr/share/X11/fonts/cyrillic"
        FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/Type1"
        FontPath "/usr/share/X11/fonts/CID"
        FontPath "/usr/share/X11/fonts/100dpi"
        FontPath "/usr/share/X11/fonts/75dpi"
         # paths to defoma fonts
        FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load "GLcore"
        Load "i2c"
        Load "bitmap"
        Load "ddc"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
EndSection

Section "InputDevice"
        Identifier "Generic Keyboard"
        Driver "kbd"
        Option "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc105"
        Option "XkbLayout" "intl"
EndSection

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ImPS/2"
        Option "Emulate3Buttons" "true"
        Option "ZAxisMapping" "4 5"
EndSection

#Section "InputDevice"
#        Identifier "Synaptics Touchpad"
#        Driver "synaptics"
#        Option "SendCoreEvents" "true"
#        Option "Device" "/dev/psaux"
#        Option "Protocol" "auto-dev"
#        Option "HorizScrollDelta" "0"
#EndSection

Section "InputDevice"
   Identifier   "Synaptics Touchpad"   # Don't change this from whatever value you have set already.
   Driver       "synaptics"
   Option       "SendCoreEvents"        "true"
   Option       "Device"                "/dev/psaux"
   Option       "Protocol"              "auto-dev"

   Option       "LeftEdge"              "130"
   Option       "RightEdge"             "840"
   Option       "TopEdge"               "130"
   Option       "BottomEdge"            "640"
   Option       "FingerLow"             "14"
   Option       "FingerHigh"            "15"
   Option       "MaxTapTime"            "180"
   Option       "MaxTapMove"            "110"
   Option       "ClickTime"             "0"
   Option       "MaxDoubleTapTime"      "100"
   Option       "EmulateMidButtonTime"  "75"
   Option       "VertScrollDelta"       "20"
   Option       "HorizScrollDelta"      "20"
   Option       "MinSpeed"              "0.60"
   Option       "MaxSpeed"              "1.10"
   Option       "AccelFactor"           "0.030"
   Option       "EdgeMotionMinSpeed"    "200"
   Option       "EdgeMotionMaxSpeed"    "200
   Option       "UpDownScrolling"       "1"
   Option       "CircularScrolling"     "1"
   Option       "CircScrollDelta"       "0.1"
   Option       "CircScrollTrigger"     "2"
   Option       "SHMConfig"             "true"
   Option       "Emulate3Buttons"       "on"
EndSection

Section "Device"
        Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller 0"
        Driver "i810"
        BusID "PCI:0:2:0"
        Screen 0
        Option "MonitorLayout" "DFP,LFP"
EndSection

Section "Device"
        Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller 1"
        Driver "i810"
        BusID "PCI:0:2:0"
        Screen 1
        Option "MonitorLayout" "DFP,LFP"
EndSection

Section "Monitor"
        Identifier "Monitor"
        Option "DPMS"
EndSection

Section "Monitor"
        Identifier "External Monitor"
        Option "DPMS"
EndSection

Section "Screen"
      Identifier  "Screen"
      Device            "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller 0"
      Monitor           "Monitor"
      DefaultDepth      24
      SubSection "Display"
            Depth       1
            Modes       "1280x800"
      EndSubSection
      SubSection "Display"
            Depth       4
            Modes       "1280x800"
      EndSubSection
      SubSection "Display"
            Depth       8
            Modes       "1280x800"
      EndSubSection
      SubSection "Display"
            Depth       15
            Modes       "1280x800"
      EndSubSection
      SubSection "Display"
            Depth       16
            Modes       "1280x800"
      EndSubSection
      SubSection "Display"
            Depth       24
            Modes       "1280x800"
      EndSubSection
EndSection



Section "Screen"
        Identifier "Secondary Screen"
        Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller 1"
        Monitor "External Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 1
                Modes "1280x1024"
        EndSubSection
        SubSection "Display"
                Modes "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth 8
                Modes "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier "Dual-monitor Layout"
        Screen 0  "Screen" 0 0
	Screen 1  "Secondary Screen" RightOf "Screen"
	Option "Xinerama" "On"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
        InputDevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
        Identifier "Laptop Layout"
        Screen   "Screen"
        Option "Xinerama" "Off"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
        InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
    Option         "Composite" "1"
EndSection 
```

what is wrong? When I am on my work I have an extra LCD which I would like to use too sometimes. (xinerama or are there better sollutions?)

Thanks for any advice!

---

### Post by The Pinny Parlour on 2007-09-01
I have no windows borders.  How do I get them back please?

Very nice and easy installer BTW.  Thank you.  :)

GTK Windows Decorator has no windows borders
Emerald does?  I don't understand.

Any help would be great.

---

### Post by The Pinny Parlour on 2007-09-01
whoa! Bad bad bad

This is buggy as hell.  I really want my stable Beryl back now.  I can't use this.  Panels disappear through simple changes in CF settings.  I have to Crtl+Alt+Backslash all the time.  What a great shame.

---

### Post by Tiftof on 2007-09-01
> **The Pinny Parlour said:**
> whoa! Bad bad bad

This is buggy as hell.  I really want my stable Beryl back now.  I can't use this.  Panels disappear through simple changes in CF settings.  I have to Crtl+Alt+Backslash all the time.  What a great shame.

Why going back to beryl? Why not try Compiz Fusion from some repository? Will be better than Beryl I guess, unless you're having another problem with Compiz Fusion that is not related to this script.

---

### Post by austin1030 on 2007-09-01
holy cow - this is bad script I ever seen

I ran script as follow and nothing happen. Also, there is no compiz installed as what is claim to be.
Not only that, it asks to delete older version after installing compiz...what???? I don't think I need to explain why.

Any how, this is not so good script for sure.

BTW, if you want to bring your compiz fusion back, then add Trevino's repository

```

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-*

```

---

### Post by The Pinny Parlour on 2007-09-01
How does one totally rid/uninstall ALL this pretty desktop eye candy crap from their PC?

---

### Post by dannyboy79 on 2007-09-02
> **The Pinny Parlour said:**
> whoa! Bad bad bad

This is buggy as hell.  I really want my stable Beryl back now.  I can't use this.  Panels disappear through simple changes in CF settings.  I have to Crtl+Alt+Backslash all the time.  What a great shame.
are you sure you have to ctrl-alt-backspace? I can always just run alt-f2, then type in metacity --replace and it'll replace your window manager with metacity. OR you can just ctrl-alt f1 thru f6 and then issue ps aux | grep compiz and find out the process id, then kill it with sudo kill 76541. there's no reason to kill your xserver that I am aware of. just hang in there with the script as I had issues at first but eventually it worked and it's more stable than Trevino's repo and a little more up to date because this works right from the git repo, and who knows how often trevino updates his packages. just keep re-running the script and watching for errors. you can use "script"
to view the entire process of the script running. script will output the entire bash session to a file so you can review it later. just issue script filename (enter)

---

### Post by kylor on 2007-09-02
Didn't work for a while then I tried again later and it just worked...So I guess I have nothing to complain about now.

---

### Post by st33med on 2007-09-02
How do I install this for multiple users???

---

### Post by peitschie on 2007-09-03
st33med,

Once installed, any user can run it just by using the Fusion icon (can be launched by hitting alt+f2 to bring up the run dialog, and typing in 'fusion-icon' without the ' makes).

---

### Post by souldaddy on 2007-09-03
> **CryptiniteDemon said:**
> So I ran this script and it executed through just fine, but when i actually go click the compiz-fusion icon in the applications menu, nothing happens at all.  Or when I try it in the preferences menu, still nothing happens.

So what's up?

I have the same problem.  Anyone have any ideas for this one?  Thanks!

---

### Post by Nigmah on 2007-09-03
[COLOR=DarkOrange]**new kernal headers were updated in gutsy, messed the install. Uninstalled and installed from git but still get a white screen. Going to check if my xorg.conf file is stsill set up properly but i'm away from my main computer tomarrow will post back when i'm finished fixing.**[/COLOR]

---

### Post by peitschie on 2007-09-03
> **souldaddy said:**
> I have the same problem.  Anyone have any ideas for this one?  Thanks!

Hi souldaddy,

Are there any errors that appear while running the CF install script?  If you could open up a terminal and type in "compiz --replace", it may print out some useful error messages that you could paste here too.

Cheers.

---

### Post by souldaddy on 2007-09-03
> **peitschie said:**
> Hi souldaddy,

Are there any errors that appear while running the CF install script?  If you could open up a terminal and type in "compiz --replace", it may print out some useful error messages that you could paste here too.

Cheers.

No errors, however when I type that I basically lose control of my desktop.  I can't move windows around anymore, re-size them, etc.  Hmmm, gonna try and reboot.

---

### Post by Crisco on 2007-09-03
The CF installer works great for me when I select to do it through 'git' instead of doing the stable install, but how do I get my bars at the top of my windows to come back once everything is running, because that is a slight annoyance to me

---

### Post by peitschie on 2007-09-03
Hi Crisco.

Hit alt+f2 and type in 'emerald --replace'

---

### Post by Crisco on 2007-09-03
That got it, thanks a lot

---

### Post by vassalle on 2007-09-03
hi.. i'm interested in using your script. However, I cant seem to connect to your website. Is the script stored elsewhere? Thanks.

---

### Post by oceanelement on 2007-09-03
Just a few comments to post:

Your scripts works brilliantly and is much faster than the deb's. Thanks so much for making the effort to optimize the Compiz Fusion install with a script and sharing it. 

There was some issues with the install. When I tried to initiate the program after the first install with the stable version, nothing happened. So, I uninstalled everything and then reinstalled with git. Then it worked flawlessly. 


Cheers

---

### Post by avc302000 on 2007-09-03
Hello!
I've tried to install compiz fusion from the stable side and it started giving errors after errors when tried to install plugins, etc...
Is the gits or gitz better?

At the end, rebooting ubuntu, does the compiz takeover or do we have to do the Alt+F2 and write compiz --replace... all the times?

Best regards!

---

### Post by FuzzMaster on 2007-09-03
Hi, I ran your script, installation seemed to be going okay, but when I hit the icon nothing happens.  I tried fusion-icon in the terminal and I got

```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

Edit:  Should mention I have an nVidia GPU and am using Edgy !  If you need anything else, please ask.

---

### Post by icecoldmilk on 2007-09-04
i got a bug or i dont kw myabe its only my problem which is :::

some of my plugins not working after i updater my Compiz fusion tonight to 0.6.99>_<

i try to check the shift switcher and window previews  but after i checked it,  it discheck itself 1 sec after.

but some others r working fine!! 

anyone got the same problem?

any helps would be really appreciated!!:popcorn::popcorn::popcorn:

---

### Post by spartan777 on 2007-09-04
i've already successfully installed cf with the script and all, but now, a few weeks later as I'm trying to upgrade/update it, I get the following errors:

```
Do you use Gnome or KDE?(g/k):
g

Do you want to (un)install Compiz Fusion or update it?(i/u):
u
CF_Installer-Updater_v.3.sh: line 414: cd: /home/calvin/.cf_i-u/compiz: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion (ignore it if you didn't installed it from git) ?(y/n):
y
CF_Installer-Updater_v.3.sh: line 418: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 426: cd: /home/calvin/.cf_i-u/bcop: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion Option Code Generator?(y/n):
y
CF_Installer-Updater_v.3.sh: line 430: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 438: cd: /home/calvin/.cf_i-u/ccsm: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update CompizConfig Settings Manager?(y/n):
y
python: can't open file 'setup.py': [Errno 2] No such file or directory
CF_Installer-Updater_v.3.sh: line 450: cd: /home/calvin/.cf_i-u/compizconfig-python: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update CompizConfig-Python?(y/n):
y
CF_Installer-Updater_v.3.sh: line 454: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 462: cd: /home/calvin/.cf_i-u/emerald: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Emerald?(y/n):

calvin@calvin-desktop:~$ 


```

---

### Post by icecoldmilk on 2007-09-04
> **icecoldmilk said:**
> i got a bug or i dont kw myabe its only my problem which is :::

some of my plugins not working after i updater my Compiz fusion tonight to 0.6.99>_<

i try to check the shift switcher and window previews  but after i checked it,  it discheck itself 1 sec after.

but some others r working fine!! 

anyone got the same problem?

any helps would be really appreciated!!:popcorn::popcorn::popcorn:


btw i got an ERROR like this when im trying to installing~~
> 
convert   : shift.xml.in -> build/shift.xml
bcop'ing  : build/shift.xml -> build/shift_options.h
bcop'ing  : build/shift.xml -> build/shift_options.c
schema    : build/shift.xml -> build/compiz-shift.schema
compiling : shift.c -> build/shift.loshift.c:46:25: error: compiz-text.h: No such file or directory
shift.c: In function 'shiftRenderWindowTitle':
shift.c:286: error: 'CompTextAttrib' undeclared (first use in this function)
shift.c:286: error: (Each undeclared identifier is reported only once
shift.c:286: error: for each function it appears in.)
shift.c:286: error: expected ';' before 'tA'
shift.c:313: error: 'tA' undeclared (first use in this function)
shift.c:322: error: 'TEXT_STYLE_BOLD' undeclared (first use in this function)
shift.c:322: error: 'TEXT_STYLE_NORMAL' undeclared (first use in this function)
shift.c:327: error: 'TextRenderWindowTitleWithViewport' undeclared (first use in this function)
shift.c:329: error: 'TextRenderWindowTitle' undeclared (first use in this function)
shift.c:335: error: 'TEXT_ID' undeclared (first use in this function)
shift.c: In function 'shiftInitDisplay':
shift.c:2435: error: 'TEXT_ABIVERSION' undeclared (first use in this function)
make: *** [build/shift.lo] Error 1
mkdir: cannot create directory `/home/icecoldmilk/.cf_i-u/plugins': File exists
Initialized empty Git repository in /home/icecoldmilk/.cf_i-u/plugins/showdesktop/.git/
remote: Generating pack...
remote: Done counting 68 objects.
remote: Deltifying 68 objects...
remote:  100% (68/68) done
Indexing 68 objects...
remote: Total 68 (delta 30), reused 0 (delta 0)
 100% (68/68) done
Resolving 30 deltas...
 100% (30/30) done



anyone kw how to fix this?^^:popcorn::popcorn::popcorn:

---

### Post by Nossie on 2007-09-04
apart from Git,

what are the other requirements/dependencies I need to compile and install Compiz?

I tried installing this on a fresh ubuntu box but I'm getting a lot of missing packages.

---

### Post by sultanoswing on 2007-09-04
Since a recompile (using git) a couple of days ago, I also no longer have the 'Shift Window Switcher' plugin (or the ring switcher for that matter).

Any clever ideas? Does the script need updating? Any place I can download that individual plugin?

---

### Post by ElemonGW on 2007-09-04
> **st33med said:**
> How do I install this for multiple users???

It should run from any user. However, if you also want to be able to update, open the script with a text editor and at the 3rd line after downdir= change ~/.cf_i-u with the full path to the folder where the script has downloaded everything.

> **vassalle said:**
> hi.. i'm interested in using your script. However, I cant seem to connect to your website. Is the script stored elsewhere? Thanks.

It was under maintenance for a few hours. It is up and running now.

> **oceanelement said:**
> Just a few comments to post:

Your scripts works brilliantly and is much faster than the deb's. Thanks so much for making the effort to optimize the Compiz Fusion install with a script and sharing it. 

There was some issues with the install. When I tried to initiate the program after the first install with the stable version, nothing happened. So, I uninstalled everything and then reinstalled with git. Then it worked flawlessly. 


Cheers

Thanks for the good words!

> **avc302000 said:**
> Hello!
I've tried to install compiz fusion from the stable side and it started giving errors after errors when tried to install plugins, etc...
Is the gits or gitz better?

At the end, rebooting ubuntu, does the compiz takeover or do we have to do the Alt+F2 and write compiz --replace... all the times?

Best regards!

1. It is better to install it from git.
2. You could add fusion-icon at your start-up list (of course you should also activate emerald & compiz from there).

> **FuzzMaster said:**
> Hi, I ran your script, installation seemed to be going okay, but when I hit the icon nothing happens.  I tried fusion-icon in the terminal and I got

```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

Edit:  Should mention I have an nVidia GPU and am using Edgy !  If you need anything else, please ask.

1.It is not tested under Edgy.
2.In case that no other errors appear, you may want to try installing the packages python-qt4 and python-qt4-dev.

> **spartan777 said:**
> i've already successfully installed cf with the script and all, but now, a few weeks later as I'm trying to upgrade/update it, I get the following errors:

```
Do you use Gnome or KDE?(g/k):
g

Do you want to (un)install Compiz Fusion or update it?(i/u):
u
CF_Installer-Updater_v.3.sh: line 414: cd: /home/calvin/.cf_i-u/compiz: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion (ignore it if you didn't installed it from git) ?(y/n):
y
CF_Installer-Updater_v.3.sh: line 418: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 426: cd: /home/calvin/.cf_i-u/bcop: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Compiz Fusion Option Code Generator?(y/n):
y
CF_Installer-Updater_v.3.sh: line 430: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 438: cd: /home/calvin/.cf_i-u/ccsm: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update CompizConfig Settings Manager?(y/n):
y
python: can't open file 'setup.py': [Errno 2] No such file or directory
CF_Installer-Updater_v.3.sh: line 450: cd: /home/calvin/.cf_i-u/compizconfig-python: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update CompizConfig-Python?(y/n):
y
CF_Installer-Updater_v.3.sh: line 454: ./autogen.sh: No such file or directory
CF_Installer-Updater_v.3.sh: line 462: cd: /home/calvin/.cf_i-u/emerald: No such file or directory
fatal: Not a git repository: '.git'
Would you like to update Emerald?(y/n):

calvin@calvin-desktop:~$ 


```

I have changed the script's working folder at the newest version. You can either rename the folder compiz located @ your home folder to .cf_i-u or open the script with a text editor and at the 3rd line after downdir= change ~/.cf_i-u to ~/compiz

---

### Post by Nigmah on 2007-09-04
[COLOR=DarkOrange]**got it fixed by purging xgl which i had leftover from my old card.**[/COLOR]

---

### Post by AlexenderReez on 2007-09-04
> **Nigmah said:**
> [COLOR=DarkOrange]**got it fixed by purging xgl which i had leftover from my old card.**[/COLOR]

can you explain a liitle bit more about that..i still got that error...

EDIT =

> reez@aLeXeNdeRreEz:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named compizconfig
... Trying another interface
* Using the Qt3 Interface
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 73, in import_interface
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
RuntimeError: the qt and PyQt4.QtCore modules both wrap the QObject class


---

### Post by mlyons16 on 2007-09-04
Alrighty!

I downloaded the file, "CF_Installer-Updater_v.3.sh" to my desktop... How do I use it now... I want to start using these cool desktop effects.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-09-04
Do you know if this works for ubuntu x64 
i am trying right now will report back and let you know
it should right kuss your compialing hhaha i cant spell


Edit: well it works just have to configure it its all screwd up i bascliy installed every thing
the title bar at the tops of windows isn't working just right

---

### Post by mlyons16 on 2007-09-04
I can't seem to get a clear response to my question.. How the hell do I install those effects. Like can someone lay out some clear step by steps.

---

### Post by mlyons16 on 2007-09-04
I want to use these effects demonstrated here:

[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

and

[http://www.youtube.com/watch?v=82ZTV82OmKo](http://www.youtube.com/watch?v=82ZTV82OmKo)

---

### Post by bunker on 2007-09-04
I got a good compiz-fusion going today, but I thought I'd let you know there seem to be a few bugs in the install helper (or possibly it's not taking into account my kde-based configuration).

There are only two things: ./configure of compiz needs xsltproc (and presumably the lib that it depends on); secondly one of the make install's calls /bin/moc directly which is installed in /usr/bin/moc.  Since the first install fails, the package compiz can't be found, and therefore libcompizsettings can't be installed which in turn prevents you from installing anything else.

It'd be nice if you chained the commands so that one failure will not cause a waste of time compiling all the other stuff.

Apart from those two things, it all seemed to work ok, though I ended up doing make/make install from the downloaded sources as I was fixing the problems.

Thanks for writing the script.

Edit: I have a sneaking suspicion that I downloaded an old version of your script by accident so it could be safe to ignore my comments ;).  The `moc` problem might still be valid though.

---

### Post by Nigmah on 2007-09-05
> **AlexenderReez said:**
> can you explain a liitle bit more about that..i still got that error...

EDIT =
did you have xgl installed before? If so this command should work
```
sudo apt-get purge xgl
```

anyways i've got a new problem i can't enable some plugins, they stay checked for a few seconds then uncheck any idea?

---

### Post by mangaman on 2007-09-05
Hi, to anyone getting this error:

```
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
```

I have a solution that worked for me. Install Compiz from git not stable.... atleast it fixed it for me.

I was having the same problem. I tried it install the stable version over and over but all I got was the same error. I was getting frustrated and after reading to the 26th page on this thread I thought I would never get it, but I always give things a last chance. This time I was very sure to read as much as I could while I was installing the stable version. Then I noticed it, the one word I was looking for... ERROR. It happened during the "Settings Library for Plugins" :

```
compiz.c:42:25: error: compiz-core.h: No such file or directory
compiz.c: In function 'initColorValue':
compiz.c:515: warning: implicit declaration of function 'MAX'
compiz.c:515: warning: nested extern declaration of 'MAX'
compiz.c:515: warning: implicit declaration of function 'MIN'
compiz.c:515: warning: nested extern declaration of 'MIN'
compiz.c: In function 'initIntInfo':
compiz.c:720: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:720: error: (Each undeclared identifier is reported only once
compiz.c:720: error: for each function it appears in.)
compiz.c:721: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c: In function 'initFloatInfo':
compiz.c:788: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:789: error: 'MAXSHORT' undeclared (first use in this function)
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/mangaman/.cf_i-u/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mangaman/.cf_i-u/libcompizconfig'
make: *** [all] Error 2

```

After that the "CompizConfig-Python" had this to say:

```
checking for CCS... configure: error: Package requirements (libcompizconfig >= 0.5.2 glib-2.0 >= 2.6 ) were not met:

No package 'libcompizconfig' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CCS_CFLAGS
and CCS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Well I thought that I was never going to figure this out. So as always with me I tried one last time, this time with the git version. TADA no compile errors. Then I tried fusion-icon in the console and no errors, Compiz started with no problems. 

I'm not saying that this will fix everyone who has this problem but it might help. Here is a file containing the full error compiles, they are just a cut and paste from the console. Maybe someone can find out why this happened.

---

### Post by maduranga on 2007-09-05
ok.. i came to a point to make a decision between "git" and "stable". please some one help me to understand what those words means? and what what is the best choice?

---

### Post by st33med on 2007-09-05
"git" has the most recent plugins and updates, however, it is so up to date, that it is considered **alpha** software. This means it could have a better chance of it crashing, maybe even everything!

"stable" is just as it says. It is a stable version, 0.5.2. However, I (and a few others) have had problems downloading from this source. 

Try using git for now.

---

### Post by phaedOne on 2007-09-05
I have refactored the CF script and wrapped around it a more intuitive installer that gives you success feedback after compiling each component.

It can be found here:  [http://ubuntuforums.org/showthread.php?p=3316829](http://ubuntuforums.org/showthread.php?p=3316829)

---

### Post by airtonix on 2007-09-06
This is regarding the installer provide in first post....did not see post before mine.

ran the installer.
at the point where its asking me wether or not i have KDE apps....i say no..
it then proceeds to install a heap of kde stuff.
WTF?
Oh and it failed horribly, ergo no compiz/3d w/e

edit: ok so that installer is for gutsy....what about feisty?

---

### Post by avc302000 on 2007-09-06
Hi again... thanks for you answer by the way.

I have a problem, I've choosed git as mencioned and even changed the download directory.

However the following error appears....

Downloading Compiz Fusion...
fatal: unable to connect a socket (Connection timed out)
fetch-pack from 'git://git.freedesktop.org/git/xorg/app/compiz' failed.

I'm behind a firewall but every download passed but this one... is the address ok?

Is the server off?

Best regards and congratulations for the script!

---

### Post by Roham on 2007-09-06
I try to run the script in the terminal but it won't work.
It says:
: command not foundr_v.3.sh: line 2: 
: command not foundr_v.3.sh: line 5: 
: command not foundr_v.3.sh: line 6: clear
Welcome to CF Installer-Updater version 3.0
: command not foundr_v.3.sh: line 8: echo
Reminder: You must have Main, Universe and Multiverse repositories enabled in order this script to work properly (otherwise not everything needed will be able to be downloaded).
: command not foundr_v.3.sh: line 10: echo
Warning: If you get an error about libcairo.so.2 uninstall Mono and it will be solved (the version which is pre-installed in Ubuntu should not cause any problems).
: command not foundr_v.3.sh: line 12: 
: command not foundr_v.3.sh: line 13: echo
Do you use Gnome or KDE?(g/k):
g
': not a valid identifiersh: line 14: read: `answer
CF_Installer-Updater_v.3.sh: line 17: syntax error near unexpected token `elif'
'F_Installer-Updater_v.3.sh: line 17: `elif [ $answer = k ] ; then
roham@ROHI:~$ 

What is wrong?

---

### Post by revchris on 2007-09-06
is ATI not supported with your script?   I got to the question "Do you have a Nvidia card (y/n)?", I choose "n" since I don't and the script quit.   

Is it done or do I need to have a nvidia card?

---

### Post by pure fusion on 2007-09-07
I had a similar problem to Roham, but eventually just decided to just copy and past the apropriate commands into the terminal replacing variables and such of course. So I got to the part where Compiz is actually installed and first I tried the stable version but got an error... then I tried the git version and now I got this error after inputting this command:
~/.cf_i-u/compiz$ ./autogen.sh --disable-kde && make && sudo make install

Error:
```
 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/libpng12 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libxml2 -DFUSE_USE_VERSION=26 "-DALL_LINGUAS=\"cs de es fi fr hu it ja pl pt_BR sv zh_CN zh_TW af ar bg bn bs ca cy da el en_GB en_US et gl gu he hi hr id ka km ko lo lt mk mr nb nl pa pt ro ru sk sl sr ta tr uk vi xh zu\"" -DLOCALEDIR=\"/usr/local/share/locale\" -DPLUGINDIR=\"/usr/local/lib/compiz\" -DIMAGEDIR=\"/usr/local/share/compiz\" -I../include -DMETADATADIR=\"/usr/local/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -MT inotify.lo -MD -MP -MF .deps/inotify.Tpo -c inotify.c -o inotify.o >/dev/null 2>&1
mv -f .deps/inotify.Tpo .deps/inotify.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -module -avoid-version -no-undefined  -o libinotify.la -rpath /usr/local/lib/compiz inotify.lo  
gcc -shared  .libs/inotify.o   -Wl,-soname -Wl,libinotify.so -o .libs/libinotify.so
ar cru .libs/libinotify.a  inotify.o
ranlib .libs/libinotify.a
creating libinotify.la
(cd .libs && rm -f libinotify.la && ln -s ../libinotify.la libinotify.la)
make[2]: Leaving directory `/home/savage/.cf_i-u/compiz/plugins'
Making all in images
make[2]: Entering directory `/home/savage/.cf_i-u/compiz/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/savage/.cf_i-u/compiz/images'
Making all in gtk
make[2]: Entering directory `/home/savage/.cf_i-u/compiz/gtk'
Making all in window-decorator
make[3]: Entering directory `/home/savage/.cf_i-u/compiz/gtk/window-decorator'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libwnck-1.0    -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include       -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -MT gtk-window-decorator.o -MD -MP -MF .deps/gtk-window-decorator.Tpo -c -o gtk-window-decorator.o gtk-window-decorator.c
gtk-window-decorator.c:51:23: error: dbus/dbus.h: No such file or directory
gtk-window-decorator.c:52:37: error: dbus/dbus-glib-lowlevel.h: No such file or directory
make[3]: *** [gtk-window-decorator.o] Error 1
make[3]: Leaving directory `/home/savage/.cf_i-u/compiz/gtk/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/savage/.cf_i-u/compiz/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/savage/.cf_i-u/compiz'
make: *** [all] Error 2

```

This is only a small portion of the who log of what the command did but I figure the rest wasnt important. I have the rest if it is needed.

Im using Gnome and Fiesty Fawn 7.04, if you need to know.

--peace
Pure Fusion

---

### Post by voltagex on 2007-09-07
There seems to be a problem with the latest script, the line encodings are DOS-style so bash seems to choke... I used a program to convert the line endings back and then the script was fine but you might want to re upload the script.

---

### Post by Roham on 2007-09-07
How did you guys fix the code? I am new to linux/ubuntu... it would be nice if you uploaded the script somewhere so I can download it .

---

### Post by ElemonGW on 2007-09-07
> **voltagex said:**
> There seems to be a problem with the latest script, the line encodings are DOS-style so bash seems to choke... I used a program to convert the line endings back and then the script was fine but you might want to re upload the script.

Sorry for that. I re-uploaded it fixing it.

[The future of CF Installer-Updater]("http://elemongw.awardspace.com/?q=node/46")

---

### Post by juanbretti on 2007-09-07
Great script! Thanks! But I cannot make it work.

I get the "Icons" and all that stuff... but the Compiz is not working.
The "Config manager" does not open, there's just the link, but not working.

Also, I cannot change in "Aparence" to any level of fancy windows :)

Help?

---

### Post by mahasmb on 2007-09-07
I ran the installer, but I get the following error message.

```
maha@maha-dlu:~$ fusion-icon &
[1] 31654
maha@maha-dlu:~$ * Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!

[1]+  Exit 1                  fusion-icon
maha@maha-dlu:~$ 

```

May it be because I have an onboard 128MB integrated graphics card?

---

### Post by torin on 2007-09-07
is it just me or does the latest compiz release in the git archive wreak total havoc on an otherwise stable system? my feisty was rock solid till i recompiled but when i turn it all off in sessions and reboot into metacity everything runs just fine :confused:

---

### Post by mahasmb on 2007-09-07
As per someone else's suggestions, I uninstalled Compiz-fusion and installed the git version instead of the stable one. I now get these error messages:

```

maha@maha-dlu:~/MyDocuments/maha/computer-stuff$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```

---

### Post by Frak on 2007-09-07
> **torin said:**
> is it just me or does the latest compiz release in the git archive wreak total havoc on an otherwise stable system? my feisty was rock solid till i recompiled but when i turn it all off in sessions and reboot into metacity everything runs just fine :confused:
Git=unstable

---

### Post by ElemonGW on 2007-09-08
[Offline Until Monday]("http://elemongw.awardspace.com/?q=node/51")
[CF Installer-Updater is dead - Say hi to Git4CF Automator]("http://elemongw.awardspace.com/?q=node/52")

---

### Post by Oen386 on 2007-09-08
```
sudo sh Git4CFAutomator.sh 
Git4CFAutomator.sh: 4: bcop git://anongit.compiz-fusion.org/fusion/libraries/bcop: not found
Git4CFAutomator.sh: 6: emerald-themes git://anongit.opencompositing.org/fusion/decorators/emerald-themes: not found
Git4CFAutomator.sh: 9: Syntax error: "(" unexpected

```

See you Monday. :)

---

### Post by T4K3Z0U on 2007-09-08
I downloaded that thing (compiz fusion?) and it opened in some strange window, so I saved it and went to terminal and entered {chmod +x CF_Installer-updater_v.X.sh} but got a message saying its no such file or directory. What did I do wrong?

EDIT: I D/L'd this
Download CF Installer-Updater Version 3

---

### Post by mahasmb on 2007-09-08
> **T4K3Z0U said:**
> I downloaded that thing (compiz fusion?) and it opened in some strange window, so I saved it and went to terminal and entered {chmod +x CF_Installer-updater_v.X.sh} but got a message saying its no such file or directory. What did I do wrong?

EDIT: I D/L'd this
Download CF Installer-Updater Version 3

```
chmod +x CF_Installer-updater_v.[COLOR="Red"]**X**[/COLOR].sh
```

Should be changed to (look in the directory you installed the file to check the actual name of the file you downloaded. The above **X** in the file name is just a place holder). 

 ```
chmod +x CF_Installer-updater_v.[COLOR="Red"]**3**[/COLOR].sh
```

---

### Post by T4K3Z0U on 2007-09-08
> **mahasmb said:**
> ```
chmod +x CF_Installer-updater_v.[COLOR="Red"]**X**[/COLOR].sh
```

Should be changed to (look in the directory you installed the file to check the actual name of the file you downloaded. The above **X** in the file name is just a place holder). 

 ```
chmod +x CF_Installer-updater_v.[COLOR="Red"]**3**[/COLOR].sh
```

I see you put a 3 there, but that also does nothing in terminal. I really need simple terms. 
I often find layman's terms difficult to understand ;)

---

### Post by s_spiff on 2007-09-08
any way to remove my beryl installation and put compiz? or can I keep oth of them and use compiz --replace command?
oops sorry, just saw that the script has a option for that too! rocking! thanks. hopefully this will work and not crash my system :D

---

### Post by mahasmb on 2007-09-08
> **T4K3Z0U said:**
> I see you put a 3 there, but that also does nothing in terminal. I really need simple terms. 
I often find layman's terms difficult to understand ;)

Well did you try the following command as well?

```
bash CF_Installer-Updater_v.3.sh
```

The "chmod" command was to make the file executable if it wasn't already. For me, the file I downloaded was already executable. So I didn't bother with the chmod command. 

Your problem was that you were trying to change the permissions of a file that wasn't actually there. Thus why I was telling you to look for the file that WAS actually.

Just try downloading the file to your home directory and then using the above bash command. And to make sure that the bash command works, double check the name of the file you downloaded. *And* make sure you use any of these commands when you're in the right directory.

If you don't want to type out the whole file name you can simply type: bash CF_installer*

It's going to look for the first/any file it finds that starts with "CF_installer"

Hope that helps.

---

### Post by T4K3Z0U on 2007-09-08
> **mahasmb said:**
> Well did you try the following command as well?

```
bash CF_Installer-Updater_v.3.sh
```

The "chmod" command was to make the file executable if it wasn't already. For me, the file I downloaded was already executable. So I didn't bother with the chmod command. 

Your problem was that you were trying to change the permissions of a file that wasn't actually there. Thus why I was telling you to look for the file that WAS actually.

Just try downloading the file to your home directory and then using the above bash command. And to make sure that the bash command works, double check the name of the file you downloaded. *And* make sure you use any of these commands when you're in the right directory.

If you don't want to type out the whole file name you can simply type: bash CF_installer*

It's going to look for the first/any file it finds that starts with "CF_installer"

Hope that helps.


So I need to D/L again? I don't know where to find the files and the commands don't work.

---

### Post by oldHat on 2007-09-08
Does this really work?  This codeblock at line 14of CF_Installer-Updater_v.3.sh looks odd:

echo -e "\033[1mDo you use Gnome or KDE?(g/k):\033[0m" ; read answer
if [ $answer = g ] ; then
        opdeskenv=kde
elif [ $answer = k ] ; then
        opdeskenv=gnome
else
        echo -e "\033[1mInvalid answer\033[0m"
        exit
fi

Does that mean that we should reply "g" for kde and "k" for gnome?

---

### Post by Shadowrunner340 on 2007-09-08
man, after installing the latest script myself (to no avail) and reading everyone else's problems, i'm just gona wait until Gutsy comes out....

---

### Post by Vermind on 2007-09-08
Hello, I have been using Treviño's 
makefusiondebs script, which is less tiringly interactive and works on my amd64 system.
[http://forum.compiz-fusion.org/showthread.php?t=2294](http://forum.compiz-fusion.org/showthread.php?t=2294)
the idea is that You say makefusiondebs and optionally give Your root password if You expect that You are missing stuff to install, and it fetches latest git stuff and builds debs.
It has worked for me for some time; today the git seems to be in a somewhat broken state,
The plugins-extra and other plugin packages following it fail to build with:
addhelper_options.c:53: error: 'CompDisplay' has no member named 'object'
. This script does not uninstall Your ubuntu compiz, so You could use the CF_installer thing to do that and then this to get the new stuff installed (or You could just do a search for compiz, emerald, heliodor and aquamarine and click stuff off in synaptic).
I am not using compiz-fusion at the moment for the practical reason of it slowing my UT2004 down too much (and requiring a metacity --replace each time I want to play)

Anyway, the makefusiondebs works most of the time. I hope someone will find it useful.
I have a bunch of amd64 debs for git dates 20070824, 20070902-8 made with the makefusiondebs and I can put these up if someone is interested. These are for GNOME; I have not compiled the kconf compiz fusion configuration backend.

---

### Post by PaulFXH on 2007-09-09
Am I missing something here?
I have used earlier versions of ElemonGW's installer with success.
Now I'm trying to do so again on a new computer but the latest version of the installer that I get from his [home page]("http://elemongw.awardspace.com/?q=projects/linux/cf_i-u") doesnt seem like an installer.
While the earlier versions are called CF Installer-Updater VersionX, what I get from version three is called default.html
What's going on here?
How can I get the latest version?

---

### Post by dustigroove on 2007-09-09
[FONT=Arial][SIZE=2][COLOR=Black]> **PaulFXH said:**
> Am I missing something here ... How can I get the latest version?

[http://elemongw.awardspace.com/?q=node/52](http://elemongw.awardspace.com/?q=node/52)

.
[/COLOR][/SIZE][/FONT]

---

### Post by dysonsphere23 on 2007-09-10
Hi,

I was having a hell of a time trying to install CF from this script.  Cheers to all those who are getting it to work, but I have not been able to, regardless of all the help offered in this thread.  Sincere thanks to all the posters.

I was able to get CF to work (as far as I know, haven't tested all the functions) just fine by compiling from git using this[ [COLOR="DarkOrange"]tutorial[/COLOR] ]("http://forum.compiz-fusion.org/showthread.php?t=1985").

So if you are getting errors and can't resolve the problem I suggest compiling on your own.  The tutorial is great and easy to follow.

---

### Post by kavatzoulas on 2007-09-10
hello from italy
i read the guide and i ve done everything as described.
after the installation  i made a restart but nothing happens.
i am going to applications selecting compiz fusion but nothing starts.also to system preferences compiz config manager nothing starts.where i have mistake?
(sorry my bad english)
thank you for the answers

i am using a laptop toshiba satellite p100-437 with T7400 and an nvidia 7900gs video card ubuntu feisty 32bit

---

### Post by ElemonGW on 2007-09-11
> **T4K3Z0U said:**
> So I need to D/L again? I don't know where to find the files and the commands don't work.
Let me take guide you.
1. Go to the page [http://elemongw.awardspace.com/?q=down_cf_i-u](http://elemongw.awardspace.com/?q=down_cf_i-u) to download it.
2. Save it at your home directory.
3. Open a terminal window and from there run
```
bash CF_Installer-Updater_v.3.sh
```

---

### Post by coloured on 2007-09-11
I have just performed an update from git and tried re-installing  - both times I have no more window decorations (if i change to metacity they come back).

Does anyone know what might be the problem? - is git broken atm?

here is my sources.list

> # # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) feisty-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## Repos for avant window navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

## Repos for screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets


Cheers
Jurgen

---

### Post by ElemonGW on 2007-09-12
> **PaulFXH said:**
> Am I missing something here?
I have used earlier versions of ElemonGW's installer with success.
Now I'm trying to do so again on a new computer but the latest version of the installer that I get from his [home page]("http://elemongw.awardspace.com/?q=projects/linux/cf_i-u") doesnt seem like an installer.
While the earlier versions are called CF Installer-Updater VersionX, what I get from version three is called default.html
What's going on here?
How can I get the latest version?
This is probably because of your browser. You could do two things:
1. Rename the downloaded file from default.html to CF_Installer-Updater_v.3.sh
2. Go to the download page, write click where it says "Click here if it does not." and select save link as (the exact name of it will vary depending on your browser.

> **dustigroove said:**
> [FONT=Arial][SIZE=2][COLOR=Black]

[http://elemongw.awardspace.com/?q=node/52](http://elemongw.awardspace.com/?q=node/52)

.
[/COLOR][/SIZE][/FONT]
This is a very early version and most things doesn't work, I don't recommend you to use it.

---

### Post by chiinox on 2007-09-12
> **chiinox said:**
> Any one know how to remove all the KDE stuff that was installed by one of the earlier scripts.  I pressed NO to KDE but still got the desktop installed along with all the apps.  I tried "sudo aptitude remove kde-core" but no glory also tried "sudo aptititude remove kubuntu-desktop" and nothing.  I had forgotten that the earlier script installed KDE but just got a bunch of updates for it and want to get rid of it to free up harddrive space.

Thanks


This is from my own post #487.  I went back and did not see any one ever address this.  How can I get rid of all the KDE junk in my system, I never wanted this stuff in the first place.  Any help would be appreciated.  Thanks:confused:

---

### Post by immersion on 2007-09-13
Hi there, thanks for the script, but only one thing...

Several plugins doesn't compile because dependency of text plugin which it need the build_global flag. After that i could compile ring switcher and shift plugins right away.

```
$ sudo make install BUILD_GLOBAL=true
```

And again, thanks for your work and sorry for my bad english xDDD. Ciao.

---

### Post by dannyboy79 on 2007-09-13
> **chiinox said:**
> This is from my own post #487.  I went back and did not see any one ever address this.  How can I get rid of all the KDE junk in my system, I never wanted this stuff in the first place.  Any help would be appreciated.  Thanks:confused:

The way that I did it was to just look through your "start" menu, write down what was installed that you didn't want to be installed. Go to synaptic and chose to "completely remove it", that should remove the app and any dependencies that it brought with it. The reason this happened to you is because you most likely had at a minimum 1 kde application and when it asked if you had any installed, you stated No, then when the installer was doing it's thing, it somehow saw that you did have kde apps installed and for whatever reason added more apps. You'd have to ask the developer why it installs apps for KDE. All I know is he told me that I should have chose Yes to having kde libraries installed and the kde apps wouldn't have been installed but I can't speak for that as I have re-run the installer. Compiz-fusion or xorg or something has a major problem with running it on 2 seperate displays to I gave up on compiz for the time being.

---

### Post by Roham on 2007-09-13
Hi ...
I noticed before (2 weeks) ago that some plugins did not get installed... due to some missing files... such as compiz-core.h , compiz-common.h and compiz-text.h...

So I downloaded the plugins manually (shift switcher) and did the make && make install...
but it didnt work... the same problem... I try the BUILD_GLOBAL=true thing... 
but no difference...

What should I do?

---

### Post by immersion on 2007-09-13
You have to compile again the desired plugins. I do this:

```
$ cd ~/.cf_i-u/plugins
$ cd text
$ sudo make install BUILD_GLOBAL=true
```

And ring switcher, shift and vpswitch like this and so on:

```
$ cd shift
$ sudo make install
```

Ahh, there's a missing library: **python-qt4-dev**

---

### Post by chiinox on 2007-09-13
> **dannyboy79 said:**
> The way that I did it was to just look through your "start" menu, write down what was installed that you didn't want to be installed. Go to synaptic and chose to "completely remove it", that should remove the app and any dependencies that it brought with it. The reason this happened to you is because you most likely had at a minimum 1 kde application and when it asked if you had any installed, you stated No, then when the installer was doing it's thing, it somehow saw that you did have kde apps installed and for whatever reason added more apps. You'd have to ask the developer why it installs apps for KDE. All I know is he told me that I should have chose Yes to having kde libraries installed and the kde apps wouldn't have been installed but I can't speak for that as I have re-run the installer. Compiz-fusion or xorg or something has a major problem with running it on 2 seperate displays to I gave up on compiz for the time being.

Thanks for the response, I had thought of that but also thought there has to be an easier way.  Was hoping for Elemon to just give a few commands to type and wham lol.  I guess if no one else responded there isn't an easier way.  Thanks again.

---

### Post by ElemonGW on 2007-09-13
[New Git4CF Automator Version out!]("http://elemongw.exofire.net/blog/2007/9/13/new-git4cf-automator-version-out%21")

---

### Post by dynamethod on 2007-09-13
heya i got caught out by the KDE thing too....

i dont want KDE but when it asked me about the KDE library, of course i said no because i got gnome, well it installed KDE, so how do i uninstall KDE now?? 

compiz still not working for my ATI X800 XT APGx8 either :S

---

### Post by kkolev on 2007-09-13
ElemonGW,

I have skipped the most part of this thread, so I want to apologise in advance if the issue I encountered is already known one. But with the intention to help you as provider of the script and others as user (and because I am too lazy to read all the posts) I will go ahead and describe the problems I dealt with.

Firs of all I started with a brand new installation of Kubuntu 7.04 (actually this is my first encounter with a distro of the Ubuntu family) with all the necessary  patches applied (KDE 3.5.6). My hardware is as follows: CeleronD 2.4x86, 1GB, Nvidia 7600GT 256.

I used your latest script (CF_Installer-Updater_v.3.sh).

My first issue was with compiling the newest compiz package from the repository (a.k.a. git - whatever it means). I have been receiving all kinds of errors (Sorry but I cannot provide a snippet). I find out that a dep-package called xsltproc was missing and (I guess it could be included a check for its existence in the script), so I installed it manually and started your script again. This time the result error was different and happened just before the completion of this step:

```

...
make[2]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk'
Making all in window-decorator
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk/window-decorator'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libwnck-1.0   -I/usr/include/metacity-1 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -MT gtk-window-decorator.o -MD -MP -MF .deps/gtk-window-decorator.Tpo -c -o gtk-window-decorator.o gtk-window-decorator.c
mv -f .deps/gtk-window-decorator.Tpo .deps/gtk-window-decorator.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2   -o gtk-window-decorator gtk-window-decorator.o ../../libdecoration/libdecoration.la -lwnck-1 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lX11 -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -pthread -lgconf-2 -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0 -ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0 -lmetacity-private -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
mkdir .libs
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o .libs/gtk-window-decorator gtk-window-decorator.o -pthread  ../../libdecoration/.libs/libdecoration.so -lwnck-1 /usr/lib/libgconf-2.so /usr/lib/libORBit-2.so /usr/lib/libgthread-2.0.so -lrt -ldbus-glib-1 -ldbus-1 -lmetacity-private /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -Wl,--rpath -Wl,/usr/local/lib
creating gtk-window-decorator
LC_ALL=C ../../intltool-merge -s -u -c ../../po/.intltool-merge-cache ../../po gwd.schemas.in gwd.schemas
Generating and caching the translation database
Merging translations into gwd.schemas.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk/window-decorator'
Making all in gnome
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk/gnome'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk/gnome'
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk'
make[2]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk'
Making all in kde
make[2]: Entering directory `/home/kkolev/.cf_i-u/compiz/kde'
Making all in window-decorator
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/kde/window-decorator'
/bin/moc decorator.h > decorator.moc.cpp
/bin/bash: /bin/moc: No such file or directory
make[3]: *** [decorator.moc.cpp] Error 127
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/kde/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kkolev/.cf_i-u/compiz/kde'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kkolev/.cf_i-u/compiz'
make: *** [all] Error 2

Would you like to install Compiz Fusion Option Code Generator?(y/n):
...

```

I looked around in Makefiles and find out that the /bin/moc is not the right place for it on my system. To override this globally instead of correcting each of the Makefiles I did this:

```
sudo ln -s /usr/bin/moc /bin/moc
```

I uninstalled everything and start again.

This time the only things that were coming out unexpectedly were messages like this one:

```

...
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

checking for a BSD-compatible install... /usr/bin/install -c
...

```


I guess they are not that fatal, but I am still fighting with errors received while compiling some of the plugins. Here is a snippet of one of the errors: 

```

...
Resolving 89 deltas.
 100% (89/89) done
convert   : ring.xml.in -> build/ring.xml
bcop'ing  : build/ring.xml -> build/ring_options.h
bcop'ing  : build/ring.xml -> build/ring_options.c
schema    : build/ring.xml -> build/compiz-ring.schema
compiling : ring.c -> build/ring.loPackage compiz-text was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz-text.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz-text' found
ring.c:43:25: error: compiz-core.h: No such file or directory
ring.c:44:25: error: compiz-text.h: No such file or directory
In file included from ring.c:45:
build/ring_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from ring.c:45:
build/ring_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
build/ring_options.h:38: error: expected ')' before '*' token
build/ring_options.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:68: error: expected ')' before '*' token
build/ring_options.h:70: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:87: error: expected ')' before '*' token
build/ring_options.h:88: error: expected ')' before '*' token
build/ring_options.h:89: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:90: error: expected ')' before '*' token
build/ring_options.h:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:93: error: expected ')' before '*' token
build/ring_options.h:94: error: expected ')' before '*' token
build/ring_options.h:95: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:96: error: expected ')' before '*' token
build/ring_options.h:98: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:99: error: expected ')' before '*' token
build/ring_options.h:100: error: expected ')' before '*' token
build/ring_options.h:101: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:102: error: expected ')' before '*' token
build/ring_options.h:104: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:105: error: expected ')' before '*' token
build/ring_options.h:106: error: expected ')' before '*' token
build/ring_options.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:108: error: expected ')' before '*' token
build/ring_options.h:110: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:111: error: expected ')' before '*' token
build/ring_options.h:112: error: expected ')' before '*' token
build/ring_options.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:114: error: expected ')' before '*' token
build/ring_options.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:117: error: expected ')' before '*' token
build/ring_options.h:118: error: expected ')' before '*' token
build/ring_options.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:120: error: expected ')' before '*' token
build/ring_options.h:122: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:123: error: expected ')' before '*' token
build/ring_options.h:124: error: expected ')' before '*' token
build/ring_options.h:125: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:126: error: expected ')' before '*' token
build/ring_options.h:128: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:129: error: expected ')' before '*' token
build/ring_options.h:130: error: expected ')' before '*' token
build/ring_options.h:131: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:132: error: expected ')' before '*' token
build/ring_options.h:134: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:135: error: expected ')' before '*' token
build/ring_options.h:136: error: expected ')' before '*' token
build/ring_options.h:137: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:138: error: expected ')' before '*' token
build/ring_options.h:140: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:141: error: expected ')' before '*' token
build/ring_options.h:142: error: expected ')' before '*' token
build/ring_options.h:143: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:144: error: expected ')' before '*' token
build/ring_options.h:146: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:147: error: expected ')' before '*' token
build/ring_options.h:148: error: expected ')' before '*' token
build/ring_options.h:149: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:150: error: expected ')' before '*' token
build/ring_options.h:152: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:153: error: expected ')' before '*' token
build/ring_options.h:154: error: expected ')' before '*' token
build/ring_options.h:155: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:156: error: expected ')' before '*' token
build/ring_options.h:158: error: expected ')' before '*' token
build/ring_options.h:159: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:160: error: expected ')' before '*' token
build/ring_options.h:162: error: expected ')' before '*' token
build/ring_options.h:163: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:164: error: expected ')' before '*' token
build/ring_options.h:166: error: expected ')' before '*' token
build/ring_options.h:167: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:168: error: expected ')' before '*' token
build/ring_options.h:170: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:171: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:172: error: expected ')' before '*' token
build/ring_options.h:174: error: expected ')' before '*' token
build/ring_options.h:175: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:176: error: expected ')' before '*' token
build/ring_options.h:178: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetDarkenBack'
build/ring_options.h:179: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:180: error: expected ')' before '*' token
build/ring_options.h:182: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetMinimized'
build/ring_options.h:183: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:184: error: expected ')' before '*' token
build/ring_options.h:186: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetSelectWithMouse'
build/ring_options.h:187: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:188: error: expected ')' before '*' token
build/ring_options.h:190: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetRingClockwise'
build/ring_options.h:191: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:192: error: expected ')' before '*' token
build/ring_options.h:194: error: expected ')' before '*' token
build/ring_options.h:195: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:196: error: expected ')' before '*' token
build/ring_options.h:198: error: expected ')' before '*' token
build/ring_options.h:199: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:200: error: expected ')' before '*' token
build/ring_options.h:202: error: expected ')' before '*' token
build/ring_options.h:203: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:204: error: expected ')' before '*' token
build/ring_options.h:206: error: expected ')' before '*' token
build/ring_options.h:207: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:208: error: expected ')' before '*' token
build/ring_options.h:210: error: expected ')' before '*' token
build/ring_options.h:211: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:212: error: expected ')' before '*' token
build/ring_options.h:214: error: expected ')' before '*' token
build/ring_options.h:215: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:216: error: expected ')' before '*' token
build/ring_options.h:218: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetWindowTitle'
build/ring_options.h:219: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:220: error: expected ')' before '*' token
build/ring_options.h:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetTitleFontBold'
build/ring_options.h:223: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:224: error: expected ')' before '*' token
build/ring_options.h:226: error: expected ')' before '*' token
build/ring_options.h:227: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:228: error: expected ')' before '*' token
build/ring_options.h:230: error: expected ')' before '*' token
build/ring_options.h:231: error: expected ')' before '*' token
build/ring_options.h:232: error: expected ')' before '*' token
build/ring_options.h:233: error: expected ')' before '*' token
build/ring_options.h:234: error: expected ')' before '*' token
build/ring_options.h:235: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:236: error: expected ')' before '*' token
build/ring_options.h:238: error: expected ')' before '*' token
build/ring_options.h:239: error: expected ')' before '*' token
build/ring_options.h:240: error: expected ')' before '*' token
build/ring_options.h:241: error: expected ')' before '*' token
build/ring_options.h:242: error: expected ')' before '*' token
build/ring_options.h:243: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:244: error: expected ')' before '*' token
build/ring_options.h:246: error: expected ')' before '*' token
build/ring_options.h:247: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:248: error: expected ')' before '*' token
ring.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
ring.c:70: error: expected specifier-qualifier-list before 'CompWindow'
ring.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
ring.c:83: error: expected specifier-qualifier-list before 'PreparePaintScreenProc'
ring.c:126: error: expected specifier-qualifier-list before 'GLfloat'
ring.c:160: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'isRingWin'
ring.c:217: error: expected ')' before '*' token
ring.c:231: error: expected ')' before '*' token
ring.c:291: error: expected ')' before '*' token
ring.c:423: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPaintWindow'
ring.c: In function 'compareWindows':
ring.c:649: error: 'CompWindow' undeclared (first use in this function)
ring.c:649: error: (Each undeclared identifier is reported only once
ring.c:649: error: for each function it appears in.)
ring.c:649: error: 'w1' undeclared (first use in this function)
ring.c:649: error: expected expression before ')' token
ring.c:650: error: 'w2' undeclared (first use in this function)
ring.c:650: error: expected expression before ')' token
ring.c:659: warning: control reaches end of non-void function
ring.c: In function 'compareRingWindowDepth':
ring.c:665: error: 'RingDrawSlot' has no member named 'slot'
ring.c:666: error: 'RingDrawSlot' has no member named 'slot'
ring.c: At top level:
ring.c:677: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'layoutThumbs'
ring.c:765: error: expected ')' before '*' token
ring.c:790: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringUpdateWindowList'
ring.c:810: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringCreateWindowList'
ring.c:833: error: expected ')' before '*' token
ring.c:878: error: expected ')' before '*' token
ring.c:892: error: expected ')' before '*' token
ring.c:935: error: expected ')' before '*' token
ring.c:1004: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPaintOutput'
ring.c:1057: error: expected ')' before '*' token
ring.c:1116: error: expected ')' before '*' token
ring.c:1146: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringTerminate'
ring.c:1203: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitiate'
ring.c:1269: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringDoSwitch'
ring.c:1327: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNext'
ring.c:1338: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrev'
ring.c:1349: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNextAll'
ring.c:1360: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrevAll'
ring.c:1371: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNextGroup'
ring.c:1382: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrevGroup'
ring.c:1393: error: expected ')' before '*' token
ring.c:1437: error: expected ')' before '*' token
ring.c:1513: error: expected ')' before '*' token
ring.c:1565: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringDamageWindowRect'
ring.c:1612: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitDisplay'
ring.c:1670: error: expected ')' before '*' token
ring.c:1683: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitScreen'
ring.c:1737: error: expected ')' before '*' token
ring.c:1766: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitWindow'
ring.c:1790: error: expected ')' before '*' token
ring.c:1799: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitObject'
ring.c:1813: error: expected ')' before '*' token
ring.c:1827: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInit'
ring.c:1837: error: expected ')' before '*' token
ring.c:1842: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringVTable'
ring.c:1853: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/ring.lo] Error 1
mkdir: cannot create directory `/home/kkolev/.cf_i-u/plugins': File exists
...

```

I'll be grateful If someone could help with this one. Apart of these "minor" :confused: errors everything seems to be working for now, but I haven't played with it a lot, so will see if something else comes up.

Thanks.

**Edited: I saw the information about the BUILD_GLOBAL=true option in the recent posts, so I'll try to modify the script tomorrow to see if my last problem will work out.**

---

### Post by ElemonGW on 2007-09-14
> **kkolev said:**
> My first issue was with compiling the newest compiz package from the repository (a.k.a. git - whatever it means). I have been receiving all kinds of errors (Sorry but I cannot provide a snippet). I find out that a dep-package called xsltproc was missing and (I guess it could be included a check for its existence in the script), so I installed it manually and started your script again.
Yes, this is a known new dependency. Git4CF Automator will install it for you in future versions (as currently it doesn't handle dependencies at all).  > **kkolev said:**
> This time the result error was different and happened just before the completion of this step:

```

...
make[2]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk'
Making all in window-decorator
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk/window-decorator'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libwnck-1.0   -I/usr/include/metacity-1 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -MT gtk-window-decorator.o -MD -MP -MF .deps/gtk-window-decorator.Tpo -c -o gtk-window-decorator.o gtk-window-decorator.c
mv -f .deps/gtk-window-decorator.Tpo .deps/gtk-window-decorator.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2   -o gtk-window-decorator gtk-window-decorator.o ../../libdecoration/libdecoration.la -lwnck-1 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lX11 -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -pthread -lgconf-2 -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0 -ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0 -lmetacity-private -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
mkdir .libs
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o .libs/gtk-window-decorator gtk-window-decorator.o -pthread  ../../libdecoration/.libs/libdecoration.so -lwnck-1 /usr/lib/libgconf-2.so /usr/lib/libORBit-2.so /usr/lib/libgthread-2.0.so -lrt -ldbus-glib-1 -ldbus-1 -lmetacity-private /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -Wl,--rpath -Wl,/usr/local/lib
creating gtk-window-decorator
LC_ALL=C ../../intltool-merge -s -u -c ../../po/.intltool-merge-cache ../../po gwd.schemas.in gwd.schemas
Generating and caching the translation database
Merging translations into gwd.schemas.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk/window-decorator'
Making all in gnome
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk/gnome'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk/gnome'
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/gtk'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk'
make[2]: Leaving directory `/home/kkolev/.cf_i-u/compiz/gtk'
Making all in kde
make[2]: Entering directory `/home/kkolev/.cf_i-u/compiz/kde'
Making all in window-decorator
make[3]: Entering directory `/home/kkolev/.cf_i-u/compiz/kde/window-decorator'
/bin/moc decorator.h > decorator.moc.cpp
/bin/bash: /bin/moc: No such file or directory
make[3]: *** [decorator.moc.cpp] Error 127
make[3]: Leaving directory `/home/kkolev/.cf_i-u/compiz/kde/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kkolev/.cf_i-u/compiz/kde'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kkolev/.cf_i-u/compiz'
make: *** [all] Error 2

Would you like to install Compiz Fusion Option Code Generator?(y/n):
...

```

I looked around in Makefiles and find out that the /bin/moc is not the right place for it on my system. To override this globally instead of correcting each of the Makefiles I did this:

```
sudo ln -s /usr/bin/moc /bin/moc
```
Thanks for that, this secures my suspicious that the script should install Compiz Fusion with /usr prefix. So it was a wise decision to make Git4CF Automator install Compiz Fusion that way ;) .

> **kkolev said:**
> I uninstalled everything and start again.

This time the only things that were coming out unexpectedly were messages like this one:

```

...
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

checking for a BSD-compatible install... /usr/bin/install -c
...

```


I guess they are not that fatal.
Right, this should not consider you at all, they are minor and doesn't cause any problems at all.

> **kkolev said:**
> But I am still fighting with errors received while compiling some of the plugins. Here is a snippet of one of the errors: 

```

...
Resolving 89 deltas.
 100% (89/89) done
convert   : ring.xml.in -> build/ring.xml
bcop'ing  : build/ring.xml -> build/ring_options.h
bcop'ing  : build/ring.xml -> build/ring_options.c
schema    : build/ring.xml -> build/compiz-ring.schema
compiling : ring.c -> build/ring.loPackage compiz-text was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz-text.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz-text' found
ring.c:43:25: error: compiz-core.h: No such file or directory
ring.c:44:25: error: compiz-text.h: No such file or directory
In file included from ring.c:45:
build/ring_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from ring.c:45:
build/ring_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
build/ring_options.h:38: error: expected ')' before '*' token
build/ring_options.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:68: error: expected ')' before '*' token
build/ring_options.h:70: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:87: error: expected ')' before '*' token
build/ring_options.h:88: error: expected ')' before '*' token
build/ring_options.h:89: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:90: error: expected ')' before '*' token
build/ring_options.h:92: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:93: error: expected ')' before '*' token
build/ring_options.h:94: error: expected ')' before '*' token
build/ring_options.h:95: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:96: error: expected ')' before '*' token
build/ring_options.h:98: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:99: error: expected ')' before '*' token
build/ring_options.h:100: error: expected ')' before '*' token
build/ring_options.h:101: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:102: error: expected ')' before '*' token
build/ring_options.h:104: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:105: error: expected ')' before '*' token
build/ring_options.h:106: error: expected ')' before '*' token
build/ring_options.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:108: error: expected ')' before '*' token
build/ring_options.h:110: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:111: error: expected ')' before '*' token
build/ring_options.h:112: error: expected ')' before '*' token
build/ring_options.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:114: error: expected ')' before '*' token
build/ring_options.h:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:117: error: expected ')' before '*' token
build/ring_options.h:118: error: expected ')' before '*' token
build/ring_options.h:119: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:120: error: expected ')' before '*' token
build/ring_options.h:122: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:123: error: expected ')' before '*' token
build/ring_options.h:124: error: expected ')' before '*' token
build/ring_options.h:125: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:126: error: expected ')' before '*' token
build/ring_options.h:128: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:129: error: expected ')' before '*' token
build/ring_options.h:130: error: expected ')' before '*' token
build/ring_options.h:131: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:132: error: expected ')' before '*' token
build/ring_options.h:134: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:135: error: expected ')' before '*' token
build/ring_options.h:136: error: expected ')' before '*' token
build/ring_options.h:137: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:138: error: expected ')' before '*' token
build/ring_options.h:140: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:141: error: expected ')' before '*' token
build/ring_options.h:142: error: expected ')' before '*' token
build/ring_options.h:143: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:144: error: expected ')' before '*' token
build/ring_options.h:146: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:147: error: expected ')' before '*' token
build/ring_options.h:148: error: expected ')' before '*' token
build/ring_options.h:149: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:150: error: expected ')' before '*' token
build/ring_options.h:152: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:153: error: expected ')' before '*' token
build/ring_options.h:154: error: expected ')' before '*' token
build/ring_options.h:155: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:156: error: expected ')' before '*' token
build/ring_options.h:158: error: expected ')' before '*' token
build/ring_options.h:159: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:160: error: expected ')' before '*' token
build/ring_options.h:162: error: expected ')' before '*' token
build/ring_options.h:163: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:164: error: expected ')' before '*' token
build/ring_options.h:166: error: expected ')' before '*' token
build/ring_options.h:167: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:168: error: expected ')' before '*' token
build/ring_options.h:170: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:171: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:172: error: expected ')' before '*' token
build/ring_options.h:174: error: expected ')' before '*' token
build/ring_options.h:175: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:176: error: expected ')' before '*' token
build/ring_options.h:178: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetDarkenBack'
build/ring_options.h:179: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:180: error: expected ')' before '*' token
build/ring_options.h:182: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetMinimized'
build/ring_options.h:183: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:184: error: expected ')' before '*' token
build/ring_options.h:186: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetSelectWithMouse'
build/ring_options.h:187: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:188: error: expected ')' before '*' token
build/ring_options.h:190: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetRingClockwise'
build/ring_options.h:191: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:192: error: expected ')' before '*' token
build/ring_options.h:194: error: expected ')' before '*' token
build/ring_options.h:195: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:196: error: expected ')' before '*' token
build/ring_options.h:198: error: expected ')' before '*' token
build/ring_options.h:199: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:200: error: expected ')' before '*' token
build/ring_options.h:202: error: expected ')' before '*' token
build/ring_options.h:203: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:204: error: expected ')' before '*' token
build/ring_options.h:206: error: expected ')' before '*' token
build/ring_options.h:207: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:208: error: expected ')' before '*' token
build/ring_options.h:210: error: expected ')' before '*' token
build/ring_options.h:211: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:212: error: expected ')' before '*' token
build/ring_options.h:214: error: expected ')' before '*' token
build/ring_options.h:215: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:216: error: expected ')' before '*' token
build/ring_options.h:218: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetWindowTitle'
build/ring_options.h:219: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:220: error: expected ')' before '*' token
build/ring_options.h:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringGetTitleFontBold'
build/ring_options.h:223: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:224: error: expected ')' before '*' token
build/ring_options.h:226: error: expected ')' before '*' token
build/ring_options.h:227: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:228: error: expected ')' before '*' token
build/ring_options.h:230: error: expected ')' before '*' token
build/ring_options.h:231: error: expected ')' before '*' token
build/ring_options.h:232: error: expected ')' before '*' token
build/ring_options.h:233: error: expected ')' before '*' token
build/ring_options.h:234: error: expected ')' before '*' token
build/ring_options.h:235: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:236: error: expected ')' before '*' token
build/ring_options.h:238: error: expected ')' before '*' token
build/ring_options.h:239: error: expected ')' before '*' token
build/ring_options.h:240: error: expected ')' before '*' token
build/ring_options.h:241: error: expected ')' before '*' token
build/ring_options.h:242: error: expected ')' before '*' token
build/ring_options.h:243: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:244: error: expected ')' before '*' token
build/ring_options.h:246: error: expected ')' before '*' token
build/ring_options.h:247: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/ring_options.h:248: error: expected ')' before '*' token
ring.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
ring.c:70: error: expected specifier-qualifier-list before 'CompWindow'
ring.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
ring.c:83: error: expected specifier-qualifier-list before 'PreparePaintScreenProc'
ring.c:126: error: expected specifier-qualifier-list before 'GLfloat'
ring.c:160: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'isRingWin'
ring.c:217: error: expected ')' before '*' token
ring.c:231: error: expected ')' before '*' token
ring.c:291: error: expected ')' before '*' token
ring.c:423: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPaintWindow'
ring.c: In function 'compareWindows':
ring.c:649: error: 'CompWindow' undeclared (first use in this function)
ring.c:649: error: (Each undeclared identifier is reported only once
ring.c:649: error: for each function it appears in.)
ring.c:649: error: 'w1' undeclared (first use in this function)
ring.c:649: error: expected expression before ')' token
ring.c:650: error: 'w2' undeclared (first use in this function)
ring.c:650: error: expected expression before ')' token
ring.c:659: warning: control reaches end of non-void function
ring.c: In function 'compareRingWindowDepth':
ring.c:665: error: 'RingDrawSlot' has no member named 'slot'
ring.c:666: error: 'RingDrawSlot' has no member named 'slot'
ring.c: At top level:
ring.c:677: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'layoutThumbs'
ring.c:765: error: expected ')' before '*' token
ring.c:790: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringUpdateWindowList'
ring.c:810: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringCreateWindowList'
ring.c:833: error: expected ')' before '*' token
ring.c:878: error: expected ')' before '*' token
ring.c:892: error: expected ')' before '*' token
ring.c:935: error: expected ')' before '*' token
ring.c:1004: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPaintOutput'
ring.c:1057: error: expected ')' before '*' token
ring.c:1116: error: expected ')' before '*' token
ring.c:1146: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringTerminate'
ring.c:1203: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitiate'
ring.c:1269: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringDoSwitch'
ring.c:1327: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNext'
ring.c:1338: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrev'
ring.c:1349: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNextAll'
ring.c:1360: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrevAll'
ring.c:1371: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringNextGroup'
ring.c:1382: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringPrevGroup'
ring.c:1393: error: expected ')' before '*' token
ring.c:1437: error: expected ')' before '*' token
ring.c:1513: error: expected ')' before '*' token
ring.c:1565: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringDamageWindowRect'
ring.c:1612: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitDisplay'
ring.c:1670: error: expected ')' before '*' token
ring.c:1683: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitScreen'
ring.c:1737: error: expected ')' before '*' token
ring.c:1766: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitWindow'
ring.c:1790: error: expected ')' before '*' token
ring.c:1799: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInitObject'
ring.c:1813: error: expected ')' before '*' token
ring.c:1827: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringInit'
ring.c:1837: error: expected ')' before '*' token
ring.c:1842: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'ringVTable'
ring.c:1853: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/ring.lo] Error 1
mkdir: cannot create directory `/home/kkolev/.cf_i-u/plugins': File exists
...

```
I guess you chose to install all plugins, well don't! At the latest version I added this option, which would download and install each plugins individually. However this doesn't work good, as most plugins display errors and are not installed. You should choose to install plugins according to where they are classified and from there install all the packages. 4 plugins which are not in any package will not be installed, however it is better from getting all these errors and having only a few (?) plugins successfully installed ;) .

---

### Post by master_kernel on 2007-09-16
ElemonGW, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

---

### Post by tilleyrw on 2007-09-17
When run, the script fails during compilation of the Compiz-Settings package.  Here some of the errors produced:

 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/local/include/compiz -I/usr/include/libxml2 -I../include -I../src -DPLUGINDIR=\"/usr/local/lib/compiz\" -DMETADATADIR=\"/usr/local/share/compiz\" -DLIBDIR=\"/usr/local/lib\" -DGLOBALMETADATA=\"/usr/local/share/compizconfig/global.xml\" -DSYSCONFDIR=\"/usr/local/etc\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT compiz.lo -MD -MP -MF .deps/compiz.Tpo -c compiz.c  -fPIC -DPIC -o .libs/compiz.o
compiz.c:42:25: error: compiz-core.h: No such file or directory
compiz.c: In function 'initColorValue':
compiz.c:515: warning: implicit declaration of function 'MAX'
compiz.c:515: warning: nested extern declaration of 'MAX'
compiz.c:515: warning: implicit declaration of function 'MIN'
compiz.c:515: warning: nested extern declaration of 'MIN'
compiz.c: In function 'initIntInfo':
compiz.c:720: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:720: error: (Each undeclared identifier is reported only once
compiz.c:720: error: for each function it appears in.)
compiz.c:721: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c: In function 'initFloatInfo':
compiz.c:788: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:789: error: 'MAXSHORT' undeclared (first use in this function)
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/tilleyrw/.cf_i-u/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tilleyrw/.cf_i-u/libcompizconfig'
make: *** [all] Error 2

Does anyone have ideas about how to correct this?

Thanks, Bob

---

### Post by jimmio on 2007-09-17
I've tried numerous times, but it fails to find ./autogen.sh... can someone please point out what I need to do? It also fails to install python at the very beginning, and I'm not quite sure why.

Thanks,
Jim

---

### Post by joshuachad on 2007-09-17
Jimmio if your interested i can give you a script my friend wrote which installs compiz beautifully when i get home. Let me know.

---

### Post by dannyboy79 on 2007-09-18
can anyone comment how to save the download link as a file instead of as a html file when downloading script thru firefox? ALso, I am curious what you mean about not installing ALL plugins. I would like ALL plugins, so what is the preferred method to get all the plugins when using your script? Thanks for your hard efforts.

---

### Post by jammasterstan on 2007-09-18
im not sure if im doing this right. ive been working with this automatic compiz-fusion for the last 4 hours and i cant seem to get it working. i went out and got "git-core" to help me run the program but i still cant seem to get it working i to the point of installing it but then after i get compiz itself installed its saying that it cant find all these folders that idk where they are. well heres what what ive got 

```
Downloading Compiz Fusion...
CF_Installer-Updater_v.3.sh: line 107: git: command not found
CF_Installer-Updater_v.3.sh: line 108: cd: /home/toxic/.cf_i-u/compiz: No such file or directory
Installing Compiz Fusion...
CF_Installer-Updater_v.3.sh: line 110: ./autogen.sh: No such file or directory

Would you like to install Compiz Fusion Option Code Generator?(y/n):
y
Downloading Compiz Fusion Option Code Generator...
CF_Installer-Updater_v.3.sh: line 135: git: command not found
CF_Installer-Updater_v.3.sh: line 136: cd: /home/toxic/.cf_i-u/bcop: No such file or directory
Installing Compiz Fusion Option Code Generator...
CF_Installer-Updater_v.3.sh: line 138: ./autogen.sh: No such file or directory

Would you like to install the Settings Library for Plugins?(y/n):
y
Downloading the Settings Library for Plugins...
CF_Installer-Updater_v.3.sh: line 151: git: command not found
CF_Installer-Updater_v.3.sh: line 152: cd: /home/toxic/.cf_i-u/libcompizconfig: No such file or directory
Installing the Settings Library for Plugins...
CF_Installer-Updater_v.3.sh: line 154: ./autogen.sh: No such file or directory

Would you like to install CompizConfig-Python?(y/n):
y
Downloading CompizConfig-Python...
CF_Installer-Updater_v.3.sh: line 167: git: command not found
CF_Installer-Updater_v.3.sh: line 168: cd: /home/toxic/.cf_i-u/compizconfig-python: No such file or directory
Installing CompizConfig-Python...
CF_Installer-Updater_v.3.sh: line 170: ./autogen.sh: No such file or directory

Would you like to install CompizConfig Settings Manager?(y/n):
y
Downloading CompizConfig Settings Manager...
CF_Installer-Updater_v.3.sh: line 183: git: command not found
CF_Installer-Updater_v.3.sh: line 184: cd: /home/toxic/.cf_i-u/ccsm: No such file or directory
Installing CompizConfig Settings Manager...
python: can't open file 'setup.py': [Errno 2] No such file or directory

Would you like to install all the currently available plugins for Compiz Fusion or choose which to install according to where they are classified?(all/choose):
all
Downloading and Installing all available Compiz Fusion Plugins...
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/3d: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/addhelper: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/animation: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/atlantis: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/bench: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/colorfilter: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/compiz-scheme: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/crashhandler: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/cubecaps: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/cubereflex: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/expo: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/extrawm: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/ezoom: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/fadedesktop: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/fakeargb: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/firepaint: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/gears: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/group: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/jpeg: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/mblur: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/mswitch: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/neg: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/opacify: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/put: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/reflex: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/resizeinfo: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/ring: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/scaleaddon: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/scalefilter: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/screencasting: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/shift: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/showdesktop: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/snap: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/snow: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/splash: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/text: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/thumbnail: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/tile: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/trailfocus: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/vpswitch: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/wall: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/wallpaper: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/widget: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/winrules: No such file or directory
make: *** No rule to make target `install'.  Stop.
mkdir: cannot create directory `/home/toxic/.cf_i-u/plugins': File exists
CF_Installer-Updater_v.3.sh: line 201: git: command not found
CF_Installer-Updater_v.3.sh: line 202: cd: /home/toxic/.cf_i-u/plugins/workarounds: No such file or directory
make: *** No rule to make target `install'.  Stop.

Would you like to install Emerald?(y/n):
y
Downloading Emerald...
CF_Installer-Updater_v.3.sh: line 263: git: command not found
CF_Installer-Updater_v.3.sh: line 264: cd: /home/toxic/.cf_i-u/emerald: No such file or directory
Installing Emerald...
CF_Installer-Updater_v.3.sh: line 266: ./autogen.sh: No such file or directory

Would you like to install a Package of Themes for Emerald?(y/n):
y
Downloading a Package of Themes for Emerald...
CF_Installer-Updater_v.3.sh: line 279: git: command not found
CF_Installer-Updater_v.3.sh: line 280: cd: /home/toxic/.cf_i-u/emerald-themes: No such file or directory
Installing a Package of Themes for Emerald...
CF_Installer-Updater_v.3.sh: line 282: ./autogen.sh: No such file or directory

Would you like to install Compiz Fusion Icon?(y/n):
y
Downloading Compiz Fusion Icon...
CF_Installer-Updater_v.3.sh: line 295: git: command not found
CF_Installer-Updater_v.3.sh: line 296: cd: /home/toxic/.cf_i-u/fusion-icon: No such file or directory
Installing Compiz Fusion Icon...
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

Do you have a NVidia graphics card?(y/n):
y

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Installation Completed
```

---

### Post by joshuachad on 2007-09-18
I wanted to post an error here thats been happening when compiling CF in general. Not really related to this script except that it may happen to ppl that use it. But it happened to me even without using a script.

Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: libcompizconfig.so.0: cannot open shared object file: No such file or directory

Thats what the error looks like if you try and run ccsm or fusion-icon from terminal. Any rate the fix is to copy the files  libcompizconfig.so.0 and  libemeraldengine.so.0(IF you compiled emerald) from /usr/local/lib to /usr/lib.

Not sure if anyone else got this but i wanted to get it somewhere on the forum in case.

Cheers.

---

### Post by styxie on 2007-09-19
This may have already been reported, but the 3D windows plugin isn't working. And on Youtube are all these compiz videos of dodging windows and flying windows and burning windows (when you close them). Why can't I do stuff like that?

PS: I don't wanna be negative, I think the CF script is awesome, I wouldn't be using compiz if it weren't for this script, so mucho kuddos to the dude who made this possible.

---

### Post by rand0m on 2007-09-20
If you install from Git things may be broken. Fixes come out pretty quick but things often break aswell. It is bleeding edge after all. Right now, my CF lost expo, tile, and window animations. They worked before I updated (which was probably a mistake).

---

### Post by ElemonGW on 2007-09-20
> **master_kernel said:**
> ElemonGW, please visit [http://ubuntuforums.org/showthread.php?p=3376011](http://ubuntuforums.org/showthread.php?p=3376011) and add your program to the list of the best of the Ubuntu community.

Well, you have already done it ;)

> **dannyboy79 said:**
> can anyone comment how to save the download link as a file instead of as a html file when downloading script thru firefox?
You could do two things:
1. Rename the downloaded file to CF_Installer-Updater_v.3.sh
2. Go to the download page, write click where it says "Click here if it does not." and select save link as.

> **dannyboy79 said:**
> ALso, I am curious what you mean about not installing ALL plugins. I would like ALL plugins, so what is the preferred method to get all the plugins when using your script? Thanks for your hard efforts.
You could manually download and install the rest available plugins. Otherwise, you have to w8 until stable version of Git4CF Automator comes out. Btw., I may release a bug fixing version of CF Installer-Updater soon fixing that too

> **tilleyrw said:**
> When run, the script fails during compilation of the Compiz-Settings package.  Here some of the errors produced:

 gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/local/include/compiz -I/usr/include/libxml2 -I../include -I../src -DPLUGINDIR=\"/usr/local/lib/compiz\" -DMETADATADIR=\"/usr/local/share/compiz\" -DLIBDIR=\"/usr/local/lib\" -DGLOBALMETADATA=\"/usr/local/share/compizconfig/global.xml\" -DSYSCONFDIR=\"/usr/local/etc\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT compiz.lo -MD -MP -MF .deps/compiz.Tpo -c compiz.c  -fPIC -DPIC -o .libs/compiz.o
compiz.c:42:25: error: compiz-core.h: No such file or directory
compiz.c: In function 'initColorValue':
compiz.c:515: warning: implicit declaration of function 'MAX'
compiz.c:515: warning: nested extern declaration of 'MAX'
compiz.c:515: warning: implicit declaration of function 'MIN'
compiz.c:515: warning: nested extern declaration of 'MIN'
compiz.c: In function 'initIntInfo':
compiz.c:720: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:720: error: (Each undeclared identifier is reported only once
compiz.c:720: error: for each function it appears in.)
compiz.c:721: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c: In function 'initFloatInfo':
compiz.c:788: error: 'MINSHORT' undeclared (first use in this function)
compiz.c:789: error: 'MAXSHORT' undeclared (first use in this function)
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/tilleyrw/.cf_i-u/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tilleyrw/.cf_i-u/libcompizconfig'
make: *** [all] Error 2

Does anyone have ideas about how to correct this?

Thanks, Bob
It could be a problem of libcompizconfig (try deleting the folder where it was downloaded and then re-download it & install it. It can also be a problem with which prefix compiz is installed, I have to play with prefixes and find the best location for it. Sry, I can't provide any more help without my adsl (I want it back :( ) .

> **jimmio said:**
> I've tried numerous times, but it fails to find ./autogen.sh... can someone please point out what I need to do? It also fails to install python at the very beginning, and I'm not quite sure why.

Thanks,
Jim

In order for me to help you, I need to know the exact errors. You may post the full terminal output (btw., most probably it didn't downloaded the files for some reason)

> **jammasterstan said:**
> i went out and got "git-core" to help me run the program but i still cant seem to get it working i to the point of installing it but then after i get compiz itself installed its saying that it cant find all these folders that idk where they are. well heres what what ive got

From the errors, it seems that git-core was not installed correctly for some reason. Which is your distro and its version? Also, how did you installed git-core (from what i understand you didn't let the script install it but installed it manually, right?)?

> **joshuachad said:**
> I wanted to post an error here thats been happening when compiling CF in general. Not really related to this script except that it may happen to ppl that use it. But it happened to me even without using a script.

Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: libcompizconfig.so.0: cannot open shared object file: No such file or directory

Thats what the error looks like if you try and run ccsm or fusion-icon from terminal. Any rate the fix is to copy the files  libcompizconfig.so.0 and  libemeraldengine.so.0(IF you compiled emerald) from /usr/local/lib to /usr/lib.

Not sure if anyone else got this but i wanted to get it somewhere on the forum in case.

Cheers.

Thnx for mentioning it, one more proof that I have to play with prefixes choose the most appropriate for compiz (either /usr or /usr/local ).

> **styxie said:**
> This may have already been reported, but the 3D windows plugin isn't working. And on Youtube are all these compiz videos of dodging windows and flying windows and burning windows (when you close them). Why can't I do stuff like that?

PS: I don't wanna be negative, I think the CF script is awesome, I wouldn't be using compiz if it weren't for this script, so mucho kuddos to the dude who made this possible.
You could activate the plugins you want through ccsm. Also, how did you installed the plugins (all/packages). Finally, it is possible that some packages may be broken due to changes compiz fusion developers make, which usually is fixed after a while.

---

### Post by WolfLust on 2007-09-20
I apologise for not going through every page of this topic but my eyes just couldn't handle reading more than 13-14 pages.

I downloaded the file and went through the installation, everything seemed successful, I restarted and clicked on the Compiz Fusion Icon and nothing started, then I clicked on the CompizFusion Settings Manager and nothing started either.

I tried doing: compiz --replace 
and got: compiz (core) - Fatal: No composite extension
anyone got an idea what to do?

I am on Feisty, with an ATI Radeon 9800XT.

Thank you.

---

### Post by ElemonGW on 2007-09-20
> **WolfLust said:**
> I apologise for not going through every page of this topic but my eyes just couldn't handle reading more than 13-14 pages.

I downloaded the file and went through the installation, everything seemed successful, I restarted and clicked on the Compiz Fusion Icon and nothing started, then I clicked on the CompizFusion Settings Manager and nothing started either.

I tried doing: compiz --replace 
and got: compiz (core) - Fatal: No composite extension
anyone got an idea what to do?

I am on Feisty, with an ATI Radeon 9800XT.

Thank you.
Run Compiz Fusion Icon (fusion-icon) and CompizFusion Settings Manager (ccsm) from terminal and post the errors here.

---

### Post by WolfLust on 2007-09-20
Sure thanks for the reply:

fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig




ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

---

### Post by Hark3n on 2007-09-20
Wolflust, I get exactly the same errors as you

---

### Post by ElemonGW on 2007-09-21
> **WolfLust said:**
> Sure thanks for the reply:

fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig




ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

> **Hark3n said:**
> Wolflust, I get exactly the same errors as you

Probably compizconfig was not installed correctly. Try re-installing it and post here any errors you may get.

---

### Post by pilotet on 2007-09-21
Hi,
After executing the script and then fusion-icon I have the next error:
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

I've tried to reinstall and try again, also install all and choose plugins but I have the same Error.

Feisty x64 on ASUS a8j
ATI RADEON X2300

Anybody has solved this?

---

### Post by searayman on 2007-09-21
just used this script after not using it in a while, and now my animations dont work at all......

---

### Post by WolfLust on 2007-09-21
> **ElemonGW said:**
> Probably compizconfig was not installed correctly. Try re-installing it and post here any errors you may get.

Do I need to install Git? I have no idea what that is.

---

### Post by stalker145 on 2007-09-22
My error is slightly different from others encountered here.
```
stalker145@DaLaptop:~/Downloads$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```
and
```
stalker145@DaLaptop:~/Downloads$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

```

_Dell C640_
ATI Mobility Radeon 7500 32MB
1024 RAM
1.8Ghz Intel CPU

---

### Post by Prisoner_97p904 on 2007-09-22
> **stalker145 said:**
> My error is slightly different from others encountered here.
```
stalker145@DaLaptop:~/Downloads$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```
and
```
stalker145@DaLaptop:~/Downloads$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

```


I get the exact same error. I installed with git and yes to all other options.

---

### Post by ThomasBS on 2007-09-23
Some error for me. Just installed it (stable, all other "yes") and didn't do anything else.

Hope someone can help with this problem ;)

Cheers,
Thomas

---

### Post by Lattyware on 2007-09-23
It appears to be missing the dependancy 'python-compizconfig'

---

### Post by coloured on 2007-09-24
> **searayman said:**
> just used this script after not using it in a while, and now my animations dont work at all......

I too have the same problem... I tried updating - now none of the animations in the animation plugin work.

Any ideas?

---

### Post by Pekkaniska on 2007-09-26
the link to the newest release doesn't work. mirrors?

---

### Post by maduranga on 2007-09-26
**Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 617 bytes) in /home/elemongw/public_html/includes/common.inc on line 2159**


link doesn't work :(

---

### Post by bigjdcrockett on 2007-09-26
I cannot download the version 3 link, is there another mirror?

---

### Post by Israphel on 2007-09-26
I ran the script and answered correctly all the questions but when I run Compiz Fusion Icon nothing happen. If I go to the manager, nothing happen too. If I add it to the startup apps the windows border dissapears (Yes, I have the line in the xorg.conf). When I write metacity --replace, all come back to be normal. If I write compiz --replace, it says that compiz is not installed.

So, I don't know what to do. I didn't have the old compiz or beryl or nothing, I just run the script and follow the orders.

Please help.

Thanks.

(I'm not english speaker).

---

### Post by Maverick321 on 2007-09-26
Is There a mirror for this script.  The link doesn't work.  

Page only shows this error
Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 283 bytes) in /home/elemongw/public_html/includes/common.inc on line 2176

---

### Post by joetaxpayer on 2007-09-27
> **stalker145 said:**
> My error is slightly different from others encountered here.
```
stalker145@DaLaptop:~/Downloads$ fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```
and
```
stalker145@DaLaptop:~/Downloads$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

```

_Dell C640_
ATI Mobility Radeon 7500 32MB
1024 RAM
1.8Ghz Intel CPU

Same error here, too.

---

### Post by Pekkaniska on 2007-09-27
Tried installing and nothing happens. fusion-icon doesn't start

---

### Post by cryogenic on 2007-09-27
Yep... same here. I run fusion-icon and the cursor just bounces and nothing happens. When I try to manually run compiz, no luck. It tells me compiz is not installed.

---

### Post by Roque2 on 2007-09-27
did anyone get the emerald themes to work. I know that atleast came up

---

### Post by Pekkaniska on 2007-09-27
do you know what would be really nice for version4 ;) if the script asked all the questions at first, then started downloading and installing:) wouldn't have to wait in front of the screen :P

btw. still not working :P

```
skynet@skynet:~$ fusion-icon 
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig
skynet@skynet:~$ 


```

how to fix that? feisty and radeon 9600

---

### Post by Prisoner_97p904 on 2007-09-27
> **Pekkaniska said:**
> do you know what would be really nice for version4 ;) if the script asked all the questions at first, then started downloading and installing:) wouldn't have to wait in front of the screen :P


Yeah, that would be nice with all inputs in the start and then sleep for 1 hour ;) And of course if it actually works :-\"

---

### Post by joetaxpayer on 2007-09-27
> **Pekkaniska said:**
> do you know what would be really nice for version4 ;) if the script asked all the questions at first, then started downloading and installing:) wouldn't have to wait in front of the screen :P

btw. still not working :P

```
skynet@skynet:~$ fusion-icon 
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig
skynet@skynet:~$ 


```

how to fix that? feisty and radeon 9600

I get past this point by installing python-compizconfig and compizconfig-settings-manager from the repositories, but then I get other errors:

KeyError: decoration

 and something about ccp

:confused: stumped

---

### Post by Pekkaniska on 2007-09-28
So.. I tried a clean install of gutsy.. Formatted my feisty (and everything i had left of windows:) )away and installed gutsy. On a clean install i ran this script. Everything went fine until the motherf*cker came and took it all away :) . Currently no window manager on startup, and aren't able to start one afterwards either. It installed a bunch of KDE crap and i'm running gnome. fusion-icon crashes when I try starting it from terminal, or the icon in the system tools menu.

---

### Post by kris2pe on 2007-09-28
I tried clicking on the Compiz Icon & nothing happens!
I have accidentally install the KDE modules or some files in KDE what should I do?
BTW I'm using Gnome!

---

### Post by ElemonGW on 2007-09-28
[Git4CF Automator Version 0.1 Beta 1]("http://elemongw.exofire.net/blog/2007/9/28/git4cf-automator-version-0.1-beta-1")
I have my ADSL after a whole month finally back. So this version comes with bug fixes too (which were mading it unusable). As of the reported problems, I will be installing Feisty tomorrow at my other computer, so I will be able to test it, find the problems and fix them.

---

### Post by Yusayoh on 2007-09-28
I already had CF installed and since I read that GIT is much more updated (or something), I decided to use this script to get the GIT. I just wanted to update and after the update, I restarted my X and all my window borders were gone. I've tried the nvidia command to put into the terminal and restarted, but still no window border so I just took off compiz. When CF is running, the borders are gone, but when it isn't, they're fine. I've tried uninstalling and reinstalling 3 different times, but to no avail. Help anyone?
By the way, I know I'm stupid and all, but I accidentally closed the installer while it was updating the first time when it was in the middle of something

[btw, I like your script. It's a nice text-based installer, which I like :D]

---

### Post by Pekkaniska on 2007-09-29
this is really wrong. Yesterday nothing worked, and today everything works. I won't be shutting my pc down since i can't know if it works the next time i boot.

---

### Post by maduranga on 2007-09-29
I tried the script on two different computers that are occupied by Feisty Fawn. Script finished the installation successfully. But when i click on the fusion-icon, nothing happens. 

 when i give the command " **compiz --replace**  " it gives the following error message.
```

  Could not open location 'file:///compiz --replace'
  The location or file could not be found.
```

 This happens on both computers.

---

### Post by nikoPSK on 2007-09-29
I do not know where to save the script. Do I view or save it somewhere?:KS

---

### Post by Frak on 2007-09-29
> **nikoPSK said:**
> I do not know where to save the script. Do I view or save it somewhere?:KS
Save it in your home folder for easier access in the terminal.

---

### Post by nikoPSK on 2007-09-29
Thanks I can name it whatever? Or do I have to leave the name unchanged?:confused:

Thanks In advance
Niko

(I keep writing thbnks!!!)

---

### Post by nikoPSK on 2007-09-29
Saved it in my home folder and left the name unchanged...

```
niko@home:~$ bash CF_Installer-Updater_v.X.sh
bash: CF_Installer-Updater_v.X.sh: No such file or directory
niko@home:~$ chmod +x CF_Installer-Updater_v.X.sh
chmod: cannot access `CF_Installer-Updater_v.X.sh': No such file or directory
niko@home:~$ 


```

:confused:

---

### Post by Frak on 2007-09-29
Run
```
bash CF_Installer-Updater_v.*.sh
```
Instead

---

### Post by unabatedshagie on 2007-09-29
I assume it's fine to run the newest version of this script over a current install of compiz-fusion or would it be best to remove the current compiz-fusion and start again?

---

### Post by maduranga on 2007-09-30
> **ElemonGW said:**
> [Git4CF Automator Version 0.1 Beta 1]("http://elemongw.exofire.net/blog/2007/9/28/git4cf-automator-version-0.1-beta-1")
I have my ADSL after a whole month finally back. So this version comes with bug fixes too (which were mading it unusable). As of the reported problems, I will be installing Feisty tomorrow at my other computer, so I will be able to test it, find the problems and fix them.

 How can I reset the configuration of the first run of the script?

---

### Post by kris2pe on 2007-09-30
This script SUCKS! I'm sorry its the truth! 
How do I remove everything being made here! 
Its terrible!

---

### Post by Ruazinn on 2007-09-30
At the first prompt asking if you want to (un)install or update, enter don't enter "u" for uninstall, enter "i".   But at the second prompt, enter "u" for uninstall.  Yes, it's confusing.  I had to look at the script to figure that out.

fusion-icon wouldn't run, because of "Module compizconfig not found", so I just uninstalled.  Looks like gutsy comes with that module, so I'll worry about compiz fusion when I install gutsy in a month or so.

---

### Post by nikoPSK on 2007-09-30
> **Frak said:**
> Run
```
bash CF_Installer-Updater_v.*.sh
```
Instead

Thanks! It works! I get the update options but before that I'm going to try re-installing compiz to try to fix my problem:)

---

### Post by Prisoner_97p904 on 2007-10-01
> **maduranga said:**
> How can I reset the configuration of the first run of the script?

I typed:

rm -r ~/.git4cf

and the configuration was deleted :)

edit: I think it is enough with: "rm ~/.git4cf/settings", but haven't tested it.

---

### Post by joetaxpayer on 2007-10-01
Is the new script working for anyone?

---

### Post by TheBlackCat13 on 2007-10-01
> **ElemonGW said:**
> [Git4CF Automator Version 0.1 Beta 1]("http://elemongw.exofire.net/blog/2007/9/28/git4cf-automator-version-0.1-beta-1")
I have my ADSL after a whole month finally back. So this version comes with bug fixes too (which were mading it unusable). As of the reported problems, I will be installing Feisty tomorrow at my other computer, so I will be able to test it, find the problems and fix them.

When I run the new version it is full of errors like this:

```
Installing package compiz...
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec '--prefix=/usr' did not match any file(s) known to git.
error: pathspec '--disable-gnome' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'make' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'make' did not match any file(s) known to git.
error: pathspec 'install' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'export' did not match any file(s) known to git.
error: pathspec 'PKG_CONFIG_PATH=/usr/lib/pkgconfig' did not match any file(s) known to git.
Did you forget to 'git add'?

```

It looks to me like the script is interpreting lines like:

```
install_way="git checkout origin/compiz-0.6 && ./autogen.sh --prefix=/usr --disable-$opdeskenv && make && make install && export PKG_CONFIG_PATH=/usr/lib/pkgconfig"
```

as having all the commands apply to git.  That is, it isn't recognizing the && command like it should.  I don't know why this is the case, but it renders the script unusable.

---

### Post by joetaxpayer on 2007-10-02
I found a version of the script over at Compiz forums:

[http://forum.compiz-fusion.org/showthread.php?t=3960&highlight=install+plugin](http://forum.compiz-fusion.org/showthread.php?t=3960&highlight=install+plugin)

Works good for me after I installed libcompizconfig0 from the repos.

---

### Post by ElemonGW on 2007-10-02
> **unabatedshagie said:**
> I assume it's fine to run the newest version of this script over a current install of compiz-fusion or would it be best to remove the current compiz-fusion and start again?
When you tell current, you mean the current version of CF Installer-Updater, right? And from which version do you want to upgrade?

> **Prisoner_97p904 said:**
> I typed:
edit: I think it is enough with: "rm ~/.git4cf/settings", but haven't tested it.
Right!

> **joetaxpayer said:**
> Is the new script working for anyone?
Currently it is only for previewing how it will be and if anyone wants, help me fixing problems/report me current bugs. As soon as it is ready for use, I will announce it.

> **TheBlackCat13 said:**
> When I run the new version it is full of errors like this:

```
Installing package compiz...
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec '--prefix=/usr' did not match any file(s) known to git.
error: pathspec '--disable-gnome' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'make' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'make' did not match any file(s) known to git.
error: pathspec 'install' did not match any file(s) known to git.
error: pathspec '&&' did not match any file(s) known to git.
error: pathspec 'export' did not match any file(s) known to git.
error: pathspec 'PKG_CONFIG_PATH=/usr/lib/pkgconfig' did not match any file(s) known to git.
Did you forget to 'git add'?

```

It looks to me like the script is interpreting lines like:

```
install_way="git checkout origin/compiz-0.6 && ./autogen.sh --prefix=/usr --disable-$opdeskenv && make && make install && export PKG_CONFIG_PATH=/usr/lib/pkgconfig"
```

as having all the commands apply to git.  That is, it isn't recognizing the && command like it should.  I don't know why this is the case, but it renders the script unusable.

Yes, thnx for reporting it. I found out that yesterday (I think). The problem appears because of the "" . I have fixed it so the next version will not have that problem.

---

### Post by joetaxpayer on 2007-10-02
> **ElemonGW said:**
> Currently it is only for previewing how it will be and if anyone wants, help me fixing problems/report me current bugs. As soon as it is ready for use, I will announce it.

Maybe you should edit this into the original post so people don't think they are downloading a working vesion. :popcorn:

---

### Post by KhaaL on 2007-10-03
smspillaz just released a [GIT installer for CF.]("http://smspillaz.wordpress.com/2007/10/02/graphical-git-script/")

I hope you dont mind me posting about another mans similiar work, ElemonGW!

---

### Post by Frak on 2007-10-03
Hey ElemonGW, what are you going to make for Gutsy, since CF is automatically installed?

---

### Post by TheBlackCat13 on 2007-10-03
I'm pretty sure the CF in Gutsy is the stable version, which is pretty old.

---

### Post by ElemonGW on 2007-10-03
> **KhaaL said:**
> smspillaz just released a [GIT installer for CF.]("http://smspillaz.wordpress.com/2007/10/02/graphical-git-script/")

I hope you dont mind me posting about another mans similiar work, ElemonGW!
No, of course not ;)

> **Frak said:**
> Hey ElemonGW, what are you going to make for Gutsy, since CF is automatically installed?
What TheBlackCat13 said is what I believe. The version of CF in gutsy will not be the latest so it may lack new features etc. So there will still be a reason of using it ;) .

---

### Post by nikoPSK on 2007-10-03
got it woking (compiz) and the script works wonderfully. Thanks:KS

---

### Post by Frak on 2007-10-03
> **ElemonGW said:**
> No, of course not ;)


What TheBlackCat13 said is what I believe. The version of CF in gutsy will not be the latest so it may lack new features etc. So there will still be a reason of using it ;) .
Thanks, just wanted to know.

---

### Post by ElemonGW on 2007-10-05
> **joetaxpayer said:**
> Maybe you should edit this into the original post so people don't think they are downloading a working vesion. :popcorn:
Will do so soon!

---

### Post by ElemonGW on 2007-10-05
Please everybody participate at [this]("http://elemongw.exofire.net/poll/which-branch-would-you-like-git4cf-automator-checkout%3F") poll. I want to make a decision and I want to hear your opinion.
PS: The poll is about which branch Git4CF Automator will checkout.

---

### Post by ElemonGW on 2007-10-05
[Some Good News]("http://elemongw.exofire.net/blog/2007/10/5/some-good-news")

---

### Post by maduranga on 2007-10-06
ElemonGW, do u have anything like this for Xfce? :)  Or can i get this script working under Xubuntu?  I'm using Xubuntu Gusty and I tried this, but ddnt worked.

---

### Post by ElemonGW on 2007-10-06
> **maduranga said:**
> ElemonGW, do u have anything like this for Xfce? :)  Or can i get this script working under Xubuntu?  I'm using Xubuntu Gusty and I tried this, but ddnt worked.
The upcoming beta (of Git4CF Automator) has support for XFCE (I haven't tested it but it should work). The new beta has lots of new features and will probably be he last one before the final. It will also be ready for use. I am currently making some visual changes and I will release it.

---

### Post by ElemonGW on 2007-10-06
[Git4CF Automator version 0.1 Beta 2 just got released]("http://elemongw.exofire.net/blog/2007/10/6/git4cf-automator-version-0.1-beta-2")

---

### Post by Nossie on 2007-10-07
and it just doesnt work :(

I cant get the same results that I did with the original... sorry :-|

This is admittedly running on gutsy but for whatever reason I just cant get the damn thing to compile.

any other gutsy users having issues?

---

### Post by ElemonGW on 2007-10-07
> **Nossie said:**
> and it just doesnt work :(
Git4CF Automator or CF Installer-Updater? What errors do you face?

> **Nossie said:**
> I cant get the same results that I did with the original... sorry :-|
Original? You mean the compiz fusion that comes pre-installed @ gutsy?

Finally, have you removed compiz fusion from your system before using it? You should remove any previous versions of Compiz Fusion-Emerald before using it.

---

### Post by Nossie on 2007-10-07
no... I meant with your original script....

if I was to flush what your original script had done... how would I do that and start fresh again? when I upgraded to gutsy I never installed compiz and continued to use your mostly working older script

---

### Post by Nossie on 2007-10-07
e.g the following...

```

In file included from /usr/include/GL/gl.h:2150,
                 from ../include/compiz.h:48,
                 from main.c:37:
/usr/include/GL/glext.h:3943: error: expected declaration specifiers or ‘...’ before ‘*’ token
/usr/include/GL/glext.h:3943: error: ‘vOid’ declared as function returning a function
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/ian/.git4cf/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/.git4cf/compiz'
make: *** [all] Error 2

```

and this :-|

```

Executing autogen
  Status:      Succeeded! 
Executing make
  Status:      Failed! 

----------------------------------- Last loglines ------------------------------
colorfilter_options.c:493: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsSetObjectOption'
colorfilter_options.c:505: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c:511: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [colorfilter_options.lo] Error 1
make[3]: Leaving directory `/home/ian/.git4cf/plugins-main/src/colorfilter'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ian/.git4cf/plugins-main/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/.git4cf/plugins-main'
make: *** [all] Error 2

```

this?

```

addhelper_options.c:369: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperOptionsSetObjectOption'
addhelper_options.c:380: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.c:386: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [addhelper_options.lo] Error 1
make[3]: Leaving directory `/home/ian/.git4cf/plugins-extra/src/addhelper'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ian/.git4cf/plugins-extra/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/.git4cf/plugins-extra'
make: *** [all] Error 2

```

and this? :)

```

----------------------------------- Last loglines ------------------------------
fakeargb_options.c:261: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fakeargbOptionsSetObjectOption'
fakeargb_options.c:272: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
fakeargb_options.c:278: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [fakeargb_options.lo] Error 1
make[3]: Leaving directory `/home/ian/.git4cf/plugins-unsupported/src/fakeargb'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ian/.git4cf/plugins-unsupported/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/.git4cf/plugins-unsupported'
make: *** [all] Error 2

```

and thats all the errors :-| I did try doing a seach and remove all compiz mentions apart from the awn and cairo clock packages before I started your script...

---

### Post by Nossie on 2007-10-07
after I ran through the script there... I updated it 

```

compiz.c:852: error: incompatible types in assignment
compiz.c:852: warning: statement with no effect
compiz.c:853: error: 'MAXSHORT' undeclared (first use in this function)
compiz.c:853: error: incompatible types in assignment
compiz.c:853: warning: statement with no effect
make[2]: *** [compiz.lo] Error 1
make[2]: Leaving directory `/home/ian/.git4cf/libcompizconfig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/.git4cf/libcompizconfig'
make: *** [all] Error 2

```

---

### Post by searayman on 2007-10-07
don't work I get this error:



-------------------------------      Installing      ---------------------------
Executing autogen
  Status:      Succeeded! 
Executing make
  Status:      Failed! 

----------------------------------- Last loglines ------------------------------
../include/compiz.h:2355: error: expected specifier-qualifier-list before ‘GLint’
../include/compiz.h:2950: error: expected specifier-qualifier-list before ‘GLushort’
main.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘defaultColor’
main.c: In function ‘compLogMessage’:
main.c:116: error: ‘CompDisplay’ has no member named ‘logMessage’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/mike/.git4cf/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/.git4cf/compiz'
make: *** [all] Error 2
--------------------------------------------------------------------------------

Complete log file: /home/mike/.git4cf/logs/compiz_make)

Ignore and continue or abort (ignore/abort) ?

---

### Post by ElemonGW on 2007-10-07
As far as I can remember it is a dependency error. As soon as I get home I will tell you for sure and give you the dependency 's name (you see, I am connected through my mobile phone now ;) ) .

---

### Post by Nossie on 2007-10-07
> **ElemonGW said:**
> As far as I can remember it is a dependency error. As soon as I get home I will tell you for sure and give you the dependency 's name (you see, I am connected through my mobile phone now ;) ) .

I went back over the git compiz dependancies and ran 

```
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev 
```

missing packages were:
The following NEW packages will be installed:
  automake1.9 git-doc gitweb 

I'll give the install a go now :)

newp :( same problems for me.... heh either I'm missing a dependency or you werent talking about my issue :D

---

### Post by ElemonGW on 2007-10-07
You may try installing libglu1-mesa-dev. However, now that I see it better, this might not fix your problem. Anyway, you don't lose anything to install it, right? :)
PS: Git4CF Automator is NOT tested @ Gutsy.

---

### Post by Nossie on 2007-10-07
> **ElemonGW said:**
> You may try installing libglu1-mesa-dev. However, now that I see it better, this might not fix your problem. Anyway, you don't lose anything to install it, right? :)
PS: Git4CF Automator is NOT tested @ Gutsy.

Lose anything? I wouldnt be using Gutsy if I wasn't PLANNING on losing everything :D

but sadly no :( no joy..  I tried installing libglu1-mesa-dev but it said the package was already installed.

CompizFusion does run.... but if I tab switch I think I lose all the decorations and it goes a bit funny.. not sure if thats because of where its failing to compile

**Edit:** I tried tab switching again and it seems to be working.... nothing is not working that was working before.. but yeah I do have those failures on compile

---

### Post by searayman on 2007-10-07
> **ElemonGW said:**
> You may try installing libglu1-mesa-dev. However, now that I see it better, this might not fix your problem. Anyway, you don't lose anything to install it, right? :)
PS: Git4CF Automator is NOT tested @ Gutsy.

ok so while i waited for you to get back to me I tried your old cf installer and it installed a lot of things, but cf didnt work. So then I had it uninstall cf and went back to the new installer and cf installed fine. Your old version must have installed what ever dependencies i was missing.

But when i run cf, it doesnt have any window boarders nor do the animations work....

I get this error:

mike@mike-desktop:~$ fusion-icon
* Detected Session: gnome
* Searching for installed applications...
Backend : ini
Integration : true
Profile : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
* Using the GTK Interface
* Starting Compiz
... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering
compiz (core) - Error: Couldn't load plugin 'ccp'

---

### Post by maduranga on 2007-10-10
Is it worth installing manually compiled Compiz Fusion from git and remove gusty's default available compiz fusion? Will i get the same result by just installing compizconfig-settings-manager and enabling needed plugins and configuring cf?

---

### Post by dannyboy79 on 2007-10-10
> **maduranga said:**
> Is it worth installing manually compiled Compiz Fusion from git and remove gusty's default available compiz fusion? Will i get the same result by just installing compizconfig-settings-manager and enabling needed plugins and configuring cf?

if you want the latest greatest CF than yes. If you're satisfied with CF that's already with Gutsy than no. The differences are that the CF from Gutsy is older and was compiled with CF sources that are older. The reason is that CF is constantly being developed fixed etc etc, so there may be some little things fixed by using this script which will retreive the latest source files for CF from git and compile them and install CF on your machine. 

NOTE: The developer for this script states that his script was NOT tested on Gutsy so he isn't sure it'll work right. You can see by anohter user above, that he tried it on gutsy and despite having some compiling errors, he states that it's still working.

You're call.

---

### Post by dannyboy79 on 2007-10-10
> **searayman said:**
> ok so while i waited for you to get back to me I tried your old cf installer and it installed a lot of things, but cf didnt work. So then I had it uninstall cf and went back to the new installer and cf installed fine. Your old version must have installed what ever dependencies i was missing.

But when i run cf, it doesnt have any window boarders nor do the animations work....

I get this error:

mike@mike-desktop:~$ fusion-icon
* Detected Session: gnome
* Searching for installed applications...
Backend : ini
Integration : true
Profile : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
* Using the GTK Interface
* Starting Compiz
... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering
compiz (core) - Error: Couldn't load plugin 'ccp'

simple search using the error line within ubuntuforums search tool results in this:
[http://ubuntuforums.org/showthread.php?t=499979&page=2](http://ubuntuforums.org/showthread.php?t=499979&page=2)
if you do it at google, I am sure you'll find plenty of answers.

---

### Post by ElemonGW on 2007-10-10
> **dannyboy79 said:**
> [...]NOTE: The developer for this script states that his script was tested on Gutsy[...]
You mean not tested, right ;)

> **dannyboy79 said:**
> if you want the latest greatest CF than yes. If you're satisfied with CF that's already with Gutsy than no. The differences are that the CF from Gutsy is older and was compiled with CF sources that are older. The reason is that CF is constantly being developed fixed etc etc, so there may be some little things fixed by using this script which will retreive the latest source files for CF from git and compile them and install CF on your machine. 
=D>=D>=D> ;)

> **dannyboy79 said:**
> simple search using the error line within ubuntuforums search tool results in this:
[http://ubuntuforums.org/showthread.php?t=499979&page=2](http://ubuntuforums.org/showthread.php?t=499979&page=2)
if you do it at google, I am sure you'll find plenty of answers.

Exactly!!! People, errors like compile errors are certainly not because of the script. I believe you should post them elsewhere where you would probably also be able to get more help. I would suggest you to post here only errors you think that by changing some things at the script they should be fixed (so script-sided). Also you may post any dependency errors so that I will add them to be automatically installed.

---

### Post by dannyboy79 on 2007-10-10
[QUOTE=ElemonGW;3509660]You mean not tested, right ;)QUOTE]

oops, that's what I meant to write. I updated it. good catch

---

### Post by ElemonGW on 2007-10-10
> **dannyboy79 said:**
> oops, that's what I meant to write. I updated it. good catch
:mrgreen::mrgreen::mrgreen:

---

### Post by Starks on 2007-10-15
i'm getting makefile errors with Git4CF in gutsy.

---

### Post by ElemonGW on 2007-10-15
> **Starks said:**
> i'm getting makefile errors with Git4CF in gutsy.
Well, try some googling with the errors you get or try posting them at compiz fusion forums. You may also post them here but I don't guarantee you that I will be able to help (I have never tested it @ Gutsy).

---

### Post by st33med on 2007-10-15
In Gutsy, Compiz source will not download because, in my theory, it has been rid of since Compiz Fusion has taken place, and it is not going to release the compiz source in the repositories. I think there needs to be a workaround for this...

---

### Post by Frak on 2007-10-15
You need to do
```
sudo aptitude remove compiz-fusion -y
sudo aptitude update
sudo aptitude safe-upgrade
sudo apt-get build-dep compiz-fusion
```

In Gutsy.

---

### Post by coloured on 2007-10-18
should I run this script in uninstall mode before I upgrade to gutsy?
I am currently running 7.04 and installed compiz using this script.

cheers

---

### Post by TheBlackCat13 on 2007-10-18
For some reason the 3D windows plugin is not appearing, or at least I can't find it, even though I picked the "install all" option.

---

### Post by ElemonGW on 2007-10-19
> **coloured said:**
> should I run this script in uninstall mode before I upgrade to gutsy?
I am currently running 7.04 and installed compiz using this script.

cheers
Well, it is recommended to do so to avoid conflicts (also don't forget to uninstall pidgin if you have it installed, it can also cause conflicts).

> **TheBlackCat13 said:**
> For some reason the 3D windows plugin is not appearing, or at least I can't find it, even though I picked the "install all" option.
I removed it at the newest beta as it will not compile with compiz fusion from the 0.6 branch. It will be added back at the stable version of Git4CF Automator as it will also have support for installing compiz fusion from the head branch.

---

### Post by 7llusion on 2007-11-04
It doesn't work... It installed perfectly, but ow compiz gve me the infamous error:
```
seb@acer-laptop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```
I removed compiz before using the script to install...
Is there a command that can completely remove compiz, built, from git or from a deb?
PS:I'm on gutsy and used the
sudo aptitude remove compiz-fusion -y
sudo aptitude update 
sudo aptitude safe-upgrade
sudo aptitude safe-upgrade

---

### Post by shadowplane676 on 2007-11-07
it also doesnt work for me after a good install with no hickups

Kubuntu 7.04 Feisty x64 2.6.20-16 kernel
HP zv6000 laptop
ATI Radeon Xpress 200M  graphics card
i have the addin to the xorg.conf for no composite but i still get the error:

compiz (core) - Fatal: No composite extension

thats the only thing that errors. not sure what to do about it, any ideas?

---

### Post by ethan961 on 2007-11-10
```
compiz --replace
``` will not work wen compiling from git.
You must use ```
LIBGL_ALWAYS_INDIRECT=true compiz --replace --indirect-rendering --sm-disable ccp &
``` for ATI open source drivr with AIGLX,
```
LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &
``` for Intel/AIGLX. I am not sure about NVIDIA.
Ethan

---

### Post by ElemonGW on 2007-11-17
[Git4CF Automator version 0.1 Released]("http://elemongw.exofire.net/blog/2007/11/17/git4cf_automator_version_0.1_released")

---

### Post by ElemonGW on 2007-11-19
[Git4CF Automator Version 0.1.5 is Out!]("http://elemongw.exofire.net/blog/2007/11/19/git4cf_automator_version_0.1.5_is_out%21")

---

### Post by ElemonGW on 2007-11-25
[Git4CF Automator Version 0.1.7 is Out!]("http://elemongw.exofire.net/blog/2007/11/25/git4cf_automator_version_0.1.7_is_out%21")

---

### Post by smartboyathome on 2007-12-23
I get an error when running the Git4CF script, when trying to install plugins-main, it screws up.

```
make  all-recursive
make[1]: Entering directory `/home/aabbott/.git4cf/plugins-main'
Making all in metadata
make[2]: Entering directory `/home/aabbott/.git4cf/plugins-main/metadata'
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po animation.xml.in animation.xml
Generating and caching the translation database
Merging translations into animation.xml.
CREATED animation.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po colorfilter.xml.in colorfilter.xml
Found cached translation database
Merging translations into colorfilter.xml.
CREATED colorfilter.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po expo.xml.in expo.xml
Found cached translation database
Merging translations into expo.xml.
CREATED expo.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po ezoom.xml.in ezoom.xml
Found cached translation database
Merging translations into ezoom.xml.
CREATED ezoom.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po imgjpeg.xml.in imgjpeg.xml
Found cached translation database
Merging translations into imgjpeg.xml.
CREATED imgjpeg.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po neg.xml.in neg.xml
Found cached translation database
Merging translations into neg.xml.
CREATED neg.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po opacify.xml.in opacify.xml
Found cached translation database
Merging translations into opacify.xml.
CREATED opacify.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po put.xml.in put.xml
Found cached translation database
Merging translations into put.xml.
CREATED put.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po resizeinfo.xml.in resizeinfo.xml
Found cached translation database
Merging translations into resizeinfo.xml.
CREATED resizeinfo.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po ring.xml.in ring.xml
Found cached translation database
Merging translations into ring.xml.
CREATED ring.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po snap.xml.in snap.xml
Found cached translation database
Merging translations into snap.xml.
CREATED snap.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po text.xml.in text.xml
Found cached translation database
Merging translations into text.xml.
CREATED text.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po thumbnail.xml.in thumbnail.xml
Found cached translation database
Merging translations into thumbnail.xml.
CREATED thumbnail.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po wall.xml.in wall.xml
Found cached translation database
Merging translations into wall.xml.
CREATED wall.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po winrules.xml.in winrules.xml
Found cached translation database
Merging translations into winrules.xml.
CREATED winrules.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po workarounds.xml.in workarounds.xml
Found cached translation database
Merging translations into workarounds.xml.
CREATED workarounds.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po scaleaddon.xml.in scaleaddon.xml
Found cached translation database
Merging translations into scaleaddon.xml.
CREATED scaleaddon.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po vpswitch.xml.in vpswitch.xml
Found cached translation database
Merging translations into vpswitch.xml.
CREATED vpswitch.xml
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po shift.xml.in shift.xml
Found cached translation database
Merging translations into shift.xml.
CREATED shift.xml
make[2]: Leaving directory `/home/aabbott/.git4cf/plugins-main/metadata'
Making all in src
make[2]: Entering directory `/home/aabbott/.git4cf/plugins-main/src'
Making all in animation
make[3]: Entering directory `/home/aabbott/.git4cf/plugins-main/src/animation'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c -o animation.lo animation.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c animation.c  -fPIC -DPIC -o .libs/animation.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c animation.c -o animation.o >/dev/null 2>&1
mv -f .deps/animation.Tpo .deps/animation.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT airplane3d.lo -MD -MP -MF .deps/airplane3d.Tpo -c -o airplane3d.lo airplane3d.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT airplane3d.lo -MD -MP -MF .deps/airplane3d.Tpo -c airplane3d.c  -fPIC -DPIC -o .libs/airplane3d.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT airplane3d.lo -MD -MP -MF .deps/airplane3d.Tpo -c airplane3d.c -o airplane3d.o >/dev/null 2>&1
mv -f .deps/airplane3d.Tpo .deps/airplane3d.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT beamup.lo -MD -MP -MF .deps/beamup.Tpo -c -o beamup.lo beamup.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT beamup.lo -MD -MP -MF .deps/beamup.Tpo -c beamup.c  -fPIC -DPIC -o .libs/beamup.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT beamup.lo -MD -MP -MF .deps/beamup.Tpo -c beamup.c -o beamup.o >/dev/null 2>&1
mv -f .deps/beamup.Tpo .deps/beamup.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT burn.lo -MD -MP -MF .deps/burn.Tpo -c -o burn.lo burn.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT burn.lo -MD -MP -MF .deps/burn.Tpo -c burn.c  -fPIC -DPIC -o .libs/burn.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT burn.lo -MD -MP -MF .deps/burn.Tpo -c burn.c -o burn.o >/dev/null 2>&1
mv -f .deps/burn.Tpo .deps/burn.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT curvedfold.lo -MD -MP -MF .deps/curvedfold.Tpo -c -o curvedfold.lo curvedfold.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT curvedfold.lo -MD -MP -MF .deps/curvedfold.Tpo -c curvedfold.c  -fPIC -DPIC -o .libs/curvedfold.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT curvedfold.lo -MD -MP -MF .deps/curvedfold.Tpo -c curvedfold.c -o curvedfold.o >/dev/null 2>&1
mv -f .deps/curvedfold.Tpo .deps/curvedfold.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dodge.lo -MD -MP -MF .deps/dodge.Tpo -c -o dodge.lo dodge.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dodge.lo -MD -MP -MF .deps/dodge.Tpo -c dodge.c  -fPIC -DPIC -o .libs/dodge.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dodge.lo -MD -MP -MF .deps/dodge.Tpo -c dodge.c -o dodge.o >/dev/null 2>&1
mv -f .deps/dodge.Tpo .deps/dodge.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT domino.lo -MD -MP -MF .deps/domino.Tpo -c -o domino.lo domino.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT domino.lo -MD -MP -MF .deps/domino.Tpo -c domino.c  -fPIC -DPIC -o .libs/domino.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT domino.lo -MD -MP -MF .deps/domino.Tpo -c domino.c -o domino.o >/dev/null 2>&1
mv -f .deps/domino.Tpo .deps/domino.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dream.lo -MD -MP -MF .deps/dream.Tpo -c -o dream.lo dream.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dream.lo -MD -MP -MF .deps/dream.Tpo -c dream.c  -fPIC -DPIC -o .libs/dream.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT dream.lo -MD -MP -MF .deps/dream.Tpo -c dream.c -o dream.o >/dev/null 2>&1
mv -f .deps/dream.Tpo .deps/dream.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT explode3d.lo -MD -MP -MF .deps/explode3d.Tpo -c -o explode3d.lo explode3d.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT explode3d.lo -MD -MP -MF .deps/explode3d.Tpo -c explode3d.c  -fPIC -DPIC -o .libs/explode3d.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT explode3d.lo -MD -MP -MF .deps/explode3d.Tpo -c explode3d.c -o explode3d.o >/dev/null 2>&1
mv -f .deps/explode3d.Tpo .deps/explode3d.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fade.lo -MD -MP -MF .deps/fade.Tpo -c -o fade.lo fade.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fade.lo -MD -MP -MF .deps/fade.Tpo -c fade.c  -fPIC -DPIC -o .libs/fade.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fade.lo -MD -MP -MF .deps/fade.Tpo -c fade.c -o fade.o >/dev/null 2>&1
mv -f .deps/fade.Tpo .deps/fade.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT focusfade.lo -MD -MP -MF .deps/focusfade.Tpo -c -o focusfade.lo focusfade.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT focusfade.lo -MD -MP -MF .deps/focusfade.Tpo -c focusfade.c  -fPIC -DPIC -o .libs/focusfade.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT focusfade.lo -MD -MP -MF .deps/focusfade.Tpo -c focusfade.c -o focusfade.o >/dev/null 2>&1
mv -f .deps/focusfade.Tpo .deps/focusfade.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fold3d.lo -MD -MP -MF .deps/fold3d.Tpo -c -o fold3d.lo fold3d.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fold3d.lo -MD -MP -MF .deps/fold3d.Tpo -c fold3d.c  -fPIC -DPIC -o .libs/fold3d.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT fold3d.lo -MD -MP -MF .deps/fold3d.Tpo -c fold3d.c -o fold3d.o >/dev/null 2>&1
mv -f .deps/fold3d.Tpo .deps/fold3d.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT glide.lo -MD -MP -MF .deps/glide.Tpo -c -o glide.lo glide.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT glide.lo -MD -MP -MF .deps/glide.Tpo -c glide.c  -fPIC -DPIC -o .libs/glide.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT glide.lo -MD -MP -MF .deps/glide.Tpo -c glide.c -o glide.o >/dev/null 2>&1
mv -f .deps/glide.Tpo .deps/glide.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT horizontalfold.lo -MD -MP -MF .deps/horizontalfold.Tpo -c -o horizontalfold.lo horizontalfold.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT horizontalfold.lo -MD -MP -MF .deps/horizontalfold.Tpo -c horizontalfold.c  -fPIC -DPIC -o .libs/horizontalfold.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT horizontalfold.lo -MD -MP -MF .deps/horizontalfold.Tpo -c horizontalfold.c -o horizontalfold.o >/dev/null 2>&1
mv -f .deps/horizontalfold.Tpo .deps/horizontalfold.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT leafspread.lo -MD -MP -MF .deps/leafspread.Tpo -c -o leafspread.lo leafspread.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT leafspread.lo -MD -MP -MF .deps/leafspread.Tpo -c leafspread.c  -fPIC -DPIC -o .libs/leafspread.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT leafspread.lo -MD -MP -MF .deps/leafspread.Tpo -c leafspread.c -o leafspread.o >/dev/null 2>&1
mv -f .deps/leafspread.Tpo .deps/leafspread.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT magiclamp.lo -MD -MP -MF .deps/magiclamp.Tpo -c -o magiclamp.lo magiclamp.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT magiclamp.lo -MD -MP -MF .deps/magiclamp.Tpo -c magiclamp.c  -fPIC -DPIC -o .libs/magiclamp.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT magiclamp.lo -MD -MP -MF .deps/magiclamp.Tpo -c magiclamp.c -o magiclamp.o >/dev/null 2>&1
mv -f .deps/magiclamp.Tpo .deps/magiclamp.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT options.lo -MD -MP -MF .deps/options.Tpo -c -o options.lo options.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT options.lo -MD -MP -MF .deps/options.Tpo -c options.c  -fPIC -DPIC -o .libs/options.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT options.lo -MD -MP -MF .deps/options.Tpo -c options.c -o options.o >/dev/null 2>&1
mv -f .deps/options.Tpo .deps/options.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT particle.lo -MD -MP -MF .deps/particle.Tpo -c -o particle.lo particle.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT particle.lo -MD -MP -MF .deps/particle.Tpo -c particle.c  -fPIC -DPIC -o .libs/particle.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT particle.lo -MD -MP -MF .deps/particle.Tpo -c particle.c -o particle.o >/dev/null 2>&1
mv -f .deps/particle.Tpo .deps/particle.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT polygon.lo -MD -MP -MF .deps/polygon.Tpo -c -o polygon.lo polygon.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT polygon.lo -MD -MP -MF .deps/polygon.Tpo -c polygon.c  -fPIC -DPIC -o .libs/polygon.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT polygon.lo -MD -MP -MF .deps/polygon.Tpo -c polygon.c -o polygon.o >/dev/null 2>&1
mv -f .deps/polygon.Tpo .deps/polygon.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT rollup.lo -MD -MP -MF .deps/rollup.Tpo -c -o rollup.lo rollup.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT rollup.lo -MD -MP -MF .deps/rollup.Tpo -c rollup.c  -fPIC -DPIC -o .libs/rollup.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT rollup.lo -MD -MP -MF .deps/rollup.Tpo -c rollup.c -o rollup.o >/dev/null 2>&1
mv -f .deps/rollup.Tpo .deps/rollup.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT skewer.lo -MD -MP -MF .deps/skewer.Tpo -c -o skewer.lo skewer.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT skewer.lo -MD -MP -MF .deps/skewer.Tpo -c skewer.c  -fPIC -DPIC -o .libs/skewer.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT skewer.lo -MD -MP -MF .deps/skewer.Tpo -c skewer.c -o skewer.o >/dev/null 2>&1
mv -f .deps/skewer.Tpo .deps/skewer.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT wave.lo -MD -MP -MF .deps/wave.Tpo -c -o wave.lo wave.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT wave.lo -MD -MP -MF .deps/wave.Tpo -c wave.c  -fPIC -DPIC -o .libs/wave.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT wave.lo -MD -MP -MF .deps/wave.Tpo -c wave.c -o wave.o >/dev/null 2>&1
mv -f .deps/wave.Tpo .deps/wave.Plo
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT zoomside.lo -MD -MP -MF .deps/zoomside.Tpo -c -o zoomside.lo zoomside.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT zoomside.lo -MD -MP -MF .deps/zoomside.Tpo -c zoomside.c  -fPIC -DPIC -o .libs/zoomside.o
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT zoomside.lo -MD -MP -MF .deps/zoomside.Tpo -c zoomside.c -o zoomside.o >/dev/null 2>&1
mv -f .deps/zoomside.Tpo .deps/zoomside.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -module -avoid-version -no-undefined -lGLU   -o libanimation.la -rpath /usr/lib/compiz animation.lo airplane3d.lo beamup.lo burn.lo curvedfold.lo dodge.lo domino.lo dream.lo explode3d.lo fade.lo focusfade.lo fold3d.lo glide.lo horizontalfold.lo leafspread.lo magiclamp.lo options.lo particle.lo polygon.lo rollup.lo skewer.lo wave.lo zoomside.lo -lX11-xcb -lXcomposite -lXdamage -lXrandr -lXinerama -lSM -lxslt -lstartup-notification-1 -lX11 -lxcb -lXfixes -lICE -lxml2   
gcc -shared  .libs/animation.o .libs/airplane3d.o .libs/beamup.o .libs/burn.o .libs/curvedfold.o .libs/dodge.o .libs/domino.o .libs/dream.o .libs/explode3d.o .libs/fade.o .libs/focusfade.o .libs/fold3d.o .libs/glide.o .libs/horizontalfold.o .libs/leafspread.o .libs/magiclamp.o .libs/options.o .libs/particle.o .libs/polygon.o .libs/rollup.o .libs/skewer.o .libs/wave.o .libs/zoomside.o  -lGLU -lX11-xcb -lXcomposite -lXdamage -lXrandr -lXinerama -lSM /usr/lib/libxslt.so -lstartup-notification-1 -lX11 -lxcb -lXfixes -lICE /usr/lib/libxml2.so  -Wl,-soname -Wl,libanimation.so -o .libs/libanimation.so
ar cru .libs/libanimation.a  animation.o airplane3d.o beamup.o burn.o curvedfold.o dodge.o domino.o dream.o explode3d.o fade.o focusfade.o fold3d.o glide.o horizontalfold.o leafspread.o magiclamp.o options.o particle.o polygon.o rollup.o skewer.o wave.o zoomside.o
ranlib .libs/libanimation.a
creating libanimation.la
(cd .libs && rm -f libanimation.la && ln -s ../libanimation.la libanimation.la)
make[3]: Leaving directory `/home/aabbott/.git4cf/plugins-main/src/animation'
Making all in colorfilter
make[3]: Entering directory `/home/aabbott/.git4cf/plugins-main/src/colorfilter'
/usr/local/bin/bcop --header colorfilter_options.h ../../metadata/colorfilter.xml
/usr/local/bin/bcop --source colorfilter_options.c ../../metadata/colorfilter.xml
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR='"/usr/share/compiz"' -DPREFIX='"/usr"' -DLIBDIR='"/usr/lib"' -DLOCALEDIR="\"/usr/share/locale\"" -DIMAGEDIR='"/usr/share/compiz"'              -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT colorfilter_options.lo -MD -MP -MF .deps/colorfilter_options.Tpo -c -o colorfilter_options.lo colorfilter_options.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -DDATADIR=\"/usr/share/compiz\" -DPREFIX=\"/usr\" -DLIBDIR=\"/usr/lib\" -DLOCALEDIR=\"/usr/share/locale\" -DIMAGEDIR=\"/usr/share/compiz\" -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT colorfilter_options.lo -MD -MP -MF .deps/colorfilter_options.Tpo -c colorfilter_options.c  -fPIC -DPIC -o .libs/colorfilter_options.o
In file included from colorfilter_options.c:19:
colorfilter_options.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.h:59: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.h:63: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterGetFilterDecorations'
colorfilter_options.h:67: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.h:71: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c:25: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c:26: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsVTable'
colorfilter_options.c:44: error: array type has incomplete element type
colorfilter_options.c:50: error: array type has incomplete element type
colorfilter_options.c: In function 'colorfilterGetToggleWindowKeyOption':
colorfilter_options.c:56: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetToggleWindowKeyNotify':
colorfilter_options.c:62: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterGetToggleScreenKeyOption':
colorfilter_options.c:68: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetToggleScreenKeyNotify':
colorfilter_options.c:74: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterGetSwitchFilterKeyOption':
colorfilter_options.c:80: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetSwitchFilterKeyNotify':
colorfilter_options.c:86: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:90: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c: In function 'colorfilterGetFiltersOption':
colorfilter_options.c:98: error: dereferencing pointer to incomplete type
colorfilter_options.c:98: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetFiltersNotify':
colorfilter_options.c:104: error: dereferencing pointer to incomplete type
colorfilter_options.c:104: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterGetFilterDecorations'
colorfilter_options.c: In function 'colorfilterGetFilterDecorationsOption':
colorfilter_options.c:116: error: dereferencing pointer to incomplete type
colorfilter_options.c:116: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetFilterDecorationsNotify':
colorfilter_options.c:122: error: dereferencing pointer to incomplete type
colorfilter_options.c:122: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:126: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c: In function 'colorfilterGetFilterMatchOption':
colorfilter_options.c:134: error: dereferencing pointer to incomplete type
colorfilter_options.c:134: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetFilterMatchNotify':
colorfilter_options.c:140: error: dereferencing pointer to incomplete type
colorfilter_options.c:140: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:144: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
colorfilter_options.c: In function 'colorfilterGetExcludeMatchOption':
colorfilter_options.c:152: error: dereferencing pointer to incomplete type
colorfilter_options.c:152: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterSetExcludeMatchNotify':
colorfilter_options.c:158: error: dereferencing pointer to incomplete type
colorfilter_options.c:158: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterGetDisplayOption':
colorfilter_options.c:164: error: dereferencing pointer to incomplete type
colorfilter_options.c: In function 'colorfilterGetScreenOption':
colorfilter_options.c:170: error: dereferencing pointer to incomplete type
colorfilter_options.c:170: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:174: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsDisplayOptionInfo'
colorfilter_options.c:180: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsSetDisplayOption'
colorfilter_options.c: In function 'colorfilterOptionsGetDisplayOptions':
colorfilter_options.c:225: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:230: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsScreenOptionInfo'
colorfilter_options.c:237: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsSetScreenOption'
colorfilter_options.c: In function 'colorfilterOptionsGetScreenOptions':
colorfilter_options.c:290: error: dereferencing pointer to incomplete type
colorfilter_options.c:290: error: dereferencing pointer to incomplete type
colorfilter_options.c: At top level:
colorfilter_options.c:295: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsInitScreen'
colorfilter_options.c: In function 'colorfilterOptionsFiniScreen':
colorfilter_options.c:319: error: 'colorfilterPluginVTable' undeclared (first use in this function)
colorfilter_options.c:319: error: (Each undeclared identifier is reported only once
colorfilter_options.c:319: error: for each function it appears in.)
colorfilter_options.c:320: warning: 'return' with a value, in function returning void
colorfilter_options.c:322: error: dereferencing pointer to incomplete type
colorfilter_options.c:322: error: dereferencing pointer to incomplete type
colorfilter_options.c:325: warning: implicit declaration of function 'compFiniScreenOptions'
colorfilter_options.c:325: warning: nested extern declaration of 'compFiniScreenOptions'
colorfilter_options.c: At top level:
colorfilter_options.c:330: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsInitDisplay'
colorfilter_options.c: In function 'colorfilterOptionsFiniDisplay':
colorfilter_options.c:360: error: 'colorfilterPluginVTable' undeclared (first use in this function)
colorfilter_options.c:361: warning: 'return' with a value, in function returning void
colorfilter_options.c:363: error: dereferencing pointer to incomplete type
colorfilter_options.c:365: warning: implicit declaration of function 'freeScreenPrivateIndex'
colorfilter_options.c:365: warning: nested extern declaration of 'freeScreenPrivateIndex'
colorfilter_options.c:367: warning: implicit declaration of function 'compFiniDisplayOptions'
colorfilter_options.c:367: warning: nested extern declaration of 'compFiniDisplayOptions'
colorfilter_options.c: At top level:
colorfilter_options.c:372: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'colorfilterOptionsInit'
colorfilter_options.c: In function 'colorfilterOptionsFini':
colorfilter_options.c:389: error: 'colorfilterPluginVTable' undeclared (first use in this function)
colorfilter_options.c:390: warning: 'return' with a value, in function returning void
colorfilter_options.c:393: warning: implicit declaration of function 'freeDisplayPrivateIndex'
colorfilter_options.c:393: warning: nested extern declaration of 'freeDisplayPrivateIndex'
colorfilter_options.c: At top level:
colorfilter_options.c:404: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [colorfilter_options.lo] Error 1
make[3]: Leaving directory `/home/aabbott/.git4cf/plugins-main/src/colorfilter'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aabbott/.git4cf/plugins-main/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aabbott/.git4cf/plugins-main'
make: *** [all] Error 2
```

Help. :confused:

---

### Post by rosspoko on 2008-02-26
When I try to install, I get this error while in the "Executing autogen" section after downloading compiz's Git repository:  

```
autoreconf: running: aclocal
configure.ac:197: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:33: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:197: error: possibly undefined macro: AM_GCONF_SOURCE_2
autoreconf: /usr/bin/autoconf failed with exit status: 1
```

---

