---
title: "How-To: Install Compiz-Fusion from GIT"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by Espreon on 2007-12-17
OK, so you wanna install the latest CF from GIT? Well this guide will tell you how!
Lets get a couple of things straight:

1: Whenever I ask you to run a command with "/home/yourhome" replace "yourhome" with the name of your home folder

2: The latest CF from GIT is just as stable as the one shipped from Gutsy (in my experiences at least, and I poke around A LOT with settings and whatnot)

3: IDK if this guide will work on Feisty

4: I am no Linux guru so use this guide at your own risk

What you will get from this guide:

-The latest version of CF
-Some really cool plugins, like Atlantis2, Snowglobe, Freewins, etc
-The latest version of CCSM, Emerald
-Lots of Emerald themes
-The CF Icon
-Some tips
-An adventure (maybe)

Enough small talk, lets begin...

[B]1. Install one of the most important app for any CF user who wants bleeding edge features... GIT:
[/B]
Enter this in the terminal:

```
sudo apt-get install git-core
```
[B]
2. Temporarliy switch to a different WM:[/B]

For GNOME users:

```
metacity --replace
```

For KDE users:

```
kwin --replace
```

**3. [B]Completely** uninstall CF:[/B]

```
sudo apt-get remove compiz compiz-core compiz-dev compiz-bcop compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-kde emerald libcompizconfig-0 python-compiz --purge
```

If you wanna play it safe delete the .compiz folder in your home folder (it is hidden so you will need to enable the sight of hidden folders)

**4. Make Compiz directory:**

```
mkdir Compiz
```

**5. Get the important stuff:**

Download [this]("http://gitweb.beryl-project.org/?p=users/3v1n0/compiz-patches;a=snapshot;h=HEAD") and [this]("http://personales.ya.com/telemako/makefusion.tar.gz") to your newly created Compiz directory

Now extract the "makefusion.tar.gz" so that the file "makefusion" is at the root of the Compiz directory. Extract the "compiz-patches-HEAD.tar.gz" to root of the Compiz directory.

If you followed the directions correctly you should see a "makefusion" file and a "compiz-patches" directory in your Compiz directory.

**6. Manipulate the makefusion script (If you use only GNOME with CF you can skip this step)**

GNOME users:

```
gedit /home/yourhome/Compiz/makefusion
```

For KDE users:

```
kate /home/yourhome/Compiz/makefusion
```

Now that we opened the script search for this: COMPIZREMOVE="kde"

If you only use CF with KDE change "kde" to "gnome"
If you use CF with both remove the line
Also if you are a KDE user search for ubuntu and change it to kubuntu
[B]
7. Change the script permissions:[/B]

```

cd Compiz
chmod +x makefusion

```
[B]
8. Install the dependencies:[/B]

```

./makefusion packages

```
[B]
9. Download the source code from the CF GIT repos:[/B]

```

./makefusion clone

```
[B]
10.Apply Patch[/B]

```

cp ~/Compiz/compiz-patches/compiz-disable-libx11-xcb-support.patch ~/Compiz/compiz

```

Then enter this"

```

cd compiz
patch < compiz-disable-libx11-xcb-support.patch

```

When it asks for files to patch enter this first:

```

include/compiz-core.h

```

Hit enter and enter this:

```

src/display.c

```in

After you finish patching those files enter this:

```

cd ..

```

**11. Compile Time!**

Enter this:

```

sudo ./makefusion install

```

This will take a while

After its finished please proceed
[B]
12. Making it so CF still autostarts...[/B]

This guide breaks Ubuntu's CF startup mechanism and you can no longer manually start CF by entering "compiz" in the terminal. So you will need to make it so the CF Icon is automatically started.

Enter this:

```

sudo cp /usr/bin/fusion-icon /usr/local/bin

```

For GNOME users:

Goto: System>Preferences>Sessions

Hit add, for the name put "CF Icon" (w/o quotes) and for the command put "fusion-icon" (w/o quotes). Hit OK.

For KDE users:

You are on your own, IDK how to make things autostart on KDE, the important thing is that the command to start the CF Icon is "fusion-icon" (w/o quotes)

For KDE 4 users:

Create a file in /usr/lib/kde4/share/autostart 
called Fusion-Icon.desktop and fill the empty file with this:

```

[Desktop Entry]
Encoding=UTF-8
Exec=fusion-icon

```

**13. The most important step..**.

Configure and Enjoy.

To configure CF enter this:

```

ccsm

```

Or Look for "Advance Desktop Effects Settings" in your menu.
In GNOME it is found under: System>Preferences

[B]
Updating:[/B]

If you wanna update CF to its latest enter this in the terminal (assuming the workin directory is your home folder)

```

cd Compiz
sudo ./makefusion clone
sudo ./makefusion install

```

Remember this can break CF, and before wasting your time check this website, to see if anything was recently changed:

[http://gitweb.beryl-project.org/](http://gitweb.beryl-project.org/)
[B]
Uninstalling:[/B]

If you wanna uninstall the GIT Version of CF do the following (assuming the workin directory is your home folder):

```

cd Compiz
sudo ./makefusion uninstall

```

If you wanna play it safe delete the .compiz folder in your home folder (it is hidden so you will need to enable the sight of hidden folders)

[B]
Optional Stuf**f:**

Finding additional plugins to add to your collection:[/B]

Goto this website:

[http://gitweb.beryl-project.org/](http://gitweb.beryl-project.org/)

Look for something that sounds nice and heres example commands to enter:

```

git-clone git://gitweb.beryl-project.org/fusion/plugins/3d
cd 3d
make
sudo make install

```
[B]
Re-enabling the authentic "Genie Effect":[/B]

This is what you need to do to re enable the authentic Genie Effect in CF:

```

sudo apt-get install ghex

```

Now enter this:

For GNOME users:

```

sudo gedit /usr/local/share/compiz/animation.xml

```

For KDE users:

```

sudo kate /usr/local/share/compiz/animation.xml

```

Search for (w/o quotes): "<short>Magic Lamp Max Waves</short>"

Now goto the line (w/o quotes) "<min>3</min>" and change 3 to 0. Save and quit.

Then enter this:

```

sudo ghex2 /usr/local/lib/compiz/libanimation.so

```

Goto Edit>Find

In the Second box (the smaller one) type in (w/o quotes) "magic_lamp_max_waves"

Change the 3 in this "<min>3</min" next to "magic_lamp_max_waves" to 0, save and quit.

Open CCSM and goto Animations>Effect Settings>Magic Lamp>Magic Lamp Max Waves and reduce the 3 to 0.

Enjoy..

Most of this tutorial was taken from this great site: [http://compizfusionrevolution.wordpress.com/2007/11/10/install-compiz-fusion-git-step-by-step-from-makefusion-script/](http://compizfusionrevolution.wordpress.com/2007/11/10/install-compiz-fusion-git-step-by-step-from-makefusion-script/)

**Help Desk (If any1 has a better name please yell out):**
[B]
If you are having errors with CCSM try this before complaining (thanks bfoos):
[/B]
```
sudo ldconfig
```

**If Compiz is significantly increasing boot/login time then look at these tips:**

1. Disable plugins you don't need or ever use (Disabling lots of plugins you do not use can noticably decrease boot/login time)

If anybody has any more tips that will decrease login time that relates to Compiz please yell out...

---

### Post by glennric on 2007-12-18
Why do you say to copy the file /usr/bin/fusion-icon to /usr/local/bin?  This should have nothing to do with whether or not compiz loads at startup.  The only thing needed is to add fusion-icon to your session.  This may conflict with compiz loading at startup, so you may need to do something about that.  

Also, instead of editing animation.xml and libanimation.xml after installing you should edit the source files before compilation.  Then you won't have to edit a hex file.  I have attached a patch that will make these changes.
From the directory for plugins-main type
```
bzcat path/to/fix-min-magic-lamp-waves.patch.bz2 | patch -p1
```
You will still have to change the setting in ccsm.

Edit:  I forgot to point out that to install ghex2 you should type 
```
sudo apt-get install ghex
```
not sudo apt-get install ghex2

Edit2:  Oh, I also forgot the most important thing.  That is thanks for the post.  I didn't use your script, but I essentially used the method in the script, and the patches were useful.

---

### Post by Espreon on 2007-12-18
On the contrary, in my experiences CF Icon, even though it is set to auto start with GNOME, will not start unless fusion-icon is located in /usr/local/bin... Thanks for your feedback.
But did my guide work for you? (Even though I am sure I know the answer).

Also the script is not mine, it was from that great website.

---

### Post by glennric on 2007-12-19
> **Espreon said:**
> On the contrary, in my experiences CF Icon, even though it is set to auto start with GNOME, will not start unless fusion-icon is located in /usr/local/bin... Thanks for your feedback.
But did my guide work for you? (Even though I am sure I know the answer).

Also the script is not mine, it was from that great website.

That is odd, and doesn't make sense.  Both /usr/bin and /usr/local/bin should be in your path.  So if you add fusion-icon to your session it should start if it is in either of those.  It works for me without copying it by the way.  The other thing is that with your prefix set to /usr/local, as is the default in your script, fusion-icon should be installed to /usr/local/bin by default.  So you aren't really copying it there, it is already there.  

As to whether your guide worked.  Yes, I got everything installed and running.  Although, I really only used your guide to get an idea of the order of installation and to locate the git repository to use.  I actually made debian packages of it all, modifying the ubuntu gutsy deb scripts appropriately.

---

### Post by shadow sk1ll on 2007-12-24
ok i followed everything up to ccsm.
when i do that i get 

skynet@skynet:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsStringToEdges
skynet@skynet:~$ 

what ya think i should do?

---

### Post by Espreon on 2007-12-24
Hmmmm, try recompiling CCSM, otherwise I really do not know.

---

### Post by bfoos on 2007-12-25
I had the same exact issue as shadow sk1ll. I followed your guide to the letter and got no window decorator for my time. Had to remove the git build and install from synaptic to get everything working correctly.

---

### Post by joshuachad on 2007-12-25
you dont have to recomplie anything. Provided you installed to /usr/local all you need to do anytime you complile something is run sudo ldconfig.

Then you should be straight.

---

### Post by kpel on 2007-12-25
Huh, I just followed the instructions and have almost everything working.  I've got the effects and the icon, but I've got the good 'ole no windows border thing.  Configuration screens won't come up either.  Edit: Alt+F2 also fails to pull up the window.  I'm sure this is all the same bug, but I've yet to figure it out.


Nvidia 7950GX2, drivers from the repos, and I've already got the argb, -d 24, composite, and render accel flags set in xorg.conf.  Gotta see if I can figure it out, I don't like the CF version in the ubuntu repos.

Edit2: I can now get the Emerald and CCSM windows, I installed the libemeraldengine package via synaptic along with it's dependency as I noticed an error output for the library.  Now I've just got the window border problem....I imagine that alt+f2 not working anymore is a result of CF stealing key bindings...

Edit3: Apparently all of that Christmas food kept my brain from functioning properly.  If you happen to have the problem I did, and can get into CCSM, make sure the Window Decoration plugin is enabled.  As I look through it I'm noticing a lot of rather necessary stuff isn't on by default, like the move plugin.  Double check what plug-ins are enabled.  I actually feel rather stupid having not figured that out faster, but I'll leave this post here for anyone else that might run into the problem.


Big thanks to Espreon for the How-To.

---

### Post by bfoos on 2007-12-25
^ Yup, all plugins are disabled by default. I racked my brain and was just about to remove the git build when I figured I'd just start enabling plugins until my window borders were functioning properly. At first, only the first rendered window was decorated. Now all is peachy. Much nicer than the version in the repos. Many thanks to the author of this guide. 

I know it may be a no brainer for some, but you should add..

Run:
```
sudo ldconfig
```

before running ccsm.

It's not so obvious to some of us newbies.

---

### Post by Ubumby on 2007-12-30
After I installed this script for my compiz and set it up to start up (Fusion Icon) every time I log into my fresh install of ubuntu gutsy, I have to wait 3-4 minutes for it to start. Therefore it slows down my other startup applications. Does anyone know what is causing this?

---

### Post by tylerspaska on 2007-12-31
i'm using feisty and it worked great for me.

now i have to spend the next 3 weeks tweaking every little nuance.

---

### Post by glennric on 2008-01-06
> **Ubumby said:**
> After I installed this script for my compiz and set it up to start up (Fusion Icon) every time I log into my fresh install of ubuntu gutsy, I have to wait 3-4 minutes for it to start. Therefore it slows down my other startup applications. Does anyone know what is causing this?

This is adding several plugins that are not installed in the default ubuntu install, as well as emerald.  When compiz starts it has to initialize all of these plugins with all of their settings, and load emerald.  This adds to the time it takes to load.

---

### Post by lonely man on 2008-01-07
hi.. Espreon

I this link it's not work with me.

[http://personales.ya.com/telemako/makefusion.tar.gz](http://personales.ya.com/telemako/makefusion.tar.gz)

can u kindly plz upload it again to another server or upload it here?

---

### Post by ST.x on 2008-01-07
> **glennric said:**
> That is odd, and doesn't make sense.  Both /usr/bin and /usr/local/bin should be in your path.  So if you add fusion-icon to your session it should start if it is in either of those.  It works for me without copying it by the way.

Yep same here, it works without copying it. Thanks to Espreon :)
For the method to update it, does GIT check only for the updated files or does it download the whole thing again?

---

### Post by airbornemist6 on 2008-01-07
Gah! I have that same problem, I'm going to see if I can fix it... I don't think it should take this long. I understand it taking 30 seconds, but not 3-4. I can load my xp machine, log-in, open firefox, and get to this thread before it starts. I definately would not call that normal.

---

### Post by Espreon on 2008-01-07
> **lonely man said:**
> hi.. Espreon

I this link it's not work with me.

[http://personales.ya.com/telemako/makefusion.tar.gz](http://personales.ya.com/telemako/makefusion.tar.gz)

can u kindly plz upload it again to another server or upload it here?

The link works fine with me...

---

### Post by Espreon on 2008-01-07
> **ST.x said:**
> Yep same here, it works without copying it. Thanks to Espreon :)
For the method to update it, does GIT check only for the updated files or does it download the whole thing again?

I believe it redownloads the whole thing, but I am not sure...

---

### Post by Espreon on 2008-01-07
For those who are experiencing login/boot time being increased then a good thing is to disable some plugins you do not need or do not ever use.

---

### Post by airbornemist6 on 2008-01-07
the problem is i have almost all my plugins disabled. if i disabled any more, it would be better for me to just go back to the repo version of compiz fusion

EDIT: I tried disabling... just about everything, and it still does it. I then tried taking it off startup entirely, and guess what, it's still loading slow, and it looks like it's the network driver causing the slow load time... which could be either the result of an update (unlikely) or something did something really weird during the install... on another note, I didn't run sudo ldconfig until after I installed, might that have something to do with it?

---

### Post by sensimilla on 2008-01-10
Just followed the how-to and it's working great, no problems.

Had a couple of errors during the download and install, relating, I think, to the mouse gestures plugin, stuff about git repo not existing. It looked like the script had terminated early but I carried on and all is good.

many thanks to Espreon

:guitar:

[edit]

hmm, looks like I spoke too soon. I am getting the 2-3 minute start up problem.

The startup process appears to hang after loading the desktop and toolbars. This seems to be just before the gnome session startup is run. I can start programs but they have no window decorations until after compiz-icon starts. It may be something to do with no network access as my network does not start until it is run from gnome sessions startup (wireless).
Running top shows that no process is using more than 1% cpu while the start-up is stalled.

Anyone got any ideas how to fix or troubleshoot this problem ?

---

### Post by airbornemist6 on 2008-01-10
It has nothing to do with no network access. I'm looking at my system log and it looks like it might have something to do with the network, however I can't track down what is causing it. There is like a minute of completely unaccounted for time in the log and it's not being caused by the previous entry.

---

### Post by Phil420 on 2008-01-11
hey i've got some problems after installing...
when i write ccsm in the terminal, there are some errors at the end... take a look
```

Initializing core options...done
Initializing firepaint options...done
Initializing move options...done
Initializing text options...done
Initializing cubecaps options...done
Initializing cube options...done
Initializing atlantis options...done
Initializing fireflies options...done
Initializing regex options...done
Initializing video options...done
Initializing scale options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing wobbly options...done
Initializing neg options...done
Initializing snow options...done
Initializing ezoom options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing expo options...done
Initializing decoration options...done
Initializing 3d options...done
Initializing glib options...done
Initializing fade options...done
Initializing cubedbus options...done
Initializing resizeinfo options...done
Initializing animation options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing resize options...done
Initializing rotate options...done
Initializing png options...done
Initializing shift options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing dbus options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing vpswitch options...done
Initializing place options...done
Initializing imgjpeg options...done
Initializing svg options...done
Initializing mswitch options...done
Initializing cubereflex options...done
Initializing workarounds options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```
If someone knows what to do, plz help!
Thanks! :)

---

### Post by ST.x on 2008-01-11
^ I've got this as well, but ccsm works properly.

---

### Post by airbornemist6 on 2008-01-11
Hmmmm not sure if I got that, but I imagine it shouldn't have hurt anything really.

---

### Post by Phil420 on 2008-01-11
okay i've deleted the whole thing and did the how to again... and when i run compiz --replace to activate it, it does this
```

phil@Phil-Desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0
phil@Phil-Desktop:~$ 

```
help!
thanks :P

---

### Post by airbornemist6 on 2008-01-12
... *twitch* lol uh... that series of error messages is pretty self-explanatory, I think. I believe you could try reinstalling your video driver. That's what it looks like to me... but don't take my advice, i'd say wait until someone answers that knows what they are talking about.

---

### Post by Phil420 on 2008-01-12
> **airbornemist6 said:**
> ... *twitch* lol uh... that series of error messages is pretty self-explanatory, I think. I believe you could try reinstalling your video driver. That's what it looks like to me... but don't take my advice, i'd say wait until someone answers that knows what they are talking about.

thanks dude, i'll try to find suitable drivers for my card... because there's still things weird.
If anybody knows a good place for good drivers to get for my ATI Radeon X1650 Series Pro graphic card or help me maybe please it bugs me a lot i only wanted Ubuntu to do these cool effects XD so thanks guys!

---

### Post by airbornemist6 on 2008-01-12
hmmm... have you tried using XGL?

---

### Post by DarkAngel88 on 2008-01-12
airbornemist6: I have the same problem as yours...  it takes 2-3 minutes for CF to load !!!  Doesn't make any sense !!  I'll have to get back to the "old" compiz in the repositories i guess !

Edit : have you found a way to solve this issue ?

---

### Post by Phil420 on 2008-01-12
> **airbornemist6 said:**
> hmmm... have you tried using XGL?

don't know if it's that x server thing, but when i installed it and tried to install my graphic card, it went wrong and i couldn't log back in after reboot. i couldn't do anything. until i got to another pc any learned that i could reconfigure the x server so it would work again. and it did. but now i don't know if its working or whatever :S

---

### Post by airbornemist6 on 2008-01-12
XGL is usually the best choice for radeon cards if you can get it working. It's fast, and when it's working you rarely ever have bug problems. The ati drivers are now finally capable of running (read as : walking at a slow pace) without XGL, but it's still not a good idea to skip on it.

---

### Post by airbornemist6 on 2008-01-12
@ DarkAngel88 I'm still working on it. I believe it might be an error in compiling causing things to go kablooey. I just reinstalled ubuntu on my laptop because in addition to this I also broke my sound (while trying to fix it), so I'm going to see if I can get both working at the same time before touching anything else.

EDIT:

Wow, sorry about the double post, I'm so ADD xD

---

### Post by Phil420 on 2008-01-12
> **airbornemist6 said:**
> XGL is usually the best choice for radeon cards if you can get it working. It's fast, and when it's working you rarely ever have bug problems. The ati drivers are now finally capable of running (read as : walking at a slow pace) without XGL, but it's still not a good idea to skip on it.

okay sounds like a good idea but i don't exactly know what to do because when i do it, it doesn't work properly :S

---

### Post by airbornemist6 on 2008-01-12
I shall look for a howto for you, and when I find one I shall valiantly edit this post and... post it!

I hope this works for you. If not... see if you can install the ATi proprietary drivers off their website... or atleast find a guide for it... something.
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748) (just make sure not to install the old versions of compiz xD)

---

### Post by Phil420 on 2008-01-12
thanks a lot but i think i'll fall asleep on my key board so i'll check it when i wake up.
thanks again bud:)

---

### Post by DarkAngel88 on 2008-01-12
The compiling error makes sense I think.  I had a couple of errors during installation but nothing to stop compiz & cie from compiling.

If it help you, I'm using a Nvidia card under 7.10 x64... but as I just saw, you're using 7.04 and have the issue... :S  Oh well, if I can help you in any way let me know !

---

### Post by airbornemist6 on 2008-01-12
Oh no, I'm a gutsy user, but I totally forgot to update that. Thanks for pointing it out. I'm also using Nvidia, it's on my laptop, an HP dv6446us. Nice laptop, but alternative OS support sucks.

---

### Post by DarkAngel88 on 2008-01-12
Hehe no problems !!

I'm heading to bed now... I'll try to find the root cause of this issue tomorrow !!  I'll come back in this thread to add info i have !  Later !

---

### Post by airbornemist6 on 2008-01-12
Hooray! Now we just need to get the attention of someone else who might actually know what to do! lol

---

### Post by glennric on 2008-01-13
> **ST.x said:**
> Yep same here, it works without copying it. Thanks to Espreon :)
For the method to update it, does GIT check only for the updated files or does it download the whole thing again?

The update method just updates those files that have changed.  It does not re-download the whole thing.  The .git sub-directory contains the information git needs to decide what needs to be upgraded.

---

### Post by airbornemist6 on 2008-01-13
Ok, I just did a cean install, and then ran this script again. Once again I have the long boot problem. I'm starting to think this might just not work regardless of what I do.

---

### Post by Espreon on 2008-01-16
Guide Fixes, fixed KDE installation instructions, and autostart instructions for KDE 4 have been added...

---

### Post by adarkenigma on 2008-01-17
slow start up is really annoying.. has anyone found fix for it yet?

---

### Post by Shroin on 2008-01-17
Hi, the install went just fine but I receive the following error after running ccsm:

> $ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsStringToEdges


Thanks for any help!

---

### Post by airbornemist6 on 2008-01-17
did you run 
```
sudo ldconfig
```

after you installed?

---

### Post by Shroin on 2008-01-17
That does it! Must have missed that one.

---

### Post by airbornemist6 on 2008-01-18
glad to hear it fixed your problem. by any chance are you also having long boots?

---

### Post by joshuachad on 2008-01-19
This issue bugs me cuz I am kinda lost why this is happening with the long boots. airbornemist6 if you don't mind being a Ginni pig try this:

sudo gedit /etc/ld.so.conf

then check and see if you have the lib directory called out that you installed CF to which would be if you used the script /usr/local/lib

if you DONT see it add it. Then reboot and see if the issue persists. I havent heard of this before at all.

Well I came back to edit this and apparently there is a lot of ppl that have this issue. Not sure what causing it but the devs for gnome are looking for volunteers to run straces and such. Now I was wondering is it the login that takes a while? Or boot time? I think its login time you guys are talking about and you should be specific and say that cuz installing CF wouldnt effect boot time at all. So when you search i.e. google for a fix make sure you specify login time.

In the meantime if you wish you can read this thread :[http://ubuntuforums.org/showthread.php?t=585635&page=25](http://ubuntuforums.org/showthread.php?t=585635&page=25)
I will warn you that there is probably 10 diffrent reasons this is happening listed there. So in a nutshull Gutsy is not the best release and Hardy is going to be awesome.

---

### Post by airbornemist6 on 2008-01-23
Ok, sorry it took so long for me to answer. I've been busy lately. I looked in my ld.so.conf and /usr/local/lib wasn't listed so I added:

```
 include /usr/local/lib/ 
```

I hope that's right, as I didn't really know what to put in there.

As for a better explanation of my problem:
When I start the computer everything is going fine, I get my gnome login, I type my username and password, and then I get to the desktop. The panel comes up, and sound, search applet, and switch user applet load, and it stops there. Beyond that I have to wait 3-4 minutes for anything to show up at all. I have no network connections, no window borders, etc. I'll check the thread you posted, since I'm at work and have like 5 hours of free time on my hands. I hope I can get this solved.

On another note, yeah I was looking forward to Gutsy before it came out. But then it reared it's ugly head when I first tried getting things to work. It's kind of like, the Ubuntu community felt that as a flagship for linux, they had to copy the flagship for operating systems (Microsoft) and release a crappy operating system that no one wants, but everyone will have to use.

---

### Post by Jinx-Wolf on 2008-02-22
I'm having a similar problem.

After I log in, my background and cursor show, but they just stay there, nother ever loads. I restart X and log in again, and then everything loads fine, except pidgin's window is never how I left it.

Other than that, everything is fine.

---

### Post by Jinx-Wolf on 2008-02-23
Ok, part of the reason is gnome-panel I think.
Once I can see my background, I simple use my shortcut key to open up a Terminal and kill gnome-panel.

After that everything loads fine, except when I switch to another user, and try to switch back. Then the whole screen turns black and I can only see my cursor.

I love all the extra features I get from the GIT install, but this is way to buggy for me to keep using. (I'll keep trying for a couple more days, and keep an eye on this thread)

---

### Post by Piddy on 2008-02-25
I'm sure the answer to my problem is in here, but I don't have enough time to read the whole thread, so here we go. When I entered the ccsm code, this came up:

Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: No module named compizconfig

---

### Post by airbornemist6 on 2008-02-25
sudo ldconfig

fixed.

or it should be anyway.

---

### Post by Piddy on 2008-02-26
> **airbornemist6 said:**
> sudo ldconfig

fixed.

or it should be anyway.

It didn't work. Still same error.

---

### Post by airbornemist6 on 2008-02-26
...oh... damn in that case, where are you getting this error? Is the script giving it to you? Or did you get it when you try and start ccsm

---

### Post by Jinx-Wolf on 2008-02-27
> **Piddy said:**
> I'm sure the answer to my problem is in here, but I don't have enough time to read the whole thread, so here we go. When I entered the ccsm code, this came up:

Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: No module named compizconfig

I've installed LinuxMint 4.0 and now i'm getting the same error. Tried the ldconfig, and I'm still getting it after I try to launch ccsm from the terminal.

I also get the following when trying to launch fusion-icon:
```
Traceback (most recent call last):
  File "/usr/local/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: No module named compizconfig

```

I'm going to attempt a reinstall from the start.

---

### Post by airbornemist6 on 2008-02-27
hmmm you may need to add a module for compiz... but it should have done that for you.

---

### Post by Jinx-Wolf on 2008-02-28
After installing it again, everything worked fine.

---

### Post by mac71 on 2008-03-02
I tried this in Fiesty, and it worked acharm. Sadly, in Gutsy it takes around 3-4 mins to start up, so I've uninsalled and  gone for the packaged one.

All is not lost though! I went here 

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

Its is a how to on installing new features as plugins. I installed the 3d windows and screensaver as that was all i was interested in. I now have just a short pause and all is well. This might just help to ease some of those frustfations.:mad:

---

### Post by airbornemist6 on 2008-03-03
There was some good news I forgot to report, if you use the script to uninstall this version of compiz, the startup problem does in fact disappear.

---

### Post by papershreddr on 2008-03-18
> **Jinx-Wolf said:**
> I'm having a similar problem.

After I log in, my background and cursor show, but they just stay there, nother ever loads. I restart X and log in again, and then everything loads fine, except pidgin's window is never how I left it.

Other than that, everything is fine.

I was having this problem too, but I was able to fix it.  Go to **System > Preferences > Appearance**, click the **Visual Effects** tab, and then pick the **None** option. 

That should cause your computer to load Metacity at startup instead of Compiz, which will stop it from breaking gnome-panel and nautilus.  You can still have Compiz load when you boot up by using fusion-icon.  This should also lessen startup time a bit because your computer will only try to load Compiz once instead of twice.

Hope that helps!

---

### Post by papershreddr on 2008-03-18
> **Phil420 said:**
> okay i've deleted the whole thing and did the how to again... and when i run compiz --replace to activate it, it does this
```

phil@Phil-Desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0
phil@Phil-Desktop:~$ 

```
help!
thanks :P

When you install using this script (or any other method of compiling from source that I'm aware of,) you can no longer use the "**compiz --replace**" command to start Compiz.  Instead, use "**fusion-icon**".  That should hopefully fix your problem.

---

### Post by Dr.Dixie on 2008-03-22
*bes depressed at unstable experience during short use*


!Dr.Dixie!

---

### Post by airbornemist6 on 2008-03-24
Sorry to hear that, but the good news is, hardy heron comes out later this month.

---

### Post by smackcode on 2008-03-29
i've installed compiz fusion using the guide from the first post, work ok with hardy heron but i noticed that everytime i set the horizontal virtual size to 4 it automatically reverts to 2 in about a second. virtual size seems to be ok with larger and lower values than 4, possible bug? or did i miss something?

---

### Post by airbornemist6 on 2008-03-31
> **smackcode said:**
> i've installed compiz fusion using the guide from the first post, work ok with hardy heron but i noticed that everytime i set the horizontal virtual size to 4 it automatically reverts to 2 in about a second. virtual size seems to be ok with larger and lower values than 4, possible bug? or did i miss something?

Are you using the slider to set it or manual input?

---

### Post by smackcode on 2008-04-08
i've tried both but the behavior is still the same

---

### Post by Firm18 on 2008-04-13
whenever I do: CCSM it says:
Bash: command not found

What should I do?

Also when I write Compiz in terminal it does:

/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0

---

### Post by techno-mole on 2008-04-17
i follwed this guide and it works perfectly, i had to enable some stuff, like window decorations, and the cube, but apart from that it works (i even have the screensaver plugin, which is what i was after)
by the way i used this guide to install cf on hardy (the beta) and its all stable, even with everything cranked up as high as my system will take. 
cheers

---

### Post by airbornemist6 on 2008-04-17
My suggestion to everyone: Wait the 7 days until hardy comes out. You could also just install the beta right now, the first (and probably last) release candidate comes out tomorrow, and it's running really nicely. You won't have all the plugins, but as long as you have the latest version of compiz, which it does, it's not hard to get them.

---

### Post by alexsabree on 2008-04-24
Thanks a bunch for this man.. although its a little buggy.. its still very nice knowing you have the latest version of compiz..

---

### Post by adityakavoor on 2008-05-11
[here]("http://kavoor.wordpress.com/2008/05/11/compile-compiz-from-git/") is my tutorial

---

### Post by blackvd on 2008-06-16
I received this error when updating

```
Ejecutando make
Makefile:58: *** [ERROR] No package 'compiz-text' found.  Stop.

Ejecutando make install
Makefile:58: *** [ERROR] No package 'compiz-text' found.  Stop.

Ejecutar compiz-manager o fusion-icon para iniciar Compiz Fusion.
 
Ejecutar ccsm o simple-ccsm para configurar Compiz Fusion.
```

Does that mean it didn't finish and when I reboot I'm screwed? Or should I be using a different method of install and updating now?

---

### Post by blackvd on 2008-06-17
I rebooted and all seemed fine ...but what now? How do I update compiz without this error? Someone must know since a lot of people followed this script.

---

### Post by Brando569 on 2008-06-22
great guide, works a lot better than git-compiz which seems to break on me every five minutes, i only have one problem with your script: it keeps on saying that compiz isnt installed:

Ejecutando make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

the second line there shows up about a good 10-15 times

---

### Post by kurci2 on 2008-06-23
I have a problem too.
Installation went perfectly.
But when i tryed to enable "Animations" i get a question if a want to disable Minimaze effect and i click YES.
But l can't see any window borders!!!!!:mad:
I think that the Magic Lamp plugin have some problems!
Can anyone help me???

---

### Post by Brando569 on 2008-06-23
i actually started over (deleted all the downloaded and git'd stuff) with git-compiz and it worked perfectly, well aside from 3 of the unsupported plugins not compiling.

---

### Post by kurci2 on 2008-06-23
So you don't know anythink about my problem.
If Magic lamp is enabled in animations i can't see the windows borders, if i set same different animation everythink is OK!

---

### Post by duncanyoyo1 on 2008-06-25
Well i recently installed Compiz Fusion from Git using the guide found [HERE](http://forum.compiz-fusion.org/showthread.php?t=1985#post16632)

And it appears to be working, but I have no window borders and cannot use any plugins. But it is somewhat working because AWN works, which needs a compositor to work.

I am on Ubuntu 8.04 with an nVidia GeForce 8500 GT

Any suggestions?

---

### Post by kurci2 on 2008-06-25
I have the same problem!
I hope that, they willl made some updates quickly!!

---

### Post by chalewa on 2008-06-26
i seem to keep getting errors of compiz complaining that it can't find itself...

also, how does one whitelist fglrx... /usr/bin/compiz doesn't exist. or am i way off.

thanks a lot

---

### Post by Fredizdman on 2008-06-27
I have the exact same issue as **duncanyoyo1**.

Awn is working so at least I know compiz is doing something...but no window borders and no plugins work. I've tried enabling/disabling various plugins and yes I have window decorations enabled.

BTW- anyone still having a ccsm error that will not allow it to start and relates to python. You can just install the latest compizconfig-python from [[COLOR="Blue"]here[/COLOR]]("http://releases.compiz-fusion.org/0.7.6/")

---

### Post by 5735guy on 2008-06-29
Hey there, this is ALMOST great, its just I have no window borders. I have tried emerald --replace I cannot open the emerald manager either ?? HELP PLEASE !!!:confused::confused:

---

### Post by travelinman81 on 2008-07-01
you may have to try to reinstall emerald. 

I am on 8.04 Hardy I followed the guide I was having problems with some glitches in the repository version and thought if I built it from git it would fix some stuff. It was the best Idea ever its working perfectly I have so much more control over everything cheers to the person that put this howto together

---

### Post by blazercist on 2008-07-01
is the guide in the original post still working? I mean, it has been a long time since it was posted.                            edit: never mind, worked like a charm.

---

### Post by 5735guy on 2008-07-02
Oh yes I reinstalled and its all up and running:):) So pleased I have found a script that works on Gutsy after much searching MANY MANY THANKS :):):guitar::):)

---

### Post by 5735guy on 2008-07-03
Now I am thoroughly happy that it works on gutsy, would I be pushing my luck to try it out on feisty?

---

### Post by 5735guy on 2008-07-09
It just keeps better and better. This script works on Feisty as well:):) Once again MANY MANY THANKS :guitar::guitar::guitar:

---

### Post by NovruzeliH on 2008-07-11
i tried this but it doesnt seem to be working idk why :(

---

### Post by antid0te on 2008-07-20
I'm using Hardy Heron and follow the instructions. Everything's ok except the window manager, there is no window manager.

```

The program 'emerald' is currently not installed.  You can install it by typing:
sudo apt-get install emerald
bash: emerald: command not found
```

i try to compile emerald from source, which has been kept back in compiz-git source directory, but error in compiling.

```
......
checking whether byte ordering is bigendian... no
configure: Using PKG_CONFIG_PATH=NONE/lib/pkgconfig
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EMERALD... configure: error: Package requirements ( xrender >= 0.8.4  		    gtk+-2.0 >= 2.8.0 		    libwnck-1.0	      		    libdecoration     		    pangocairo) were not met:

No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMERALD_CFLAGS
and EMERALD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

i've done apt-cache search wnck
```
libwnck-common - Window Navigator Construction Kit - common files
libwnck22 - Window Navigator Construction Kit - runtime files
```

and run 
```

apt-get install libwnck-common libwnck22
```:(:(:(
buat compiling still result in error..
any help for this? thx anyway..

EDIT: Solved!! I'm using libwnck-dev from [here]("https://launchpad.net/ubuntu/hardy/i386/libwnck-dev/2.22.1-0ubuntu1"). Delete the compiz-git-source and start all over again, voila! Emerald was just running ;)

---

### Post by ebeckhusen on 2008-07-20
Okay, I installed following the directions on the first page.  Then I used the gconf-editor to make it so I could have separate wallpapers for each desktop.  Now when I log in all I  can see is the desktop, no toolbars and alt-f2 doesn't do anything.  The only way I have found to get things working again is to delete .gconfd from my home directory and reboot.  But then the next time I reboot the problem is back again.

Any suggestions how to fix this, aside from having to delete .gconfd and reboot every time I restart the computer?  Or do I have to live without my different wallpapers (not a big deal but I like having them).

---

