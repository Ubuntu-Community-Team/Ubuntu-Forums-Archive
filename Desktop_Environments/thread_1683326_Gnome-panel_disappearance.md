---
title: "Gnome-panel disappearance"
date: 2011-02-07
forum: Desktop Environments
---

### Post by jurchiks on 2011-02-07
I've already asked about this problem here: [http://superuser.com/questions/242688/gnome-panel-disappearance-in-ubuntu-10-10/242700](http://superuser.com/questions/242688/gnome-panel-disappearance-in-ubuntu-10-10/242700)
but unfortunately nothing has helped so far.
The problem is that today, after about a week of normal running my taskbar disappeared. Alt+F2 also doesn't work, and it is VERY inconvenient because I can't run almost any application unless I can find their executables, which is hard because I am an absolute beginner in Linux. I tried deleting gnome settings (rm -rf .gnome .gnome2 .gconf .gconfd), I tried deleting general settings (rm -rf ~/.config/), I tried reinstalling gnome-panel (sudo apt-get --purge remove gnome-panel, sudo apt-get install gnome-panel), I tried sudo apt-get install gnome-desktop, which downloaded and updated some stuff, but NOTHING helped.

Googling for hours for a fix, I found someone mentioning that it might be due to 3d hardware acceleration and I do remember yesterday installing a program that supposedly does that, BUT since Ubuntu refused to understand the nvidia driver package that I had downloaded from the official nvidia site I have no video drivers installed (not even the ones ubuntu suggested to install, because I have an extremely crappy internet connection atm, it would take me half a day to download them). In the end, the program said that it can't find supported hardware or drivers or smth like that.

The main question is - how can I get back my desktop environment? I can currently only browse my hard drives and open the web browser thanks to the desktop shortcuts I already had.
Of course, I have lots of other questions, mainly about silly/stupid/extremely annoying things, but that's for later.

---

### Post by cjhabs on 2011-02-07
What happens if you run "gnome-panel" from the command line?
Does it come back, does it crash, etc?

---

### Post by Krytarik on 2011-02-07
The mentioned directory removal fix will only work if you logout before and do it at the console, press Alt+Ctrl+F1 to switch to one. But you only have to remove "~/.gconf/apps/panel/" and "~/.gnome2/panel2.d".

The mentioned package removal/reinstalling fixes wont affect your settings.

---

### Post by jurchiks on 2011-02-08
> **cjhabs said:**
> What happens if you run "gnome-panel" from the command line?
Does it come back, does it crash, etc?

it says:
"(gnome-panel:1910):Gtk-WARNING **: cannot open display:"

@Krytarik - it doesn't help no matter where I do it.

How is it even possible that installing one program (assuming that's what caused it) disables most of the GUI? That is a damn unreasonable bug, such things should never happen!

---

### Post by cjhabs on 2011-02-08
You need to run this from a terminal window while in the windowing system, not from an Alt-Fx console.

---

### Post by Krytarik on 2011-02-08
> **cjhabs said:**
> You need to run this from a terminal window while in the windowing system, not from an Alt-Fx console.
+1

Besides this, are there any serious errors logged in "~/.xsession-errors"?

---

### Post by jurchiks on 2011-02-09
> **cjhabs said:**
> You need to run this from a terminal window while in the windowing system, not from an Alt-Fx console.

In case you couldn't read it, I clearly wrote "it doesn't work no matter where I do it"! And I also wrote that Alt+F2 DOES NOT WORK for me.
Being a smartass doesn't help.

@Krytarik - 
I reinstalled my ubuntu yesterday and all I changed was some ordering on panels and in start menu. I didn't even install anything except chromium, no updates, nothing else. Clean install, extremely minor changes.

These are the errors that I have in the file you mentioned.
What matters is the compiz part, but why the hell would it refuse to load it?
I don't have any video drivers installed, but it ran fine yesterday.


```
(polkit-gnome-authentication-agent-1:1567): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1567): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Unable to find a synaptics device.
Initializing nautilus-gdu extension
** (update-notifier:1785): DEBUG: --security-updates-unattended: 0

** (update-notifier:1785): DEBUG: aptdaemon on bus: 0
** (update-notifier:1785): DEBUG: Skipping reboot required
/usr/bin/jockey-gtk:130: Warning: g_str_has_suffix: assertion `str != NULL' failed
  gtk.main()
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Regarding "Workarounds for broken applications disabled" - it doesn't affect this, tried enabling and no effect.

---

### Post by Krytarik on 2011-02-09
I think we can now rule out any errors in the config of gnome-panel.

What if you load Metacity instead of Compiz, and the run gnome-panel again:
```
metacity --replace
setsid gnome-panel
```

Check .xsession-errors after that.

PS: Alt+F2 isn't working because it's a feature of gnome-panel.

---

### Post by jurchiks on 2011-02-09
It says:
"Window manager error: Unable to open X display"

---

### Post by Krytarik on 2011-02-09
> **jurchiks said:**
> If I type it in while logged in, it says:
"Window manager error: Unable to open X display"
I'll try before logging in now.
You have to be logged in and run it in a terminal.

EDIT: Is this the output of the first or the second command?

---

### Post by jurchiks on 2011-02-09
The first ofc.
You mean the Ctrl+Alt+F1 terminal, right? Because if there are more terminals then I know nothing about them...
I tried both logged in and out, the command 'metacity' as such gave this error.

---

### Post by Krytarik on 2011-02-09
> **jurchiks said:**
> The first ofc.
You mean the Ctrl+Alt+F1 terminal, right? Because if there are more terminals then I know nothing about them...
I tried both logged in and out, the command 'metacity' as such gave this error.
No, I mean a "terminal-emulator", like gnome-terminal. And, again, you must be definetely logged in, otherwise it makes completely no sense.

If you haven't found a way to launch gnome-terminal, which I would totally understand, then just create a launcher for each of those commands, for gnome-panel without "setsid" then.

PS: The Alt+Ctrl+F*, non-X, sessions are usually referred to as "console".

---

### Post by jurchiks on 2011-02-09
Ok, creating launchers and running them did bring up the taskbar again.
Edit: after restart it's still the same and the .xsession-errors is also practically the same:
```

(polkit-gnome-authentication-agent-1:1589): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1589): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Unable to find a synaptics device.
```

---

### Post by Krytarik on 2011-02-09
> **jurchiks said:**
> Ok, creating launchers and running them did bring up the taskbar again.
Edit: after restart it's still the same and the .xsession-errors is also practically the same:

Good that it at least works without Compiz, that tells us that everthing else is ok.
That you get the same issues after a restart is the expected behaviour.

Now we have to find a way to bring up Compiz without killing gnome-panel.

Why exactly couldn't you install the proprietary video driver?
I guess, at the moment the somewhat unstable "nouveau" driver is run.
It would be very helpful, if you could install the proprietary driver in any way.

What is the output of the following command?:
```
lshw -c video
```

---

### Post by jurchiks on 2011-02-09
```
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 9800 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f4000000-f5ffffff ioport:a000(size=128) memory:f7000000-f701ffff

```
I have the nvidia drivers downloaded, but the file extension is .run and it tries to open it with text editor (wtf really?). I also had JDK and Eclipse both for Linux, but Eclipse simply refused to open (no reaction on double-clicking the executable) and JDK was in the .tar.gz archive and mounting it I also couldn't run the main file (but I'm not 100% sure on this one as I've already forgotten, I had too many problems with this stuff).

Edit: found some ways of running the .run file, first one (Properties>Permissions>Allow executing file as program) is reset the moment I tick it.
Using console and chmod +x, made it work, but now running it gives me this error: "ERROR: nvidia-installer must be run as root"

But of course, Ubuntu has no root account, how cool is that?
Now I'm digging to find out how to run the file from the root terminal.

Edit2: great, nvidia homepage has a shitload of reading on how to install video drivers... amazing to say the least.

---

### Post by Krytarik on 2011-02-09
Just run it with the prefix "sudo", you will be asked for your (own) password then.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jurchiks on 2011-02-10
I'm running it in root terminal (the one in applications>system tools menu), but now it asks me to turn off X server.
Edit: right, turning off Xorg process didn't help, running it before logging in didn't help, running it from root console from recovery mode (the next choice in grub's boot menu) also didn't help as it couldn't find the damn file! I cd to my home folder (/home/jurchiks) and try to run the damn file but it says it doesn't exist! Every other console/terminal can find it but this one can't! WTH is going on with this ****?
Why is installing video drivers such a science on Linux?

---

### Post by Krytarik on 2011-02-10
Normally it's not that difficult to install the driver, you wouldn't have to do it manually, but since you said your internet connection is crippling slow, I didn't want to entail you the "normal" way, which is via "System -> Administration -> Additional Drivers".

So, it seems that nothing has changed since I installed the driver manually the last time. You have to run the installer either like you did, at the console of the recovery mode, or logout and stop X/GDM:
- logout
- switch to a console by pressing Alt+Ctrl+F1
- login
```
sudo service gdm stop
```
- locate the installer
- run it like that:
```
./NVIDIA*.run
```
- reboot (just to be sure)

---

### Post by jurchiks on 2011-02-10
The problem is that it gives me an error: "The distribution-provided pre-install script failed!"
It offers to continue, but since I can't know if that pre-install script is necassary I chose not to take the risk.
Should I ignore it and continue after all?

---

### Post by Krytarik on 2011-02-10
Did you follow something like that?:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

But since you would have to download more packages that way either, I think it would be even faster, and simplier and more forsighted anyways, if you would choose to install the driver via "Additional Drivers".

---

### Post by jurchiks on 2011-02-11
That guide is outdated, there is no xorg.conf in that directory. If there was I probably wouldn't ask here on how to install the thing.
But yeah, I had read that and it seemed the most explanatory of all I found.

As I already said, the Additional Drivers way shows me ~24 hours of download time (at least that's when I turned it off, maybe it's an even bigger number).

Edit: nvm, suffered through 3 hours of downloading (no progress indication whatsoever, only the slider :@ So frustrating!) and it's installed now. Amazingly stable connection today...

But the gnome-panel still doesn't load up on startup.

---

### Post by Krytarik on 2011-02-11
> **jurchiks said:**
> That guide is outdated, there is no xorg.conf in that directory. If there was I probably wouldn't ask here on how to install the thing.
But yeah, I had read that and it seemed the most explanatory of all I found.

I seem to keep on saying that (I should create a shortcut for it ;-)):
Nowadays there is no xorg.conf by default, but you can place one as usual in /etc/X11 and it will be processed as usual.
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Try adding the following option to the "Screen" section of your now created xorg.conf (!), I need to have it there, although it is said to be enabled by default:
```
Option         "AddARGBGLXVisuals" "True"
```Otherwise I also have sometimes no panels, sometimes no desktop, and sometimes both. One of these options is granted.

---

### Post by Krytarik on 2011-02-11
> **jurchiks said:**
> 
As I already said, the Additional Drivers way shows me ~24 hours of download time (at least that's when I turned it off, maybe it's an even bigger number).

Edit: nvm, suffered through 3 hours of downloading (no progress indication whatsoever, only the slider :@ So frustrating!) and it's installed now. Amazingly stable connection today...

Btw., did you check how much you would have to download the other way?!

You need the package "linux-headers-*-generic" in both cases, that's why your install didn't work.

For the manual install you also need the "build-essential" package, which pulls in additional 24 MB at my system.

For the automatic way you need of course the nvidia driver packages, which are some 26 MB (for the current version, unless you are running the 64-bit version of Ubuntu).

---

### Post by jurchiks on 2011-02-11
Ok, this is really starting to get on my nerves...
Had downloaded and installed half of the available updates thanks to the amazingly good connection and just now tried running that command "sudo xOrg -configure" from your link, and it gave me an error (smth about the xserver), but created the file (with very little in it). I also couldn't edit it, so I thought it's probably bcuz of the error.
Then I tried "sudo service gdm stop" and ran the command again, but then it said "command xOrg not recognised".
Since I was doing this in the console, I clicked Ctrl+Alt+F7, but (and this isn't even remotely the first time this occurs) the GUI didn't come back, instead I had smth like a few lines of debug messages and no options to do anything, i.e. can't type anything here either.
So I clicked Ctrl+Alt+Delete, which restarts the PC.
Now, when I log into my account, it gives me 3 errors, first one being "Unable to configure /home/jurchiks/IVConfigure" if I remember correctly, the last of them is about being unable to create "/home/jurchiks/Desktop" and one other folder. Basically things got ****** up (again...).
Also, right after I installed the video drivers, I restarted the PC, but the loading screen had went to 800x600 resolution and 256 colors (before it had always been my native resolution and full color). It also displayed some debug info (something it had never done before) beneath the 4 dots (used to be 5), the ones that change color when loading.
So basically both the video drivers and the updates, and, possibly, the weird error because of unsuccessful command, have once again screwed up my system.
BUT - all is not lost, because I had enabled the root account before I installed the drivers, just to see what's different (nothing really, apart from no annoying password popups).
The weird thing is that those errors only occur on my normal account, not the root one, that is I am now logged in from the root, because my normal account is completely out.
I have to say I'm amazed at how many ways there are to do NORMAL things and still manage to **** up the system, you would never be able to do it with Windows...

Now I'll probably run the recovery mode and see if there's anything it can do to fix this, otherwise I'll just have to stick with the root account, because, amazingly enough, IT WORKS.



Edit: finished the "fix broken packages", it downloaded some stuff but didn't fix anything. Here are the exact error messages I get when logging into my account:
1) Could not update ICEAuthority file /home/jurchiks/.ICEAuthority
2) There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
3) Nautilus could not create the following required folders: /home/jurchiks/Desktop, /home/jurchiks/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

---

### Post by Krytarik on 2011-02-11
1. In order to get back to the GDM login, you have to restart it, did you that?:
```
sudo service gdm start
```
It then automatically pops up.

2. It seems you have managed to hand over the ownership of the file "~/.ICEauthority" to root, by using "sudo" instead of "gksudo":
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3. Try creating a proper xorg.conf by using the following command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```

---

### Post by jurchiks on 2011-02-13
made the xorg.conf, but what about the errors?
I'll try to chmod 770 on my home folder from console, but I'm not sure it will help.

Edit: chmod 770 helped, the three errors disappeared... That sure sucked.
But there's still the weird graphical problem with the loading screen. Why is it 800x600 256colors? Before I installed the video drivers it was normal.
Also, is there any way to change the way it looks? I don't like the violet color.

---

### Post by Krytarik on 2011-02-13
1. You didn't follow the second hint of my previous post.

And I didn't notice your edit of your previous post, please post a new message, when your original message has already been answered to, otherwise no one notices your edit, because the subscribers don't get notified about edits.

But the error messages underpin my assumption, and there is still a problem, since the file is still owned by "root", following your post. To check this enter this in the terminal:
```
ls -al /home/jurchiks/.ICEAuthority
```To fix it:
```
sudo chown jurchiks.jurchiks /home/jurchiks/.ICEAuthority
```2. I have set up my splash/console resolution just by editing "/etc/default/grub", you may of course set a higher resolution:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=800x600
[/B]#GRUB_GFXPAYLOAD=keep
[B]GRUB_GFXPAYLOAD_LINUX=800x600
[/B]
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```After editing the file, run this in the terminal, to update Grub:
```
sudo update-grub
```Guide to Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you really need to change the color depth also, follow this guide:
[http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/](http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/)

3. To change the splash screen try those tools:
[http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html](http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html)
[http://www.webupd8.org/2010/10/install-and-change-plymouth-themes-in.html](http://www.webupd8.org/2010/10/install-and-change-plymouth-themes-in.html)
Please give feedback if you found a cool splash!

4. How about your original issue, the gnome-panel!?

---

### Post by jurchiks on 2011-02-14
1. The link didn't say anything about how to fix it so I fixed it my way. Worksforme.
2. Did it, all that's left to do is restart and see if it worked.
Edit: it worked perfectly :)
3. I'll definately try, thanks.
4. Well, it loads fine since I put it in startup programs, no problems there, and no related errors in xsession-errors afaik.

---

### Post by rvchari on 2011-02-14
> **jurchiks said:**
> I've already asked about this problem here: [http://superuser.com/questions/242688/gnome-panel-disappearance-in-ubuntu-10-10/242700](http://superuser.com/questions/242688/gnome-panel-disappearance-in-ubuntu-10-10/242700)
but unfortunately nothing has helped so far.
The problem is that today, after about a week of normal running my taskbar disappeared. Alt+F2 also doesn't work, and it is VERY inconvenient because I can't run almost any application unless I can find their executables, which is hard because I am an absolute beginner in Linux. I tried deleting gnome settings (rm -rf .gnome .gnome2 .gconf .gconfd), I tried deleting general settings (rm -rf ~/.config/), I tried reinstalling gnome-panel (sudo apt-get --purge remove gnome-panel, sudo apt-get install gnome-panel), I tried sudo apt-get install gnome-desktop, which downloaded and updated some stuff, but NOTHING helped.

Googling for hours for a fix, I found someone mentioning that it might be due to 3d hardware acceleration and I do remember yesterday installing a program that supposedly does that, BUT since Ubuntu refused to understand the nvidia driver package that I had downloaded from the official nvidia site I have no video drivers installed (not even the ones ubuntu suggested to install, because I have an extremely crappy internet connection atm, it would take me half a day to download them). In the end, the program said that it can't find supported hardware or drivers or smth like that.

The main question is - how can I get back my desktop environment? I can currently only browse my hard drives and open the web browser thanks to the desktop shortcuts I already had.
Of course, I have lots of other questions, mainly about silly/stupid/extremely annoying things, but that's for later.

go thru this thread...
you might solve ur problem...

LINK => [http://ubuntuforums.org/showthread.php?t=1685821](http://ubuntuforums.org/showthread.php?t=1685821)

---

### Post by Krytarik on 2011-02-14
> **rvchari said:**
> go thru this thread...
you might solve ur problem...

LINK => [http://ubuntuforums.org/showthread.php?t=1685821](http://ubuntuforums.org/showthread.php?t=1685821)
Yeah, check this thread for more detailed instructions:
[http://ubuntuforums.org/showthread.php?t=1682949](http://ubuntuforums.org/showthread.php?t=1682949)

---

### Post by jurchiks on 2011-02-14
Meh, doesn't matter, it works now so I couldn't care less anymore, it ****** enough with my brain.
Now I'm just trying to make a loading screen of my own since all the ones I found are either wrong resolution (doesn't look good and I don't even know if it scales fine, didn't check), not for plymouth (usplash and whatnot), or for different versions of Ubuntu or even different distributions (and it's written in some corner or worse). The problem is that plymouth-manager says that the image must be .png <500kb, but at my resolution (1680x1050) it's impossible. Guess I'll just have to see what happens...

Edit: BTW, found a good tutorial on making my own theme: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

