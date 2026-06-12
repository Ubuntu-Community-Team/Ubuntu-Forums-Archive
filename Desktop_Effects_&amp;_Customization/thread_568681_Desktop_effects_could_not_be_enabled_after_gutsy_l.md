---
title: "Desktop effects could not be enabled after gutsy linux-restricted-modules update"
date: 2007-10-06
forum: Desktop Effects &amp; Customization
---

### Post by martynp on 2007-10-06
Hi All,

So the linux-restricted-modules were greyed out last night so had to work with bad graphics for a while. Got up this morning to find the update going through ok. Rebooted and re-enable restricted drivers but am getting 'Desktop Effects Cannot Be Enabled' error on selecting ANY level of desktop effects from the Appearance>Visual Effects tab.

Is anyone else seeing this or am I missing something?

I'm on Nvidia GeForce 6 series and all worked ok up til last night

Many Thanks

---

### Post by Forlong on 2007-10-06
Post the output of ```
compiz
``` in a terminal as well as your xorg.conf

---

### Post by Lord Illidan on 2007-10-06
Or..```
compiz --replace
```

EDIT : NOT NECCESSARY

---

### Post by Forlong on 2007-10-06
That's not necessary anymore with Gutsy.

---

### Post by Lord Illidan on 2007-10-06
>  		That's not necessary anymore with Gutsy.

Hmm, thanks for the input. Wasn't aware of that. You're quite right, when did this happen?

---

### Post by Forlong on 2007-10-06
> **Lord Illidan said:**
> when did this happen?
Some weeks ago with the overhaul of the compiz-wrapper.

---

### Post by hyperair on 2007-10-06
I think I know what went wrong with martynp's computer. The new kernel installed, and then he rebooted, but without the matching linux-restricted-modules package. Hence, the nvidia kernel module couldn't be loaded, and he landed up seeing displayconfig-gtk. At that point he probably selected the nv driver, and went into his desktop. Now that linux-restricted-modules is back, he hasn't changed back to the nvidia driver yet. So, Compiz refuses to run.

Solution: Open System->Administration->Screen and Graphics, and select the old driver you were using (i.e. "nvidia"). Or, just open your /etc/X11/xorg.conf, and in your "Device" section, change the driver from "nv" to "nvidia".

---

### Post by titanman128 on 2007-10-06
I have the same problem. I have the nvidia driver enabled but I still can't enable Compiz. From a terminal it says XGL not present. In addition, when I try and open Screens and Graphics all I get is a crash report and it won't open. I am running Gutsy Beta and did all the updated this morning that fixed the restricted module. Can someone point me in the right direction? Do I need to edit xorg.conf file?

---

### Post by Acoustyk on 2007-10-10
I have the same problem except with a radeon mobility x series.  I know im capable of running it because I did before...  any idea on the driver for radeon?

btw I have three xorg.conf files: xorg.conf.1 xor.conf.2 and xorg.conf.3 is that the way its supposed to be?!  If so which one would I edit?

---

### Post by hyperair on 2007-10-10
I'm not very sure, but if you were using restricted drivers, you could just launch the Restricted Drivers Manager and enable it. If it's already enabled, disable and reenable it.

---

### Post by neodorian on 2007-10-11
I tried disabling and re-enabling drivers.  Still I get the same thing.  I'm using a geforce 5200 go in a laptop.  It worked reasonably well on feisty but since I installed gutsy it won't let me enable desktop effects at all.

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0328 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```

It's weird that it blames a lack of memory because it should allow me to run some semblance of desktop effects even if not fully.  It used to work fine with beryl.

---

### Post by grinchman on 2007-10-11
> **martynp said:**
> Hi All,

So the linux-restricted-modules were greyed out last night so had to work with bad graphics for a while. Got up this morning to find the update going through ok. Rebooted and re-enable restricted drivers but am getting 'Desktop Effects Cannot Be Enabled' error on selecting ANY level of desktop effects from the Appearance>Visual Effects tab.

Is anyone else seeing this or am I missing something?

I'm on Nvidia GeForce 6 series and all worked ok up til last night

Many Thanks

Check under SYSTEM > ADMINISTRATION > SCREENS AND GRAPHICS

Mine had the wrong monitor and resolution and changing it fixed this problem for me.

---

### Post by Forlong on 2007-10-12
> **neodorian said:**
> I tried disabling and re-enabling drivers.  Still I get the same thing.  I'm using a geforce 5200 go in a laptop.  It worked reasonably well on feisty but since I installed gutsy it won't let me enable desktop effects at all.
[...]
It's weird that it blames a lack of memory because it should allow me to run some semblance of desktop effects even if not fully.  It used to work fine with beryl.
That's OK. Ubuntu has to make sure people with low-key graphics card do not run Compiz by default (if you want to know more, see [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710))
So if you want to run Compiz now, you have to tell it: »I don't care if it's not wise, do as I say«
```
SKIP_CHECKS=yes compiz
```

---

### Post by andref on 2007-10-12
hi all,
 i use Ubuntu Gutsy with compiz-fusion without any problem, but yesterday, during the configuration of one plug-in all desktop effects crash and now i could not enable it. if i go to Sistem >> Preference and i try to enable effects, a pop-up say, "Desktop effects could not be enable"

what i can do?

thanks

---

### Post by Forlong on 2007-10-12
andref, what output gives ```
compiz
``` in a terminal? Maybe your graphics card/driver has been blacklisted too.

---

### Post by andref on 2007-10-12
this is my compiz's output 
```
andrea@andrea-home:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
andrea@andrea-home:~$ 

```

but the strange thing is that yesterday morning all desktop effects worked well!!

ah, i tried to uninstall compiz, but i had the same problem, Desktop effects could not...

what i can do?

thanks

---

### Post by hyperair on 2007-10-12
Try compiz --replace, and post the output here again.

---

### Post by andref on 2007-10-12
this is the output
```
andrea@andrea-home:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
andrea@andrea-home:~$ 

```
but after compiz --replace all windows' border disappear... and i've to type metacity --replace...

thanks

---

### Post by 900se on 2007-10-12
This worked for me on an nvidia card (restricted driver):

[http://ubuntuforums.org/showthread.php?t=563809](http://ubuntuforums.org/showthread.php?t=563809)

---

### Post by Forlong on 2007-10-12
andref, if you need to run 'compiz --replace' you do not have Gutsy's packages installed.
Please post the output of ```
dpkg -l | grep compiz
```

---

### Post by andref on 2007-10-12
well, 
this is the output
```
andrea@andrea-home:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
rc  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
rc  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
andrea@andrea-home:~$ 
```

what's the problem?

thanks!

---

### Post by Little_Tiger on 2007-10-12
I've also had this problem.
I was working with Feisty and everything worked. But when I update (upgrade) to Gusty,
I've got that problem. Desktop effect not ...

So what I did to solve this was, by doing a clean installation. And everything worked just fine
(btw I'm on a macbook 1st generation)

---

### Post by Forlong on 2007-10-12
> **andref said:**
> this is the output

what's the problem?

According to this, there's nothing wrong but for whatever reason you are not using the compiz-wrapper from Gutsy.

First, let's get rid of old configs:
```
sudo dpkg --purge emerald gnome-compiz-manager libemeraldengine0 libgnome-compiz-manager0
```

Then try this:
```
sudo rm /usr/bin/compiz && sudo apt-get install --reinstall compiz-core
```

Afterwards, post the output of
```
compiz
```

---

### Post by andref on 2007-10-12
```
andrea@andrea-home:/media/MEMORY LG$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
andrea@andrea-home:/media/MEMORY LG$ 

```

---

### Post by Forlong on 2007-10-12
edit: Try this first:
```
sudo rm /usr/bin/compiz.real && sudo apt-get install --reinstall compiz-core
```

You don't have any third party repository enabled, right?

---

### Post by andref on 2007-10-12
[here the link!]("http://www.pastebin.org/4707")

thanks

---

### Post by Forlong on 2007-10-12
Sorry, I edited my last posting posting. Please see above.

But see, here's what the script you posted says:
```
COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
```
There must be a reason, why it doesn't use it.

Did you upgrade from Feisty to Gutsy? If so, did you have Compiz Fusion installed and how did you do that?

---

### Post by andref on 2007-10-12
mmm, i don't understand...

I've had upgrade from feisty, but some months ago!! and compiz-fusion was work well
but now i can't enable any effects...

---

### Post by neodorian on 2007-10-12
> **Forlong said:**
> That's OK. Ubuntu has to make sure people with low-key graphics card do not run Compiz by default (if you want to know more, see [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710))
So if you want to run Compiz now, you have to tell it: »I don't care if it's not wise, do as I say«
```
SKIP_CHECKS=yes compiz
```

Where do I add this line?

edit:  figured it out but now when I try to enable it, it still just waits a long time and tells me that I can't enable desktop effects.  I tried running compiz from terminal and it appeared to get stuck in a loop of trying to enable it and failing.  I eventually had to reboot after letting it loop like that for 15 minutes.

---

### Post by houms on 2007-10-13
> I tried disabling and re-enabling drivers. Still I get the same thing. I'm using a geforce 5200 go in a laptop. It worked reasonably well on feisty but since I installed gutsy it won't let me enable desktop effects at all.

Code:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0328 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

It's weird that it blames a lack of memory because it should allow me to run some semblance of desktop effects even if not fully. It used to work fine with beryl.

I had this problem too I have a laptop (dell inspiron 8600) with a nvidia 5200 and I kept getting the same error... My solution which seems to work like a charm was to edit the 

/usr/bin/compiz file

I commented out the following line

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
[COLOR="Red"]#[/COLOR]NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

It seems like compiz was written to check for this memory thershold of 64MB, at least for this video card. commenting it out worked.. Now I just add compiz --replace --inderect-rendering to the sessions so that it starts up during login, and it works just like it did for me in feisty...(Note: the --indirect-rendering option is to avoid borderless windows which I always have a problem with with this video card... Though I have not tried I may also modify this option in the /usr/bin/compiz file so that it is enabled by default...

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

[COLOR="Red"]# No indirect by default
INDIRECT="no"[/COLOR]

# Set to yes to enable verbose
VERBOSE="yes"
 Now when I go to pref>>app.>>visual effects, I can change from none, normal, extra, and even custom.. (note: i got custom by install compizconfig setting manager and enabling certain plugins I wanted. Let me know if ya need any help.

---

### Post by GoPool on 2007-10-14
I was having the same problem with destop effects not starting, even though I had it running under feisty. It seems that the compiz programmers were a little conservative in the hardware check compiz had to go through before starting. This meant that a lot of not so old computer that were able to run compiz under feisty fawn were being flagged, and desktop effects were not being enabled using the appearance tab. However, if you were to run ```
skip_CHECK=yes compiz
``` in a terminal window, compiz works just fine. But you must leave that terminal open for the entire session, and enable compiz manually ever time you log in.

The way I got around this was the add the "ship_CHECK=yes" to my compiz-manager file at ```
/etc/xdg/compiz/compiz-manager
```

Now compiz works geat. I hope this help people having problems.

---

### Post by saulysw on 2007-10-18
Hi all!

I'm still pretty new to Ubuntu (but not computers in general). I upgraded from 7.04 -> 7.10 last night. Actually, I let it run overnight, when I looked at my PC next the screen was black and nothing I did could get it to display an image so I restarted it. Anyway, 7.10 seems to come up fine, so I'm assuming it's ok. Except, I can't get the desktop effects to work of course.

```
saul@saul-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

I have an NVidia 8600 GT. Looking in the System : Administration : Screens and Graphics, it's using the "nv - nVidia Riva blah blah" driver. If I try the driver simply called "nvidia", nothing happens and re-opening the Screens and Graphics shows it back to original driver. If I select "nvidia" then press the test button the screen goes black for a bit then comes back with the Screens and Graphics window closed. 

What's curious to me is that when the machine first started, it looks like it starts to load different icons and menu effects, but these quickly revert back to the older style. 

Anyone got any suggestions?

I also tried this, because I am a thrill seeker...

```
saul@saul-desktop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by houms on 2007-10-18
saulysw,

looking at the compiz --replace output... it looks like you don't have the driver installed for your video card or the video card you have is not supported... Whats the make and model of your video card...?

---

### Post by Drevor on 2007-10-18
Hey ive got a fresh install and I don't seem to be able to enable compiz either
```
~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f9 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)
``` any ideas?:confused:

---

### Post by Amaranth on 2007-10-18
You can't use Xinerama with nvidia. Use Twinview instead.

---

### Post by Drevor on 2007-10-18
Well ... I didn't exactly tell it to do the one nor the other ... all I did was to allow it to use the restricted drivers and set up my displays via system->admin->screens :???:
thus...> Use Twinview instead....how?

//edit
ah yes ... gksu nvidia-settings

---

### Post by kombucha on 2007-10-19
I'm in precisely the same spot as Drevor - Xinerama works for me, but while using it Compiz doesn't with a similar error:
> ...Checking for Xgl: not present.
Starting emerald
Segmentation fault (core dumped)

Discussing here as well: [http://ubuntuforums.org/showthread.php?p=3566309#post3566309](http://ubuntuforums.org/showthread.php?p=3566309#post3566309)

Thanks in advance :)

---

### Post by DrewBoo on 2007-10-19
> **houms said:**
> 
# Set to 262144 to require 256MB
[COLOR="Red"]#[/COLOR]NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default


Great sleuthing, houms!

That one quoted change got things working for me.

---

### Post by flx2000 on 2007-10-19
As like as GoPool said, I resolved adding SKIP_CHECKS="yes" at the end of the file /etc/xdg/compiz/compiz-manager

Then I applied the Extra visual effects you found in the System menu.

I'm using an integrated Intel 965 with the i810 driver module.

---

### Post by jrny99 on 2007-10-20
maybe someone can help me with this error, i upgraded to gutsy while it was still beta, when i try to enable visual effects it says Desktop effects could not be enabled


ed@ed-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0343 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2048x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 337 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)
ed@ed-desktop:~$

---

### Post by nelio2k on 2007-10-20
I foudn that you could sudo gedit /usr/bin/compiz, and change the memory from 64MB to 32 by entering 32768 instead of the 65536. That's only if you have a 32MB video card though.

Now I'm running into some more errors, that I've not seen before:

/usr/bin/gtk-window-decorator: /home/neilhuang/mono-1.2.5/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
/usr/bin/metacity: /home/neilhuang/mono-1.2.5/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

EDIT: Nevermind. It worked for me, actually. I just had to enable desktop effects from the system -> preference -> appearance menu, instead of typing compiz in the terminal.

Thanks everyone!

> **Forlong said:**
> That's OK. Ubuntu has to make sure people with low-key graphics card do not run Compiz by default (if you want to know more, see [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710))
So if you want to run Compiz now, you have to tell it: »I don't care if it's not wise, do as I say«
```
SKIP_CHECKS=yes compiz
```

---

### Post by bootsbradford on 2007-10-20
I am so frustrated! :mad:

Compiz-fusion was running fine following my upgrade to Gutsy. I have an ATI Radeon X600 card and I was running the open source 'ati' driver. I had the occasional freeze - nothing as bad as under Feisty, but I thought I would try to restricted driver.

I installed xserver-xgl and the restricted driver. I then rebooted **but was faced simply with a black screen and nothing else.**

Using the recovery mode, I reconfigured xorg using:

```
dpkg-reconfigure xserver-xorg
```

I assumed that, at the very least, everything would now be back to how it was before, since my xorg settings were the same as before I installed the restricted driver. Oh no...

Now when I go to reenable Compiz-Fusion I am told **"Desktop Effects could not be enabled"**. 

If I type in compiz --replace into terminal, I am given this output:

> mark@mark-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:3e50 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Nothing ever seems to go smoothly with Ubuntu. Can anyone help me sort this out?

---

### Post by bootsbradford on 2007-10-20
Solution was simple in the end. For those wanting to use Desktop Effects with open source drivers and AIGLX, you need to make sure that flgrx is properly removed. 

```
sudo apt-get remove xorg-driver-fglrx
``` will do the trick.

---

### Post by Kver on 2007-10-23
I've tried everything in this thread and Compiz still won't kick in; Upgraded from feisty, this is my error:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0328 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
[: 352: -lt: argument expected
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

When I enable through the appearance menu, it will grey out every option, then fall back to metacity, and after about a minute, flick into metacity again...

---

### Post by sporto on 2007-10-24
> **Drevor said:**
> Well ... I didn't exactly tell it to do the one nor the other ... all I did was to allow it to use the restricted drivers and set up my displays via system->admin->screens :???:
thus......how?

//edit
ah yes ... gksu nvidia-settings

Same problem here, fresh Gutsy install and same error. Is there any disadvantage in disabling the default enabled xinerama and enabling twinview?

---

### Post by dmgerbino on 2007-11-02
I am running Ubuntu 7.10 (Gutsy) on a Toshiba Tecra M2-S430. My video card is the NVIDIA NV34M [GeForce FX Go5200 32M/64M]. My video card has 32M.

Compiz worked with 7.04. It did not work with the default install of 7.10.

After reading this thread I realized that the failure point was the memory check in the config file. The config file was looking for 64MB and I only have 32MB.

so all I had to do was the following:
[LIST]
[*]Edit the config file with this command: sudo gedit /usr/bin/compiz
[*]Then edit the file with this: 
# NVIDIA_MEMORY="65536" # 64MB [COLOR=Red]==> comment out the 64MB line[/COLOR]
NVIDIA_MEMORY="32768" # 32MB [COLOR=Red]==> add the 32MB line[/COLOR][/LIST][COLOR=Red][COLOR=Black]Now when I turn on Compiz it works.[/COLOR]


[COLOR=Black]Please note that I did not have to use the skip check command to get it to work.[/COLOR]
[/COLOR]

---

### Post by hyperair on 2007-11-02
Well of course! It was an either-or thing. You either use the skip-checks method, or you edit the amount of memory they look for. One thing I don't get though. I thought all the more recent GPUs (after nVidia Geforce 4 MX) had >= 64MB VRAM. Looks like I was wrong there eh.

---

### Post by houms on 2007-11-03
> **DrewBoo said:**
> Great sleuthing, houms!

That one quoted change got things working for me.

No problem...Glad it helped someone....

---

