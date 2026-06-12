---
title: "Desktop effects could not be enabled?"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by steerguy on 2007-10-18
I just got Gutsy today hoping it would be more user friendly than 7.04, which scared me away from Linux until now. I'm trying to get the custom desktop effects working but every time I try to increase the effects level from anything other than "None" I get and error that says "Desktop effects could not be enabled" which can't be a hardware problem, I'm running a 7800GTX. here's the return for compiz:
> Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0091 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (2880x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
Segmentation fault (core dumped)
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

When I first got gutsy up I had basic effects but after I got my dual screen working and changed some other stuff I noticed that the effects stopped. I've read a bunch of threads with similar problems but none seemed to help me.

---

### Post by klange on 2007-10-18
Segmentation fault <- That's your real problem

Beyond that, getting dual monitors and Compiz working together is a complex and painstaking task.

---

### Post by steerguy on 2007-10-18
At the risk of making it more obvious that I'm new to linux, I have to ask, wtf is a segmentation fault? Do you happen to have a thread/guide on hand on how to fix it? You also say that it's hard to get compiz on dual monitors, should I just give up now?

---

### Post by Nite23 on 2007-10-18
same problem here....

compiz --replace output:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0291 (rev a1) (prog-if 00 [VGA])
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
  (Details: serial 350 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

dmesg:
```
 compiz.real[7975]: segfault at 00000000000008a0 rip 00002aefc7c2b8c9 rsp 00007fffe4a17a18 error 4
```

relevant parts of xorg.conf:
```
Section "ServerLayout"
Identifier     "Default Layout"
Screen      0  "Default Screen" 0 0
Screen      1  "screen1" RightOf "Default Screen"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

ubuntu: 7.10, 2.6.22-14-generic x86_64
graphic card: nvidia 7900GT
driver: 100.14.19

---

### Post by mrbungle on 2007-10-18
same problem here! anymore more info on this?

---

### Post by birrafondaio on 2007-10-20
Same problem here!

---

### Post by jtekUSA on 2007-10-20
I have an NVidia video card and installed the restricted drivers but could not get the visual effects working as I was told the composite extensions were missing.  Although this was written for ATI cards, it worked beautifully for me and my NVidia card (Dell D620):

[http://ubuntuforums.org/showpost.php?p=3562227&postcount=10]("http://ubuntuforums.org/showpost.php?p=3562227&postcount=10")

In my case, the composite entry was set to "disabled" so I changed it to a "1" per the instructions.  I then had to download the xgl drivers, too.  I did a reboot instead of a log off to make sure the new settings would load.  After the system loaded, I was able to use any of the effects on the Visual Effects tab.

I hope this helps.  I am fairly new to all this, so I can not help any further.  Sorry.

---

### Post by Fnyar on 2007-10-21
I've got the same problem (running 7.10 and get the same errors). The problem appears to be related to having multiple screens. I can run compiz with only one screen, but compiz.real segfaults when I enable the second.

/var/log/apport.log:
```

apport (pid 6103) Sat Oct 20 17:31:20 2007: called for pid 6101, signal 11
apport (pid 6103) Sat Oct 20 17:31:20 2007: executable: /usr/bin/compiz.real (command line "/usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --replace ccp")
apport (pid 6103) Sat Oct 20 17:31:20 2007: apport: report /var/crash/_usr_bin_compiz.real.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
```

/var/log/messages:

```
Oct 20 17:31:20 blackmango kernel: [  349.770005] compiz.real[6101]: segfault at 00000000000008a0 rip 00002aaf7a6fa8c9 rsp 00007fff31f4b2f8 error 4
```

This looks like it's shaping up to be a fairly common problem. For now, it's back to metacity for me (the "no effects" option) unless I see find a solution soon.

---

### Post by fisting_mayfield on 2007-10-21
I wish I'd seen this post before spending the best part of today trying to figure out why I can't get Compiz working.  I guess I'll just wait to see if someone comes up with a dual-monitor way of enabling desktop effects :)

---

### Post by 0xffffffff on 2007-10-21
I have installed Gutsy on 3 PC's so far, and I have always had to install xserver-xgl to make the 3D effects work. Use:
[INDENT][FONT="Courier New"]sudo apt-get install xserver-xgl[/FONT][/INDENT]
After re-booting this has always worked for me. I also have the restricted graphics driver in use - see System->Administration->Restricted drivers manager.

The first line of your output from compiz shows you need xgl.

---

### Post by phurley on 2007-10-21
I was having the exact same problem. Installing xserver-xgl fixed the problem:

sudo apt-get install xserver-xgl

Restart xserver -- enable effects, until I enabled effects with xserver-gl installed, my desktop did not work correctly, especially on a window move.Of course now maximize stretches across both monitors, but I have lots of fancy effects - let me know if anyone finds a better solution.

pth

---

### Post by OldGrey on 2007-10-21
I tried installing xserver-xgl with synaptic, but i got this message:

Xgl server setup changed 

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable 

I wasn't sure what this meant / how to do this so I bottled and uninstalled xserver-xgl. Advise plaese as I would like to get the effects working.

---

### Post by WBuik on 2007-10-21
I have the same dual monitor using nVidia setup that seems to cause compiz to have issues.  Installing xserver-xgl did fix the problem, but the side effects finally forced me to remove it.  Having my monitors spanned instead of treated separately was a nuisance and not worth the effects.
However, it gets it compiz working pretty well if you don't care about the other stuff.
I guess I will just have wait until they fix the bug... :(

---

### Post by Raistlin355 on 2007-10-21
But what about the "segmentation fault (core dumped)" error?  is there a fix for this or is a reinstall nessary?  I have reinstalled compiz, xgl nothing works anymore and if I leave xgl off I get a TON of errors at startup, so I guess I'll wipe and reload.......................

SOLVED : Off subject does anyone know how to get ubuntu to show the bootup sequence?  you know all the devices that its finding and enabling?  I need this because my system hangs somewhere and I don't know what holding it up and a 5-7 min boot time is really getting on my nerves

Ok wipe and reload done compiz works perfectly and even starts at bootup!!  Still have no clue what the "segmentation fault" error was though

---

### Post by drted on 2007-10-24
> **0xffffffff said:**
> I have installed Gutsy on 3 PC's so far, and I have always had to install xserver-xgl to make the 3D effects work. Use:
[INDENT][FONT="Courier New"]sudo apt-get install xserver-xgl[/FONT][/INDENT]
After re-booting this has always worked for me. I also have the restricted graphics driver in use - see System->Administration->Restricted drivers manager.

The first line of your output from compiz shows you need xgl.

Thank you!! This solved my (similar) problem.  After following your tip I am now running desktop effects fine on dual monitors (1920x1200 apple cinema 23" + generic 1024x768 lcd with nvidia geforce 6800).

Oddly, my main desktop is now stretched across both monitors and "Screen and Graphics Prefs" lists my default monitor as 2944x1200, but still, at least I have 3d effects on both monitors, just needs a little more tweaking, i'm sure.

---

### Post by knownboyofno on 2007-11-05
> **Raistlin355 said:**
> SOLVED : Off subject does anyone know how to get ubuntu to show the bootup sequence?  you know all the devices that its finding and enabling?  I need this because my system hangs somewhere and I don't know what holding it up and a 5-7 min boot time is really getting on my nerves


Yea, I have the same problem.  I have to ctrl+alt+F1 after grab countdown ends.  Then my computer starts up in a min. I hope that helps.

---

### Post by giutax on 2007-11-06
Thanks....running sudo apt-get install xserver-xgl in terminal fixed my desktop effect issues.

:guitar:

---

### Post by Leed on 2007-11-07
Hi Guys, I had the same problem, I could only get compiz dual screen working with xserver-xgl with the Desktop stretched over both screens, but I managed to fix it.

I'm running a GeForce 6800GT

What I did.

[LIST]
[*]Remove xserver-xgl
[*]restart xserver (ctrl+alt+backspace)
[*]sudo nvidia-xconfig
[*]restart xserver
[*]sudo nvidia-settings
[*]X Server Display Configuration -> Display -> Configure
[*]Switch to TwinView
[*]don't forget to click the "Save to X Configuration File" button
[*]restart xserver
[/LIST]

After that I had both screens working, without the ugly stretch effect.

Hope it works as good for you, as it did for me

---

### Post by gabes on 2007-11-09
This solution (sudo apt-get install xserver-xgl) worked for a *different* problem that I had.

Initially I added some extra compiz-fusion effects on the super user account, restarted, and found that the effects had disappeared, ubuntu had set desktop effects to "none", and that nasty error message "Desktop effects could not be enabled" appeared whenever I tried to change it.

In my ubuntu n00bness, I reinstalled (a quick and painless exercise as you all know), and all was well for the super user.

However, when I added new users, desktop effects couldn't be enabled for them.

The answer: sudo apt-get install xserver-xgl

Thank you for this suggestion.

---

