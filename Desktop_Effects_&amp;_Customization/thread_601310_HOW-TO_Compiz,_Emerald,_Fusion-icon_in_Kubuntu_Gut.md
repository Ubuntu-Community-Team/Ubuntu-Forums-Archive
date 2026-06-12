---
title: "HOW-TO: Compiz, Emerald, Fusion-icon in Kubuntu Gutsy"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by dentaku65 on 2007-11-03
This is a quick and dirty guide to install Compiz, Emerald and Fusion-icon on Kubuntu Gutsy, based on my own experience. The guide works for Intel graphic cards (855GM mine) and, I think, with the proper configuration of xorg.conf and drivers works with other graphic cards as well.

See this thread to find a proper xorg.conf for your card (if is posted):
[http://ubuntuforums.org/showthread.php?t=629303]("http://ubuntuforums.org/showthread.php?t=629303")


The guide is based on **Kubuntu ** (KDE env) upgraded from Feisty to Gutsy with 3rd party repositories on Feisty side (for instance Trevino repos for Compiz), but even in a clean installation worth a try in case of issues with Compiz.

Please be sure to have enabled *only* official Ubuntu repositories and to have enabled all of them (universe, multiverse, etc..).

Let's start.

**1) The cleaning part (can be omitted by the users with a clean install and no 3rd party repository and/or scripts)**

Clean apt 
```
sudo apt-get clean
```

Remove all Compiz/Emerald
```
sudo aptitude purge ~ncompiz ~nlibdecoration
```

Update the slocate database (it takes a while)
```
sudo updatedb
```

Save your actual settings of Compiz in your Home dir (not mandatory)
```
cp ~/.config/compiz/compizconfig/Default.ini ~/
```

Remove one-by-one all the occourences of Compiz/Emerald left on your box, here how to find them.
For Compiz:
```
locate compiz |more
```

For ccsm:
```
locate ccsm |more
```

For Emerald:
```
locate emerald |more
```

After the deletion of files/directories above we have a really clean box and we are ready for the second part.

**2) The installation part**

Install the official packages
```
sudo apt-get install compiz-bcop compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-kde compiz-plugins compizconfig-settings-manager emerald libcompizconfig-backend-kconfig libcompizconfig0 libdecoration0 libemeraldengine0 python-compizconfig librsvg2-common
```

Install the Fusion-icon launcher (not provided by Ubuntu repositories)
Be sure to have essential packages for compilation
```
sudo apt-get install build-essential
```

Download and save on your desktop this version of Fusion-icon
```
http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=b3217b36e92fd76b39310de98a9c983923a7464a
```

Then install it:
```
cd ~/Desktop
```
```
tar xvfz fusion-icon-b3217b36e92fd76b39310de98a9c983923a7464a.tar.gz
```
```
cd fusion-icon/
```
```
make
```
```
sudo make install
```

*NOTE*: this is not the last version of Fusion-icon, but is the one that works with kwin (or at least the one that I was able to make it works)

Install at least one theme for Emerald (the package emerald-themes is not provided by Ubuntu repositories)
Go here and choose one or more:
```
http://www.compiz-themes.org/index.php?xsortmode=high&xcontentmode=103&page=0
```

Or choose one of my favorites :-)
```
http://www.compiz-themes.org/content/show.php/Kubuntu+Edgy+Default+%28trueglass%29?content=48646
```

Save a theme package on your desktop

**3) The configuration part**

Launch the Fusion-icon
```
fusion-icon &
```

Press enter twice in the console.
The Fusion-icon launcher will be appear in the tray next to clock, right click on it and choose "Emerald Theme Manager", then click Import button, point to the theme file saved on the desktop and close.
Right click again on Fusion-icon, choose "Select window decorator" and thick on Emerald
Anyway, the Fusion-icon is pretty clear and will restart automatically to the next boot

Save your new settings of Compiz and switch back your original one (if needed, maybe after a test) *not mandatory*
```
cp ~/.config/compiz/compizconfig/Default.ini ~/.config/compiz/compizconfig/Default.ini.original
```
```
cp  ~/Default.ini ~/.config/compiz/compizconfig/Default.ini
```

Now you can delete fusion-icon-b3217b36e92fd76b39310de98a9c983923a7464a.tar.gz, fusion-icon/ dir and Emerald theme package from your desktop

That's it. Hope it helps.

**Addendum**
In order to disable annoyances with OpenOffice and Emerald/Compiz (windows out of screen and menu flickering) do a right click on Fusion-icon and choose Settings Manager, go to Utility section, enable the **Workarounds** plugin and in the Workarounds general tab unthick "Legacy Fullscreen Support" and enable all other options.

Consider to use as configuration file the flat-file option (instead of KDE Configuration Backend)
CCSM -> Preferences -> Backend -> Flat-file Configuration Backend

---

### Post by mrvertigo on 2007-11-03
Awesome, great job

---

### Post by dentaku65 on 2007-11-03
> **mrvertigo said:**
> Awesome, great job

Thx mrvertigo 
:guitar:

---

### Post by StitchJAcket on 2007-11-05
I can't get this to work when i run the 
sudo apt-get install compiz-bcop compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-kde compiz-plugins compizconfig-settings-manager emerald libcompizconfig-backend-kconfig libcompizconfig0 libdecoration0 libemeraldengine0 python-compizconfig librsvg2-common
Command i get
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-bcop

So what should i do?
I really want emerald theme manager for a them i am attempting to load for a seminar on how Ubuntu can improve your business in December so it would be greatly appreciated.

---

### Post by dentaku65 on 2007-11-05
> **StitchJAcket said:**
> I can't get this to work when i run the 
sudo apt-get install compiz-bcop compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-kde compiz-plugins compizconfig-settings-manager emerald libcompizconfig-backend-kconfig libcompizconfig0 libdecoration0 libemeraldengine0 python-compizconfig librsvg2-common
Command i get
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-bcop

So what should i do?
I really want emerald theme manager for a them i am attempting to load for a seminar on how Ubuntu can improve your business in December so it would be greatly appreciated.

Do not include compiz-bcop (it is not mandatory), try this:

```
sudo apt-get install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-kde compiz-plugins compizconfig-settings-manager emerald libcompizconfig-backend-kconfig libcompizconfig0 libdecoration0 libemeraldengine0 python-compizconfig librsvg2-common
```

Or try to enable all the ubuntu repos like universe, multiverse... etc in order to include compiz-bcop

---

### Post by StitchJAcket on 2007-11-05
I tried that last command and i got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-core has no installation candidate

---

### Post by StitchJAcket on 2007-11-05
So i tried to change the repositories and that seems to be doing it so thank you very much for your help i appreciate it.

---

### Post by silvagroup on 2007-11-12
Thanks this worked really well. Compiz seems to be behaving much better after following this post.
One question, I used to be able to drag a window from one desktop top to another, but now I can't. How do I get that function back?

Thanks in advance.:confused:

---

### Post by daniel_szollosi-nagy on 2007-11-12
Thanks, this is exactly what I've been looking for!

One quick question - after starting Compiz, I got a small window with a green sphere icon in it at the top left corner of my screen (Adept Notifier). I can't close it - is there any way of getting rid of it?

---

### Post by silvagroup on 2007-11-12
You can just double click on it and put in your task bar and close it. Or you can just log out log back in and it should correct itself. At least that worked for me.

---

### Post by keezy88 on 2007-11-13
I am new to the Linux scene. I have a few questions regarding the use of compiz.

First off, I went through and followed all of these instructions, which work perfectly, but when I restart my computer the skin that I am currently using, along with all of my effects, are disabled. I was wondering how to fix that.

Secondly, I would like to change the number of workspaces I have enabled. I right click on the workspaces and go to the properties and change the amount, and nothing happens. Anyone have any ideas of what is going on?

---

### Post by keezy88 on 2007-11-13
nvm, i got it figured out.

---

### Post by dentaku65 on 2007-11-14
> **silvagroup said:**
> Thanks this worked really well. Compiz seems to be behaving much better after following this post.
One question, I used to be able to drag a window from one desktop top to another, but now I can't. How do I get that function back?

Thanks in advance.:confused:

I supposed that you have to enable the plugin Rotate Cube
Open Settings Manager -> Desktop -> Rotate Cube

---

### Post by st0kes on 2007-11-15
Great how-to. Thanks :)

---

### Post by silvagroup on 2007-11-16
> I supposed that you have to enable the plugin Rotate Cube
 Open Settings Manager -> Desktop -> Rotate Cube
It is enabled. I looked at the settings and could not see anything that appeared to address this.
The window can be drug partially into the next desktop but I have to stop the drag and then move into the other desktop and then totally drag it into that desktop.
Must bi in one of the settings just not sure which one.
Currently I just use Move To Desktop from the border.

---

### Post by dentaku65 on 2007-11-16
> **silvagroup said:**
> It is enabled. I looked at the settings and could not see anything that appeared to address this.
The window can be drug partially into the next desktop but I have to stop the drag and then move into the other desktop and then totally drag it into that desktop.
Must bi in one of the settings just not sure which one.
Currently I just use Move To Desktop from the border.

Enable Edge Flip Move under the configuration of Rotate Cube

---

### Post by desudesudesu on 2007-11-16
I did it all, and then, like every other time I´ve tried to install Compiz or Beryl, my borders disappear and I have to switch back to kwin.

Any ideas?

---

### Post by dentaku65 on 2007-11-16
> **desudesudesu said:**
> I did it all, and then, like every other time I´ve tried to install Compiz or Beryl, my borders disappear and I have to switch back to kwin.

Any ideas?

Beryl is not available in the official repositories... please check again my #1 post and, first of all, remove all occurrences of your previous installation of compiz and emerald as I suggested.

---

### Post by desudesudesu on 2007-11-16
I meant from the past times I've tried with Fiesty and Dapper, before I switched back over to Windows for a bit.
The one I have right now is a fresh install, not even an hour old, and I followed your guide to the letter.
I deleted all the files that it found, and double checked to make sure they really were gone.

I have an ATI x1600 AGP, which is most likely the problem.

Edit: In conjunction with another guide, I got it to work! (finally)

Thanks for the guide dentaku65.

---

### Post by dentaku65 on 2007-11-17
> **desudesudesu said:**
> I meant from the past times I've tried with Fiesty and Dapper, before I switched back over to Windows for a bit.
The one I have right now is a fresh install, not even an hour old, and I followed your guide to the letter.
I deleted all the files that it found, and double checked to make sure they really were gone.

I have an ATI x1600 AGP, which is most likely the problem.

Edit: In conjunction with another guide, I got it to work! (finally)

Thanks for the guide dentaku65.

Great desu^3 
it would be nice to have some specification of your fixing if is pertinent with my guide in order to update the post #1

;-)

---

### Post by desudesudesu on 2007-11-17
I've been looking for that post again, but I can't find it.
I wanted to use it on my xubuntu box too since, it has videocard that can run it.

---

### Post by silvagroup on 2007-11-17
:KS Flip edge was the trick I was looking for. Now I can drag windows around desktops again:)
Thank you. Great post everything with compiz working great.

Have you tried the new release yet. I imagine that newer compiz probably will not be added to repos till 8.04.
Any suggestions on how one would go about with installing in 7.10?

---

### Post by jayachandranm on 2007-11-17
There is a repo for the Fusion-icon available from,

[http://ubuntulinuxtipstricks.blogspot.com/2007/10/compiz-fusion-notification-area-icon.html](http://ubuntulinuxtipstricks.blogspot.com/2007/10/compiz-fusion-notification-area-icon.html)

I used this repo for installation and it just works for my Gutsy.

Jaya

---

### Post by dentaku65 on 2007-11-18
> **jayachandranm said:**
> There is a repo for the Fusion-icon available from,

[http://ubuntulinuxtipstricks.blogspot.com/2007/10/compiz-fusion-notification-area-icon.html](http://ubuntulinuxtipstricks.blogspot.com/2007/10/compiz-fusion-notification-area-icon.html)

I used this repo for installation and it just works for my Gutsy.

Jaya

Thx Jaya for the info, I've just some doubts to add a different repo than the official ones...is this working with Kubuntu Gutsy (kde) as well?

---

### Post by twent4 on 2007-11-20
Hi guys, i followed the instructions and everything seems to install correctly, the icon is showing on the taskbar and the window decorator is working fine... however, none of the compiz features seem activated, no matter how much i play with them inside CCSM... is this just a rendering/video issue, or did i miss something?

running kubuntu 7.10
Sapphire Radeon x800GT (restricted drivers)

thanks

---

### Post by silvagroup on 2007-11-20
Make sure your video board is set up correctly.

---

### Post by dentaku65 on 2007-11-21
> **twent4 said:**
> Hi guys, i followed the instructions and everything seems to install correctly, the icon is showing on the taskbar and the window decorator is working fine... however, none of the compiz features seem activated, no matter how much i play with them inside CCSM... is this just a rendering/video issue, or did i miss something?

running kubuntu 7.10
Sapphire Radeon x800GT (restricted drivers)

thanks

See on opencompositing the documentation for your card:
[http://compiz.org/ATI]("http://compiz.org/ATI")

and set your xorg.conf how is stated there.

Can you post the output of this?
```
glxinfo |grep render
```

---

### Post by RSJ on 2007-11-22
Hello, first thank you very much for the write up. I've followed it up to starting compiz as the window manager, when it starts I have no window decorations, am unable to move windows, and lacking just about any compiz features =P. This is the output I get when I start compiz:

```
* switching to compiz.real ...
* Starting: compiz.real
compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
compiz.real (core) - Error: Couldn't activate plugin 'dbus'
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
* switching to kwin ...
* Starting: kwin

```
I realize I should probably be able to derive something from that, but I'm still in the early learning stages. Anyone have any suggestions? Thanks again.

Edit: Welp, I feel silly, I wasn't turning on the window decorator. However, there's still a small annoyance, I have to click directly on the bar of a window to bring it to the front, instead of anywhere on the window.

---

### Post by dentaku65 on 2007-11-22
> **RSJ said:**
> ..

Edit: Welp, I feel silly, I wasn't turning on the window decorator. However, there's still a small annoyance, I have to click directly on the bar of a window to bring it to the front, instead of anywhere on the window.

Can you post the output of this?
```
cat ~/.config/compiz/compizconfig/Default.ini
```

---

### Post by RSJ on 2007-11-22
Can't locate, the only thing in my compizconfig directory is config.

---

### Post by dentaku65 on 2007-11-23
> **RSJ said:**
> Can't locate, the only thing in my compizconfig directory is config.

AFAIK you have to enable the flat-file backend:

CCSM -> Preferences -> Backend -> Flat-file Configuration Backend

---

### Post by twent4 on 2007-11-24
Thanks for the replies silvagroup and dentaku65
It appears to be simpler than i thought: the restricted drivers got disabled after a reboot, so i was back to software rendering for everything... compiz is working fine now.

Got another question tho: while it was not working, i enabled "indirect rendering", hoping maybe it will fix the problem (before i knew it was a driver thing). Now that everything is working fine, the option is grayed out and i cannot turn it off. Compiz is eating up resources, and i think it might actually be better for my system to turn direct rendering back on... anyone know what i have to turn off/edit in order for the option to become available again?

thanks

---

### Post by julio.jacobo on 2007-11-24
Hi, 
after typing

fusion-icon &

the screen goes blank. I've recorded the output, it is

/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/kde-window-decorator
/usr/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* Using the Qt4 Interface
* Searching for installed applications...
* KDE is running
* Decorator "" is invalid.
... choosing kde-window-decorator --replace as default decorator
* Starting: compiz.real

I've got an nvidia g-force 6200 card, I am using the proprietary driver and the corresponding entry on the xorg.conf file is

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

any clue of what could be wrong?
thank you in advance!!

---

### Post by dentaku65 on 2007-11-24
> **julio.jacobo said:**
> Hi, 
after typing

fusion-icon &

the screen goes blank. I've recorded the output, it is

/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/kde-window-decorator
/usr/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* Using the Qt4 Interface
* Searching for installed applications...
* KDE is running
* Decorator "" is invalid.
... choosing kde-window-decorator --replace as default decorator
* Starting: compiz.real

I've got an nvidia g-force 6200 card, I am using the proprietary driver and the corresponding entry on the xorg.conf file is

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

any clue of what could be wrong?
thank you in advance!!

Did you tried to load  kde-window-decorator after fusion-icon & command?
Let's try:
```
 kde-window-decorator --replace
```
Then in the fusion-icon menu choose Emerald Theme Manager then install at least one theme and reload emerald as window decorator.

---

### Post by dentaku65 on 2007-11-24
> **twent4 said:**
> Thanks for the replies silvagroup and dentaku65
It appears to be simpler than i thought: the restricted drivers got disabled after a reboot, so i was back to software rendering for everything... compiz is working fine now.

Got another question tho: while it was not working, i enabled "indirect rendering", hoping maybe it will fix the problem (before i knew it was a driver thing). Now that everything is working fine, the option is grayed out and i cannot turn it off. Compiz is eating up resources, and i think it might actually be better for my system to turn direct rendering back on... anyone know what i have to turn off/edit in order for the option to become available again?

thanks

I dunno how to turn off the indirect rendering... as far as I know is something inside the code of compiz derived from a better performances for nvidia cards; maybe with some switches in a personalized script you're able to do it, but I don't know how to perform this inside compiz-fusion launcher...

---

### Post by julio.jacobo on 2007-11-24
Thank you very much for your reply, dentacu65.
I've  tried  issuing the command

kde-window-decorator --replace

before issuing  the command "fusion-icon &" and also after.
In both cases what I got was the same blank screen.
The difference was that the recorded output from the "fusion-icon &" command was 

/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/kde-window-decorator
/usr/bin/emerald
/usr/bin/metacity
/usr/bin/kwin

only.
Thanks again!

---

### Post by dentaku65 on 2007-11-25
> **julio.jacobo said:**
> ..
before issuing  the command "fusion-icon &" and also after.
In both cases what I got was the same blank screen.
...

Seems something of your xorg configuration; first of all we need to know your card... btw I have the suspect that if run this:

```
compiz --replace
```

you will get the same error....

---

### Post by sbrown1038 on 2007-11-25
Thanks for the great 'how to'.  I got compiz to work fine on my notebook.  I was very pissed about being forced from beryl to compiz until I got it working with your 'how to'.  At home, however, I am having a problem.

I had beryl working fine on this machine until I upgraded to kubuntu 7.10.  I had to do something special in order for the borders, title bar, etc. to draw with the beryl window manager.  I'm having the same problem now -- no borders, title bar, etc.

I have an nvidia card which seems to be configured correctly.  Issuing 'compiz --replace &' from the command line gives this:

```

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```


What else do I need to do to get compiz working on my home desktop PC?

Thanks for your help.

---

### Post by StitchJAcket on 2007-11-27
What kind of Nvidia card do you have?

---

### Post by tradesman on 2007-11-27
I get as far as> [http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=b3217b36e92fd76b39310de98a9c983923a7464a](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=b3217b36e92fd76b39310de98a9c983923a7464a)

and get the following

> bash: [http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon:](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon:) No such file or directory


so help needed please.

edit sorry my mistake I was pasting in terminal

---

### Post by tradesman on 2007-11-27
Followed this how to to the letter I think  but compiz doesent seem to be working.
When type compiz in terminal I get this

> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

xserver-xgl shows as installed in synaptic package manager
I'm using abuilt in graphics engine 

my OS is ubuntu 7.10 AMD 64bit.
Still in need of help here thanks in advance.

---

### Post by StitchJAcket on 2007-11-27
In order to use any of the desktop effects you need to be using your brand specific drivers and not the default ones that Ubuntu loads. This can usually be accomplished by going to restricted drivers manager and checking the specific driver for your card. Keep in mind if you are using NVidia and the restricted driver is legacy then chances are without some heavy coding exp. you wont be able to run compiz fusion

---

### Post by tradesman on 2007-11-27
> **StitchJAcket said:**
> In order to use any of the desktop effects you need to be using your brand specific drivers and not the default ones that Ubuntu loads. This can usually be accomplished by going to restricted drivers manager and checking the specific driver for your card. Keep in mind if you are using NVidia and the restricted driver is legacy then chances are without some heavy coding exp. you wont be able to run compiz fusion

Thanks for the  reply just been to the restricted drivers manager and got this

> Your hardware does not need any restricted drivers.

---

### Post by Spacebaboon on 2007-11-28
just registered on the site to say thanks :)

I've spent a couple of nights wrestling with this, couldn't quite get the right permutation, and then found your post. 2 minutes later, all is gorgeous.

---

### Post by Lithia on 2007-11-28
I installed Kubuntu 7.10 last week, moving from OpenSuSE 10.2.  I have moderate experience with rpm-based linux, but this is my first deb-based distro.  I have followed the steps on this page, but I still am having difficulty with the compiz/emerald software.

I am running a Dell XPS (gen 1) laptop with an ATI Radeon Mobility 9800.  I have installd the fglrx drivers provided by ATI and have allowed the use of restricted drivers.  However, when i try to run compiz from the command line, I receive the following output.  (Similar to a post above)

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

What more do I need to install to enable Xgl?

Any assistance would be vastly appreciated!

-Lithia

---

### Post by Melcar on 2007-11-28
Add fglrx to the whitelist in /usr/bin/compiz.  Also, some video cards are blacklisted on that same file.

---

### Post by StitchJAcket on 2007-11-28
> **tradesman said:**
> Thanks for the  reply just been to the restricted drivers manager and got this

Ok so what kind of NVidia card do you have. Do you know the model? Because from what is sounds your card is older and might be unable to support this feature.

---

### Post by tradesman on 2007-11-28
> **StitchJAcket said:**
> Ok so what kind of NVidia card do you have. Do you know the model? Because from what is sounds your card is older and might be unable to support this feature.

As you say StichjAcket I figured it was my built in graphics that would not accept compiz so I obtained a dedicated Geforce XFX card and had to do a clean install as I did'nt know how to reboot my 64bit install.
Strangely  though although I have not installed compiz when I do a locate-compiz more in terminal I get this.

> jack@jack-desktop:~$ locate compiz |more
/home/jack/.gconf/apps/compiz
/home/jack/.gconf/apps/compiz/%gconf.xml
/home/jack/.gconf/apps/compiz/general
/home/jack/.gconf/apps/compiz/general/%gconf.xml
/home/jack/.gconf/apps/compiz/general/allscreens
/home/jack/.gconf/apps/compiz/general/allscreens/%gconf.xml
/home/jack/.gconf/apps/compiz/general/allscreens/options
/home/jack/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
/home/jack/.config/compiz
/home/jack/.config/compiz/compizconfig
/home/jack/.config/compiz/compizconfig/config
/usr/share/gnome-control-center/keybindings/50-compiz-desktop-key.xml
/usr/share/gnome-control-center/keybindings/50-compiz-key.xml
/usr/share/man/man1/compiz.real.1.gz
/usr/share/man/man1/compiz.1.gz
/usr/share/compiz
/usr/share/compiz/decoration.xml
/usr/share/compiz/clone.xml
/usr/share/compiz/cubecaps.xml
/usr/share/compiz/scale.xml
/usr/share/compiz/widget.xml
/usr/share/compiz/compizcap.png
/usr/share/compiz/screenshot.xml
--More--



what now:confused:

---

### Post by tradesman on 2007-11-28
Also get the following after typing compiz

> jack@jack-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


---

### Post by tradesman on 2007-11-29
Ok I just followed the guide again, now when I start the fusion icon the screen goes white & I have to reboot.

these are the answers I got to three posts in terminal


 > jack@jack-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


jack@jack-desktop:~$ glxinfo |grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: GeForce 8500 GT/PCI/SSE2
jack@jack-desktop:~$ 



jack@jack-desktop:~$ cat ~/.config/compiz/compizconfig/Default.ini
[core]
as_active_plugins = decoration;vpswitch;extrawm;animation;place;video;svg;snap;move;png;regex;workarounds;fade;neg;text;imgjpeg;dbus;cube;resize;scale;switcher;expo;rotate;ezoom;resizeinfo

jack@jack-desktop:~$ 



I must be getting closer but a nudge in the right direction would  be appreciated.

---

### Post by StitchJAcket on 2007-11-29
> **tradesman said:**
> Ok I just followed the guide again, now when I start the fusion icon the screen goes white & I have to reboot.

these are the answers I got to three posts in terminal


 

I must be getting closer but a nudge in the right direction would  be appreciated.

You should be done now
From what your output says compiz is now installed
So here's what you do
Make sure ur nvidia driver is enabled
If it is which it looks as so
Then go to System>Preferences>Advanced Desktop Effects Setting
And that's compiz
Now if it's not enabled you must enable it
Go to System>Preferences>Appearence
Click on the visual effects tab
Then click custom
And your done =)
Also just in case anybody gets this error i got today after updating
Your compiz settings might not be working so here's what you do
Disable your nvidia driver in restricted drivers
Then it will uninstall the driver for ur card
After that reboot then enable them it will get the new drivers
And then reboot again and it should all work
Don't know if any of you will encounter this issue but i did so fair warning lol

---

### Post by tradesman on 2007-11-30
Thank's for all your help Stitch m8 the problem was my NVIDIA driver not installed, I cheated and used ENVY to install it now all's well:lolflag:

Just one question how do I restart the xserver?

---

### Post by tradesman on 2007-11-30
Ok now just did                               > sudo /etc/init.d/gdm restart                                                                                                                                 and all changed, now to find out how to stop the damn screen rotation every time I press the return key:)

---

### Post by z-itou16 on 2007-11-30
thanks dentaku. amazing how-to guide

---

### Post by Brando569 on 2007-12-01
thanks for the guide, its great. compiz works fine for me until i reboot and then it doesnt work anymore. I have an Nvidia GeForce 7600GT and a 8600 GTS (not in use at the same time) and it doesnt work either of them after the initial reboot.

i have the restricted drivers installed and i installed xserver-xgl but it still says that it cant find glx when i type compiz --replace. (i cant remember what the actual error says since im not on my pc) sometimes when i try to switch from kwin to compiz it will just give me a white screen and other times it will display the windows but there arent any frames around them and there arent any effects.

i had this problem before but i thought it was because i tried to install KDE4 and then removed it, i just fixed it by reinstalling kubuntu.

---

### Post by deguz on 2007-12-02
Hi!

When i type:

fusion-icon &

the windows' top (the title bar) go away, and i can't controll them. Much of them don't even work. I have intel video card, i don't know what to do. Please help me!

---

### Post by StitchJAcket on 2007-12-03
> **tradesman said:**
> Ok now just did                                                                                                                                                                and all changed, now to find out how to stop the damn screen rotation every time I press the return key:)

To change this all you do is go to System>Preferences>Advanced Desktop Effects Settings Then click the desktop cube then click the actions tab, then change your key bindings =)
Hope that helps

---

### Post by dentaku65 on 2007-12-03
> **deguz said:**
> Hi!

When i type:

fusion-icon &

the windows' top (the title bar) go away, and i can't controll them. Much of them don't even work. I have intel video card, i don't know what to do. Please help me!

Try to type only:
```
fusion-icon
```
and post the output that appears on the console.

---

### Post by deguz on 2007-12-03
The situation is the same. Message:

* switching to compiz.real ...
* Starting: compiz.real
compiz.real (core) - Error: Another window manager is already running on screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by dentaku65 on 2007-12-03
> **deguz said:**
> The situation is the same. Message:

* switching to compiz.real ...
* Starting: compiz.real
compiz.real (core) - Error: Another window manager is already running on screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0

Check this infos for your Intel card:
[http://wiki.opencompositing.org/Intel_with_AiGLX]("http://wiki.opencompositing.org/Intel_with_AiGLX")

---

### Post by deguz on 2007-12-03
Now i tried it, and when i try to load compiz, the problem is the same, and i get this message:

Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

---

### Post by dentaku65 on 2007-12-03
> **deguz said:**
> Now i tried it, and when i try to load compiz, the problem is the same, and i get this message:

Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

What is the output of:

```
lspci -v |grep VGA
```

---

### Post by deguz on 2007-12-03
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])

---

### Post by dentaku65 on 2007-12-03
> **deguz said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA])

See this thread:
[http://ubuntuforums.org/showthread.php?t=619099]("http://ubuntuforums.org/showthread.php?t=619099")

---

### Post by deguz on 2007-12-03
I tried it, but after that, X server didn't even start :(

---

### Post by deguz on 2007-12-04
please help me, i really need to use compiz

---

### Post by zauberberg on 2007-12-04
well, I've followed all steps and I've obtain this problem in last step (fusion-icon &):
...
* KDE is running
* fglrx found, exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Starting: compiz.real
compiz.real (core) - Fatal: No composite extension
...

someone can help me? 
Thanks

Juan

---

### Post by StitchJAcket on 2007-12-04
> **zauberberg said:**
> well, I've followed all steps and I've obtain this problem in last step (fusion-icon &):
...
* KDE is running
* fglrx found, exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Starting: compiz.real
compiz.real (core) - Fatal: No composite extension
...

someone can help me? 
Thanks

Juan
Are you using an ATI graphics card?

---

### Post by zauberberg on 2007-12-04
yes: "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
I can resolve the problem change ----> Option          "Composite"     "1" before "0".

But now the problem is:# xorg.conf (xorg X Window System server configuration file)
[HTML]#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Monitor		"Monitor genérico"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection[/HTML]

* fglrx found, exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Starting: compiz.real
compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display: 0.0

And after that kde falls. 

I post my xorg.conf maybe the problem is here:

---

### Post by zauberberg on 2007-12-04
sorry the xorg.conf text should go at the end

---

### Post by deguz on 2007-12-04
try to add this to xorg.conf:

Section "Extensions"
        Option          "Composite" "Enable"
EndSection

---

### Post by StitchJAcket on 2007-12-04
> **deguz said:**
> try to add this to xorg.conf:

Section "Extensions"
        Option          "Composite" "Enable"
EndSection
Yeah i think that should work for his issue

---

### Post by craigsall on 2007-12-13
I just installed a fresh copy kubuntu gutsy x86_64 and used this guide to install compiz on my laptop. The installation went well, except for when it came to make and make install of the file i was only able to compile it by issuing the command:

sudo make install

Anyways, the installation went fine and the guide was great. 3D desktop was working and then i rebooted a few times and received this error:

Starting emerald
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: no manageable screens found on display :1.0exec: 378: /usr/bin/metacity: not found

I searched google for this error and only returned me to this forum with no answer as of yet.

I am using the ATI restricted from restricted driver manager as well as the package xserver-xgl installed. Please, help me solve this issue as well others with the same problem. Thanks in advance.

---

### Post by tradesman on 2007-12-13
Try ENVY to install ATI driver

> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by msubzwari on 2007-12-13
Very accurate guide.  Followed it to the letter after changing from Ubuntu to Kubuntu Gusty and everything worked like clock work.

One trivial update....the config file seems to be *~/.config/compiz/compizconfig/config* instead of the Default.ini as mentioned in the guide (used in last step to backup config).

---

### Post by craigsall on 2007-12-13
Tradesman, I am going to do another fresh install of gutsy x86_64 and use the ubuntu .deb. Do also still need use xserver-xgl as well? Thanks in advance for help guys.

---

### Post by tradesman on 2007-12-13
> **craigsall said:**
> Tradesman, I am going to do another fresh install of gutsy x86_64 and use the ubuntu .deb. Do also still need use xserver-xgl as well? Thanks in advance for help guys.

Just let Envy sort it for you.

---

### Post by craigsall on 2007-12-13
Alright, fresh install of kubuntu gutsy x86_64. Then I used the ubuntu .deb envy script. Then proceeded to install compiz. When trying to run compiz --replace I get this error:

craig@LAPTOP:~$ compiz --replace
Checking for Xgl: not present.
Blacklisted PCIID '1002:5955' found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting


Any ideas? Thanks again in advance!

---

### Post by tradesman on 2007-12-13
@ craigsall when I type compiz --replace in terminal i get this

> -desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0421 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


as you can see xgl not present here also but compiz is working, your problem is not xgl you need someone more experienced to tell you what it is.
Have you downloaded and ran Envy?

---

### Post by craigsall on 2007-12-13
Yes, I have ran the envy script. I now have 3d Desktop working. I had to use the restricted driver managerand install xserver-xgl. I'm not sure why it did not work out of the box with the envy script. I beleive it did not set up my xorg.conf correctly. And without the package xserver-xgl 3d would not work. So, im not sure I actually need the envy script, but we'll see if my previous symptoms of 3d going away after a few reboots. i will keep posted. If you have any further ideas/ suggestions shoot.

---

### Post by craigsall on 2007-12-13
Okay so as I predicted yet again after rebooting a few times, compiz refuses to run.. I am back to my first error messages from compiz --replace:

/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
 /usr/bin/compiz.real (core) - Fatal: no manageable screens found on display :1.0exec: 378: /usr/bin/metacity: not found

If anyone could point me to a guide to install my ati card that would be appreciated. I don't know what is posing the issue. Any help is appreciated. Thank you.

---

### Post by craigsall on 2007-12-13
Here is my card: sorry left it out my last post.

VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

---

### Post by craigsall on 2007-12-13
Well, okay guys. I just cannot live without having my 3D Desktop. This issue must be something with KDE only. I just installed Ubuntu Gutsy x86_64 edition and have 3D desktop working fine. All I did was enable ATI Accelerated Graphics Driver from the restricted-manager and install xserver-xgl. It automatically configured my /etc/X11/xorg.conf  . Thank you for all your help, maybe I will try with KDE and compiz at a later time, until then I will suffice with the tad bitter slower gnome desktop.

---

### Post by jairo.serrano on 2007-12-16
Works perfectly with Nvidia 7600M GT. :guitar:

---

### Post by fmartinez on 2007-12-16
Is there a similar post for fusion-icon for gnome desktop env????

---

### Post by StitchJAcket on 2007-12-16
Ubuntu is run on a gnome core so it should work the same way.

---

### Post by Smatt454 on 2007-12-23
i cant seem to get my compiz to work....it comes up by my clock when I do 
```
fusion-icon & 
```

and i get this message back

```
Using the Qt4 Interface
* Searching for installed applications...
/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/kde-window-decorator
/usr/bin/emerald
/usr/bin/kwin
* KDE is running
* nvidia found, exporting: __GL_YIELD="NOTHING"
* Active WM is already running
* switching to compiz.real ...
* Starting: compiz.real
compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0
* switching to kwin ...
* Starting: kwin
Info: No sexy-python package found, don't worry it's optional.
```

i've never worked with compiz before, so im a little rusty. and yes my 3d acceleration works. i just tried glxgears and the gears came up

:EDIT:
I should note that configuring my xorg has given me problems. When I enable my drivers....the biggest resolution I can choose from is a 800x600. I tried fixing this and doing 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this fixes the resolution problem but disables my driver. after that i tried manually enabling my driver through my xorg file...which didnt fix the problem. I then tired using the GUI "Restricted Drivers" option in my system settings, and that messed up my resolution, but fixed my driver problem.

I dont know if this problem has anything to do with compiz not working..but i thought since it had to  do with xorg....it might be. here is my current xorg file.
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV10DDR [GeForce 256 DDR]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"DELL D1028L"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV10DDR [GeForce 256 DDR]"
	Monitor		"DELL D1028L"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"720x350"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

:EDIT (2nd edit):
I also forgot to explain that I can get into the compiz settings and emerald settings, but none of the compiz effects work, I may be configuring the settings wrong...i've never worked with compiz or beryl before.
.

thanks in advanced:guitar:

---

### Post by jesusrop on 2007-12-23
Incredible. Works perfect!

---

### Post by Smatt454 on 2007-12-25
does anyone think they can help me with my problem?

---

### Post by win32blows on 2008-01-13
All I had to do to get it working again was

```
rm ~/.kde/share/config/kdesktoprc
```

You may want to back it up first

---

### Post by eyal p on 2008-02-28
Finally a guide that does it!
Thank you for the excellent guide. I followed it to the letter and at last the compiz works butifully.
Posted a link to it in my local ubuntu forum.
Eyal

---

### Post by macogw on 2008-02-28
> **dentaku65 said:**
> Thx Jaya for the info, I've just some doubts to add a different repo than the official ones...is this working with Kubuntu Gutsy (kde) as well?

I promise you, it's safe.  I pulled it from SVN and packaged it myself.  And yes, it works on KDE.  That's my Personal Package Archive that was linked.

---

### Post by macogw on 2008-02-28
> **fmartinez said:**
> Is there a similar post for fusion-icon for gnome desktop env????

It's just Python, if I recall correctly, in which case the package is fine to use for other versions of Ubuntu, Debian, PCLOS, Mepis...anything that uses deb.  For Red Hat based distros, convert it with Alien.

---

### Post by reeseslover531 on 2008-03-12
> **Brando569 said:**
> thanks for the guide, its great. compiz works fine for me until i reboot and then it doesnt work anymore. I have an Nvidia GeForce 7600GT and a 8600 GTS (not in use at the same time) and it doesnt work either of them after the initial reboot.

i have the restricted drivers installed and i installed xserver-xgl but it still says that it cant find glx when i type compiz --replace. (i cant remember what the actual error says since im not on my pc) sometimes when i try to switch from kwin to compiz it will just give me a white screen and other times it will display the windows but there arent any frames around them and there arent any effects.

i had this problem before but i thought it was because i tried to install KDE4 and then removed it, i just fixed it by reinstalling kubuntu.

I have the same problem
I followed your directions and everything worked, restarted the computer and when I start fusion-icon i lose all my title bars and it says ```
compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0

```
I have an 8800GT with the latest drivers that I installed from the nvidia download.

---

### Post by paulyballs on 2008-04-16
Hi guys - I'm having a similar issue as others with ATI cards.  When I enable compiz I lose the title bars, borders, and can't move my windows around.  Here is the output from fusion-icon:

paul@paul-desktop:~/Desktop/fusion-icon$ fusion-icon
* Using the Qt4 Interface
* Searching for installed applications...
/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/kde-window-decorator
/usr/bin/emerald
/usr/bin/kwin
* KDE is running
* No GLX_EXT_texture_from_pixmap present with direct rendering context
... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* fglrx found, exporting: LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa
* Active WM is already running

Any ideas?  I'm using the ATI restricted driver.

Thanks!

---

### Post by theZoid on 2008-05-15
Does all this work with Kubuntu Hardy final?  That's what I'm using now.  Thanks !!

---

