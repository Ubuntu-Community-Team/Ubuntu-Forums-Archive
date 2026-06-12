---
title: "3D Cube/Wobble Compiz...won't work.trying everything I can find"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by Gideon147 on 2007-11-02
Hello everyone. I'm an XP convert working my way into linux for the first time. My only experience was Unix back in '96. So I'm not entirely ignorant but I know little of these environments.

I installed Ubuntu 7.04? And well...I looooooooooved it. I thought the Desktop Effects were just the right eye candy to sell my wife on linux long term. Being new, when I discovered the upgrade, I did so right away.

Now I have no eye candy and I'm in a panic. What made it great for her was the Wobbley and the Cube. They worked fine with Feisty but they flat out don't exist on Gutsy.

I have Compiz Settings Manager running fine. I can check and uncheck things to my hearts desire. But it has absolutely no affect on my environment. Turn cube on, off, wobble on, off, Opacify, Zoom, whatever. Nothing actually works or changes anything.

System > Preferences > Desktop Effects
returns "Desktop Effects cannot be enabled."

System > Preferences > Advanced Desktop Effects Settings
returns: Runs fine but doesn't give me any effects.

I've searched the internet for hours and have tried every "fix" I can find. I've been at this since 11am. I'm running an Inspiron 4100 and it's 'not' new..but seriously, if it worked in 7.04, shouldn't it be able to work in 7.10? If not, I'll reinstall. But if I CAN get it work, please tell me how.

And this is my first post. Hello! :)

Please and thank you,

Desperate in Kansas

---

### Post by Happy_Man on 2007-11-02
Quite an interesting pickle.... I will try and get all the pseudo-embarrassing questions out of the way first. 

Did you install the restricted driver, and then reboot?

Did you try the command ```
compiz --replace
``` from a Terminal (Applications --> Accessories --> Terminal) and see what it says?

What video card do you have?

---

### Post by Gideon147 on 2007-11-02
I've kind of gotten lost in all the fixes I've tried. But I just took your advice. The only restricted driver listed is "Software Modem Driver" I disabled, enabled, and rebooted.

Same pickle.

I'm really new and a fairly quick study, but in Ubuntu(Linux) how do I tell what graphics hardware this laptop is running?

Thanks in advance...

---

### Post by mysticmatrix on 2007-11-02
There exist graphical long way of doing it. For short way, just post output of this command```


lspci
```

If you have Intel G965, it has been blacklisted. :(

---

### Post by Gideon147 on 2007-11-02
lspci returns:

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller

---

### Post by mysticmatrix on 2007-11-02
You have a 

> ATI Technologies Inc Radeon Mobility M6 LY

Please post output of 

```
compiz --replace
```

---

### Post by Gideon147 on 2007-11-02
Okie doke...learning as I go:
compiz --replace 
returned:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by mysticmatrix on 2007-11-02
> **Gideon147 said:**
> Okie doke...learning as I go:
compiz --replace 
returned:

Checking for Xgl: not present. 
[COLOR="Red"]No whitelisted driver found[/COLOR]
aborting and using fallback: /usr/bin/metacity

Clearly, your card/driver combination is blacklisted. So no compiz by default. :(

We may try to fix things tomorrow. Right now, I'm going to sleep. Till then, can you post output of

```
glxinfo
```

---

### Post by Gideon147 on 2007-11-02
All right...here it is:

glxinfo

returned:

(In terminal) 

Xlib extension "GLX" missing on display ":0.0." (repeated 7 times)

output to file:

name of display: :0.0

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by mysticmatrix on 2007-11-03
> **Gideon147 said:**
> All right...here it is:

glxinfo

returned:

(In terminal) 

Xlib extension "GLX" missing on display ":0.0." (repeated 7 times)

output to file:

name of display: :0.0

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Hmnn. Tha's odd. There might be a trouble in your graphics driver.
Go to System --> Administration --> Screens and Graphics
On the Graphics card tab, select 'radeon' as your driver and restart.

---

### Post by Gaztech on 2007-11-03
I've just been experiencing the same problems on a fresh install of Gutsy. 

The answer to my problems was to install the following packages:

gnome-compiz-manager
gnome-compiz-manager0
xserver-xgl

After installing those and a reboot I now have desktop effects!

---

### Post by Gideon147 on 2007-11-03
Good morning!

I would have to say yes, there is trouble in my graphics driver. It defaults to low graphics mode:

Model: Plug 'n' Play
Resolution: 800x600 (yuck)
at: 61Hz
Driver: vesa - Generic VESA-compliant video cards

Every time I reboot now I get these defaults after returning which probably have something to do with "No resume image" message during boot screen.

---

### Post by Gideon147 on 2007-11-03
@Gaztech

It sounds like we have the same problem but possibly for different reasons

gnome-compiz-manager (installed)
gnome-compiz-manager0 (not found)
xserver-xgl (already installed)

Note: 800x600 on a little laptop monitor is slow torture.

---

### Post by Zorael on 2007-11-03
"No resume image" just means your system isn't restarting from hibernation, not to worry.

It seems to me X isn't starting with the driver you want it to. Are you sure you have it enabled?

Copy/paste the output of 'lshw -C video', please.

---

### Post by Gideon147 on 2007-11-03
Well I selected the driver again and rebooted. But this is just getting out of hand now...

I log in, the screen goes solid brown?, then it goes black, then I get a flash of bunch of text on the screen, then it goes black, then it prompts me to log in again. But I do have full resolution on my screen...that's something.

Now to get past the login.

---

### Post by Zorael on 2007-11-03
Does /sys/var/gdm.0.log show anything of interest?

Or kdm.0.log if you're running KDE. Possibly xdm.0.log if you're running Xfce, I don't know.

---

### Post by 1337455 10534 on 2007-11-03
Have you 
```

sudo apt-get install gnome-compiz-manager0

```
yet?

---

### Post by Gideon147 on 2007-11-03
Ok, logged on using GNOME failsafe. I'm back in!

---

### Post by 1337455 10534 on 2007-11-03
> 
/sys/var/gdm.0.log

Where do you want him to run that? Open it in file browser, or terminal? Be specific, it is a help forum.

---

### Post by Gideon147 on 2007-11-03
sudo apt-get install gnome-compiz-manager0
returns

"E: Coudln't find package gnome-compiz-manager0"

---

### Post by Zorael on 2007-11-03
> **1337455 10534 said:**
> Where do you want him to run that? Open it in file browser, or terminal? Be specific, it is a help forum.

Naturally. It is a text file, so open it in a text editor, such as gedit, kate, or mousepad.

---

### Post by Gideon147 on 2007-11-03
/sys/var/ 
No such file or directory.

Searched for gdm.0.log via terminal "No such file or directory."

Places > Search for Files > "gdm.0.log" via "Shane" & "File System" & "Floppy1" & "sda3" & "70.0 GB Volume"

No results.

---

### Post by 1337455 10534 on 2007-11-03
Try dloading it from here:
[http://packages.ubuntu.com/gutsy/gnome/gnome-compiz-manager](http://packages.ubuntu.com/gutsy/gnome/gnome-compiz-manager)

perhaps:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Zorael on 2007-11-03
Doh, I miswrote.

```
**/var/log**/gdm.log
```

Does that one exist, then?

My apologies, I don't use Gnome myself, so I can't really be sure.

---

### Post by 1337455 10534 on 2007-11-03
I think that
```

gksudo gedit /var/log/gdm.log

```
would work fastest (but i dont really know what that file is anyway). anyways, did GDebi install the manager from that site for you? I tried my own advice through a terminal with the same response as what you g ot, but it works if you manually download it.
btw: my fusion works perfect without the manager but what the heck

---

### Post by Gideon147 on 2007-11-03
Would you mind explaining how that works? I'm navigating around the site and when I select download all I get is another page listing the contents of the package. Is this done via terminal?

sudo apt-get update returns:

"Fetched 7B in 2s (3B/s)"
"Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/feisty-security/Release](http://nl.archive.ubuntu.com/ubuntu/dists/feisty-security/Release)  Unable to find expected entry  restrived/binary-i386/Packages in Mega-index file (malformed Release file?)
Reading package lists...Done
E: Some index files failed to download, they have been ignored, or old ones used instead."

sudo apt-get upgrade returns:

"Reading package lists... Done"
"Reading state information... Done"
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

By the way, I appreciate you guys helping me out the way you are.

---

### Post by Gideon147 on 2007-11-03
gksudo gedit /var/log/gdm.log
returns

new (empty) file.

---

### Post by 1337455 10534 on 2007-11-03
No, sorry. Scroll to the very bottom of the page, and under the Download gnome-compiz-manager heading, pick your architecture. Then, open with GDebi and ignore any warnings

---

### Post by Gideon147 on 2007-11-03
Wait, back in terminal window:

"gedit:6268): GnomeUI-WARNING **:While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

---

### Post by 1337455 10534 on 2007-11-03
"gedit:626: GnomeUI-WARNING **:While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

--
Odd. Try finding the file in a file browser, but please try installing the manager first..

---

### Post by Zorael on 2007-11-03
If you upgraded from Feisty (which if I understand your first post you did?), and the Settings Manager doesn't start, you may need to purge everything compiz-related and reinstall it. (Complete Removal in Synaptic, or 'sudo apt-get purge compiz* libcompiz* libdeco*' in the terminal.)

---

### Post by Gideon147 on 2007-11-03
GDebi...I apologize, but what is that and how do I use it?

---

### Post by 1337455 10534 on 2007-11-03
Zorael is very correct. If you want a GUI for this process, goto System->Admin->Synaptic Package Manager. Press Ctl+F, or find, type 'compiz'. Uninstall and reinstall all packages.

---

### Post by Zorael on 2007-11-03
Gdebi is the package installer that by default starts when you double-click a .deb file. I believe it's included in the normal Ubuntu bundle.

---

### Post by 1337455 10534 on 2007-11-03
GDebi...I apologize, but what is that and how do I use it?
--
It installs .deb packages for UBuntu. You never have to tell it to start, just pick your acrchitecture, and choose OPen with Gdebi

---

### Post by Gideon147 on 2007-11-03
I thought I would remember more than this from when I was in college. I was wrong.

I scrolled down to the bottom of the page. I selected my architecture (i386) and I get a new page listing the contents. I select the contents, and I am returned to the original page. 

Tried terminal:

sudo apt-get purge compiz* libcompiz* libdeco*

done

restarted computer...still can't login under anything other than GNOME failsafe.

---

### Post by Zorael on 2007-11-03
But you do get to the login screen, right?

At that screen, is the resolution "correct", or way low?

---

### Post by 1337455 10534 on 2007-11-03
[http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/g/gnome-compiz-manager/gnome-compiz-manager_0.10.3-0ubuntu2_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/g/gnome-compiz-manager/gnome-compiz-manager_0.10.3-0ubuntu2_i386.deb)

Ttry this link.

---

### Post by Zorael on 2007-11-03
> **1337455 10534 said:**
> [http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/g/gnome-compiz-manager/gnome-compiz-manager_0.10.3-0ubuntu2_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/g/gnome-compiz-manager/gnome-compiz-manager_0.10.3-0ubuntu2_i386.deb)

Ttry this link.

With Compiz uninstalled, would that help? I'm more suspicious of the video card driver at this point, though that's the perspective from a Kubuntu KDE user, where Compiz is nowhere near as integrated as in Ubuntu. Compiz is not my default window manager; I have to launch it.

So pardon my ignorance.

---

### Post by Gideon147 on 2007-11-03
@Zorael: yes, I hadn't tried a Linux distro since 99'. I had Ubuntu on CD from a few months back and thought heck, why not. So I partitioned up a clean drive and installed XP, Feisty, and left room for more later if I felt like it. Loved Feisty. When I upgraded my wife's favorite features (ergo only selling points) were gone. No wobbly, no cube. The Desktop Effects could not be enabled. the Advanced Desktop effects could be changed relatively at will but they didn't actually affect the environment. I assume that's because the basic "Desktop Effects" weren't enabled.

Here I am, two days and a dozen "Fixes" later (I've gotten lost in them) and have encountered resolution (fixed) and login difficulty as now I can only login under GNOME Failsafe..and still no cube or wobble.

lol...I like learning, and this *is* interesting...but...I feel like I'm sliding backwards rather than making any headway.

---

### Post by Gideon147 on 2007-11-03
Login screen: yes. & Resolution is correct.

---

### Post by DarkOx on 2007-11-03
First off, I'd suggest you back up the data on your hard drive (probably everything in the /home directory). If you're having trouble logging in, then there's a decent chance you'll get the system in such a state that you won't be able to easily access your files. So copy everything over to another computer, to CDs, to an external hard drive, something. 

(As an aside, there are ways to recover files if you can't log in to your computer but they're not as user-friendly for a new user as copying them over when you can easily log in.)

Secondly, have you considered either a new, clean install of Gusty or, failing that, a new, clean install of Feisty? Especially in the latter case, are there any features that are "must haves" for you in Gusty? If not, it may be best to go back to what worked -- after making a backup, of course.

---

### Post by 1337455 10534 on 2007-11-03
So after you have uninstalled all compiz parts, reinstall them, and then click on the 2nd link i gave you.

We all have our moments.

---

### Post by Zorael on 2007-11-03
Well, although it would be "giving up", you could back up your /home directory and do a fresh install. :>

-- edit: If you have proper resolution at the login screen, I really might be off the mark, so feel free to ignore me. But honestly, I'd advice you to do a fresh install. It's not that much work since you can backup your home directory. Your experience will be much, much less problem-ridden.

[quote="Me, in my ignorance"]With Compiz uninstalled, I'm of the belief it's an issue with your videocard driver somehow crashing X. Then again, my knowledge of the Gnome/Compiz integration is very limited, so I may not prove the most reliable source.

You could edit your /etc/X11/xorg.conf (through 'gksu gedit', or 'sudo nano' in a terminal), find the Device section for your video card, and change the driver to vesa. That *SHOULD* make you able to log into Gnome in non-failsafe, but you may experience low(er) resolution.

If you have an ATI or an Nvidia card (which you probably mentioned and I forgot), you couldtry Envy - a script that drivers from the manufacturer and installs it. This would be deviating from the Canonical-supported drivers though, so beware. You'll need to rerun Envy every time you upgrade your kernel to get X to start again, but this can be done from a terminal. It *is* more work, but you'll get the latest driver.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)[/quote]


I've never done an upgrade, instead taking the opportunity of new Kubuntu releases to get rid of gunk that's gathered over the months since my last installation.

---

### Post by Gideon147 on 2007-11-03
[http://ubuntu.mirrors.tds.net/ubuntu...untu2_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu...untu2_i386.deb)

Package Installer - gnome-compiz-manager
returns 

"Same version is available in a software channel. You are recommended to install the software from the channel instead."

Installed anyway.

---

### Post by Gideon147 on 2007-11-03
Ok, quick question then:

I've had Linux for about a week, no need to back up the drive, I haven't done anything with it.

Any way I can back up my Tetravex top 10? My wife is trying to beat my top score (31s) and it's the 3rd best selling point.

I know it's petty...but I have to ask. lol

---

### Post by Zorael on 2007-11-03
Of course. :>

All your user-specific settings are saved in your home folder.

Open it with the file manager of your choice and show hidden folders (Alt+H?). Chances are there's a ".tetravex" folder; copy this and you're good to go.

If it doesn't exist, check ".config". If there's nothing there, see if there's an, uh, developer? ...mentioned somewhere in the actual game. The settings may, for instance, be saved in "~/.developer/game".

Now, if these highscores are saved globally across all users, I'm not sure where they'd be. You only have write privileges to your home folder and /tmp, if I'm not mistaken - and other users would not have access to *your* home folder, naturally. But to save stuff in /tmp would be stupid. :>

edit-- to clarify, settings would include highscores. :)

---

### Post by Happy_Man on 2007-11-03
I'm... not sure where you'd look for that. My guess would be either in /usr/lib or in /usr/share. Go exploring!

---

### Post by Gideon147 on 2007-11-03
Great, will do and thank you. Going to start 7.10 from scratch. If no luck...well, I'll go back to Feisty until the solution reveals itself. 

I appreciate you bearing with me. I hope you guys have a great day.

---

### Post by suziq on 2007-11-06
I had similar problems with my cube and wobbly windows!!!!

I tried all sorts of things!
The thing that worked for me was ENVY - it got everything i needed and then installed everything and now my desktop effects work perfectly!

you can download ENVY from [http://albertomilone.com/index.html](http://albertomilone.com/index.html)
It works for both Nvidia and ATI graphics cards!

Hope it works as well as it worked for me!!!!

---

