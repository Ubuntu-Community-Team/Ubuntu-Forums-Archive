---
title: "After the install get blank screen"
date: 2006-01-04
forum: General Help
---

### Post by dmnokia on 2006-01-04
Hi,

I have a acer travelmate laptop with ATI x700.
After installation, when the laptop first boot, My screen
can not switch the graphical window. Only a blank screen.
I know the problem is ATI X700 graphic card.
I dont know how to solve this problem.

If I use xwindows at least vesa mode, I will try to
correct the screen problem installing or compiling necesssary
kernel or driver. But I cant login the system.

Any help is welcome,

D.M

---

### Post by audax321 on 2006-01-04
Have you tried CNTRL+ALT+F1 to see if you get a terminal? Then you can login and do:

sudo nano /etc/X11/xorg.conf

to edit xorg.conf... then do CNTRL+X to exit and indicate if you want to save or not. When you are back at the prompt, try restarting gdm:

sudo /etc/init.d/gdm restart (for gnome)

for KDE, it might be:

sudo /etc/init.d/kdm restart  (or just do startx) :)

---

### Post by swinster on 2006-03-17
Hey Dmnokia, did you get this problem solved? I have exactly the same issue with my Rock laptop and an X700 graphics chipset. 

And audax321, what exactly do I need to alter in the xorg.conf file? Dring setup I chose the correct resolusion for my laptop screen (1440x900 widescreen) which is it's native resolution.

---

### Post by incubus on 2006-03-17
swinster,

I got an ASUS laptop with the same card. Interestingly, never had a problem but I do have to edit xorg.conf.

To get it working fast, I would go to Section "Device" and replace "ati" for "vesa". That should allow you to at least get X working. You can test by:
$ startx

Then you'll probably want to install the driver "fglrx" to get 3D acceleration working. Let's see if that works first.

incubus

---

### Post by swinster on 2006-03-17
Cheers. I'm having a few issue at the mo. I scanned through a few of the podts that give a few different solutions or ways to edit the file.

First there is the editor above 'sudo nano /etc/X11/xorg.conf'. However, my user account (the only one I though I have set up during install) asked me for a password when entering this then simply seaid that I was editing a new file. I tried to logout and back in as root but I don't even seem to know the password! Christ I only set one up during install and it ain't that.

Then the pas a command I saw that went 'dpkg -reconfigure xserver -xorg' but this tells me hat there is a mismatch or something. I looked at help on 'dpkg' but couldn't see anything about the '-reconfigure' option, the closest was the '--configure' option. I tried to run this but the bloody thing said I needed to be a superuser! ARRRGGGGG.

Oh hold on, jest read more and relised that there no spaces between the options. Right lets try again

---

### Post by NOmAK on 2006-03-17
You don`t need to be root in ubuntu when you are dealing with problems that needs to be root.You should use "sudo" 
$ **sudo**  *your instructions...*
"sudo" is like a temporary root access and you must use your own password not the roots yet you didn`t create a root account

---

### Post by swinster on 2006-03-17
That would explain th 'sudo' command and why I can' log in as root. What arethe root user account details then in ubuntu? I this now standard for all Linux distros or just Ubuntu?

Back off to try again. I should have installed in a VM in windows.

---

### Post by swinster on 2006-03-17
Well I tried. I managed to get into the configuration and I even managed to get KDE to load, using the VESA setting instead on ATI! COOL - er - well no.

KDE would only start in 1024x768 not 1440x990 so the resolution and screen size was way off. In fact I could even get to some of the option buttons in the system start up windows. So I went back into the configuration and added the 1440x990 resolution to my list. I then restarted X and &#8211; NOTHING. Startx throws up a fatal error and on the screen it makes reference to a screen being available but no supported.

No problem I thought, simply put everything back the way it was an restart x. STILL NOTHING! There is still the same fatal error. I have tried umpteen combinations and I can&#8217;t get the thing to work again. What a waste of time. 

It seems as though the configuration utill believes there is a CRT installed, not a LCD laptop display. I noticed that when you get to the refresh option (Simple, Medium and Advanced) it says in the blurb that the Simple option should be disabled for LCD display, yet this was still active and in the advanced options I see the upper and lower bound for a monitor refresh rate. Even setting the vertical refresh to a static 60 (or even 60-60) did not make any difference)

7 years ago I looked at Linux and I battled for days to set up a video card and modem then. I would have thought that it would have grown up by now but unfortunately the same basic lack of support is still evident. At this rate Linux will never really make inroads into the desktop market. This seems like such a shame.

If anyone else has got any suggestion I am all ears. But after I manage to get the desktop to work, I still have to get the Wireless network working. For the short while I was in KDE I could see in the network options that a wireless network was disabled. When I went into the Wireless network options I tried to configure these with Admin privileges &#8211; I entered my password but again nothing.

I know I have a lot to learn but this is heavy going.

---

### Post by pelle.k on 2006-03-18
Be sure to really look up your horizontal/vertical refresh rates because if you get them wrong, you will most likely not only get screwed up output, but also damage electronic circuits in your monitor. A friend of mine got smoke coming out of his crt after pushing it to hard. google is your friend.

Refresh rates does NOT work the way you think. 60 vertical, 60 horizontal does not make it 60 Hz.
My monitor is 1440*900 (60 Hz), and my settings are HorizSync  28-72, VertRefresh 43-60. Look your values up!

Ubuntu is a derivate of debian, and thus have the same basic layout, which include sudo. Mepis too.

Search for fglrx in adept or install command line (sudo apt-get install xorg-driver-fglrx). Is that the correct name? (use "sudo apt-cache search fglrx" to find out...)

Then replace vesa with fglrx (again, i have nvidia so i'm not sure about this).
OK?

There has been a quirk for you somewhere, cause it usually works the first time. Linux is soooooo much more ready for the desktop than 7 years ago.

I should now, i'm a recent convert.

---

### Post by pelle.k on 2006-03-18
By the way tell us about your wireless config. card brand? use wep? use dhcp?

---

### Post by ozorba on 2006-03-18
[QUOTE=swinster]That would explain th 'sudo' command and why I can' log in as root. What arethe root user account details then in ubuntu? I this now standard for all Linux distros or just Ubuntu?

Back off to try again. I should have installed in a VM in windows.[/QUOTE]

sudo su

will allow you lo login as root after you enter your password.

then type

passwd

to change the root password.

type exit afterwards...


-----

---

### Post by swinster on 2006-03-18
Hey Pete, ozorba and everyone else thanks for this tips. Still having issues.

What I don't undersatnd is that I actually had KDE up and running for a brief while. Every time I made a change with dkpg it makes a backup of the xorg.conf file with a date/time extension. I have been back through all the VESA conf files and copied each one in turn back to xorg.conf then run startx.

Each file still give the same basic error:

VESA :No matching modes
Screens found, but none have usable configurations.

I can't understand why at least one of these backup xorg.conf file don't work. I will tr the Rock forums and see if anyone knows that actual H and V refresh setting for this notebook.

I have download the latest ATI linux driver although it is stored on a local FAT32 partition. I can't run any updates within Linux as I do not have a Internet connection. Kunbuntu fails to even recognise my inbuilt 10/100/1000 ethernet adapter and the wireless adapter is disabled (from my brief foray into KDE). 

The Wireless adapter is a an MSI MP54G2 module plugged into the laptop motherboard. They don't have any driver in thier site but I have contacted thier support, yet I don't hold out much luck. I run WPA in windows although the router supports WPA2, the driver for the module from MSi doesn't.

---

### Post by swinster on 2006-03-20
Well, I've tried loads of timing and still can't get past the above errors. Tried a shearch on these forums and althoughI can across similar issue there were no fixes. On the Rock forums I can across a link ([http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)) that calclated a custom modeline based on my expected resolution and refresh rate, but it was it is for the XFree86 not Xorg thinges an I couldn't actually figure out how to implement the change.

As a last resort I have downloaded Kubuntu 6.04 (Dapper Drake flash 5) to see if there is any improvement as I believe these have the latest ATI driver included. Otherwise I will give SUSE or Mandrake a whirl.

---

### Post by swinster on 2006-03-23
Well, i have tried Kubuntu 6.04 (Dapper Drake) and I must say I'm dissapointed as hs appears to have exactly the same bugs and flaws as the 5.10 version.

Firstly, the install will hand on my machine  not a major problem as I know know to add to the command line NOAPIC NOLAPIC, but still not very good.

Secondaly, the install will not detect my ethernet port built into the laptop, either my hard fired 10/100/1000 port or the Wireless network module, and only give my the option of setting up a Network via Firewire.

Lastly, and most important to this post, is that the screen is STILL blank after the install! It looks as though either the new driver are not installed from the outset oe they do not function.

Overall, a very poor installation leading to an unusable OS. You Linux boys still have a LOOOOOOONNGGG way to go.

---

### Post by swinster on 2006-03-24
OK, I managed to get get a GUI - holy sh**!

I had to edit the xorg.conf file as shown before-

sudo nano /etc/X11/xorg.conf

Instead of changing the drivers to "vesa", I left them as "ati", but in the "monitors" section I changed the folowing line:

Option "DMPS"

to

Option "MonitorLayout" "LVDS"

This has allowed me to start KDE at 1024x768. I can alter the resolution even to the LCD screens native 1440x900 although the desktop gets a little sqrewed up. I guess that installing the latest ATI drivers might resolve this issue.

Now I need to figure out how to get my network working along with my Wireless module.

---

### Post by pelle.k on 2006-03-25
never heard of that lvds option before, good work man!

I did a search, and the MSI MP54G2 is equipped with a rt2500 chip.
You're in luck because it's supported out of the box in dapper.

I don't now about wpa though... i use wep. You might need wpa supplicant.

---

### Post by swinster on 2006-03-28
Ok, After a bit more reading, I think that allthough the above fix worked for me, I put the option in the worng place in xorg.conf file. I think it should go in the Device section concerning the graphics driver, not the monitor section replaceing the DPMS option. 

Somthing like-
```
Section "Device"
        Identifier      "ATI"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MonitorLayout" "LVDS"
EndSection

```

I have seen other post with other additions to the LVDS thingy, but I don't relly have a clue what they all do.

---

