---
title: "desktop effects could not be enabled"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Lee7 on 2007-10-19
I have an ATI X1950 PRO graphics card and have enabled restricted drivers for this card.

Direct rendering is enabled when I check in Terminal. I heard there was a bug in compiz that returned this error, but I'm not sure whether it is fixed or related to my card.

Could somebody tell me how to fix this problem?

---

### Post by lazyart on 2007-10-19
type 'compiz' from the terminal and post the output.  that will help troubleshoot.

---

### Post by Sanjuro82 on 2007-10-20
I have the same problem.  Except that I have a ATI Radeon X700 Pro as my video card.  

Here's my 'compiz' output:


```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5e4b (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by IanWatson on 2007-10-20
Ditto, with ATI All-in-Wonder 2006.

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

---

### Post by Lee7 on 2007-10-20
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by afterburn on 2007-10-20
I also have an x1950 PRO and the exact same thing.
Fist it started with
"the composite extension is not available"
and then I commented the line out in xorg.conf like this
```

Section "Extensions"
#	Option		"Composite"	"0"
EndSection

```

And now the message is "Desktop effects could not be enabled"

by the way; this is a clean install of 7.10 with nothing but the ati restricted driver installed. So nothing was done to mess up the system, this is how it came out of the box :(

---

### Post by Lee7 on 2007-10-20
That's exactly what I've done so far afterburn.

---

### Post by afterburn on 2007-10-20
Well, lets hope we find someone how got this to work with the ATI drivers :(

I've changed my xorg.conf back the way it was, because i'm hoping this can be solved without the console or anything of the sort. At least this is what i was expecting from the new release of ubuntu, but lets see if we can live up that dream ;)

---

### Post by Faud on 2007-10-20
.

---

### Post by Amaranth on 2007-10-20
The fglrx driver does not support texture_from_pixmap and thus cannot run compiz. You have to use the open source driver (if you can) or use Xgl. Install the xserver-xgl package, logout, and when you login it'll be running and compiz should automatically start (unless you  turned it off).

---

### Post by afterburn on 2007-10-20
Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

---

### Post by Masozi Mbali on 2007-10-20
I have a similiar problem. nVidia card however, GeForce 2 MX. nVidia propritarry driver. It worked on Red Hat Fedora. It does texture_from_pixmap. I have not gaven XGL a try yet, but compiz output from Terminal:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```
If post is not correct, sorry. My first post.

---

### Post by gamx on 2007-10-20
I have a similar problem here. My Dell Latitude C640 has a Ati Radeon Mobility 7500. Compiz was working fine with Feisty but after upgrading to Gutsy, it is not working. When I type compiz it reads like this:

compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c57 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

Any ideas about what might be going on? Thanks

---

### Post by Lee7 on 2007-10-20
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.
That fixed it. Thanks to both of you. :)

---

### Post by Masozi Mbali on 2007-10-20
gamx: Your problem is in the error
> Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
You could try at a lower resolution. However that will look blurry.

I also realised that my problem is
> Less than 65536kb of memory and nVidia
Still. This doesn't explain why _new compiz refuses to work while older versions worked fine_. Albiet a bit slow with a lot of windows. May be compiz hardware requirements were raised so people would not complain of slowness?

---

### Post by gamx on 2007-10-20
Thanks for the advice. I found a quick and dirty fix for my problem with textures. It is here

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

---

### Post by kev82 on 2007-10-20
I did this, installed XGL and that got compiz working.

However after logging out and in, my keyboard layout was gone (went to us english from icelandic) - I changed that and seems to be working alright, but thought it was strange.


Also, I have a dual monitor setup, and before installing XGL I had two separate monitors to pick from in screens and graphics under administration. However now I have two monitors there, but I can only use one, and that one is 3200x1200 (my both monitors combined).

I want to keep my monitors separate, I don't like my panels extending to both the monitors, and new windows being displayed in the middle of the screen - on both monitors.

How do I fix this so it works like I want it to work?

---

### Post by okst666 on 2007-10-20
lol, you have it the way I want it to have..I want to have one big desktop...
My Desktop is just mirrored and I cant bring it to extend to the right

---

### Post by gorge on 2007-10-20
Installing the xserver-xgl package definitely worked, NOW I'M ENJOYING COMPIZ!!!:guitar:

---

### Post by kev82 on 2007-10-20
> **okst666 said:**
> lol, you have it the way I want it to have..I want to have one big desktop...
My Desktop is just mirrored and I cant bring it to extend to the right

Yeah I don't want it mirrored, but I want it to be 2x 1600x1200 screens, not just one big 3200x1200... It was like that before I installed xgl, but now I can't change it back..

---

### Post by Smoothcrm7 on 2007-10-21
This is what I get when i type compiz in terminal
santa rosa chipset dedicated video card with 4 gigs of ram


Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by kev82 on 2007-10-21
> **Smoothcrm7 said:**
> This is what I get when i type compiz in terminal
santa rosa chipset dedicated video card with 4 gigs of ram


Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

Your video card is blacklisted because it behaves weirdly with compiz.

You can override it, but you'll probably get that aforementioned "weird" behaviour then :)

---

### Post by Mithrandir06 on 2007-10-21
mithrandir@mithrandir-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

this is what i get.  I have installed the xserver-xgl and enabled my restricted drivers and installed my ati drivers through envy.  After installing the xserver-xgl package my graphics is running really slow and i am still getting desktop effects could noot be enabled.

---

### Post by Phyxsius on 2007-10-21
> **Mithrandir06 said:**
> mithrandir@mithrandir-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

this is what i get.  I have installed the xserver-xgl and enabled my restricted drivers and installed my ati drivers through envy.  After installing the xserver-xgl package my graphics is running really slow and i am still getting desktop effects could noot be enabled.

I'm having the exact same problem. I hope someone knows how to fix this. :(

I should also mention that if I try and run 'flgrxinfo' at this point it restarts my session.

---

### Post by Tamale on 2007-10-21
this might seem like an off-topic post, but why was gutsy pushed out with such a huge mistake?

why isn't there some sort of clue in the error message that points users to the xgl package if compiz can't start and you have an ATI card?

i really thought gutsy would get things right and working "out of the box" :[

---

### Post by Jeanpaul145 on 2007-10-21
> **Tamale said:**
> this might seem like an off-topic post, but why was gutsy pushed out with such a huge mistake?

why isn't there some sort of clue in the error message that points users to the xgl package if compiz can't start and you have an ATI card?

i really thought gutsy would get things right and working "out of the box" :[

On one hand, you're absolutely right: things are expected to work "out of the box".

On the other hand, there were more pressing bugs to take care of before the release of Gutsy, some of which aren't even fixed yet (for details, see launchpad). Next to that, Compiz fusion still **is** beta software, although for most people it works well enough for regular use, i.e. you shouldn't be surprised to encounter such half-assed messages, and you shouln't be surprised to find actual bugs, either.
What matters is not that you find bugs - since you can find those in "finished" software (what an oxymoron eh?) as well - but when those bugs are resolved.:popcorn:

---

### Post by Lord_Dicranius on 2007-10-22
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.
This worked for me! :)

---

### Post by xxxYURAxxx on 2007-10-22
intel 965 video card
compiz not work

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by michael37 on 2007-10-22
> **Lee7 said:**
> I have an ATI X1950 PRO graphics card and have enabled restricted drivers for this card.

Direct rendering is enabled when I check in Terminal. I heard there was a bug in compiz that returned this error, but I'm not sure whether it is fixed or related to my card.

Could somebody tell me how to fix this problem?

For ATI graphics cards only, please go to [thread=569654]thread dedicated to ATI restricted driver[/thread].

---

### Post by michael37 on 2007-10-22
> **Mithrandir06 said:**
> mithrandir@mithrandir-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

this is what i get.  I have installed the xserver-xgl and enabled my restricted drivers and installed my ati drivers through envy.  After installing the xserver-xgl package my graphics is running really slow and i am still getting desktop effects could noot be enabled.

Your Xgl doesn't start right.  It should provide a screen :1 if it is configured correctly.  See for a ATI-only link above.

---

### Post by michael37 on 2007-10-22
> **Tamale said:**
> this might seem like an off-topic post, but why was gutsy pushed out with such a huge mistake?

why isn't there some sort of clue in the error message that points users to the xgl package if compiz can't start and you have an ATI card?

i really thought gutsy would get things right and working "out of the box" :[

ATI cards with their binary-only drivers are hard to get working.  90% of troubleshooting Compiz, Xgl and/or Gutsy is not really that -- it's about troubleshooting this closed source driver.  Life would be VERY VERY different had ATI open sourced it.  If you are unhappy with your ATI card, return it and buy an Nvidia or Intel card.

---

### Post by bbt5001 on 2007-10-24
Here's my twist on the problem.

I installed Ubuntu for the first time yesterday.  Rebooted from the hard drive. Updated the recommended packages, added a few utilities. One of my colleagues recommended the desktop effects, so a right-click on the desktop got me to the Change Desktop Background option. The visual effects tab gave me 3 options, I turned on effects -- very cool.

I rebooted the system, now visual effects can not be selected. Oh, and there are 4 options, not 3 ("Custom") was added. Can't even select "Normal".

Found this thread, then installed xserver-glx.  Restarted the window manager, the screen goes blank then returns me to the login screen. After a try or two I select the failsafe gnome session, remove the xserver-glx package, restart the window manager. Back to where I was.

I then booted from the install disk. Whaddya know: I can run desktop effects if I boot off of the 7.10 install CD, but not if I boot the system upgraded since then.

[INDENT]compiz reports:
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02. 0300: 0086:2562 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity[/INDENT]

My video card is an Intel 845 integrated into the motherboard (Dell Dimension 2100)

Any suggestions?

---

### Post by bbt5001 on 2007-10-24
*[INDENT]Here's my twist on the problem.[/INDENT]*

OK, this was my fault. 

This Dell had on-board graphics but I also installed an nvidia PCI video card. Trouble was that the Dell refused to acknowledge the existence of the second video card, so I took it out (along with a fax/modem card). Installing the nvidia driver somehow messed up the normal configuration. Removing the nvidia system didn't make matters better.

My solution: since I only installed this yesterday I just went ahead and re-installed from scratch. Coming from the Gentoo environment, this installer is an absolute joy to use.

Since then I broke the configuration again, but was able to fix things without a complete reinstall. What fun!

---

### Post by michael37 on 2007-10-24
> **bbt5001 said:**
> *[INDENT]Here's my twist on the problem.[/INDENT]*

OK, this was my fault. 

This Dell had on-board graphics but I also installed an nvidia PCI video card. Trouble was that the Dell refused to acknowledge the existence of the second video card, so I took it out (along with a fax/modem card). Installing the nvidia driver somehow messed up the normal configuration. Removing the nvidia system didn't make matters better.

My solution: since I only installed this yesterday I just went ahead and re-installed from scratch. Coming from the Gentoo environment, this installer is an absolute joy to use.

Since then I broke the configuration again, but was able to fix things without a complete reinstall. What fun!

Gentoo users tend to break Ubuntu since they try to overwrite its powerful auto-config scripts :-)

Not sure why your Nvidia PCI card is not working, but glad your Intel card is working.

---

### Post by masry4life on 2007-10-25
I FOUND IT!!
Well not really but I found something that might really help.  After a whole month of trying to get compiz to work with my ati radeon card I finally got it to work today!

OK so here it is for all you ati users:
   1. This website will help you out greatly.          
                [http://ubuntuforums.org/showthread.php?t=591066](http://ubuntuforums.org/showthread.php?t=591066)
   2. After you do everything it prob still wont work so:
   3. Run 'fglrx' in a terminal
   4. if your card is recognized great!
   5. Run 'glxinfo | grep direct'
   6. If you get 'direct rendering: yes' great!
   7. finally put this into the terminal:
             echo SKIP_CHECKS="yes" >> ~/.config/compiz/compiz-manager
   9. Now go back to System-->preferences-->Appearance clcik on 'visual effects' tab and click on one of the options you prefer.
   
    8. If it works: Enjoy!
          if it doesn't then I am very sorry but keep trying and you'll get it sooner or later.

Good Luck and let me know if it works

---

### Post by michael37 on 2007-10-25
> **masry4life said:**
> I FOUND IT!!
Well not really but I found something that might really help.  After a whole month of trying to get compiz to work with my ati radeon card I finally got it to work today!

OK so here it is for all you ati users:
   1. This website will help you out greatly.          
                [http://ubuntuforums.org/showthread.php?t=591066](http://ubuntuforums.org/showthread.php?t=591066)
   2. After you do everything it prob still wont work so:
   3. Run 'fglrx' in a terminal
   4. if your card is recognized great!
   5. Run 'glxinfo | grep direct'
   6. If you get 'direct rendering: yes' great!
   7. finally put this into the terminal:
             echo SKIP_CHECKS="yes" >> ~/.config/compiz/compiz-manager
   9. Now go back to System-->preferences-->Appearance clcik on 'visual effects' tab and click on one of the options you prefer.
   
    8. If it works: Enjoy!
          if it doesn't then I am very sorry but keep trying and you'll get it sooner or later.

Good Luck and let me know if it works

If it doesn't, you are among majority for whom the build of special just-released drivers does not work.

An more workable alternative which doesn't involve any building is decribed [thread=569654]here[/thread]

---

### Post by lylepratt on 2007-10-29
I was able to fix (or bypass) the GL_MAX_TEXTURE_SIZE error by adding this to the beginning of my /usr/bin/compiz file:

SKIP_CHECKS=yes


Doing this allowed me to successfully start compiz with my Radeon IGP320m card. Both "Normal" and "Extra" settings work for me without any errors so far.

You can run compiz from the command line using this command to test:

SKIP_CHECKS=yes compiz



Hope this helps some of you. I have been trying to get 3d acceleration and compiz working on my Emachines m5312 laptop for months now and finally succeeded today.

-Lyle

---

### Post by lylepratt on 2007-10-29
Also, if anyone doesn't know this already. To get the 3d desktop rotation and other effects enabled in compiz you have to install the compizconfig-settings-manager package.

Do this by typing:
sudo apt-get install compizconfig-settings-manager


This is a really handy tool that gives you total control of the effects enabled on your desktop. For example: I like the 3d desktop rotation effect, but hate the wobbly windows. You can enable one and disable the other using this handy tool. 

In my opinion, it should be pre-installed in gutsy.

---

### Post by Kaji on 2007-10-29
Here is my output from running compiz in terminal:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 350 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

```

I'm still pretty new to linux, any help for solving this?

---

### Post by DiverseNerd on 2007-10-29
I have ATI Radeon Xpress 200  graphics and when I try to enable visual effects, all I get is a message that says "The composite extension is not available" When I typed "compiz" into the terminal, it said 
"/usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager."
I tried the xserver-xgl thing twice and it still wont run. Any thoughts?

---

### Post by madhatter563 on 2007-10-29
Hello, I am also trying to get compiz to work, and this is what i get

```
trinity@Trinity:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

I INSTALLED the xserver-xgl package as requested, and restarted, it gave the message that it would automatically start, etc, so i know it is installed.  Im not sure where to troubleshoot from here.  Oh by the way, I am using a thinkpad t23 which uses the _SuperSavage IX/C SDR by IBM_.  Perhaps this is just too old to run it correctly.  Thanks for any help!

---

### Post by divadotrebla on 2007-10-30
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

Thanks, this worked to me.

---

### Post by booyip on 2007-10-30
> **divadotrebla said:**
> Thanks, this worked to me.

Me too (Radeon 9550).  Thanks.

:)

---

### Post by voidreality on 2007-10-31
Pretty much a clean Ubuntu 7.10 Desktop Edition 32-bit installation from LiveCD. Got an older Nvidia Legacy graphics card.. can't enable Ubuntu's new desktop effects in the Appearances control panel. When I type compiz in a terminal I get this:

```
owner@Emily:~$ compiz

Checking for Xgl: present. 

Checking for nVidia: not present. 

Checking for Xgl: present. 

Enabling Xgl with nVidia drivers...

Starting gtk-window-decorator

/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing

/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0

/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0


```

So far I've enabled the Nvidia driver in the restricted drivers control panel (nvidia-glx-legacy), and I've installed xserver-xorg as it is said to do so in this topic. Also can't get the resolution higher than 640x480 which is really annoying. My guess is the Nvidia drivers aren't working properly. Also on the no manageable screens part of the errors, I think that's because I'm not using a directly connected monitor. I'm using remote desktop from another machine to access this Ubuntu machine. Help please?

---

### Post by Blurple on 2007-11-01
> SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: /usr/bin/glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


I get no white list driver found... I have tried to install ATI many different times.  this happend after I allowed it as a restricted driver.  thanks for any help

I am using a 9600

Non of the fixes so far have worked for me thank you in advance for any suggestions

---

### Post by zzfive on 2007-11-01
im having a similar issue 

here is my output

> /usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.



suggestions would be great

---

### Post by masry4life on 2007-11-02
zzfive try using:
compiz --replace

---

### Post by paladin_knight on 2007-11-03
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

I faced the same problem. It warning was about "Could not launch menu item : failed to execute child process "desktop effects"( no such a file or directory)". But, I had already xserver-xgl installed on my Ubuntu. I just upgraded from Feisty anyway. Anyone knows how to solve this. I really want to see the cube and etc on my Ubuntu. I had also Mandriva running well on my PC with its cube anyway.:KS:KS

---

### Post by dondolo on 2007-11-03
hi to all, i'm running 64bit edition of gutsy with an 8800 gts so,i got lot of problems with compiz:

 when i write > compiz --repleace i receive back 

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'


if i try to download and install the unofficial plugin...

> E: /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070728~jbs0_amd64.deb: {try yo overwrite}tentata sovrascrittura di `/usr/lib/compiz/libwidget.so',that is in compiz-fusion-plugins-extra pack too




that's for > ccsm 

> dondolo@dondolo-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList





and i if i try to instal emerald synaptic says that's impossible to do....... thanks

---

### Post by Neo4 on 2007-11-03
I have the new driver installed
composite and aiglx enabled on the xorg.conf file
whitelisted fglrx on the compiz-manager but when I run conpiz it says:

 compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

i don't want xgl i want to run compiz from aiglx...
any idea?

this error only occurred after the compiz update today. before that all was okay
 
thanks

---

### Post by Tron24 on 2007-11-03
I got the same thing as well and I am using Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03).

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

This sux!! I hope someone has a solution.

---

### Post by RedFishBlueFishGreenFish on 2007-11-04
I have an ATI had card and when i install the xserver-xgl package it turns off my 3d rendering. so my question is is there any way i can have both 3d rendering and desktop effects?

---

### Post by o_portista17 on 2007-11-07
Hello there, i'm using Ubuntu 7.10 Gutsy, and i have the same problem as above... i've just installed the "xserver-xgl" , and my direct rendering is gone... ;(

Before i install that i only had 1 display, and now i have to, one with Direct Rendering, and the other one, the one i'm using, without...

here's the glxinfo of booth displays...


glxinfo -display :0
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x55 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None




 glxinfo -display :1
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6650 (8.39.4))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


Is there a way, to use the Display :0 , and use the Compiz?

Sorry about the mess ;x

---

### Post by stuffman64 on 2007-11-08
After a nightmare trying to get the 8.42 drivers working on my computer with full dual-head and all that jazz, I would like to get compiz working properly but just can't seem to do it. When I tried to install the xserver-xgl package and tried logging back in, the session would crash and go back to the login screen. I was able to start in failsafe and remove the xserver-xgl, but compiz won't start without it.

Another user had the same problem earlier in the thread, but I don't think the issue was actually resolved.


(x86_64, Radeon 9600XT, Gutsy)

---

### Post by Padakwaak on 2007-11-08
Thank you for the help.

I had to install xserver-xgl  package and made a minor change to my /etc/X11/xorg.conf file to get the Visual Effects (compiz) to work with my old Geforce2 GTS using nVidia Legacy GLX drivers.

Some people suggested to disable the Composite extension to get the GLX working ( which it did), although it prevented me from starting compiz.
```
Section "Extensions"
	Option		"Composite"	"Disable"
EndSection
```

Then I tried to use the following to fix it:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Which just resulted in an "unrecognized option" error.

The solution to the problem above was to add the following in the xorg.conf in the screen section:
```
Option         "AddARGBGLXVisuals" "True"
Option         "AllowGLXWithComposite" "True"
```

I'm still fairly new in the Ubuntu environment, so please correct me if I went wrong somewhere!

---

### Post by lattmau on 2007-11-09
> **Padakwaak said:**
> Thank you for the help.

I had to install xserver-xgl  package and made a minor change to my /etc/X11/xorg.conf file to get the Visual Effects (compiz) to work with my old Geforce2 GTS using nVidia Legacy GLX drivers.

Some people suggested to disable the Composite extension to get the GLX working ( which it did), although it prevented me from starting compiz.
```
Section "Extensions"
	Option		"Composite"	"Disable"
EndSection
```

Then I tried to use the following to fix it:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Which just resulted in an "unrecognized option" error.

The solution to the problem above was to add the following in the xorg.conf in the screen section:
```
Option         "AddARGBGLXVisuals" "True"
Option         "AllowGLXWithComposite" "True"
```

I'm still fairly new in the Ubuntu environment, so please correct me if I went wrong somewhere!

I use the Nvidia Legacy drivers too.  In my xorg.conf file, I have this only
```
Option         "AllowGLXWithComposite" "True"
```

but what does this do?
```
Option         "AddARGBGLXVisuals" "True"
```
 
I also read that having "AllowGLXWithComposite" enabled is bad, but its how it started working for me.  Can anyone provide an authoritative confirmation?

---

### Post by mahasmb on 2007-11-09
I have a desktop I bought since 2004 with an integrated graphics card. I've upgraded to Gutsy.

When I type "compiz" into the terminal, I get this: 

```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

What's the best solution for someone with an integrated graphics card??

---

### Post by giovannicosta on 2007-11-16
> **mahasmb said:**
> I have a desktop I bought since 2004 with an integrated graphics card. I've upgraded to Gutsy.

When I type "compiz" into the terminal, I get this: 

```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

What's the best solution for someone with an integrated graphics card??

I have the exact same problem, except I custom built my pc... HELP!

---

### Post by swoop_ubu on 2007-11-16
[deleted - I overlooked there are actually 6 pages in this thread :-(]

---

### Post by Amaranth on 2007-11-16
Your system is not capable of using desktop effects.

---

### Post by _mirinda_ on 2007-11-23
Got Compiz working, but now everything is very slow... scrolling pages, moving windows, all of that makes my PC suffer...

I have an ATI x1400 video card with the 8.42.3 drivers.

What can I do?

---

### Post by Forlong on 2007-11-23
Nothing, the driver is buggy.
Go back to fglrx from the repos + Xgl (or, if your card is supported by the [open radeon driver](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/radeon.4.html) - use this one)

---

### Post by Cjpettit on 2007-11-23
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

I have no idea what to do here...

---

### Post by solarhexagon on 2007-11-24
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


help!!! I am using a macbook, and i have ubuntu running in vmware fusion (no flames!!!:mad:) and I cant get the effects to work!

(I put "compiz" into the terminal)

---

### Post by Forlong on 2007-11-25
> **solarhexagon said:**
> i have ubuntu running in vmware
What do you expect? Virtual machines don't have 3D acceleration.

---

### Post by Cjpettit on 2007-11-25
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1


How do I set the screen to 1?

---

### Post by fooman on 2007-11-25
i have 2 gateway laptops with ati graphics (one has the X200m the other has X1150).  3d effects worked great until yesterday morning when there was a compiz update.  after that i was getting this when i ran compiz in the terminal:

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

i had used envy to install the ati drivers when gutsy was installed.  so alls i did was uninstall the ati driver using envy,  then reinstalled the driver with envy once again.

compiz is working perfectly now.  :)

---

### Post by Forlong on 2007-11-25
Cjpettit, what type of graphics card are you using?

---

### Post by Cjpettit on 2007-11-25
I have an ati Mobility Radeon 9000.  I know that ATI has compatability issues with the drivers and it doesn't help that mine is super old, but compiz effects was working perfectly until I logged off and logged back in. I try to run compiz through terminal but all I get is:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0


so with that I decided xgl must not be working correctly so I type in fglrxinfo and get:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

Screen should be set to 1 shouldn't?

---

### Post by Forlong on 2007-11-25
Did you install fglrx yourself? Because I don't think your card is supported by that one.
Remove it again:
```
sudo apt-get remove xorg-driver-fglrx
```
If you did something to your xorg.conf - change it back.
Oh, and remove Xgl as well:
```
sudo apt-get remove xserver-xgl
```
Then restart and try again.

---

### Post by Cjpettit on 2007-11-25
That did the trick. Do you know when or if there will be support for my card?

---

### Post by bluedragon436 on 2007-11-26
I had this issue on my desktop that I had just installed Ubuntu onto, and it was running fine with the exception of not being able to enable Compiz Fusion....but after installing the "xserver-xgl" and the Compiz Settings Manager...it is all working just fine....and then some....

---

### Post by michaelpagz on 2007-11-27
okay so I am getting the "desktop effects could not be enabled" message with my wife's newly ubuntu-ed computer. I typed "compiz" in the terminal and this came up```
compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

``` and i installed "xserver-xgl" prompted by this thread. I rebooted  but I am still getting the same messages. This computer is a used one we got from a friend and I am not sure what graphics card it has. I assume that makes a difference. How can I check that in the terminal? Is there anything else I can do to get compiz working? I certainly would like to get the effects going, my wife really wants the snow effect!
Thank you so much!

Mike.

---

### Post by Forlong on 2007-11-28
> **michaelpagz said:**
> This computer is a used one we got from a friend and I am not sure what graphics card it has. I assume that makes a difference. How can I check that in the terminal?
```
lspci | grep VGA
```
> **michaelpagz said:**
> my wife really wants the snow effect!
Haha, my wife likes that too. But I have to disappoint you: that's not in Gutsy by default.

---

### Post by michaelpagz on 2007-11-29
Yes. I know about the snow not being on here by default. I'm having trouble with that on my computer too but thats a different story. I got autumn up and running though. Here is the what came up with the graphics card: ```
 01:00.0 VGA compatible controller: STMicroelectronics STG4000 [3D Prophet Kyro Series] (rev 07)
```

Will this support compiz? If it will, how? 
Thank you!
Mike

---

### Post by Forlong on 2007-11-29
This doesn't sound well:
> I'd discussed open source drivers with them before and they are not
interested.  The only way we will get open source Kyro driver is if
someone reverse engineers the hardware and writes one.  This seems
very unlikely, as I strongly doubt they have even as much as 0.1% of
the video market.  It's easier to just buy a video card that has
supported open source drivers, than it is to become motivated to
reverse engineer the hardware.
[https://bugs.freedesktop.org/show_bug.cgi?id=1652](https://bugs.freedesktop.org/show_bug.cgi?id=1652)

In other words: there's no Linux-driver for this card at all.
Desktop effects are out of the question.

---

### Post by Nando-san on 2007-11-29
i have a NEW DESKTOP and installed UBUNTU, I deleted windows 'cause i really don't like it. I got this problem of DESKTOP EFFECTS COULD NOT BE ENABLED... i tried the xgl thing intalled and it doensn't appear to have done anything... i think what im gonna do is install Windows back and UBUNTU in a partition... can't find any help for my problem... also CANT get my true resolution, plus the way I type changed... It used not pute ' when I typed it, then i typed a letter and the ' would be con top... not it just writes 'a ... what's happening???

---

### Post by Forlong on 2007-11-29
Please give us more informations.

What version of Ubuntu?
What type of graphics card?
What's the output of ```
compiz
``` in a terminal?
And you may want to post your xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```
use the forum's CODE tag please (# button)

---

### Post by michaelpagz on 2007-11-29
> in other words: there's no Linux-driver for this card at all.
Desktop effects are out of the question. 

Well, it was worth a shot. Thanks Again.
mike.

---

### Post by uber_nerd11 on 2007-11-29
Is the blacklist issue for the Intel 965 cards an Intel driver issue or a Compiz Fusion issue?  That way I know which one to watch.

---

### Post by Forlong on 2007-11-29
> **uber_nerd11 said:**
> Is the blacklist issue for the Intel 965 cards an Intel driver issue or a Compiz Fusion issue?
Driver/AIGLX issue.

---

### Post by ntetreau on 2007-11-29
> **giovannicosta said:**
> I have the exact same problem, except I custom built my pc... HELP!

> **giovannicosta said:**
> I have the exact same problem, except I custom built my pc... HELP!

Well, not to seem puzzled by the fact that you customed muild your own PC but doesn' t seem to know what video card you put in it!  Joking, now I only know a few tricks from NVIDIA, so check that you have one or not (ATI, and intel would spring to mind):

```
   
lspci -l | grep NVIDIA
lspci -l | grep ATI

```

For NVIDIA at least, you can install the new drivers (needed to run compiz) in Synaptics (nvidia-glx) or in a terminal:

```

sudo aptitude install nvidia-glx-new

```

reboot.

For those two, I believe you can use the program called [ENVY]("http://albertomilone.com/nvidia_scripts1.html") which will [install]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb") the latest available driver, do it cleanly and let you then use compiz (without XGL)., run it from Apllications > System tools > ENVY.  Follow the instructions.  Reboot, go to System > Preferences > Appearance > Visual Effect and click Normal.  It may just work (it does for most really), or it may just ask to Enable the driver, for which you will need to reboot again.  In my case, that wasn' t enough trouble.

If you get the same message about not having the minimum of 65536 like the first chap then your card is blacklisted becuase it didn' t reach the minimum 64MB video ram.  Well, in that case you can change the criteria if you are confident that your card should work (or that you can fix it if it doesn' t,).  To do this in a terminal::

```
 
sudo gedit /usr/bin/compiz

```

Look for this line:

```
NVIDIA_MEMORY="65536" # 64MB
```

and change it to

```
NVIDIA_MEMORY="26624" # 64MB
```

try it again.

---

### Post by dimaoo7 on 2007-12-28
I have a Dell Inspiron E1505 with the ATI X1400 Card.
I've tried enabling the restricted drivers, tried the xlg solution, however I still get the "Desktop effects could not enabled"
Comsiz manager is installed:


When running compiz in terminal I get the following:
```
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

Below is my xorg.conf
```

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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
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
EndSection
```

This is my third day using Ubuntu/ any *nix environment so any and all advice would be appreciated.

---

### Post by Forlong on 2007-12-28
> **dimaoo7 said:**
> I've tried enabling the restricted drivers, tried the xlg solution
What do you mean by "tried"?
Because neither the output of Compiz nor your xorg.conf confirms this.

Go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and enable the driver for your graphics card.
Then install Xgl:
```
sudo apt-get install xserver-xgl
```
Finally reboot and see if it worked.

---

### Post by engstrom on 2007-12-28
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

NVM...(hanging head in shame for being a idiot and not paying attention) :-)

---

### Post by dimaoo7 on 2007-12-29
> **Forlong said:**
> What do you mean by "tried"?
Because neither the output of Compiz nor your xorg.conf confirms this.

Go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and enable the driver for your graphics card.
Then install Xgl:
```
sudo apt-get install xserver-xgl
```
Finally reboot and see if it worked.

xserver is installed.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.

```

Although I have tried the driver before with no avail, this time I enabled it only to find that after restart my resolution is limited to 640x480. I still tried the effects, unfortunately the same message appeared.

Any ideas?

---

### Post by dimaoo7 on 2007-12-29
Ok, just did a clean install. Enabled the drivers and installed xserver, it works, YAY.

Thank you... now onto getting my mouse to work properly.

---

### Post by Newbuntuguy on 2008-01-16
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

THANKS! This was solved the issue for me too! Appreciate the sharing of knowledge my friend... :)

---

### Post by terryfunk4life on 2008-01-17
Hello I am trying to get compiz working but every time it tries to run it says 
"xgl not present"
I have xserver-xgl installed and I have a 7900gt and the nvidia drivers installed.

---

### Post by aspora.isernia on 2008-01-18
> **Amaranth said:**
> The fglrx driver does not support texture_from_pixmap and thus cannot run compiz. You have to use the open source driver (if you can) or use Xgl. Install the xserver-xgl package, logout, and when you login it'll be running and compiz should automatically start (unless you  turned it off).

Hi Amaranth,
I do not understand if I _need_ to install Xgl in order to enable visual effects: I use nvidia drivers for a Nvidia Quadro graphic card, and installed ubuntu 7.10 from scratch.

When I try to enable visual effects, window decorations suddenly disappear, but some effects work properly (such as the desktop wall). I also installed the emerald-settings package and enabled the window decorations plugin.
Thanks for any hint.

a.i :)

---

### Post by ercanyuz on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **kev82 said:**
> I did this, installed XGL and that got compiz working.

However after logging out and in, my keyboard layout was gone (went to us english from icelandic) - I changed that and seems to be working alright, but thought it was strange.



I had the same problem about the keyboard layout. I installed XGL and got the compiz perfectly work. However my keyboard layout became "US" and it won't change neither by editing "xorg.conf" nor by changing gnome keyboard settings in the control panel, which both say the layout is "TR" (Turkish), but that's not the fact. I think there is a problem with the xgl, which makes it doesn't honour the layout settings. It makes the keyboard layout stuck with the US-Layout. I found this thread at launchpad [here.]("https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857") I tried the workaround suggested by Cappadocius. Which does not seem to be the most elegant solution, but it worked. Namely, I added the command 
```
setxkbmap -model pc105 -layout tr
``` as a startup action (Preferences -> Sessions -> Startup). "tr" is for Turkish, so use your own layout instead.

---

### Post by xiangcao on 2008-02-11
my hardware:
[PHP]00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266][/PHP]

i type "compiz" in terminal and got this:
[PHP]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
[/PHP]

i have update the wholelist that available.
and also i have installed the "xserver-xgl", and restart so many times.
i click the restricted drivers manager and got the message "your hardware does not need any restricted drivers"
i set the advanced desktop effects nothing appear, i want to enable the effects but got the message"desktop effects could not be enabled"
why?

please help me, thank you.

---

### Post by renz2k8 on 2008-02-13
I also have the same problem 

[PHP]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity [/PHP]

But my computer is Asus a6r and my hardware is ATI Radeon Xpress 200M. Thanks in advance.

---

### Post by tomiscool on 2008-03-09
i dont get it how do u get that app i havea unichrome pro igp and get this message it says desktop effects could not be enabled if ur going to tell us to install something well then show us how to get it

---

### Post by Amaranth on 2008-03-09
You can't use compiz on a via chip, via does not give enough information to write a driver to do so and no one cares enough to reverse engineer it.

---

### Post by Limvot on 2008-03-19
How bout this out put? This is on Ubuntu 7.10 PPC. Is it possible to get effects working on it?

nathan@oldcomp-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:10.0 0300: 1002:5245 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by mathewc on 2008-03-20
Hello all. I'm having the same problem on a Sony Vaio with a ATI Mobility Radeon 7500C

Here is my output.

```
mathew@somekindalinux:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c57 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity
```

I lowered my resolution to 1024x768 and got the same thing.

---

### Post by misterhead on 2008-03-24
This actually worked for me on a Dell Latitude D810, with a Radeon x600 however I started noticing other issues with xserver-xgl, from slow loading of X, to dual monitor issues, etc... I have since completely reinstalled and found this.

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#comments)

Dont know if it will work for all, but it worked GREAT for me. NO XSERVER, and compiz looks better and runs smoother.

Much props to THIS thread, though. I never would have stumbled accross that AIGLX blog, mentioned above, without first following this easy to read thread, which really does work great. My Dell just doesn't like XSERVER very well.

---

### Post by badperson on 2008-03-27
I've been having this same problem...so do ATI cards just suck w/ubuntu?
bp

---

### Post by Amaranth on 2008-03-27
> **badperson said:**
> ATI cards just suck

Fixed that for you. :)

---

### Post by JohnGalt131 on 2008-04-09
I am having similar problems. After installation, my graphics driver was the intel experimental. In this configuration, the 'Extra' visual effects worked but I could not use extended dual monitors. I did some google-ing and switched drivers to the intel i810 and now the extended desktop works (as I wanted) but now neither normal nor Extra will work for visual effects only the 'none'/unattractive settings work.

---

### Post by mathewc on 2008-04-09
I fixed this by running 16bit color depth instead of 24 and using the set SKIP_CHECKS=yes in my startup script. It's not super pretty, but it works.

While searching back for what I did to post here I ran across this which I'll try tonight: 

"I think I have found a fix for the issue of the garbage at the right/bottom when forcing compiz to start despite the failed texture size. By setting a virtual size I manage to use my preferred resolution (1280x800), without needing to revert to 16bpp:

Put this in your "Screen" section in /etc/X11/xorg.conf:

        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Virtual 1280 800
                Modes "1024x800"
        EndSubSection

Values may differ according to desired resolution and maximum texture size (1024 in my case, hence I choose 1024x800 for the modeline.

Though untested, I think compiz should in this situation start cleanly without the SKIP_CHECKS=yes option enabled."

from: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519)

-Mathew

---

### Post by buried on 2008-04-09
Good luck on that

---

### Post by daniel7860 on 2008-04-14
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity

---

### Post by Forlong on 2008-04-14
daniel7860, please always specify what version of Ubuntu you are using.
You are obviously using Hardy, did you use Compiz on Gutsy before?

---

### Post by daniel7860 on 2008-04-15
> **Forlong said:**
> daniel7860, please always specify what version of Ubuntu you are using.
You are obviously using Hardy, did you use Compiz on Gutsy before?

yes i am using hardy.  when i used gutsy it worked perfectly.
i stil have the advanced desktop effects settings and i also have the simple compizconfig.
when i got to appearence>visual effects>normal or extra>>."desktop effects could not be enabled":(

---

### Post by Forlong on 2008-04-15
```
echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager
```
Then try again.

---

### Post by daniel7860 on 2008-04-15
> **Forlong said:**
> ```
echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager
```
Then try again.

i copied and pasted that into the terminal and nothing happened.......

---

### Post by Forlong on 2008-04-15
Now try ```
compiz
``` in the terminal again.

---

### Post by daniel7860 on 2008-04-15
> **Forlong said:**
> Now try ```
compiz
``` in the terminal again.


Checking for Xgl: not present. 
Found laptop using ati driver. 
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Forlong on 2008-04-15
You *have* to give us more information.

What graphics card are you using? 
```
lspci | grep VGA
```
Did you try to install any driver?

---

### Post by daniel7860 on 2008-04-15
> **Forlong said:**
> You *have* to give us more information.

What graphics card are you using? 
```
lspci | grep VGA
```
Did you try to install any driver?


01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

if i install the restricted driver(((ATI accelerated graphics driver))) and enable the effects my screen turns white.
when i used 7.10 i did not need the restricted driver.

---

### Post by Forlong on 2008-04-15
Do you still have the restricted driver installed?

---

### Post by daniel7860 on 2008-04-15
> **Forlong said:**
> Do you still have the restricted driver installed?

NO

---

### Post by dmongo on 2008-04-15
i have xubuntu  i downloaded compiz i downloaded emeral and nothing happened i followed the advice in this post and dowloaded xserver-xgl and rebooted. now i have a black screen with pointer.. i cant get it back to normal. any fixes

---

### Post by daniel7860 on 2008-04-15
> **dmongo said:**
> i have xubuntu  i downloaded compiz i downloaded emeral and nothing happened i followed the advice in this post and dowloaded xserver-xgl and rebooted. now i have a black screen with pointer.. i cant get it back to normal. any fixes

that happened to me when i installed the restricted drivers and enabled the effects. exept my screen was white.

---

### Post by daniel7860 on 2008-04-15
........................................

---

### Post by Juhla Mokka on 2008-04-19
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

Wow, that did it! So simple! You're a :KS

---

### Post by CypherHackz on 2008-04-25
I also got the same problem. Before this in ubuntu 7.10, my compiz works perfectly with my ATI Radeon 9500FX. And I use Envy to download and update my graphic card driver. 

But then after I upgraded to Ubuntu 8.04, Ubuntu gives error saying that "Desktop effects could not be enabled" when I want to enable it in Appearance in Visual Effects tab.

Here is the result when I enter compiz in the terminal:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9588 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

It seems like Compiz is missing but I have reinstalled it so many times but it still cannot be found. So how to fix this?

-cypher.

---

### Post by Amaranth on 2008-04-25
[http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/](http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/)

---

### Post by CypherHackz on 2008-04-25
Cool! Thanks buddy!

-cypher.

---

### Post by dheff on 2008-04-29
I am having the same problem but cannot get this fixed for the life of me. I have tried installing xserver-xgl, and what was recently posted from the Realist Anew page, among other things - none of which have worked

```
dheff@dheff-laptop:~$ compiz
Checking for Xgl: not present. 
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): Operation not permitted
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

```
dheff@dheff-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

```
dheff@dheff-laptop:~$ sudo dpkg-divert --rename --remove /etc/xdg/compiz/compiz-manager
[sudo] password for dheff: 
No diversion `any diversion of /etc/xdg/compiz/compiz-manager', none removed

```

---

### Post by nathanael on 2008-04-30
> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

I tried that, and sure enough, my desktop effects worked.  My only problem was that 3D acceleration left in blender3D.  I am a new user to linux, and I have an ati radeon 7500c in a dell inspiron 5100, with hardy heron.  Is there a solution?  Please be patient with me, I am still a newbie.

---

### Post by johnhammonds on 2008-05-06
I have a Dell Latitude D620 Core 2 Duo 2.33GHz with 2GB RAM and a GeForce Go 7300 Nvida Video Card.

I recently installed gOS V.2.0 "Space" Edition on my laptop in a Triple boot configuration (Win XP/Vista Home Premium/gOS Space). I know this isn't the gOS forum, but this distro is based of Ubuntu 7.10 Gusty Gibbon.

I'm getting ye ole' "Desktop effects could not be enabled".

Pasted "Compiz" in a terminal:

```
john@Laptop-gOSpace:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - [COLOR="Red"]Error: Another composite manager is already running on screen: 0[/COLOR]
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0


```

The Restricted Drivers have been enabled and it shows in the "Restricted Drivers Manager" I have both my Intel(R) Pro/Wireless 3945 Network Connection Driver For Linux Driver Enabled and my NVIDA accelerated graphics driver (latest cards) enabled.

Don't forget that AWN comes preinstalled on gOS Space.

Xorg shows:

```
john@Laptop-gOSpace:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-72
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
john@Laptop-gOSpace:~$ 


```

I tried the suggestion back earlier in this thread:

Post #11

> **afterburn said:**
> Thanks Amaranth, that solves it. For anyone who, like me, needs to think a couple of times before it is understood what to do, here ya go:

go to system > administration > synaptic package manager
in the list on the right search for "xserver-xgl" (type it in to quickly scroll to it). Say OK to the extra packages and install.

Now xserver-xgl will run automatically (so says the yellow balloon tip) each time you logon. To start it up, hit CTRL+ALT+BACKSPACE or logout manually.

By the way, I find it a little weird that you have to do this stuff, but you don't get this kind of support at the place the error occurs. The error message is quite obscure if you're not interested in the technical background of the error... but thats a different issue.

That didn't fix the problem. And the logs posted are from after trying that fix.

I understand that it says "[COLOR="Red"]Error: Another composite manager is already running on screen: 0[/COLOR]", but I'm a noob to linux and don't really understand what is running.

I can't just click Control+Alt+Delete and check the processes.

Sessions shows that Startup includes:

avant-window-navigator
Beagle Search Daemon
Bluetooth Manager
Evolution Alarm Notifier
Power Manager
Print Queue Applet
Restricted Drivers Manager
Tracker
Update notifier
User Folders Update
Visual
Volume Manager
xcompmgr


If that is something pertinent to know.

All help appreciated! ;-)

---

### Post by lattmau on 2008-05-06
i'm new to linux too, but could it be xcompmgr is already running? you can try closing that running compiz

---

### Post by johnhammonds on 2008-05-06
> **lattmau said:**
> i'm new to linux too, but could it be xcompmgr is already running? you can try closing that running compiz

Went to Sessions and unchecked xcommgr not to start up, and once I rebooted, it was unchecked, but in the "Current Sessions", it showed up it was running. I ran "Compiz" in a terminal again, same error. I even ended the "Current Session" of xcompmgr and it still gave the same error when I ran "Compiz" in a terminal again.

That doesn't seem to be the problem, but when it comes to Linux, I don't know anything for sure! lol...

---

### Post by lattmau on 2008-05-06
i googled and came across this 

[http://forum.compiz-fusion.org/archive/index.php/t-2535.html](http://forum.compiz-fusion.org/archive/index.php/t-2535.html)

similar problem to yours i think, so it might still be because of xcompmgr...but i don't know how to get rid of it (maybe uninstall?)

---

### Post by johnhammonds on 2008-05-06
> **lattmau said:**
> i googled and came across this 

[http://forum.compiz-fusion.org/archive/index.php/t-2535.html](http://forum.compiz-fusion.org/archive/index.php/t-2535.html)

similar problem to yours i think, so it might still be because of xcompmgr...but i don't know how to get rid of it (maybe uninstall?)

I appreciate the help, but I don't see how it pertains to me as that guy is having trouble with the KDE Desktop.

gOS Space comes with Gnome just like Ubuntu.

I don't have KDE, so I don't see how my issue could be the same.

Thanks though! ;)

---

### Post by lattmau on 2008-05-06
i know, but that guy has xcompmgr running too and receiving same msg as you

from some website:
> Xcompmgr is a simple composite window manager, capable of rendering drop shadows and, with the use of the transset utility, primitive window transparency. Designed solely as a proof-of-concept, xcompmgr is a lightweight alternative to Compiz Fusion and similar composite managers.

---

### Post by johnhammonds on 2008-05-06
> **lattmau said:**
> i know, but that guy has xcompmgr running too and receiving same msg as you

from some website:

Well disabling it didn't seem to fix the issue. Even after restart. I checked the "System Monitor" under the Administraion tab and that allowed me to see the processes. Low and behold, xcompmgr was still running. I ended it. I went back to Advanced Desktop Settings and it allowed me to enable!!!

The odd thing is, if it had been a Windows machine, unchecking it would have led to it not starting again after reboot, yet even though unchecked, it still did start again. And yet even odder, ending the process fixed the problem and after reboot, the process didn't start again. Seemed kind of backwards to me, but either way, the problem seems to be fixed. Now to customize AWN and play with Compiz. :-)

Thanks for your help! You :guitar:

---

### Post by lattmau on 2008-05-06
i'm glad it worked out.

actually i think running 
> 
compiz --replace 
might have worked too..haha oh well

---

### Post by Amaranth on 2008-05-06
It would not have helped, we use --replace by default. xcompmgr does not properly give up the compositor selection so you have to manually kill it off before trying to use another compositor. Metacity actually has the same problem.

---

### Post by lattmau on 2008-05-06
ah good to know. thanks

question though, if --replace doesn't work w/ metacity, how come so many people recommened to do it?

---

### Post by Amaranth on 2008-05-06
No no, I'm saying if you use the metacity compositor you have to turn it off before starting compiz.

---

### Post by mattalexx on 2008-05-16
I'm also getting the "Desktop effects could not be enabled" error. I installed the driver for my NVIDIA GForce 8600GT vid card. My monitors are:

SAMSUNG SQ11 (1360x768)
BenQ FP202W (1680x1050))

This is what I get when I run "compiz":
```
don@don-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3040x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConxfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 339 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/usr/bin/compiz.real (core) - Fatal: No valid GL extensions string found.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Anything glaringly obvious to anyone?

---

### Post by Amaranth on 2008-05-16
You're using Xinerama on nVidia. This is not supported, use TwinView.

---

### Post by mattalexx on 2008-05-16
I get this message when I try to apply my new settings (TwinView) in nvidia-settings:

The XRandR X extension was not found. This extension must be supported by the X server and enabled for display configuration settings to be dynamically applicable.

Under Synaptic, it says that I have "xrandr" installed. Is there some sort of dependency that I'm missing?

---

### Post by mattalexx on 2008-05-19
Bump

---

### Post by montgoss on 2008-05-27
> **mattalexx said:**
> I get this message when I try to apply my new settings (TwinView) in nvidia-settings:

The XRandR X extension was not found. This extension must be supported by the X server and enabled for display configuration settings to be dynamically applicable.
I have the same error.  Anyone know what's causing it?

---

### Post by erlingwl on 2008-05-28
With 7.10 I got compiz working with the xserver-xgl package. But now that I upgraded to 8.04 I had to uninstall xserver-xgl to be able to use dual-screen.. (see [http://ge.ubuntuforums.com/showthread.php?t=733571](http://ge.ubuntuforums.com/showthread.php?t=733571)). 

What can I do know? 

Btw. I have an ATI mobility radeon X1300 using the "restricted driver".

---

### Post by nocnoc on 2008-06-01
> Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

What should i do?

---

### Post by wordmaster on 2008-06-28
I am getting the "Desktop effects could not be enabled" message. 

I am running a rig I built myself with a GEforce 2, Athlon 2600, 768 ram, and I am very new at Linux although quite experienced with windoze and others. 

When I run compiz I get:

user@user-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0150 (rev a4) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

The vid card has never failed to do what was needed in windoze. Is it simply incapable of rendering the desktop effects in Ubuntu or is there a fix?

Thank you kindly for any help.

---

### Post by yno037 on 2008-07-03
Hello,

I've been using ubuntu for a while now, and visual effects have always worked. I run ubuntu from an external hard drive which i plugged to a machined at work to recover some files from a crashwed windows. it installed nVidia drivers and it worked fine, but when I plugged the hard drive to my laptop (ACEr Aspire 5610Z where I always use ubuntu) the display was messed up.

I got the display to work, but the effects are not working now. Also, AVANT or Blender arent working..

here is the output for lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


and the output for compiz

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
/home/raul/.themes/OS-X Leopard/gtk-2.0/gtkrc:206: Unable to locate image file in pixmap_path: "Lines/line-v.png"
/home/raul/.themes/OS-X Leopard/gtk-2.0/gtkrc:209: Background image options specified without filename

I installed the xserver-xgl but effects are still messed up....


Thanks for your help

---

### Post by Amaranth on 2008-07-05
Uninstall the nvidia driver.

---

### Post by yno037 on 2008-07-05
the nVidia drive does not show under restricted drivers...if that's not what you mean,need more help

---

### Post by Amaranth on 2008-07-05
Uninstall the nvidia-glx and nvidia-glx-new packages if either one is installed.```
sudo apt-get --purge remove nvidia-glx nvidia-glx-new
```

The libGL from the nvidia driver does not work with the intel driver so you need to uninstall the nvidia driver to get the right libGL back.

---

### Post by yno037 on 2008-07-07
Thanks a lot Amaranth, it fixed the effects thing but now the graphics are extremely slow, even if I disable the effects. Any Ideas?

Again Thanks for all your help

---

### Post by Amaranth on 2008-07-07
Try adding this to the Device section of your /etc/X11/xorg.conf:```
Option "MigrationHeuristic" "greedy"
```

---

### Post by yno037 on 2008-07-07
Thanks Amaranth, adding those lines did not solve the problem, but i uninstalled the xserver-xgl and that fixed my nightmare.

THANKS A LOT

---

