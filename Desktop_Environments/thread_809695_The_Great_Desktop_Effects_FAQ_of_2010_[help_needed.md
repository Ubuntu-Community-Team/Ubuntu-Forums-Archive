---
title: "The Great Desktop Effects FAQ of 2010 [help needed]"
date: 2008-05-27
forum: Desktop Environments
---

### Post by jpeddicord on 2008-05-27
[SIZE="3"]August 2011: This thread badly needs to be updated/pruned. If you (yes, you!) would like to take over maintenance of this thread, please [send me a PM]("http://ubuntuforums.org/private.php?do=newpm&u=90021"). Members with active, helpful posting history preferred. Otherwise this thread will be unstickied at the end of the month.[/SIZE]

**This is *not* a topic for asking questions.** (Unless you can of course provide an answer along with it.)

[SIZE="5"]**[COLOR="DarkRed"]The FAQ[/COLOR]**[/SIZE]

[SIZE="4"]Compiz[/SIZE]
**What is Compiz Fusion?**
[INDENT]Compiz is what is known as a "compositing manager." It enables your desktop to run faster than with traditional window managers, and allows you to be more productive. Compiz controls the effects you see on your desktop: Shadows, animations, "the cube," and a whole bundle of other fun effects.[/INDENT]

**How do I know if Compiz is enabled (How can I disable Compiz?)**
[INDENT]On Ubuntu 7.10 and up:
Open **System > Preferences > Appearance**. Click on the **Visual Effects** tab. If Compiz and desktop effects are enabled, **Normal**, **Extra**, or **Custom** will be selected. If Compiz is disabled, **None** will be selected. To switch modes, simply click on another selection. Changes take effect immediately.[/INDENT]

**Why is my card "Blacklisted?")**
[INDENT][http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)[/INDENT]

**What is a quicker way to enable/disable Compiz?** - Gourgi
[INDENT]Install the package [fusion-icon]("apt:fusion-icon") and reload your session for a notification icon to switch between Compiz and the standard window manager.[/INDENT]

**How can I install Beryl?** - FuturePilot
[INDENT]Beryl was merged back into the Compiz project to create what is now know as Compiz Fusion. Beryl is no longer supported or developed meaning that if there is a bug, no one will fix it. Therefore it is recommended that you use Compiz Fusion which comes installed by default in Ubuntu.[/INDENT]

**How can I get Custom to appear in the Visual Effects dialog?**
[INDENT]**Custom** only appears if the package [simple-ccsm]("apt:simple-ccsm?section=universe") is installed. When you install simple-ccsm, a new selection will be available in Visual Effects, which allows you to customize what effects are active on your desktop. You can also customize the effects from **System > Preferences > Simple CompizConfig Settings Manager**.[/INDENT]

**Simple CompizConfig Settings Manager doesn't provide enough options or effects. Are there more?**
[INDENT]Simple CompizConfig is just that, simple. If you are looking for more options, install the package [compizconfig-settings-manager]("apt:compizconfig-settings-manager?section=universe"). Be sure to keep simple-ccsm installed so that the Custom option remains available in Visual Effects.

You can also access it from **System > Preferences > Advanced Desktop Effects Settings** or by opening a terminal (or Alt+F2) and typing **ccsm**.[/INDENT]

**I can't find some of the plugins mentioned in this FAQ. Where are they?**
[INDENT]As of recent Ubuntu releases, these are now available in [compiz-fusion-plugins-extra]("apt:compiz-fusion-plugins-extra"), which is not installed by default.[/INDENT]

**Desktop Effects could not be enabled?**
[INDENT]See the following thread to find out why:[Compiz-Check ]("http://ubuntuforums.org/showthread.php?t=799070")
[/INDENT]

**Is compiz for Ubuntu and Kubuntu only?** - aimpau
[INDENT]Nope! Xubuntu has it too!
[http://ubuntuforums.org/showthread.php?t=934934](http://ubuntuforums.org/showthread.php?t=934934)

Just to add, **if you want to use emerald for window decorations**, don't forget to type in alt+f2:
```
emerald --replace
```

The gtk-window-decorator cannot be controlled by Applications > Settings > Settings Manager > Window Manager since it only control xfwm4. However, you can load .cgwdtheme files through the terminal. I recommended emerald since it is really cool.[/INDENT]

**Where did my window borders go?** - cc7gir
[INDENT]This is a common mistake caused by disabling some plugins in CompizConfig Settings Manager. To fix, open the manager (System > Preferences > CompizConfig Settings Manager) and find the "Window Decorations" plugin. Check the box and you're all set.[/INDENT]

**How can I get the "cube" effect?** - overdrank
[INDENT][(Image)]("http://ubuntuforums.org/attachment.php?attachmentid=71841&d=1211934590") First, install compizconfig-settings-manager. Then, in **System > Preferences > Advanced Desktop Effects Settings**, go to General Options, Desktop Size tab, and make sure **Horizontal Virtual Size** is set to 4. Go back to the main window, and enable the Desktop Cube and Rotate Cube plugins.
You can "spin" the cube by pressing Ctrl+Alt+Left and Ctrl+Alt+Right, or hold Ctrl+Alt and click and drag.[/INDENT]

**What is the "dodge" effect?**
[INDENT][http://ubuntuforums.org/showthread.php?t=899195](http://ubuntuforums.org/showthread.php?t=899195)[/INDENT]

**How do I beam up my windows to space?** - aimpau
[INDENT]Capt. Picard: Prepare to beam up.
Data: Beaming up in 6 nanoseconds.

Press alt+f2 and type in
```
ccsm
```
(Alternatively, go to System > Preferences > Advanced Desktop Effects Settings in GNOME)

Go to Animations and on the close animation tab, click on the top animation (by default, that would be Glide 2) and press edit. Look for Beam, click ok and close. That's it! Enjoy[/INDENT]

**What are some other keyboard shortcuts?** - wolfen69
[INDENT][http://ubuntuforums.org/showpost.php?p=5180134&postcount=5](http://ubuntuforums.org/showpost.php?p=5180134&postcount=5)[/INDENT]

**How do I install a Compiz plugin from git?** - AstalaVista
[INDENT][7.10 Gutsy]("http://forum.compiz-fusion.org/showthread.php?t=5303")
[8.04 Hardy]("http://forum.compiz-fusion.org/showthread.php?t=8214")[/INDENT]

**What is Emerald?** - _DD_
[INDENT]Emerald is a replacement window decorator which supports many more effects than gtk-window-decorator, GNOME's built-in window decorator.[/INDENT]

**How do I install and enable Emerald?**
[INDENT]Install the [emerald]("apt:emerald?section=universe") package from Synaptic.
The package [emerald-themes]("apt:emerald-themes?section=universe") provides some themes to use in 8.04, but it is currently missing from the repositories. Themes must be installed manually for the time being.

To enable Emerald on login, go to System > Preferences > Sessions. Click the Add button, and type in **Emerald** for Name and **emerald --replace** for Command. Click OK and close the Sessions window. The next time you sign in, Emerald will be running.[/INDENT]

[SIZE="4"]Themes[/SIZE]
**Where can I download additional themes for my desktop?**
[INDENT]Themes for Ubuntu (GNOME) can be found at:
[LIST]
[*][GNOME Art]("http://art.gnome.org")
[*][GNOME-Look]("http://gnome-look.org")
[*][deviantART]("http://browse.deviantart.com/customization/skins/linuxutil/gnome/?order=9&alltime=yes")
[/LIST]
Themes for Kubuntu can be found at:
[LIST]
[*][KDE-Look]("http://kde-look.org")
[*][deviantART]("http://browse.deviantart.com/customization/skins/linuxutil/kde/?order=9&alltime=yes")
[/LIST]
[/INDENT]

**How can I install a custom cursor theme?** - Armed Nuke
[INDENT][http://ubuntuforums.org/showthread.php?t=820245](http://ubuntuforums.org/showthread.php?t=820245)[/INDENT]

[SIZE="4"]Other[/SIZE]
**What is the Mac-like dock I see in some screenshots?**
[INDENT]The dock is known as Avant Window Navigator. Instructions on how to install and configure it are available here:
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

Another dock available is Cairo-dock: [http://ubuntuforums.org/showthread.php?t=878603](http://ubuntuforums.org/showthread.php?t=878603)[/INDENT]

**How do I get desktop widgets?** - smartboyathome
[INDENT]There are several programs which allow you to put widgets on the desktop. The most popular is a program called Screenlets. To install it, open up **System > Preferences > Synaptic Package Manager**, and search for "screenlets". Install the "[screenlets]("apt:screenlets?section=universe")" package that comes up by double clicking on it and clicking apply on the top bar. Once it is installed, go to **Applications > Accessories > Screenlets** (or **System > Preferences > Screenlets**) and enable the screenlets that you want.[/INDENT]

**I really love these Screenlets, are there more?** - Gourgi
[INDENT]Of course! You can download screenlets either from the [3rd party Screenlets Repository]("http://screenlets.org/index.php/Category:UserScreenlets") or from the [Gnome-look Screenlets section]("http://gnome-look.org/?xcontentmode=6700").[/INDENT]

**My Screenlets package is outdated, how can I get an up to date package?** - Gourgi
[INDENT]Add these to your sources in System > Administration > Software Sources; Third Party Software; Add.
Gutsy:```
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe 
```
Hardy```
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe 
```
See [http://screenlets.org/index.php/Download](http://screenlets.org/index.php/Download) for additional sources.[/INDENT]

**How can I set up different wallpapers for each virtual desktop, with Conky, and get rid of GNOME panels?**
[INDENT][http://ubuntuforums.org/showpost.php?p=5691394&postcount=39](http://ubuntuforums.org/showpost.php?p=5691394&postcount=39)[/INDENT]


[SIZE="5"]**[COLOR="DarkRed"]Useful Links[/COLOR]**[/SIZE]
[LIST]
[*][http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)
[*][http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)
[/LIST]

[SIZE="5"]**[COLOR="DarkRed"]Contributing[/COLOR]**[/SIZE]
Attention forum members:

Want to have a chance to contribute to "The Great FAQ of Desktop Effects?" Then join me in the planning of one of the biggest events to hit this forum (well, stickies anyway). We're going to build a nice big topic to put right at the top of the forum page to hang out with the "Blacklisted?" topic. Anyone and everyone is welcome to contribute.

Interested? Great! Here's what you need to do:
Find a question about Compiz, Desktop Effects, Theming, or anything related that is fairly frequently asked, even if it may seem obvious. It can even be one of the questions above that is marked "to be written." Post your question as a reply to this thread in a format similar to:

> **Why doesn't Compiz start?**
Compiz usually won't start for the following reasons...
blah blah blah blah
or
> **Why doesn't Compiz start?**
[http://ubuntuforums.org/showtopic.php?t=12345](http://ubuntuforums.org/showtopic.php?t=12345)

Be sure to either include a link to the topic with the answer or provide the answer directly. The questions and answers will be edited into the main post (this one). I'll probably edit your questions and answers to fit them in with the rest of the questions, but the idea will remain the same.

---

### Post by overdrank on 2008-05-27
**_How can I get the cube_**

You can use this command in the terminal to install the CCSM
```
sudo apt-get install compizconfig-settings-manager
```
Or use synaptic package manager located under system, administration.
Then you can use CCSM, it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also ensure that the desktop cube and rotate cube are also checked.

---

### Post by smartboyathome on 2008-05-28
**How do I get desktop widgets?**
There are several programs which allow you to put widgets on the desktop. The most popular is a program called Screenlets. To install it, open up System > Preferences > Synaptic Package Manager, and search for "screenlets". Install the "screenlets" package that comes up my double clicking on it and clicking apply on the top bar. Once it is installed, go to Applications > Accessories > Screenlets and enable the screenlets that you want.

(P.S. Do you want the people to use the packages in the repo? The screenlets package there is quite old, and I would recommend the package from getdeb.net, which I use now.)

---

### Post by jpeddicord on 2008-05-28
> **smartboyathome said:**
> **How do I get desktop widgets?**
There are several programs which allow you to put widgets on the desktop. The most popular is a program called Screenlets. To install it, open up System > Preferences > Synaptic Package Manager, and search for "screenlets". Install the "screenlets" package that comes up my double clicking on it and clicking apply on the top bar. Once it is installed, go to Applications > Accessories > Screenlets and enable the screenlets that you want.Added. Thanks!

> **smartboyathome said:**
> (P.S. Do you want the people to use the packages in the repo? The screenlets package there is quite old, and I would recommend the package from getdeb.net, which I use now.)Yeah, we should probably stick to the repositories. The repo-available packages are much easier to install than telling a user to download a .deb that needs updated upon new releases. Packages in the repository can also be supported better in case of a problem.

---

### Post by FuturePilot on 2008-05-28
**How can I install Beryl?**
Beryl was merged back into the Compiz project to create what is now know as Compiz Fusion. Beryl is no longer supported or developed meaning that if there is a bug, no one will fix it. Therefore it is recommended that you use Compiz Fusion which comes installed by default in Ubuntu.


(P.S. I think Beryl should be removed from the description of this forum for the above reason ;))

---

### Post by chewearn on 2008-05-29
**How do I install <insert name> compiz plugin (from git)?**

[Gutsy]("http://forum.compiz-fusion.org/showthread.php?t=5303")
[Hardy]("http://forum.compiz-fusion.org/showthread.php?t=8214")

---

### Post by _DD_ on 2008-05-29
Need something do do with Emerald...

**What is Emerald?**
Emerald is a replacement window decorator which supports many more effects than Metacity, Gnome's built-in window manager.

**How do I install and enable Emerald?**
In the terminal type...
```
sudo apt-get install emerald
```
...blah blah

Also something about...
```
emerald --replace
```

---

### Post by Vadi on 2008-05-29
What's an easy to follow guide to setting up Compiz Fusion in 8.04?

[http://forlong.blogage.de/article/2008/4/26/-How-to-set-up-Compiz-Fusion-074-included-in-Ubuntu-804-Hardy-Heron#](http://forlong.blogage.de/article/2008/4/26/-How-to-set-up-Compiz-Fusion-074-included-in-Ubuntu-804-Hardy-Heron#)

---

### Post by jpeddicord on 2008-05-29
> **Vadi said:**
> What's an easy to follow guide to setting up Compiz Fusion in 8.04?

[http://forlong.blogage.de/article/2008/4/26/-How-to-set-up-Compiz-Fusion-074-included-in-Ubuntu-804-Hardy-Heron#](http://forlong.blogage.de/article/2008/4/26/-How-to-set-up-Compiz-Fusion-074-included-in-Ubuntu-804-Hardy-Heron#)

Not necessairily a FAQ, but a good guide nonetheless. I've added it to a new Links section.

---

### Post by knudsenjoe on 2008-06-06
Thought I'd post this bit of a reminder for some of us, I mean all the noobs....

If you have Ubuntu Tweak controlling some aspects of your desktop it may or may not interfere with those cool Compiz extras. Obviously you would shut off the UT stuff, get your Compiz right, then if you must maybe then you could go back and tweak with UT.

I went ahead and posted this over there at the Compiz Forums as well.

yeah, i'm guilty lol

---

### Post by Gourgi on 2008-06-06
Screenlets code is under heavy development almost every day and maybe the the version available in repositories is buggy.
there is PPA screenlets repository for Gutsy and Hardy often updated.

[COLOR="Black"]**How can i get an up to date package for screenlets **?[/COLOR]
Add to your sources.list
[COLOR="Green"]In gutsy[/COLOR] : ```
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe 
```
[COLOR="Green"]In Hardy [/COLOR] : ```
deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe 
```

[COLOR="Black"]**I really loved those screenlets, are there more ?**[/COLOR]
Of course ! 
You can download screenlets either from the [COLOR="Blue"]3rd party Screenlets Repository[/COLOR] here 
[http://screenlets.org/index.php/Category:UserScreenlets](http://screenlets.org/index.php/Category:UserScreenlets)
or from [COLOR="Blue"]Gnome-look Screenlets section[/COLOR] here
 [http://gnome-look.org/?xcontentmode=6700](http://gnome-look.org/?xcontentmode=6700)


- - - - - 
an easier method to switch through compiz <-> metacity and enabling emerald is using fusion-icon (included in hardy's repos)
```
sudo apt-get install fusion-icon
```

---

### Post by Armed Nuke on 2008-06-06
editing cursor themes:

[http://ubuntuforums.org/showthread.php?t=820245](http://ubuntuforums.org/showthread.php?t=820245)

---

### Post by Sealbhach on 2008-06-08
When I spin the cube around, it's just gray in the background. How do I change that?

Also, the top and the bottom of the cube are a plain yellow colour, anything I can do about those?


.

---

### Post by overdrank on 2008-06-08
> **Sealbhach said:**
> When I spin the cube around, it's just gray in the background. How do I change that?

Also, the top and the bottom of the cube are a plain yellow colour, anything I can do about those?


.

HI and the first is the skydome, located in the advance desktop effects settings under system, preference. Look for  desktop cube, appearance tab.There you can add images for the skydome.
The second, is the cube caps, appearance tab and there you can add images.

---

### Post by overdrank on 2008-06-13
HI and on behalf of wolfen69, found here.
[http://ubuntuforums.org/showthread.php?t=828222](http://ubuntuforums.org/showthread.php?t=828222)

here is a list of some of the things you can do

Desktop Effects1 Keyboard Shortcuts
Rotate Cube Mousewheel on Desktop
Switcher2 Alt + Tab
Shift Switcher3 Super + Tab (2 modes: flip and cover)
Ring Switcher Super + Tab - overrides Shift Switcher
Expo Super + E (toggle)
Film Effect Ctrl + Alt + Down Arrow4
Rotate Cube Manually Ctrl + Alt + Left Mouse Button
Scale Windows Alt + Shift + Up Arrow
Show/Clear Desktop Ctrl + Alt + D (toggle)
Snapping Windows Move a window across workspaces5
Screenshot Super + Left Mouse Button
Zoom In/Out Super + Mousewheel
Transparent Window Alt + Mousewheel
Resize Window Alt + F8
Move Window Alt + F7
Add Helper Super + P
Widget Layer F9 (toggle)
Water Effects Shift + F9 (toggle)
Fire Effects: On Super + Shift + Left Mouse Button
Fire Effects: Clear Super + Shift + C
Annotate: Draw Super + Left Mouse Button
Annotate: Start Super + 1
Annotate: End Super + 3
Group: Select Window(s) Super + S
Group: Group Windows Super + T
Group: Ungroup Windows Super + U
Group: Flip Windows Super + Right or Left Arrow

---

### Post by Fenris_rising on 2008-06-14
for anyone who installs the latest compiz. i recently had a problem with the
open close minimise effects being non existant (yes the animations were selected in ccsm). now i have just stumbled on this thread and on the off chance i have installed 'simple ccsm'. selected 'custom' and went into preferences. once there i selected my favorite animation (explode) well the good news is that they work now. i dont know if its a bug in the compiz git or something with my PC but this may help anyone who has the same problem.
so under system preferences i have both, CCSM and Simple CCSM.

---

### Post by LeoSolaris on 2008-06-14
Just a note, you do not have to have simple CCSM installed to enable custom effects. You can simply install the advanced CCSM and it will allow you to turn on the custom feature.

Not a big point, but I am in favor of keeping the number of programs on my machine down to save space on my hard drive.

Leo

---

### Post by Rocket2DMn on 2008-06-15
Compiz for older ATI cards requiring the open source "ati"/"radeon" drivers (which has been blacklisted) - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by jpeddicord on 2008-06-16
Sorry for the update delay. I've been on vacation without internet access for a week. :)

> **jacobmp92 said:**
> Yeah, we should probably stick to the repositories. The repo-available packages are much easier to install than telling a user to download a .deb that needs updated upon new releases. Packages in the repository can also be supported better in case of a problem.

Contradicting myself:

A 3rd party repository may be added to the FAQ as long as it is the official third party repository for that piece of software and is actively maintained.

---

### Post by overlord.gaurav on 2008-06-23
**Q: How to uninstall Compiz?**
**A:** Open a terminal and type:
```
sudo apt-get purge compiz-core && sudo apt-get autoremove
```
and press enter.

Alternatively, you can uninstall it using the Synaptic Package Manager in System -> Administration through the GUI mode.

**Q: How to theme my desktop like Windows XP/Windows Vista/OSX?**
**A:** It is very much possible to theme Ubuntu desktop like Windows XP/Windows Vista/ OSX. Follow the guide mentioned below for each of the customization:
[B]
Windows XP:[/B] [http://ubuntuforums.org/showthread.php?t=82114](http://ubuntuforums.org/showthread.php?t=82114)

**Windows Vista:** [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)  [Scroll down on the page to find the guide for Vista customization]

**Mac OSX:** [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)       [Scroll down on the page to find the guide for OSX customization]

**Q: How to install Aavnt-Window-Navigator? [The dock similar to the one in OSX]**
**A:** Follow the guide on [this page]("http://ubuntuforums.org/showthread.php?t=762363").[[http://ubuntuforums.org/showthread.php?t=762363]](http://ubuntuforums.org/showthread.php?t=762363])

---

### Post by dot2kode on 2008-06-24
Awesome guide! Thanks for putting this together! =D>

---

### Post by amisdar on 2008-06-27
Really useful tips. I always hang around at [http://www.gnome-look.org/](http://www.gnome-look.org/) and now I understand whats the meaning of Metacity, Compiz and Beryl!

Thanks for this awesome info :-)

---

### Post by sayakb on 2008-07-07
You may also have a sphere instead of a cube.
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=76669&thumb=1&d=1215380104[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=76669&d=1215380104")
Goto System->Administration->Software Sources
Click **Third party software** tab and add this: deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
Then close the window and press **Reload** when prompted to. You shall be notified by update manager that there is an update for compiz. Install the update and reboot your computer. 
Then goto Advanced desktop effects settings and you will have a **Cube reflection and deformation** and **3D Windows **plugin there.

---

### Post by billgoldberg on 2008-07-09
I recently wrote a guide to customizing Ubuntu.

Some might find it useful.

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

The following subjects are covered:

1. Setting a different wallpaper
2. Installing a new theme
3. Changing the panel size, transparency
4. Installing a new icon set
5. Setting up Compiz Fusion (and it’s effects, like the rotating cube)
6. Setting up transparent windows borders
7. Setting up true panel and menu transparency
8. Installing/changing system fonts
9. Installing/using new system sounds
10. Installing “widgets” and adding new ones
11. Making root applications use your theme/icons
12. Installing a dock
13. Installing a different login screen
14. Use a splash screen/install a new splash screen
15. Install a different grub theme
16. Install a new mouse theme

---

### Post by ba5e on 2008-07-13
ver nice post!

---

### Post by Exsecrabilus on 2008-07-20
> **jacobmp92 said:**
> **What is Emerald?** - _DD_
[INDENT]Emerald is a replacement window decorator which supports many more effects than Metacity, Gnome's built-in window manager.[/INDENT]

This section is wrong. Like you said, Emerald is a window decorator, not a window manager. Therefore, you should compare it to gtk-window-decorator, a window decorator, not Metacity, a window manager.

---

### Post by jpeddicord on 2008-07-20
> **Exsecrabilus said:**
> This section is wrong. Like you said, Emerald is a window decorator, not a window manager. Therefore, you should compare it to gtk-window-decorator, a window decorator, not Metacity, a window manager.

Didn't catch that when posted. Thanks.

---

### Post by Ingenue on 2008-08-01
Wow, very helpful thread. Thanks.

---

### Post by overdrank on 2008-08-03
How do I install cairo-dock
[http://ubuntuforums.org/showthread.php?t=878603](http://ubuntuforums.org/showthread.php?t=878603)

---

### Post by Mgiacchetti on 2008-08-12
howto install cairo dock

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Plus here's a little nugget of gold for all you who like eye candy...

attached you will find a zip file with 4 gradients.
unzip these to ~/Pictures/gradients   (you will need to create the folder 'gradients')

to use, right click cairo dock and go to cairo-dock > configure

in the first view find "activate autohide"    check this box

in the background tab, under callback zone:

set your size, (i used 500 X 15 )
in the filename, use whichever gradient corresponds to the placement of your dock

I set my transparency to 0.748  you can fiddle around to find what you like.
make sure the rotate image option is unchecked

click apply
click ok

---

### Post by markip on 2008-08-17
I gathered all the compiz-fusion shortcuts and i decided to put it here.It would be very usuful if it could become a sticky too. Here it is:

Points of Reference
the "Super" key is the key with the Microsoft Windows logo on keyboards that are so equipped. It usually is placed between Ctrl and Alt on the left side of the Space bar. 
When configuring Compiz or Compiz-Fusion plugins the mouse buttons are referred to as ButtonX according to the following table: 

Button1 .....Left Mouse Button
Button2.......enter Mouse Button (click-able scroll wheel in some cases)
Button3......Right Mouse Button
Button4........Scroll Wheel Up
Button5.......Scroll Wheel Down
If you have customized your mouse in '/etc/X11/xorg.conf' then these buttons will operate according to that map. 
Direction keys are a reference to their corresponding arrow keys: 

Up......The Up arrow key
Down......The Down arrow key
Left......The Left arrow key
Right......The Right arrow key

```
[COLOR="Red"]Most common keybindings
[/COLOR]


Rotate to Cube Face Left
<Ctrl><Alt>Left


Rotate to Cube Face Right
<Ctrl><Alt>Right



Rotate Cube with Mouse
<Ctrl><Alt>Button1


Unfold Cube
<Ctrl><Alt>Down

Next Window
<Ctrl><Alt>Tab


Previous Window
<Shift><Ctrl><Alt>Tab


Next Window (All Desktops)
<Alt>Tab


Previous Window (All Desktops)
<Shift><Alt>Tab


Show All Desktops (Expo)
<Super>E


Show All Windows (Scale)
<Alt><Shift>Up


Show Desktop
<Ctrl><Alt>D

Show Main Menu
<Alt>F1



Screenshot Desktop
PrtScn


Screenshot Window
<Alt>PrtScn


Screenshot Area
<Super>Button1

 
Move Window (Keyboard)
<Alt>F7


Move Window (Mouse)
<Alt>Button1


Decrease Opacity
<Alt>Button5



Increase Opacity
<Alt>Button4

[COLOR="Red"]
All keybindings[/COLOR]


Slow Animations
<Shift>F10



Raise Window
<Control>Button6


Lower Window
<Alt>Button6



Window Menu
<Alt>Button3



Show Desktop
<Control><Alt>D


Screenshot (Desktop)
Print



Screenshot (Window)
<Alt>Print



Close Window
<Alt>F4


Show Main Menu
<Alt>F1



Run Dialog
<Alt>F2



Unmaximize Window
<Alt>F5



Minimize Window
<Alt>F9


Maximize Window
<Alt>F10




Window Menu
<Alt>Space
General Options
Key Bindings


Toggle Window Shaded
<Control><Alt>S



Increase Opacity
<Alt>Button4


Decrease Opacity
<Alt>Button5

[COLOR="Red"]Effects
[/COLOR]
SUPER+SHIFT+DRAG LEFT MOUSE = draw fire 
SUPER+SHIFT+C = clear fire 
CTRL+ALT+DRAG LEFT MOUSE = rotate cube 
CTRL+ALT+LEFT ARROW = rotate cube 
CTRL+ALT+DOWN ARROW = flat desktop 
SHIFT+ALT+UP=initiate window picker
CTRL+ALT+DOWN=unfold cube
ALT+TAB=window switch
SUPER+TAB=flip switcher or ring switcher depending on which is enabled.
ALT+F7=initiate 'move windows'
SHIFT+F9=water effect
SHIFT+F10=slow animations
CTRL+ALT+D=show desktop

For Grouping and Tabbing: 
SUPER+S=Select Single Window
SUPER+T=Tab Group
SUPER+Left=Change Left Tab
SUPER+Right=Change Right Tab
SUPER+G=Group Windows
SUPER+U=Ungroup Windows
SUPER+R=Remove Group Window
SUPER+C=Close Group
SUPER+X=Ignore Group
hold the super button then select the windows you want to group and then hit super+g

CTRL+Middle Mouse Button - Resize Window
CTRL+Left Mouse Button - Move Window

SUPER+E - Initiate Expo Mode (if enabled)
```

CTRL+SHIFT+ALT+Left cursor or CTRL+SHIFT+ALT+Right cursor - Move window to next desktop (i think, if not it might just be CTRL+SHIFT+left or right)



[I]resourses: [http://ubuntuforums.org/showthread.php?t=494548](http://ubuntuforums.org/showthread.php?t=494548)
           [http://wiki.compiz-fusion.org/CommonKeyboardShortcuts](http://wiki.compiz-fusion.org/CommonKeyboardShortcuts)[/I]

---

### Post by Crafty Kisses on 2008-08-17
Nice writeup but I'm pretty sure Compiz already had something exactly/similar to this, but nonetheless nice one.

---

### Post by overdrank on 2008-08-17
If you do not mind I am going to move to the FAQ's located here
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
:)
Moved to the FAQ's

---

### Post by boballen55 on 2008-08-21
great post

---

### Post by austintmetal on 2008-08-23
This was helpful, got to set up the desktop cube with the help of this.

---

### Post by Warren North on 2008-08-24
I thought I mention that I like using all three desktops Gnome Kde and Xfce. I use compiz on gnome and kde. I like to keep xfce light and use it's faster features. It took along time to get here but I got bloated fun computer. More stuff works!

---

### Post by overdrank on 2008-08-24
How to enable the Dodge effect in CCSM
[http://ubuntuforums.org/showthread.php?t=899195](http://ubuntuforums.org/showthread.php?t=899195)
Thanks to sameerds

---

### Post by loomsen on 2008-08-29
Thanks for contributing everyone.

Guess it's time to give some back...

Here we go:

**How to set up different wallpapers for each virtual Desktop, still using conky, and gettin rid of gnome panels?**

First we gotta get rid of nautilus.

[COLOR="Red"]NOTE: You will lose your Desktop icons![/COLOR]

Which is actually a good news for me, I like it clean :) But you should consider for yourself whether you wanna live without it. If not, you basically should stop reading now, and activate the next tab in your favorite webbrowser.

Alright, lets go. 

First step is to enable and configure the wallpaper plugin in CCSM.
Open it up by hitting 

Alt + F2 (optional Super + Space if you have gnome do installed)
and type ccsm
navigate to utility, wallpaper. There, set up the wallpapers according to your needs.

[COLOR="#ff0000"]Note:[/COLOR] the order you specify here will be the order on your desktops.
So the first wallpaper will be drawn to your first desktop, the second one to desktop nr2 and so on.

Set up one for each desk, I got 4. U may also set up more than the number of your desks, but it wont have any effect.

Alright, now enable the plugin. If you are using Ubuntu, which obv most of us are, you wont notice any change yet. Still the same on every Desktop.

This is because nautilus, the default file manager shipped with gnome, draws our Desktop, as well as the icons lying on it and the right klick context. But don't worry, we'll be rid of it soon.

[COLOR="#ff0000"]Note:[/COLOR]You may as well find it useful taking a shot at some other file manager applications.
I like 
PCManFM 
the most. It completely replaced my nautilus, which, I'm sure saved me at least as much time as this post will take me to finish :) Ridiculously fast compared to nautilus. force --back-to-topic

Alright, so we enabled our prefered wallpapers, and they are actually there, but nautilus covers them.
I could describe it by using the gconf editor and the command line a lot, but I prefer 
gTweakUI - Nautilus
which does basically the same we would do by typing lines and lines of code.
It is available through the universe repos, open up a terminal and copy&paste this:
[/code]
sudo apt-get update
sudo apt-get install gtweakui [/code] 
[COLOR="Red"]Note:[/COLOR] You may want to use a prefix to install it into a given directory, up to you.

I prefer preventing nautilus from starting up at all, you may specify this however you like it through System --> Preferences --> Sessions. Tho gtweakui will be fine, if u wanna still use nautilus for file management purpose. However, if you decide to go with some other app, you should remove it from your startup now. Open up a terminal and do this:
```
 
cd ~/.config/autostart/
ls

```
As it is the first thing I did after I installed Hardy, I dont know what it is called, should be sth according to nautilus.desktop.
Taken it is actually called nautilus.desktop, which I cant guarantee, u may edit it by typing:
```

gedit nautilus.desktop
```
search line
```

X-GNOME-Autostart-enabled=true
```
and change it to
```
X-GNOME-Autostart-enabled=false
```
Save, and exit.

Now fire up gtweakui by typing:
```
gtweakui-nautilus
``` 
into your favorite terminal application.

Uncheck:
[ ] Use nautilus to draw desktop, close gtweakui, and hit 
Ctrl + Alt + Backspace

to restart your X-Session.
[COLOR="#ff0000"]This will not remove your nautilus! If you wanna get rid of it you gotta take further actions[/COLOR]

But it's enough for now, after logging back in, we should have that mission accomplished, and each of our desks should have his own wp now.

Next step is to get rid of your gnome panel if you want to. Many here using AWN as I saw, so have I been for a while. I switched to KiBa tho in the meanwhile. It is very customizable, and once set up, which can easily be done by modifying a .xml file, as stable as AWN. 
BUT: you may use more than one instance of it, unlike AWN. This was the main issue for me to take a shot at KiBa, and I dont regret anything :)

Alright, but configuring your desktops to fit your need should be up to every single one of you. If someone is interested in a HowTo I might set it up tomorrow or so, but now I'd like to continue with conky.

If you use it, you already might have noticed its fake transparency. And as this is due to the source code, theres nothing we could easily tweak about it, except of porting it to another language or recoding it or sth.

But as all of us are using Compiz anyway I guess, lets actually make use of it. Setting the 
own_window_transparency to "yes" wont work in this case, just because conky isn't, and actually never was transparent. It took a shot of the frame it was told to draw to, and used it as its background.

So we gotta go for a workaround, which should melt conky into our desktops, even if its not fully transparent. As I said, I like my Desktops clean, so I wrote a conky, which displays all my desired Information in just one line on top of my screen. Take a look at the screenshots... 

This way you should be able to set your conkys up as you like, if u prefer a lot of bars and colors and stuff. (Please ask google for further information of conky, if you need some, there are a lot of HowTos available all over the net)

However, your conky options should look like this:
```

own_window yes
own_window_hints undecorated  #,sticky,below,skip_taskbar,skip_pager
own_window_type normal
own_window_transparent no
background black

```

As you may notice I commented out the window_hints in my conky, and also specified to draw a background. I've chosen a black one, u may specify it to fit to your desks however you like.

Anyway, once you set up your conky, open up CCSM once again, and go to 
Window Management --> Window rules.

Mine looks like this:
[[img=http://img523.imageshack.us/img523/503/conkygrabpw0.th.png]](http://img523.imageshack.us/my.php?image=conkygrabpw0.png)
You may type it in or use the green plus to open the little helper u might notice.

However, again, set it up to fit your needs.

Last thing to do to make conky suitable is setting some transparency.

[COLOR="Red"]NOTE: Linux is case sensitive![/COLOR]
So if you type "conky" instead of "Conky" exactly nothing will change.

Alright then, once done, hit back, and navigate 
to general options, still in CCSM.

The last tab is called Opacity Settings, activate it, click on window opacities to drop it down if it isn't open yet, and hit new.

Once again enter class=Conky and consider how opaque you would like your conky to be. Sth in between 33%-66% should be finde, just toy around, it is actually applied instantly. 

Alright, I guess thats about it, some shots how this could look like once you are finished attached.

I hope you have been able to follow, I'm german, and as the shots reveal, it's pretty l8 over here by now :) However, enjoy :)

Oh, btw, my Conky:
```

use_xft yes
xftfont Sans:size=8
alignment top_right
xftalpha 0.8
update_interval 3.0
own_window yes
own_window_hints undecorated  #,sticky,below,skip_taskbar,skip_pager
own_window_type normal
own_window_transparent no
background black
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 0
border_margin 0
border_width 1
default_shade_color black
default_outline_color white
default_color white 
override_utf8_locale yes
# Minimum size of text area
minimum_size 1440 2
maximum_width 1440

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 1


use_spacer none
uppercase no
# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

TEXT
Core1${goto 40} ${cpu cpu1}%${goto 78}${hwmon 0 temp 1}°C |Core2${goto 171} ${cpu cpu2}%${goto 209}${hwmon 1 temp 1}°C |GPU   ${execi 30 nvclock -T | perl -ne 'print $1 if /temperature.*?: (\d+)./;'}°C |HDD: ${execi 30 hddtemp /dev/sda  | perl -ne 'print $1 if /250JI.*?: (\d+)./;'}°C   ${color red}|${color} Proc: $running_processes | $memperc% RAM used   ${color red}|${color} /root: ${fs_free_perc /}% | /home: ${fs_free_perc /home}% | /sto: ${if_mounted /media/DRIVE-N-GO}${fs_free_perc /media/DRIVE-N-GO}%${else}${color dark grey}absent${color}${endif}   ${color red}|${color} ${color dark grey}${texeci 300 perl ~/configs/conk/conky_scripts/check_gmail.sh n}${color} new @ gmail     $alignr${nodename} ${color red}|${color} ${kernel}-${sysname}-${machine} ${color red}|${color} ${time %A %d %B}${font OpenLogos}${color red}u${font}${color}    
```

And another one covering two lines, same options as above
```

TEXT
 Core1${goto 55} ${cpu cpu2}%${goto 84} ${hwmon 0 temp 1}°C${goto 126}${color red}||${color} GPU   ${execi 30 nvclock -T | perl -ne 'print $1 if /temperature.*?: (\d+)./;'}°C ${color red}|${color} mem   $memperc% | @: ${texeci 300 perl ~/configs/conk/conky_scripts/check_gmail.sh n} new${alignr 520}${color green}${downspeed eth0} Kb/s${color}${alignr 480}${color red}${upspeed eth0}Kb/s${color}    $alignr${nodename} ${color red}|${color} ${kernel}-${sysname}-${machine} ${color red}|${color} ${time %A %d %B}${font OpenLogos}${color red}u${font}${color}    
 Core2${goto 55} ${cpu cpu1}%${goto 84} ${hwmon 1 temp 1}°C${goto 126}${color red}||${color} hdd:  ${execi 30 hddtemp /dev/sda  | perl -ne 'print $1 if /250JI.*?: (\d+)./;'}°C ${color red}|${color} /root:  ${fs_free_perc /}% | /home:  ${fs_free_perc /home}% | /sto:  ${if_mounted /media/DRIVE-N-GO}${fs_free_perc /media/DRIVE-N-GO}%${else}absent ${endif} ${alignr 515}${color green}${totaldown eth0}${color}${alignr 490}${color red} ${totalup eth0}${color}  $alignr${execi 600 cat ~/.metar-status}  
```

Aight, enjoy.

L8rs.

---

### Post by eotakos on 2008-10-01
> Open System > Preferences > Appearance. Click on the Visual Effects tab. If Compiz and desktop effects are enabled, Normal, Extra, or Custom will be selected. If Compiz is disabled, None will be selected. To switch modes, simply click on another selection. Changes take effect immediately.

actually, when i go in this submenu, none of the options is selected, but i'm pretty sure i'm running compiz, because i've all the cubes spinning and other goodies which i control from CompizConfig Settings Manager. So i guess this isn't a general rule.

---

### Post by aimpau on 2008-10-03
**Is compiz for Ubuntu and Kubuntu only?**

Nope! Xubuntu has it too!

[http://ubuntuforums.org/showthread.php?t=934934](http://ubuntuforums.org/showthread.php?t=934934)

Just to add, don't forget to type in alt+f2

```

emerald --replace

```

the gtk-window-decorator cannot be controlled by the settings>>settings manager>>>window manager since it only control xfwm4. However, you can load .cgwdtheme files through the terminal. I recommended emerald since it is really cool.

**How do I beam up my windows to space?**

Capt. Picard: Prepare to beam up.
Data: Beaming up in 6 nanoseconds.

Press alt+f2 and type in
```

ccsm

```

Go to Animations and on the close animation tab, click on the top animation (by default, that would be Glide 2) and press edit. Look for Beam, click ok and close. That's it! Enjoy!

---

### Post by indiapavan on 2008-10-28
Very informative post. I learnt many new things about ubuntu. Now I am hooked onto it. :)

---

### Post by cgkades on 2008-10-31
there is a way to auto start emerald, and i'm surprised no one has posted about it yet. in the ccsm, you can click on "window decorations" and change the line from "/usr/bin/compiz-decorator" to "/usr/bin/emerald --replace"

---

### Post by loomsen on 2008-10-31
This conflicts with fusion-icon tho. If you got it running at startup emerald will replace itself. 

Your system monitor will prove as it will show multiple instances of "emerald --replace"

Look at the screenshot:
[[img]http://img261.imageshack.us/img261/8635/screenshot34bg1.th.png[/img]](http://img261.imageshack.us/img261/8635/screenshot34bg1.png)

So, better to leave it blank.

---

### Post by nicholasmathew on 2008-11-20
Hi everybody

I am Nicholas Mathew, new to this forum. I just want to say.. great post. Really very helpful.


Mathew

---

### Post by DaOg75 on 2008-11-27
Thank-you so much for this post. I am now the envy of North Fort Worth. Roger

---

### Post by Thievrey Corporation on 2008-11-29
Hi,

just want to say thanks to all of you. Great post. Desktop effects are just incredible.

So Good.

TC

---

### Post by EnderEcho on 2008-12-04
Thanks this is really helpful.

I'm waiting on my first Ubuntu system in the mail. A lot of the faqs are difficult to understand without a system in front of me, but this one was really helpful.

---

### Post by navidson on 2008-12-11
thank you so much. helped me a lot. thanks again.

---

### Post by vandorjw on 2008-12-24
** Compiz made my window borders disappear! How do I fix this **

-Make that you have Window Decorations Checked.

---

### Post by mc6415 on 2009-01-02
Hey great guide, I have one query though, I have installed compiz through synaptic, and when I look for System>Preferences I can't see advanced desktop effects, this is on 8.10 intrepid, how do I get to this menu?

EDIT: Got it now, forgot to add it in add/remove.

---

### Post by rushikesh988 on 2009-01-02
cool guys I HAVE SET MY 3D desktop  withthe help of all you guys 



you all are really awesome 

thanks to all !!!!!!!!!!!!!!!!!:popcorn:

---

### Post by jpeddicord on 2009-01-02
Updated the thread title to stay trendy. :D

---

### Post by sendblink23 on 2009-01-12
Fastest & Easiest way to make your 4 Workspaces with 4 different Wallpapers:

Keyboard: alt-f2
Run: gconf-editor
Head to: apps->nautilus->preferences, and uncheck the show-desktop box
Head to System>Preferences>ccsm, 

Search: wallpaper  *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*...  keep doing this till you have done all 4 Workspaces with each different Wallpaper Image... 

You are done.

---

### Post by tilerwen on 2009-01-16
I really appreciate this guide! I had so many questions after installing Ubuntu.:)

---

### Post by tarvinder on 2009-02-03
Great Guide. I've been desperate to enable desktop effects, while running Ubuntu 7.10. However I was unable to enjoy the experience because of my ATI 200M card on my laptop. I've just upgraded to Ubuntu 8.10 x64 and WoW! desktop effects worked like charm out of the box without any hassle on the same laptop, same card. I'm surprised. Ubuntu people have made it simple. After knowing that effects are working, I came back to this guide and I've added the additional packages such as simple config compiz manager and I'm pleased to have extra animations and effets. Thank you. I'm really enjoying them.

---

### Post by mrsnacker58 on 2009-02-11
also go to run, type gconf-config, go to apps, compiz, apps, and mess around

---

### Post by wjoyce on 2009-02-15
> **mrsnacker58 said:**
> also go to run, type gconf-config, go to apps, compiz, apps, and mess around

Correction to the above - it's gconf-editor, not gconf-config. :)

---

### Post by jjpcexpert on 2009-02-28
I cant get a shortcut for Xkill in Gnome or Compiz! another FAQ singular

---

### Post by tjeremiah on 2009-03-01
Every time I enable the scale feature in compiz and logoff or reset, the feature is disabled while other compiz features arent.

---

### Post by hp owner on 2009-03-22
any one know how to change the bar in this picture to look like vistas bar but with the ubuntu logo instead of the windows logo??

---

### Post by Godly on 2009-03-26
This is awesome! Thanks for all the useful posts. :guitar:

---

### Post by Godly on 2009-03-26
You da man! Thanks.

---

### Post by hp owner on 2009-04-01
for those of you how want a vista like start menu, install gnomenu, it is a customize able menu for linux. it works great

---

### Post by jpeddicord on 2009-04-05
Moved this FAQ to Desktop Environments because[LIST=1]
[*]There were too many stickies in General Help
[*]It's more relevant here
[/LIST]

:)

---

### Post by Jpardue on 2009-04-08
This is a great list of information Jacob, thanks alot

---

### Post by biji on 2009-04-11
I  use gnome-do with docky for dock like mac osx

---

### Post by emeraldgirl08 on 2009-04-27
As of this writing I am AMAZED by what Linux can do!

\\:D/

Thanks for helping us Noobs with this info!

---

### Post by Manigoldo on 2009-05-13
Thanks for the guide, very nicely done and answered many of my questions

---

### Post by CylnZ on 2009-05-27
> **sendblink23 said:**
> Fastest & Easiest way to make your 4 Workspaces with 4 different Wallpapers:

Keyboard: alt-f2
Run: gconf-editor
Head to: apps->nautilus->preferences, and uncheck the show-desktop box
Head to System>Preferences>ccsm, 

Search: wallpaper  *Click it*
*Enable it, then inside there *Background* click *New*.. Add a Wallpaper Image for the current Workspace.

Change Workspace, Add another Background Image *New*...  keep doing this till you have done all 4 Workspaces with each different Wallpaper Image... 

You are done.

Thanks, this was just what I was alookin for :KS

---

### Post by UbuntuNerd on 2009-05-29
this is a good link for compiz: [http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy)

---

### Post by zero1one0 on 2009-06-02
i like graphical effects especially the compiz
but i find that just setting the ubuntu default graphical effects to max is enough for me

this is just my opinion if u like the added effects you can do wtv u want

---

### Post by whole.grains on 2009-06-02
> **CylnZ said:**
> Thanks, this was just what I was alookin for :KS

Yes great post. Thanks!

---

### Post by factorgaming on 2009-06-12
Hai! this really helped me lot to sort off my problem. Thanking you

---

### Post by DCGStudios on 2009-06-16
> **loomsen said:**
> 
Next step is to get rid of your gnome panel if you want to. Many here using AWN as I saw, so have I been for a while. I switched to KiBa tho in the meanwhile. It is very customizable, and once set up, which can easily be done by modifying a .xml file, as stable as AWN. 
BUT: you may use more than one instance of it, unlike AWN. This was the main issue for me to take a shot at KiBa, and I dont regret anything :)


I could use some help with getting the multiple instances of KiBa working. I only found one thread about it and there were 0 replies. Enjoying the thread so far, keep it up! :popcorn:

---

### Post by Bill.the.noob on 2009-07-01
Hey there all. I enjoy all posts on this thread. I'm finding this forum very helpful as I'm a greenhorn to linux. My  predicament is this. I have recently installed compiz on my desktop {Ubuntu 9,04} and everything works great except for the animations . I can't seem to get any of them working after hours of messing around. Anyone else come across the samething. I really like the flaming windows when they close, but right now i have to hold my lighter up to the screen to get a similar but crappy effect.     I found a similar problem on another thread by Phantom Hoover " Compiz not working" I'm going to try their solution and see how far I get. Thanks                                                                               Sorry peeps . No such luck. Must be a conflict issue. I might as well uninstall it . The novelty of it is starting to wear off a bit. Later!

---

### Post by Pogibry on 2009-07-03
I too had some initial problems setting up my compiz.... for some stupid reason it would go back to default settings after I spent a while customizing it. Oh well. I love it now!!! I'm trying to ween myself from my windows dependency ;)

---

### Post by skryzak on 2009-07-12
thanks!! cube is my favorite so far.

---

### Post by Dobbie03 on 2009-07-20
Thanks, I have returned to Ubuntu and I am loving it, I wish I had never reinstalled windows.

---

### Post by finch127 on 2009-07-21
For everyone who wants quick window manager switching:

[http://ubuntuforums.org/showthread.php?t=1207203](http://ubuntuforums.org/showthread.php?t=1207203)

---

### Post by overdrank on 2009-07-21
> **finch127 said:**
> For everyone who wants quick window manager switching:

[http://ubuntuforums.org/showthread.php?t=1207203](http://ubuntuforums.org/showthread.php?t=1207203)

And the [fusion-icon]("apt:fusion-icon")

---

### Post by Dullstar on 2009-07-30
I was having an issue with the desktop cube, but I figured out what went wrong.  The "Rotate Cube" option was turned off.

---

### Post by techfanboy81 on 2009-08-22
I just want to know what is the difference between Compiz and Compiz Fusion?  Or they're just the same?

---

### Post by Capt. Blackwood on 2009-09-03
Damn, i never know you could do all that with ubuntu. I'm willing to bet that would cost a ton of money to get all that in windows (I feel ashamed that i did fork some cash to stardock).
 
I'd like to know how to display all my desktops in Cube/switcher? The site had a shot of it and i forgot where it was.
 
 
 
(I've been using ubuntu for less than a day and i'm loving it. minus the fact i may need a small Install for Windows XP)

---

### Post by Her Ghost on 2009-09-05
What is it called where you don't have a menu bar on the screen, but you can click somewhere on the desktop and have the menu appear at your cursor?

I have seen loads of screenshots of this in action, but I don't know what it is called so I can't search for it!

Here is an example: [http://www.fluxbox.org/screenshots/screenshots_full/screenshot_zan.png](http://www.fluxbox.org/screenshots/screenshots_full/screenshot_zan.png)

This is obviously running fluxbox (which I have tried, thought was cool, but don't have the energy to start configuring everything at this stage!)

Basically, I guess: Can I get the floaty menu thing on Gnome, instead of having to use fluxbox or another WM/DE?

---

### Post by stinkeye on 2009-09-14
> **Her Ghost said:**
> What is it called where you don't have a menu bar on the screen, but you can click somewhere on the desktop and have the menu appear at your cursor?

I have seen loads of screenshots of this in action, but I don't know what it is called so I can't search for it!

Here is an example: [http://www.fluxbox.org/screenshots/screenshots_full/screenshot_zan.png](http://www.fluxbox.org/screenshots/screenshots_full/screenshot_zan.png)

This is obviously running fluxbox (which I have tried, thought was cool, but don't have the energy to start configuring everything at this stage!)

Basically, I guess: Can I get the floaty menu thing on Gnome, instead of having to use fluxbox or another WM/DE?
I don't think there is a right click menu in gnome but there is a keyboard shortcut "show the panel's main menu" which will show the menu at the cursor when there is no menu applet on the panel.

---

### Post by costryan on 2009-09-19
Thank you so much if it wasn't for you i would've just have no borders!

---

### Post by simartem on 2009-09-22
i have everything installed correct. I am running compiz without any problems but cairo dock bacground is not transaparent. There is a black box. How can i make it transparent ?

> 
       *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon 9100 IGP
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master vga_palette cap_list
       configuration: latency=64 mingnt=8


---

### Post by Capt. Blackwood on 2009-09-22
I'm seeing users with their entire panel/bar transparent to some extent...how do ya'll do that?
 
Btw the system monitor screenless as a wonderful thing to have when i want to see how my system is doing on the fly. Just minimize the window and look.

---

### Post by hariks0 on 2009-09-23
Please refer
[http://ubuntuforums.org/showthread.php?t=891922&page=2](http://ubuntuforums.org/showthread.php?t=891922&page=2)

I have set the command 'main menu' under button binding as shift+button3. If there is no launcher for main menu in any panels, the main menu will pop up at the mouse cursor.

If your desktop is not drawn by nautilus so that you can have different wallpapers in each desktop. Then the button click will trigger main menu only if clicked on either panels.

Otherwise - your desktop is drawn by nautilus - the button click will trigger main menu at anywhere in the screen [over launchers, panels, open windows, terminals etc]

---

### Post by Her Ghost on 2009-09-29
thank you!  that's exactly what I wanted!

(sorry for the delay in responding!)

---

### Post by plutonium45 on 2009-10-06
my desktop became uber cool :D
I booted off windows years ago..
if these visual effects run on windows ..the processor will burn !!

---

### Post by Animortis on 2009-12-06
Nevermind, figured it out.

---

### Post by Iron Calves on 2009-12-09
I was wondering if there are anymore effects/animations that I could download? Can anyone provide a link? I looked but didn't find any.

---

### Post by hariks0 on 2009-12-21
Do you know that all except the current window could be made transparent upto 100 %. Well, it is by System > Preferences > Compiz Configuration Settings Manager > Accessibility > ADD Helper. Enable it and set the opacity to 30 to 40 %.

---

### Post by moss_gtr on 2009-12-22
I am trying to get the 3d desktop to work, but when i goto the CompizConfig Settings Manager, the Horizontal Virtual size is set to 4, the Vertical Virtual size is set to 1.  However, the Number of Desktops is set to 1.  I cannot change the number of desktops and I am wondering if that is the reason the cube is not working for me.

---

### Post by hariks0 on 2009-12-22
> **moss_gtr said:**
> I am trying to get the 3d desktop to work, but when i goto the CompizConfig Settings Manager, the Horizontal Virtual size is set to 4, the Vertical Virtual size is set to 1.  However, the Number of Desktops is set to 1.  I cannot change the number of desktops and I am wondering if that is the reason the cube is not working for me.

Set up compiz desktop size to 4 horizontal, 1 vertical and 1 desktops. Enable Desktop Cube, Enable Rotate Cube and last but not least, set the visual effects to Extra in Appearance Dialog.

---

### Post by SecretCode on 2009-12-23
> **moss_gtr said:**
> I am trying to get the 3d desktop to work, but when i goto the CompizConfig Settings Manager, the Horizontal Virtual size is set to 4, the Vertical Virtual size is set to 1.  However, the Number of Desktops is set to 1.

> **hariks0 said:**
> Set up compiz desktop size to 4 horizontal, 1 vertical and 1 desktops.

The setting "Number of desktops" confuses me. If you set horizontal to 4 (as default), don't you effectively get 4 desktops? Certainly the workspace switcher applet calls them "Desk 1" to "Desk 4".

If you set **vertical **to more than 1 you get a matrix of desktops (or whatever) in expo view - fine. But the desktop cube and rotate effect don't give you access to the vertical dimension.

So why is there another setting for number of desktops? But what is supposed to happen when you set number of desktops to more than 1? Expo view doesn't show it - the only way seems to be via the 'workspace switcher' gnome panel. 

Basically, for anything more than 1 vertical and 1 "desktop" there seems to be no consistency between the various means of navigation. Does anybody routinely use more than 1 vertical or more than 1 in the "number of desktops" setting?

---

### Post by hariks0 on 2009-12-23
> **SecretCode said:**
> The setting "Number of desktops" confuses me. If you set horizontal to 4 (as default), don't you effectively get 4 desktops? Certainly the workspace switcher applet calls them "Desk 1" to "Desk 4".

If you set **vertical **to more than 1 you get a matrix of desktops (or whatever) in expo view - fine. But the desktop cube and rotate effect don't give you access to the vertical dimension.

So why is there another setting for number of desktops? But what is supposed to happen when you set number of desktops to more than 1? Expo view doesn't show it - the only way seems to be via the 'workspace switcher' gnome panel. 

Basically, for anything more than 1 vertical and 1 "desktop" there seems to be no consistency between the various means of navigation. Does anybody routinely use more than 1 vertical or more than 1 in the "number of desktops" setting?

If vertical is set to more than 1, select a desktop from the lower set of the desktops using the 'workspace switcher' of gnome panel. You will be able to rotate those desktop cube as well. Use wallpaper plugin to view the differnt desktops and the resulting cubes.

---

### Post by SecretCode on 2009-12-23
Thanks hariks0. (By wallpaper plugin do you mean expo? 'Wallpaper' controls the background image afaics.)

What about navigation when 'number of desktops' is more than 1?

---

### Post by hariks0 on 2009-12-23
> **SecretCode said:**
> Thanks hariks0. (By wallpaper plugin do you mean expo? 'Wallpaper' controls the background image afaics.)


Wallpaper plugin is used to have different wallpaper images in each desktop. You will have to disable Nautilus drawing your desktop.

> What about navigation when 'number of desktops' is more than 1?

I have not checked that. Will reply as soon as I try.

---

### Post by hariks0 on 2009-12-23
> **hariks0 said:**
> 

What about navigation when 'number of desktops' is more than 1? 

I have not checked that. Will reply as soon as I try.

It is not possible to increase the value of Number of Desktops more than 1 in ccsm. I changed the value in gconf-editor to 2 and there was no difference. Key discription in gcong itself said that the range allowed is [1 - 1].:)

---

### Post by SecretCode on 2009-12-23
> **hariks0 said:**
> It is not possible to increase the value of Number of Desktops more than 1 in ccsm. I changed the value in gconf-editor to 2 and there was no difference. Key discription in gcong itself said that the range allowed is [1 - 1].:)

Hmm. I can change it to more than 1 in ccsm, on Jaunty. Currently running with 4 horizontal and 3 vertical workspaces, and 5 desktops. I just don't know how this is really *supposed *to work ... but I think it's a question for the compiz forums.

---

### Post by hariks0 on 2009-12-23
> **SecretCode said:**
> Hmm. Jaunty currently running with 4 horizontal and 3 vertical workspaces, and 5 desktops. I just don't know how this is really *supposed *to work ... but I think it's a question for the compiz forums.

I use Karmic. BTW, did you try the wallpaper plugin?

---

### Post by SecretCode on 2009-12-23
Yes, the wallpaper plugin is ... ok ... one drawback is that it doesn't draw under my transparent gnome-panels. At least the way I have it set so far.

---

### Post by Lepodo on 2010-01-04
Thank you, a very good FAQ that helped me alot.

---

### Post by rapidog on 2010-01-24
Tell me, when Gnome 3.0 arrives will this thread be obsolete since Gnome 3.0 does not support Compiz?

---

### Post by Garnett on 2010-02-09
Where do Conky and Fluxbox fit into this?

---

### Post by a2i3s on 2010-02-12
Thanks Sir. :)

---

### Post by xtracool_protik on 2010-02-16
Hi jpeddicord,
 Thanks for the FAQ helped me a lot when i started with compiz.
 Today I've a request can u come up with something similar for ecomorph?
 Thanks in advance

---

### Post by LinFor on 2010-03-03
> **rapidog said:**
> Tell me, when Gnome 3.0 arrives will this thread be obsolete since Gnome 3.0 does not support Compiz?

They will develop independently

---

### Post by eldinv on 2010-04-12
i just installed Ubuntu 9.10 like 30 mins ago. already did my updates and restricted drivers for my video card. 

thank you all for taking the time to show us newbies what we need for these effects. i just placed my copy of window[SIZE=1]s vista in the fireplace :lolflag:

so many headaches. now i got to look for the best programs for converting my avi and mkv files to DVD. i already noticed DeVede, ill give it a try. i loved my ConvertxtoDVD:(
[/SIZE]

---

### Post by lovecatss on 2010-04-29
very good.
> **jpeddicord said:**
> **This is *not* a topic for asking questions.** (Unless you can of course provide an answer along with it.)

[SIZE=5]**[COLOR=DarkRed]The FAQ[/COLOR]**[/SIZE]

[SIZE=4]Compiz[/SIZE]
**What is Compiz Fusion?**[INDENT]Compiz is what is known as a "compositing manager." It enables your desktop to run faster than with traditional window managers, and allows you to be more productive. Compiz controls the effects you see on your desktop: Shadows, animations, "the cube," and a whole bundle of other fun effects.[/INDENT]**How do I know if Compiz is enabled (How can I disable Compiz?)**[INDENT]On Ubuntu 7.10 and up:
Open **System > Preferences > Appearance**. Click on the **Visual Effects** tab. If Compiz and desktop effects are enabled, **Normal**, **Extra**, or **Custom** will be selected. If Compiz is disabled, **None** will be selected. To switch modes, simply click on another selection. Changes take effect immediately.[/INDENT]Be sure to keep simple-ccsm installed so that the Custom option remains available in Visual Effects.
[INDENT] 
You can also access it from **System > Preferences > Advanced Desktop Effects Settings** or by opening a terminal (or Alt+F2) and typing **ccsm**.[/INDENT]
[SIZE=5]**[COLOR=DarkRed]Contributing[/COLOR]**[/SIZE]
Attention forum members:

Want to have a chance to contribute to "The Great FAQ of Desktop Effects?" Then join me in the planning of one of the biggest events to hit this forum (well, stickies anyway). We're going to build a nice big topic to put right at the top of the forum page to hang out with the "Blacklisted?" topic. Anyone and everyone is welcome to contribute.

Interested? Great! Here's what you need to do:
Find a question about Compiz, Desktop Effects, Theming, or anything related that is fairly frequently asked, even if it may seem obvious. It can even be one of the questions above that is marked "to be written [b2b website]("http://www.alipapa.us")." Post your question as a reply to this thread in a format similar to:


or


Be sure to either include a link to the topic with the answer or provide the answer directly. The questions and answers will be edited into the main post (this one). I'll probably edit your questions and answers to fit them in with the rest of the questions, but the idea will remain the same.

---

### Post by Claus7 on 2010-05-02
Hello,

ehmm, this is the first time I'm posting on a sticky (if I remember correctly), so please be kind as usual!

I was thinking to write a thread on my own, yet I stepped upon this one, which I think a good place to write some things about compiz. So let's get started:

What we want to do:
try transparency

This post does not provide anything new. It just gathers things around the web about transparency in compiz. What I did refer to 10.04 version.

The look and feel of compiz is really nice, allowing many tampering with the options it provides. Looking around the net, I was able to see many beautiful and transparent windows, panels, menus, e.t.c., so here I sum up all these things.

Transparency can be divided in general in 3 different categories: windows, panels and menus.

Windows: the transparency of windows can be achieved pretty easily, from ccsm either from opacity or opacity, brightness and saturation menus.

Panels: this can be done pretty easily as well, right clicking on a panel, choosing properties and then customizing the panel to your liking. 

Menus: menus can be distinguished in PopupMenu and DropdownMenu

The PopupMenu category are the ones which pop up during work. For example if you use opera as your web browser then if you right click on an empty space, you will see a menu. This one is a popupmenu.

The DropdownMenu category refers to the menus of the panels. In your default Desktop environment you have to panels (bars). The top one has Applications, Places and System. The menus that appear if you click on these, are the dropdownmenus. 
These menus and their transparency is achieved differently than the one of the panels.

The difficulty in making transparent the menus is maintaining the text opaque (solid, not affected by transparency). There is a debate about this, and I have found that it can be achieved either by tampering codes or by choosing combination of themes.

Here I provide only some configurations, that will make these menus transparent, not loosing a lot in the opaqueness of the text.

In order to achieve the above follow figs 1 to 4 with the options I provide. In case you want to change settings you can do so by adjusting opacity, brightness and saturation from 0 to 100.

Also with the gnome-color-chooser you can adjust the menu colors to your liking and much much more.

Regards!

ps: helpful threads
[http://ubuntuforums.org/showthread.php?t=964943](http://ubuntuforums.org/showthread.php?t=964943)
[http://ubuntuforums.org/showthread.php?t=956039](http://ubuntuforums.org/showthread.php?t=956039)
[http://newyork.ubuntuforums.org/showthread.php?t=1285124](http://newyork.ubuntuforums.org/showthread.php?t=1285124)
[http://ubuntuforums.org/showthread.php?t=706226](http://ubuntuforums.org/showthread.php?t=706226)
[http://ubuntuforums.org/showthread.php?t=1395491](http://ubuntuforums.org/showthread.php?t=1395491)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1193287](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1193287)

[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)
[http://www.ghacks.net/2009/08/22/get-some-serious-transparency-in-gnome-and-compiz/](http://www.ghacks.net/2009/08/22/get-some-serious-transparency-in-gnome-and-compiz/)

---

### Post by starbase1 on 2010-05-07
Hello All,
I did a clean install moving to Lucid Lynx, and now I am having problems gettng my desktop back the way I liked it...

One of the coolest desktop effects was being able to scroll a mouse wheel over a blank bit of desktop, to move between them.

But now I am struggling to work out which combination of compiz settings I need to make this happen! Can anyone enlighten me please?

---

### Post by hariks0 on 2010-05-08
> **starbase1 said:**
> Hello All,
I did a clean install moving to Lucid Lynx, and now I am having problems gettng my desktop back the way I liked it...

One of the coolest desktop effects was being able to scroll a mouse wheel over a blank bit of desktop, to move between them.

But now I am struggling to work out which combination of compiz settings I need to make this happen! Can anyone enlighten me please?

It is the viewport switcher.

---

### Post by starbase1 on 2010-05-08
> **hariks0 said:**
> It is the viewport switcher.

I have found that, and turned it on, but nothing is happening.

I suspect I need to do something with the desktop based viewport switcher settings tab, but I can't work out how to tie the actions (move next and move prev I assume?) to the mouse wheel...

---

### Post by hariks0 on 2010-05-08
Hope the screenshot helps. :guitar:

Let me add that Button4 and 5 are nothing but the scroll wheel of your mouse.

---

### Post by hariks0 on 2010-05-08
> **abhishekbiwal said:**
> Hello friends, 
i have upgraded ubuntu from 9.10 to the latest version which is released, the problem is that, my desktop has become all hazy and blurred nothing is SHARP.
:sad:
Pls help how can i fix this.

One picture conveys more than 1000 words do. Why don't you post a screenshot ? We will be able to help you more.

---

### Post by starbase1 on 2010-05-08
> **hariks0 said:**
> Hope the screenshot helps. :guitar:

Let me add that Button4 and 5 are nothing but the scroll wheel of your mouse.

Aha! That explains it - I was wondering why the program designer appeared to be using a keyboard on wheels judging by the number of button!

Everything now working as intended in this department,
Thanks!

---

### Post by abhishekbiwal on 2010-05-13
I upgraded from ubuntu 9.10 to 10.04 and my display is all hazy not sharp at all pls help:(

---

### Post by jpeddicord on 2010-05-13
> **abhishekbiwal said:**
> I upgraded from ubuntu 9.10 to 10.04 and my display is all hazy not sharp at all pls help:(

overdrank split your posts into here: [http://ubuntuforums.org/showthread.php?t=1473019](http://ubuntuforums.org/showthread.php?t=1473019)

Please reply there, as this FAQ is not a support thread and you will get better help in your own thread.

---

### Post by abhishekbiwal on 2010-05-17
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)

if you need anything more let me know, 
i guess my display is screwed up, even when i see the screen shots in window they appear normal but believe me its all hazy not sharp at all.

---

### Post by karmila on 2010-05-19
> **hariks0 said:**
> Do you know that all except the current window could be made transparent upto 100 %. Well, it is by System > Preferences > Compiz Configuration Settings Manager > Accessibility > ADD Helper. Enable it and set the opacity to 30 to 40 %.

Another great compiz effect!

Cool... let me **focus** on my focus window 

This effect is made for me, lol  :P

---

### Post by hariks0 on 2010-05-20
> **karmila said:**
> Another great compiz effect!

Cool... let me **focus** on my focus window 

This effect is made for me, lol  :P

I installed peek effect for compiz and now inaddition to getting a peek preview I am getting all the windows transparent when I move mouse over any panel. That is also very cool.:)

---

### Post by nodnarb1982 on 2010-06-21
Just installed Ubuntu 10.04. I had been running version 9.04 for about the past year. Anyways, I decided to do a fresh install of 10.04, and everything is running fine. One thing I did immediately notice is some of the options in Compiz are now gone. The settings I am referring to are the Cube deformation (the setting that allowed deforming the cube into a sphere or cylinder) and the setting that allowed the windows to be raised when rotating the cube. I'm sure there are more that are missing as well, just not sure what they are yet. I don't understand why any settings (especially ones like raising windows) would be removed, but would be greatly appreciative if someone could inform me on where they went! Thanks so much!

---

### Post by jpeddicord on 2010-06-21
Added that to the FAQ:

> **I can't find some of the plugins mentioned in this FAQ. Where are they?**
[INDENT]As of recent Ubuntu releases, these are now available in [compiz-fusion-plugins-extra]("apt:compiz-fusion-plugins-extra"), which is not installed by default.[/INDENT]

---

### Post by wkhasintha on 2010-08-04
Thanx alot

---

### Post by vince2678 on 2010-08-20
Compiz cannot update the mouse cursor theme when it is updated in GNOME.  Install this package to allow compiz to notice the change and feel free  to modify it however you want. PLEASE read he control info!

Unfortunately only works with GNOME. If anyone has LXDE and XFCE please send me info on how it stores info about cursor theme and size and the program used for changing cursor theme. I have KDE in a VM so I'll try something there.

LINK: [http://ubuntuforums.org/showthread.php?t=1557297](http://ubuntuforums.org/showthread.php?t=1557297)

---

### Post by xtracool_protik on 2010-08-20
Thanks Vince,
 I always wondered whats up with that. I'll check out the package you have posted and see how it works out :)

---

### Post by xtracool_protik on 2010-08-20
Hey it says
 > The file link that you requested is not valid.
I think file is not been uploaded properly?

---

### Post by vince2678 on 2010-08-20
The link was updated. The old file no longer exists, but a new one does.

---

### Post by Gaygerbil on 2010-08-21
You guise should add how to add and customize Cario, AWN, and Docky docks.

Also adding stuff about Enlightenment would be really useful. Both docks and other window managers are pretty popular on this forum.

Oh and Conky, def useful to add that to this FAQs, there's tutorials for that in a bunch of different places.

You can also put videos of people showing things that would def help people (it helped me learn a lot by watching other people do things)

Also things about customizing your panel would be nice. Great FAQs though. :]

---

### Post by jpeddicord on 2010-08-21
> **Gaygerbil said:**
> You guise should add how to add and customize Cario, AWN, and Docky docks.

Also adding stuff about Enlightenment would be really useful. Both docks and other window managers are pretty popular on this forum.

Oh and Conky, def useful to add that to this FAQs, there's tutorials for that in a bunch of different places.

You can also put videos of people showing things that would def help people (it helped me learn a lot by watching other people do things)

Also things about customizing your panel would be nice. Great FAQs though. :]

Let me know exactly what to edit in and I'll add it. I'd love to make this thread editable by others to make things easier, but sadly I don't think it's possible.

---

### Post by xtracool_protik on 2010-08-21
Hey Vince that link worked :)
 However check these 3 screenshots, I'm not sure if it really suppose to be this way (normal cursor is still default everything else changes perfectly).
 Or am I still missing something?

---

### Post by xtracool_protik on 2010-08-21
Sorry screenshots doesn't show editing cursor or hand cursor.

Anyway the point was default cursor stays same but all other action cursors are working properly
Thanks

---

### Post by xtracool_protik on 2010-08-21
And I wanted to show off my desktop :D
Thanks to all u guys
Have a look at it [http://www.youtube.com/watch?v=6_1B9SGr3Ws](http://www.youtube.com/watch?v=6_1B9SGr3Ws)

---

### Post by vince2678 on 2010-08-21
> **xtracool_protik said:**
> Hey Vince that link worked :)
 However check these 3 screenshots, I'm not sure if it really suppose to be this way (normal cursor is still default everything else changes perfectly).
 Or am I still missing something?

Minor error. Symbolic links cant be replaced by ordinary files so the file /usr/share/icons/default/index.theme could not be replaced. Remove it and try rerunning gnome-appearance-properties.

Hope that helps!

---

### Post by xtracool_protik on 2010-08-21
yup that worked 
there is only one exception in my themes list for which it still provides default cursor.
 I would assume thats something to do with that theme

---

### Post by The Cyph3r on 2010-08-31
> **xtracool_protik said:**
> And I wanted to show off my desktop :D
Thanks to all u guys
Have a look at it [http://www.youtube.com/watch?v=6_1B9SGr3Ws](http://www.youtube.com/watch?v=6_1B9SGr3Ws)

Damn dude. Thats a masterpiece right there.
Would you mind posting a list of what you've got running there?
For example: The media workspace was just...wow.

---

### Post by xtracool_protik on 2010-08-31
Hey thanks a lot :D glad u liked it (I wanted to do some more but don't have that much time :P )
 Anyway here is all that I can recall while making it (if I've missed anything please point out I'll post it again)
 Compiz:
 Cube deformation - Cylinder, Semi transparent while rotating
 Wallpaper plugin - word of advice - u can't use conky with wallpaper plugin else it would have been awesome
 Skydome - not animated to make it look like cylinder is rotating in some kinda box (I wanted top of cylinder not to be transparent as I removed bottom wanted that butterfly to be vivid from bottom as well - though couldn't do it)
 Particular Workspaces
 Terminal workspace - check here [http://ubuntuforums.org/showthread.php?t=1509854](http://ubuntuforums.org/showthread.php?t=1509854)
 Media workspace - Its all done through screenlets
 1. equilizer - for equilizer
 2. lyrics - for lyrics
 3. ring clock - for clock
 4. output - for dmseg

 Well I suppose thats all there is, 
 I'm looking into elive and few more simple and elegant setups out there on gnome-look.org will upload if I manage to make something good again (will take quite a while)
 Hope this helps have fun :popcorn:

---

### Post by The Cyph3r on 2010-08-31
The thing I'm wondering is, are those screenlets on top of a BADASS wallpaper, or music player, etc?

---

### Post by xtracool_protik on 2010-09-01
yup thats just plain ole' wallpaper ;)

---

### Post by The Cyph3r on 2010-09-01
I've found a [very nice skin]("http://g3xter.deviantart.com/art/BlueVision-V0-2-Alpha-162478234") that I'm wondering can be configured to work in Ubuntu. It's apparently only available for Windows, but I'm curious if there's a visually identical version, or it can be migrated over.

---

### Post by xtracool_protik on 2010-09-01
thats pretty neat
 U won't find anything exactly similar (no prebuilt skin) but I'm sure u can manage to get it with conky (temp, cpu/ram/network usage, hdd, weather) and screenlets (rss reader, digital clock, weather, amarok or any music player etc) and a good wallpaper.
 I would like it that way as well but as I said wallpaper plugin and conky doesn't go together (I need to check on current status though)
 P.S. I don't have windows and I didn't see wat all things that rar provide things I mentioned above r just my opinion from wat I read in its description

---

### Post by Cavsfan on 2010-09-02
> **xtracool_protik said:**
> And I wanted to show off my desktop :D
Thanks to all u guys
Have a look at it [http://www.youtube.com/watch?v=6_1B9SGr3Ws](http://www.youtube.com/watch?v=6_1B9SGr3Ws)

That is an amazing video! Do you have a power machine maybe an I7. And did you use recordmydesktop? 
It looked like you did. I get some screen flicker when I try that.
Just curious as to how you created such a flawless video. I got the wallpaper plugin and Atlantis fish working and it looks pretty sweet.

---

### Post by jpeddicord on 2010-09-02
> **Cavsfan said:**
> That is an amazing video! Do you have a power machine maybe an I7. And did you use recordmydesktop? 
It looked like you did. I get some screen flicker when I try that.
Just curious as to how you created such a flawless video. I got the wallpaper plugin and Atlantis fish working and it looks pretty sweet.

For Compiz and most desktop effects you'd really want a good GPU, not necessarily a CPU. You could have a pretty standard processor and a 9800 graphics card and get very good results.

---

### Post by xtracool_protik on 2010-09-02
Hey thanks :D
 Here are my specs
>  C2D 2.4 GHz T8300
 4GB DDR2 RAM
 Intel GM965 graphics card
 I won't call it power machine though its decent, I would have loved a graphics card :D
 yes I used gtk-recordmydesktop and I don't get flicker not sure wats going wrong at ur place (I used mencoder to convert from ogv to avi and then used mencoder to attach song to it, recording through mic was giving a bad quality for sound)

---

### Post by Cavsfan on 2010-09-02
> **jpeddicord said:**
> For Compiz and most desktop effects you'd really want a good GPU, not necessarily a CPU. You could have a pretty standard processor and a 9800 graphics card and get very good results.

I have:
Core 2 Quad CPU Q9550 @ 2.83GHz 
4GB RAM DDR2 800
NVIDIA GeForce 9800 GT 512MB

It runs Modern Warfare 2 (my son) at 60-70 FPS in windows 7.

> **xtracool_protik said:**
> Hey thanks :D
 Here are my specs
Quote:
                                                  C2D 2.4 GHz T8300
 4GB DDR2 RAM
 Intel GM965 graphics card 
 I won't call it power machine though its decent, I would have loved a graphics card :D
 yes I used gtk-recordmydesktop and I don't get flicker not sure wats going wrong at ur place (I used mencoder to convert from ogv to avi and then used mencoder to attach song to it, recording through mic was giving a bad quality for sound)

I should be able to do this then shouldn't I. Maybe I had too much Compiz stuff going on.
I had snow, atlantis fish tank, and some other things.

Thanks to both of you for the fast reply!

---

### Post by xtracool_protik on 2010-09-02
Hey Cavsfan,
 Thats an awesome system, u can totally do it.
 And I don't have any experience with NVidia cards but r u using proprietary drivers or open source or edgers ppa? if ur using open source drivers then I would suggest proprietary or edger's drivers (but please do it after u r sure of important backup.)
 I don't think any of compiz effect causes a flickering but I would try to record it without snow, fish tank is fine.

---

### Post by Cavsfan on 2010-09-03
> **xtracool_protik said:**
> Hey Cavsfan,
 Thats an awesome system, u can totally do it.
 And I don't have any experience with NVidia cards but r u using proprietary drivers or open source or edgers ppa? if ur using open source drivers then I would suggest proprietary or edger's drivers (but please do it after u r sure of important backup.)
 I don't think any of compiz effect causes a flickering but I would try to record it without snow, fish tank is fine.

I am just using the suggested driver in Hardware Sources. I wonder if it would be worthwhile to see about getting a newer driver. 
I dual boot windows 7 and a new driver comes down the pipe every so often. I know we have upgraded the windows driver 10 times at least.
And there have been huge improvements!

Kind of squeamish though about messing what I have up. I did a clean install of 10.04.1 last week and no more monitor clicking noises! 
It used to click 2-3 times during boot and I knew that couldn't be good. 

I have a 28" Hanns-G 1080p LCD monitor with a native resolution of 1920x1200.
(before that I had a 12 year old Dell with a 17" monitor! :))

Could it be that the resolution is too big? I tried using this alternative to recordmydesktop which worked pretty well.
And I didn't need to use Jack for the sound. I just played an MP3 in Totem and the sound was awesome!
Couldn't use Rhythmbox as one is apparently alsa and the other pulseaudio. 

[URL="http://ubuntuforums.org/showthread.php?t=1392026"][COLOR=blue][U] HOWTO: Proper Screencasting on Linux
[/U][/COLOR][/URL]
But, I still had the occasional flicker.

---

### Post by xtracool_protik on 2010-09-03
Hey Cavsfan,
 I don't have exact same hardware so I may be wrong (or shooting in dark) here but as per my knowledge the drivers u r using r open source drivers.
 If u have 32 bit Ubuntu installed I would say install [http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html) drivers from that link
 else if u r interested in bleeding edge open source drivers (sometime may go wrong as very much in development phase) look at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Cavsfan on 2010-09-03
> **xtracool_protik said:**
> Hey Cavsfan,
 I don't have exact same hardware so I may be wrong (or shooting in dark) here but as per my knowledge the drivers u r using r open source drivers.
 If u have 32 bit Ubuntu installed I would say install [http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html) drivers from that link
 else if u r interested in bleeding edge open source drivers (sometime may go wrong as very much in development phase) look at [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Thanks a lot!!! But I think I just upgraded my video driver from version 195 to 256.52! :D
I wanted something real recent and looked for quite a while and found this:
(July 3rd 2010)
[[COLOR=blue]_Update nVidia drivers._[/COLOR]]("http://gamblis.com/2010/07/03/install-nvidia-256-35-display-drivers-in-ubuntu/")
I had to add a PPA and some other stuff and when I rebooted I looked in Hardware drivers and did not notice anything different.
But, when I looked in NVIDIA X server settings I seen the 256.52! And the instructions are for 256.35, so I must be on the latest. 
Smoking! :D
So, I'll have to try some stuff out! Right now I have to eat lunch as I am way late!

Thanks for your help and I will report back if that helped, but I cannot see it not helping!
:popcorn:

---

### Post by wkhasintha on 2010-09-05
> **xtracool_protik said:**
> Hey Cavsfan,
 I don't have exact same hardware so I may be wrong (or shooting in dark) here but as per my knowledge the drivers u r using r open source drivers.
 If u have 32 bit Ubuntu installed I would say install [http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html) drivers from that link
 else if u r interested in bleeding edge open source drivers (sometime may go wrong as very much in development phase) look at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Much thanx for this valuable information sir.:popcorn:

---

### Post by there.is.only.xul on 2010-10-20
I think it should be noted (at least for us GNOME users) that the GTK Window Decorator can be modified to a degree in gconf-editor. As of right now, the four options people sticking with GTK/Metacity have available off the bat are menu, minimize, maximize and close.

For those using any theme where the controls are on the left or are not in the "Correct" positions, the changes to be made under the apps/metacity/general section for the button_layout entry should be:
**menu:minimize,maximize,close**

That's how you get the little white circle that is the window menu on every window. Now here's a question: When will Emerald be updated so there is an extra titlebar option called combined menu/program icon? Like in Windows, you click the program icon to access the window options? Could be enabled by adding **P** to the titlebar layout, for example...

---

### Post by Cavsfan on 2010-10-20
Anyone running Maverick with the wallpaper plugin getting it to work? Since I installed Maverick 64 bit, when enabling the wallpaper effect
and unchecking the Show Desktop option in gconf-editor > Apps > Nautilus > Preferences it just freezes.
I have close window set to burn and when it closes the screen fills with fire like it normally would, but it just partially closes. The wallpaper 
does not change and when I try to spin the cube, there is no wallpaper and it is just transparent. I have to uncheck wallpaper for it to go 
back to normal.

---

### Post by MathewBracken on 2010-11-06
Nice replay.I think it should be noted (at least for us GNOME users) that the GTK Window Decorator can be modified to a degree in gconf-editor. That's how you get the little white circle that is the window menu on every window.

---

### Post by ThatLucidGuy12 on 2010-11-07
Thanks man. I owe you a few pints of (free) beer and a place in my bookmarks. Also gotta love the water effect.

---

### Post by Joshua Goins on 2010-11-10
Some of is a AD instead of a FAQ

---

### Post by hariks0 on 2010-11-11
> **Cavsfan said:**
> Anyone running Maverick with the wallpaper plugin getting it to work? Since I installed Maverick 64 bit, when enabling the wallpaper effect
and unchecking the Show Desktop option in gconf-editor > Apps > Nautilus > Preferences it just freezes.
I have close window set to burn and when it closes the screen fills with fire like it normally would, but it just partially closes. The wallpaper 
does not change and when I try to spin the cube, there is no wallpaper and it is just transparent. I have to uncheck wallpaper for it to go 
back to normal.

The last link in your signature [if meant anything] is not working. It would be great if you update the same with correct link to video, web page etc.:popcorn:

---

### Post by hariks0 on 2010-11-11
> **there.is.only.xul said:**
> ...

That's how you get the little white circle that is the window menu on every window. Now here's a question: When will Emerald be updated so there is an extra titlebar option called combined menu/program icon? ***[COLOR="Red"]Like in Windows, you click the program icon to access the window options?[/COLOR]*** Could be enabled by adding **P** to the titlebar layout, for example...

Can you please clarify this? I did not get what you mean.:)

---

### Post by Ricalsin on 2010-11-20
Linux absolutely rocks!  Not just the graphics, the whole architecture.

Message for the CREATIVE TYPES:  Most YouTube tutorials are very informative but not really "marketable" - as in "pass it along" types.  If you guys can begin to make some 10-30 second videos that are eye-popping it can really help us ex-Microsoft people to get our friends on board the Linux train. [ Like this one: ]("http://www.youtube.com/watch?v=ZxfSwzhSn1c&feature=related")

But keep those boring tutorials coming - need em too!

(Awesome thread!)  :p

---

### Post by Ricalsin on 2010-11-20
> **Ricalsin said:**
> Linux absolutely rocks!  Not just the graphics, the whole architecture.

Message for the CREATIVE TYPES:  Most YouTube tutorials are very informative but not really "marketable" - as in "pass it along" types.  If you guys can begin to make some 10-30 second videos that are eye-popping it can really help us ex-Microsoft people to get our friends on board the Linux train. [ Like this one: ]("http://www.youtube.com/watch?v=ZxfSwzhSn1c&feature=related")

But keep those boring tutorials coming - need em too!

(Awesome thread!)  :p

Also, put it to great NEW music - as we all know the Internet has struggling artists that are far more talented than what you see on American Idol.  Use this awesome OS to promote the whole concept of "talent" and "ingenuity."

---

### Post by nush on 2011-02-09
> **Cavsfan said:**
> Anyone running Maverick with the wallpaper plugin getting it to work? Since I installed Maverick 64 bit, when enabling the wallpaper effect
and unchecking the Show Desktop option in gconf-editor > Apps > Nautilus > Preferences it just freezes.
I have close window set to burn and when it closes the screen fills with fire like it normally would, but it just partially closes. The wallpaper 
does not change and when I try to spin the cube, there is no wallpaper and it is just transparent. I have to uncheck wallpaper for it to go 
back to normal.

anyone managed to sort this yet
thanks

---

### Post by Cavsfan on 2011-02-09
I ended up going back to the LTS and it works great once again, but the only problem is you cannot have conky,
as **show_desktop** has to be enabled so I don't use the wallpaper plugin. 

But, that is a good question on Maverick. :)

---

### Post by Cavsfan on 2011-02-09
> **hariks0 said:**
> [QUOTE=Cavsfan;10000924]Anyone running Maverick with the wallpaper plugin getting it to work? Since I installed Maverick 64 bit, when enabling the wallpaper effect
and unchecking the Show Desktop option in gconf-editor > Apps > Nautilus > Preferences it just freezes.
I have close window set to burn and when it closes the screen fills with fire like it normally would, but it just partially closes. The wallpaper 
does not change and when I try to spin the cube, there is no wallpaper and it is just transparent. I have to uncheck wallpaper for it to go 
back to normal.

The last link in your signature [if meant anything] is not working. It would be great if you update the same with correct link to video, web page etc.:popcorn:[/QUOTE]


I hadn't seen this post before today, is there a link in my sig. that doesn't work? They always have worked for me. :confused:

---

### Post by hariks0 on 2011-02-10
I meant> Lucid Lynx 64 bit / Win 7 64 bit. Is it not a comparison of these OSs?

---

### Post by Cavsfan on 2011-02-11
> **hariks0 said:**
> I meant. Is it not a comparison of these OSs?

That is just text displaying my OSs beside the 3 links.

---

### Post by Copper Bezel on 2011-04-19
[QUOTE=nush]anyone managed to sort this yet
 thanks[/QUOTE]

I guess I should note that in 10.10 32-bit, I have the wallpaper plugin working, but only for CompizStandalone and only if I don't have my external monitor attached on login. The trick was to set a 7-second delay after Compiz starts before any other startup application or service starts.

It *can* be fixed while running, under Gnome or whatever else, by switching to a VT and back, and it'll go on working for the rest of the session, regardless of what you do.

---

### Post by Kate the Enthusiast on 2011-04-20
Something cute for Ubuntu 11.04 (Unity desktop)? 
Sublets and others seem to not work here.

---

### Post by nush on 2011-04-28
hi, thanks CB
im just on with updating to natty so i will see what the future holds.
nush

---

### Post by RageMachine on 2011-08-14
hello allz just to add to what cgkades said on page 3 i think it was.

> there is a way to auto start emerald, and I'm surprised no one has posted about it yet. in the ccsm, you can click on "window decorations" and change the line from "/usr/bin/compiz-decorator" to "/usr/bin/emerald --replace"if for some resin you did what to install ccsm or any of the compiz stuff, you can still get emerald to auto star by doing the fallowing.

> go to system/preferences/startup applications
click add and enter the fallowing for
name : emerald
command : emerald --replace
comment : starts emerald


---

### Post by mörgæs on 2011-12-08
After 367,202 views this guide has served its purpose, and after agreement with Jpeddicord it has now been put to rest. Thanks to everybody participating.

A new guide on the same topic is available here: 
[http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)


Enjoy!

---

