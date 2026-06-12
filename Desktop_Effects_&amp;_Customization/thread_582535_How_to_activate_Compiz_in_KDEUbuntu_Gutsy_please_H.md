---
title: "How to activate Compiz in KDE/Ubuntu Gutsy? please HELP!"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by jonray74 on 2007-10-19
Hi Everyone,

I just installed Kubuntu on my PC with Gutsy 7.10, I have read that Ubuntu 7.10 comes with Compiz already, I've configured my video card, everything's okay, but can't seem to activate Compiz. 

How do you activate Compiz in Kubuntu? Everyone's guidelines here seems to be always in Gnome? Can someone just at least provide assistance on how to do it in Kubuntu please. Would appreciate it.

Thanks,
John

---

### Post by Wiebelhaus on 2007-10-20
system>prefrences>appearance

---

### Post by rustysail on 2007-10-20
Hey I am having the same issue.  I went to the setting in your thumbnail, and it is checked off as extra.  I get some effects when I close windows and open them, but no cube, and no way to edit the settings.

When I click on system>preferences>compiz settings manager, nothing happens at all.

Any ideas?

---

### Post by jonray74 on 2007-10-20
sx66gns,

thanks for your help but that won't work because I don't use GNOME as my Desktop, I use KDE.

I need someone to help me turn on Compiz using KDE. 

John

---

### Post by Wiebelhaus on 2007-10-20
> **rustysail said:**
> Hey I am having the same issue.  I went to the setting in your thumbnail, and it is checked off as extra.  I get some effects when I close windows and open them, but no cube, and no way to edit the settings.

When I click on system>preferences>compiz settings manager, nothing happens at all.

Any ideas?

yea , there's no configuration utility, I'm sure a hack will be posted soon.

---

### Post by Matakoo on 2007-10-20
> **jonray74 said:**
> Hi Everyone,

I just installed Kubuntu on my PC with Gutsy 7.10, I have read that Ubuntu 7.10 comes with Compiz already, I've configured my video card, everything's okay, but can't seem to activate Compiz. 

How do you activate Compiz in Kubuntu? Everyone's guidelines here seems to be always in Gnome? Can someone just at least provide assistance on how to do it in Kubuntu please. Would appreciate it.

Thanks,
John

First, open a console.

```


sudo apt-get install compiz compiz-kde compiz-settings-manager emerald
```

That should install everything you need. 

Next, to get it running:

```

/usr/bin/compiz.real
```

Now it should be running. In the K-menu, you should find a Settings sub-menu with the Settings-program. That's all I needed to do anyway, apart from activating the restricted graphics driver.

---

### Post by JeffElkins on 2007-10-20
I'm not having any luck getting this puppy running either. No fancy-shmancy cubes, rotating folders or anything :(

I'm also running Kubuntu, on a Mac mini with 2GB RAM and the Inlel integrated graphics. I started compiz in a xterm with compiz  --replace.

---

### Post by rustysail on 2007-10-20
```
E: Couldn't find package compiz-settings-manager
```

Thanks for the responce, but no luck.

---

### Post by Matakoo on 2007-10-20
> **rustysail said:**
> ```
E: Couldn't find package compiz-settings-manager
```Thanks for the responce, but no luck.

Sorry, my mistake. It should be compizconfig-settings-manager. And you need to have the universe section in apt enabled.

---

### Post by rustysail on 2007-10-20
Odd it says all of those packages are at the newest version already.

---

### Post by godog on 2007-10-20
I had the same problem, this lines worked for me:

```
 sudo apt-get remove compizconfig-settings-manager 
```

and then

```
 sudo apt-get install compizconfig-settings-manager 
```

I guess there most be another way, but that worked for me. Before that I had a "Compiz Settings Manager" in the menu... now i have "Advanced Desktop Effects Settings" and it works.

---

### Post by philcz on 2007-10-20
I guess I am not the only one that can't get KDE to work with compiz. I have set up my Workstation at work with 7.10 Gutsy, my laptop, and my home computer, and all works great in GNOME, bit nothing in KDE. 

I have gdm ad my display manger should I be running compiz-real

root      5386     1  0 20:28 ?        00:00:00 /usr/sbin/gdm
root      5389  5386  0 20:28 ?        00:00:00 /usr/sbin/gdm
root      9456  5389  3 21:41 tty7     00:00:29 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

---

### Post by meldroc on 2007-10-20
Where's a configurator in compiz and KDE?

When I used Beryl on feisty, it had a nice little system tray icon that you could click and use to play with all the settings.  Where is compiz's equivalent (for KDE, not GNOME!)

---

### Post by brel on 2007-10-21
I don't know. I HAVE the ccsm program installed and I can play around with the settings, but to no great effect. I too am looking for a general 'activate' button.

---

### Post by brel on 2007-10-21
I've just relaunched 'ccsm' and found hidden away under the 'preferences' main heading a checkbox labeled: 'Enable integration into the desktop environment'. The problem is it's non-active although it is currently checked so I assume I'm supposed to have some compiz effects.

My problem might be linked to the fact that I have this error when I start up ccsm:
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by MickS on 2007-10-21
> **brel said:**
> I've just relaunched 'ccsm' and found hidden away under the 'preferences' main heading a checkbox labeled: 'Enable integration into the desktop environment'. The problem is it's non-active although it is currently checked so I assume I'm supposed to have some compiz effects.

My problem might be linked to the fact that I have this error when I start up ccsm:


Same here but I don't get the error message on start up:confused:

Mick

---

### Post by zachthejones on 2007-10-21
I just want to chime in an say I'm having the same problem. I installed compiz-kde (as suggested on the previous page), but I've gotten everything else already installed and working perfectly on my gnome-side.

Someone did give me this code to activate compiz on Kubuntu:
```
compiz --replace ccp &
```

but that just gave me a little functionality, and the irritating loss of window borders when I closed out the terminal session - though everything was back the way it was supposed to be (with limited compiz functionality) when I logged back in.

You'd think someone would have thought of this issue...

---

### Post by pooler on 2007-10-22
The only way i've found to run kde under compiz is to use emerald. After booting KDE try this in a console window:

emerald --replace

compiz --replace

However, I don't know how to automate this procedure :(

---

### Post by zain7478 on 2007-10-22
hi,
i got compiz to work with UBUNTU 7.10 by the following steps:

please try (?) or comment
.............................. .......

1.How I activate compiz-fusiion using KUBUNTU 7.10
2.System &#8211; adept manager &#8211; in the Adept Menu, click Manage Repositories; in the Kubuntu Software Tab &#8211; click all boxes; it the Third-Party Software Tab, click on the [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) - click close Button.
3.System &#8211; adept manager &#8211; fetch updates &#8211; wait until it finishes, then close
4.System Setting &#8211; advanced, click administrator Mode, click enable driver, wait for Adept Batch to download files.
5.Restrat &#8211; after restart, there will a notice that a restricted driver is in used &#8211; mine NVDIA.
6.System &#8211; adept manager &#8211; search compiz &#8211; install compiz, and it will automatically choose other appropriate files to install
7.Also install compiz-kde and compizconfig-settings-manager; as it is not automatically installed
8.Install emerald &#8211; for window decoration
9.Click Apply Changes, and wait for download to finish.
10.Alt + F2 &#8211; type compiz &#8211;replace, click RUN, wait for some blinking of screen.
11.Setting &#8211; choose Advanced Desktop Effects Settings, try Effect &#8211; woobly windows and other options ... should be OK.

...........................

---

### Post by pooler on 2007-10-22
> **zain7478 said:**
> hi,
i got compiz to work with UBUNTU 7.10 by the following steps:

please try (?) or comment
.............................. .......

10.Alt + F2 &#8211; type compiz &#8211;replace, click RUN, wait for some blinking of screen.

...........................

After that step, the window manager dies (no window decorations, no Alt-Tab :( ). It "runs" when I write this in a terminal:
```
emerald --replace &
compiz --replace &
```
but it's very unstable/barely usable...

PD: It also "works" with ```
KDEWM="compiz" startkde
```(tried on a plain X server, no gdm/kdm), but clicking on the title bar of a window often makes it dissapear and I don't know if gdm/kdm calls "startkde" or another program when I log in

PD: My sistem was upgraded from Ubuntu 7.04 (however I am using KDE), maybe I should manually install another X server?

PD2: Full comand if someone wants to try the latter aproach (starting from the login screen):
```
(Press the key combination)Ctrl-Alt-F2 (switches to console Nº2)
sudo X -ac :1 & (runs a new instance of X without access control, so any user has full control over that server. Also, it runs in the background so you can run other programs in the console ;) )
export DISPLAY=:1 (tells any gui app to start in that X server)
KDEWM="compiz" startkde (starts KDE with the window manager defined in KDEWM instead of kwin)

```

---

### Post by Caffeine_Junky on 2007-10-22
I got compiz-fusion running on Kubuntu Gutsy (cube and all) by doing the following:

1)  Install your 3D video drivers (if you haven't already)

2) Install these packages either from Adept or Terminal:
sudo apt-get install compiz compiz-kde compizconfig-settings-manager emerald

3) Do: ALT-F2 Run: compiz -replace

4) Do: ALT-F2 Run: emerald -replace

5)  Right-click the desktop, choose "Configure Desktop > Multiple Desktops" and set it back to only show "Desktop 1".

6)  Then with your KMenu > Settings > Advanced Desktop Effects Settings, Click the "General Options ICON" go to "Desktop Size" and set Horizontal Virtual Size to "4", while leaving "Virtual Size" and "Number of Desktops" set to "1"
...and while you are there enable your Cube etc...   Now you should have a working Cube, spin it with Ctrl+Alt <direction arrows >

(ps: if window borders give you trouble, open Terminal & execute: **emerald  -replace**  then leave the Terminal OPEN and log-out and back in,  this worked for me)

good luck I hope this works for you

---

### Post by stokedfish on 2007-10-22
Any solution yet? Can't get compiz to run.

---

### Post by pooler on 2007-10-22
I'm going to try what it says in this page:
[http://wiki.compiz-fusion.org/Decorators/KDEWindowDecorator?highlight=%28kde%29](http://wiki.compiz-fusion.org/Decorators/KDEWindowDecorator?highlight=%28kde%29)

---

### Post by pooler on 2007-10-22
> **zain7478 said:**
> hi,
i got compiz to work with UBUNTU 7.10 by the following steps:

please try (?) or comment
.............................. .......

10.Alt + F2 – type compiz –replace, click RUN, wait for some blinking of screen.

...........................

Now it seems to be working (no virtual desktops, but it's working)

---

### Post by treydee211 on 2007-10-22
I've been having the same problem I get all effects but no cube. It has to be a way to use the "cube" with in KDE I've seen it in pics all over the internet. I guess I'll have togo back to GNOME. Since I've used Kubuntu for this release its hard for me to use GNOME but hey cant have your cake and eat it too huh?

---

### Post by jonray74 on 2007-10-22
I guess I wasn't the only one who's had the problems installing Compiz in KDE. I tried re-installing it again last night, but I think for now I give up. I just re-installed Ubuntu 7.10 again and added Kubuntu as my desktop for now. No Eyecandy...

I checked everything with my Video settings, I enabled Restricted Driver's to use ATI as my Video driver, and it worked well, Rendering says Yes..BUT, here's the but part...

After installing Compiz on KDE, did all the settings, and typed in "Compiz --Replace", my window borders disappeared, and I got an error saying something about Screen "0:0". Without luck, I decided to just install KDE and left it at that. 

I do love the eyecandy that Compiz offers, but what I have noticed is that most Guidelines and Installation of Compiz has only been focused more on GNOME not for KDE. It would be really nice if someone can give a better Compiz Guidelines and Installation for Kubuntu KDE than GNOME. 

If someone out there uses KDE and has the same Hardware as mine, just please post a link of installing Compiz using KDE.

my hardware specs are as follows:

ASUS MB P4V8X-V
P4 2.8Ghz CPU
1GB RAM
Sapphire Radeon 9600 Pro 256MB
Creative Labs Sound Blaster Live Value/AC97 built-in Sound

Thanks,
John

---

### Post by Eggbanjo on 2007-10-22
Managed to the cube to show, also found the cube will spin using the key commands, just wont do it with the mouse wheel.

Used the KDEWM="compiz" startkde command, logged out and back in Compiz came in straight away!

If i get to use the mouse to spin ill be well chuffed

---

### Post by jonray74 on 2007-10-22
BTW...

Compiz Fusion and Compiz are totally 2 different beasts...at least that's what I read at Compiz-Fusion.org

Thanks,
John

---

### Post by zain7478 on 2007-10-22
sorry guys - if this is the wrong place, 

but i envy mandriva 2008 -- i just wished KUBUNTU could do the same!

it does kde, compiz-fusion right from the live CD
i installed it on my computer (AMD64 AthlonX2, abit nf-m2s m/b,gforce 8500GT, 1GB memory, samsung syncmaster 931bw) in 5 minutes - that was the fastest linux installation so far, for me!

everything is there - cube, wobbly, expo cover switch ... except for the screen saver!
but i had to abandon it (for the time being) becoz i could not get the internet connected - so i stick with kubuntu

wonder why KUBUNTU or UBUNTU team did not - imitate - MANDRIVA ;-) ... or who imitate whom?

---

### Post by pooler on 2007-10-22
Here's a mini-howto to enable compiz-fusion on KDE:
1- Check that you have the proper drivers installed (either by enabling them in the restricted-drivers-manager or installing the official versions from the vendor website if you have an ATI/nVidia video card)
2- (Only if you chose to install nVidia drivers from [www.nvidia.com):](www.nvidia.com):) You must edit (with root/superuser privileges) the file /etc/lrm-nvidia to make it look like this:
```

PATH=/sbin:/bin

MODULE="$1"
shift

if [ "$MODULE" = "nvidia" ]; then
        if [ -e /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko ]; then
                MODULE="nvidia"
        fi
        if [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]; then
                MODULE="nvidia_legacy"
        fi
        if [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]; then
                MODULE="nvidia_new"
        fi
        XORG="nvidia";
elif [ "$MODULE" = "nvidia_legacy" -o "$MODULE" = "nvidia_new" ]; then
        XORG="nvidia";
elif [ "$MODULE" = "fglrx" ]; then
        XORG="fglrx";
fi

if cat /etc/X11/xorg.conf 2>/dev/null | \
  sed -n -e '/^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//;p}}' | \
  grep -q -w $XORG - ; then
        modprobe --ignore-install -Q $@ $MODULE
else
        echo "Not loading $MODULE module; not used in /etc/X11/xorg.conf" 1>&2
fi

``` or, alternatively, comment all the lines in the file /etc/modprobe.d/lrm-video.

3- Test that it works: At least one of the following commands should make the **window decorations** look like this: [IMG]http://images.howtoforge.com/images/fedora7_beryl_compizfusion/12.jpg[/IMG] 
(Sorry for the pic, but it's the only one I could find that clearly shows the window decorations)
 a- Alt-F2 -> compiz --replace
 b- (From a terminal window)emerald --replace & [Enter] and then execute compiz --replace

4- If it works and you want compiz-fusion enabled by default, then edit ~/.xsession (only for current user), /etc/X11/Xsession (for all users, if you use kdm (default in Kubuntu) or xdm, requires admin/root privileges), /etc/gdm/Xsession (same as the second one, but for gdm) and add the following line at the end of the file:
export KDEWM=compiz
(note: I have only tested the ~/.xsession way, the others should work).
Notes:
1- To use compiz-fusion, I highly recommend installing the following packages: compiz-kde, compizconfig-settings-manager .
2- Virtual desktops must be configured from ccsm (CompizConfig Settings Manager, or K-Menu->Settings->Advanced Desktop Effects Settings). However, the desktop paginator that comes with KDE doesn't work with compiz-fusion :(

---

### Post by Caffeine_Junky on 2007-10-23
I got compiz-fusion running on Kubuntu Gutsy (cube and all) by doing the following:

1) Install your 3D video drivers (if you haven't already)

2) Install these packages either from Adept or Terminal:
sudo apt-get install compiz compiz-kde compizconfig-settings-manager emerald

3) Do: ALT-F2 Run: compiz -replace

4) Do: ALT-F2 Run: emerald -replace

5) Right-click the desktop, choose "Configure Desktop > Multiple Desktops" and set it back to only show "Desktop 1".

6) Then with your KMenu > Settings > Advanced Desktop Effects Settings, Click the "General Options ICON" go to "Desktop Size" and set Horizontal Virtual Size to "4", while leaving "Virtual Size" and "Number of Desktops" set to "1"
...and while you are there enable your Cube etc... Now you should have a working Cube, spin it with Ctrl+Alt <direction arrows>

(ps: if window borders give you trouble, open Terminal & execute: **emerald -replace** then leave the Terminal OPEN and log-out and back in, this worked for me)

(pps: sorry for the double post, but I was excited I got this running and wanted to share the method I used)
good luck I hope this works for you

---

### Post by treydee211 on 2007-10-23
I finally got it working I have the Infamus Cubed desktop. It actually a lil bit of tips from everybody's post. The only problem now is working around the window decorator emerald any idea on where I can download themes for emerald? Or where and how can I get some good themes for Kubuntu Gutsy? Thanks guys.

---

### Post by zachthejones on 2007-10-23
Hey guys, I had some similar problems getting compiz-Fusion up and running in Kubuntu and I snagged some pretty good help in the Kubuntu forum. check out my own chaotic adventure in KDE Compiz [here]("http://kubuntuforums.net/forums/index.php?topic=3087758.0").

My main advice to anyone wanting to run Compiz-Fusion in KDE is to make sure you've got the hardware and then make sure you've gotten all the correct stuff installed - especially getting "kde-compiz".

It seems to me that the KDE compatibility of Compiz-Fusion needs some more work...but it's definitely worth it if you get it up and running!

---

### Post by jonray74 on 2007-10-24
Hi Caffeine_Junky,

Thanks for the guide. Unfortunately it's still a no go for me. :( I tried running the guide you posted but when I did the $ Compiz --replace and Emerald -- replace, I got that same error message saying cannot find Screen 0:0 or something, (i'll try to post the errors in detail later), also after the "emerald --replace", I got a GLIB error message.

darn, it's really frustrating :mad:

John

---

### Post by philcz on 2007-11-21
By using the instructions post earlier, I got my #D stuff working in KDE. Thanks

---

### Post by sergiom99 on 2007-12-22
> **Caffeine_Junky said:**
> I got compiz-fusion running on Kubuntu Gutsy (cube and all) by doing the following:

1) Install your 3D video drivers (if you haven't already)

2) Install these packages either from Adept or Terminal:
sudo apt-get install compiz compiz-kde compizconfig-settings-manager emerald

3) Do: ALT-F2 Run: compiz -replace

4) Do: ALT-F2 Run: emerald -replace

5) Right-click the desktop, choose "Configure Desktop > Multiple Desktops" and set it back to only show "Desktop 1".

6) Then with your KMenu > Settings > Advanced Desktop Effects Settings, Click the "General Options ICON" go to "Desktop Size" and set Horizontal Virtual Size to "4", while leaving "Virtual Size" and "Number of Desktops" set to "1"
...and while you are there enable your Cube etc... Now you should have a working Cube, spin it with Ctrl+Alt <direction arrows>

(ps: if window borders give you trouble, open Terminal & execute: **emerald -replace** then leave the Terminal OPEN and log-out and back in, this worked for me)

(pps: sorry for the double post, but I was excited I got this running and wanted to share the method I used)
good luck I hope this works for you

Caffeine, I did as you told, but I only have the screens in a flat strip in the middle of the screen.
I have a HP DV6646us, Nvidia working ok.
This is what I mean>
 [[IMG]http://img130.imagevenue.com/loc473/th_69883_instant8nea3_122_473lo.jpg[/IMG]](http://img130.imagevenue.com/img.php?image=69883_instant8nea3_122_473lo.jpg)

---

### Post by sergiom99 on 2007-12-28
any ideas on this one?

Thanks!

---

### Post by applegrew on 2008-03-08
A quick add-on remark.

No need to install compiz on kde. compiz-kde is enough. hence install

```
sudo aptitude install compiz-kde compizconfig-settings-manager emerald
```

---

### Post by buckeyered80 on 2008-03-09
After installing compiz-kde and compiz-config-settings-manager, I run compiz --replace and I get this:

```
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

```

I know installing xserver-xgl will fix this.  But, it runs terribly, so I am wondering if anyone knows another way to fix this?

---

