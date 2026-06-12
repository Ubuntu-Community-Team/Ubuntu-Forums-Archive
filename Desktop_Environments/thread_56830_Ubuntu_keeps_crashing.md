---
title: "Ubuntu keeps crashing"
date: 2005-08-14
forum: Desktop Environments
---

### Post by nawitus on 2005-08-14
I'm not sure if this is the right thread but here's my problem: Ubuntu keeps crashing.
Yesterday I made fresh install of Ubuntu on a empty hard drive. No errors. Then I started it up and updated the system with the auto update tool. I browsed little and hopped in IRC. No problems.

Today when I start up Ubuntu it freezes in about 1-3 minutes after start up. The screen just freezes and I cant move the mouse etc. I did it about 5 times and it always crashed for no reason particular. It crashed the same way in Firefox and in XChat irc so it cant be programs crashing. Its not overheating becose my cpu cooler is at full power. And its not power problem becose I only have motherboard and hard-drive on. And this has been a perfectly stable system on Windows.

I havent updated any drivers manually (becose I dont know how to) and now I wouldnt even have the time I think becose it crashes so quick. I only did the system update but I dont know if it updated drivers (im linux noob and didnt read the list fully becose it had so many items). It did work for a while after the system update so I dont think that is the problem.

Here's my setup:
AMD Duron 1800Mhz
ASRock K7S8X motherboard
ATI Radeon 7000 32mb graphic driver

ubuntu-5.04 (I downloaded it couple days ago)

---

### Post by nawitus on 2005-08-14
I booted to recovery mode and it worked fine in the command line and I browsed some dirs for quite some time. Then I booted to graphical mode and it crashed very soon  :neutral:

---

### Post by jeremytaylor on 2005-08-14
I have similar problems. The freezes seem pretty random. Either it freezes in the first few minutes or it'll be fine for days. Seems dumb to me. Not sure if it's an xserver problem (the ati cards we both have are a bit notorious) or something else.

I'm hoping breezy badger will be the solution to all the problems but I doubt it :-)

sorry I couldn't help, just letting you know it's not just you!
jeremy

---

### Post by Hikaru79 on 2005-08-14
Hm, very strange. Log into X, wait for a crash. Then reboot, go into a recovery console, and make a copy of your /var/log/Xorg.0.log file. Then log back into X, and paste the contents of that copy here. Let's see if we can get through this =)

---

### Post by RaF93 on 2005-08-14
hmm seems I am not the only one with this kinda problem occuring from time to time...as the last occurence ended me using ubuntu for now and reverting to my win-install I'll do a restart later to recover the requested file.
Btw.think the GNOME freezes up thread is more or less the same prob as here...perhaps both threads should be joined?

---

### Post by hiruzzolo on 2005-08-14
I have your same problem with an amd sempron, asrock motherboard and ati radeon 7000... I wonder if it something about some driver because we have very similar computers...

---

### Post by RaF93 on 2005-08-14
Hmm here its an AMD CPU Sempron on an ABIT NF-S Board and an NVidia GT6600...though think the ATi GFX-Card can already be ruled out as the culprit...

Also checked the Xorg Config File...but as the last crash could have had even a different cause (sorry remembered just when I looked at the file) I dont think it helps us if I post this one. But if I should have to "normal" lockup, I ll do. Perhaps someone else could post his meanwhile?

New:
A seemingly unrelated error just seen (which perhaps though could be a cause as it imho is started automatically in the background from time to time and so could explain the lockup happening sporadically?):

(synaptic:8518): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by nawitus on 2005-08-15
Ok here is the log:
[http://pastebin.com/337258](http://pastebin.com/337258)

I checked it two times and for both crashes the last lines were same
"Could not init font path element unix/:7100, removing from list! "

Now, I googled for some and found this info
"That kind of error message means that X can't talk to the font server it is expecting to find listening on port 7100. This either means you've not got an X font server (so shouldn't be trying to use it), or it's died."
But I'm really newbie to linux so how can I fix it :O.

---

### Post by RaF93 on 2005-08-15
Just had a crash here now as well...and got the same last line as error. Browsed through all logs in /var/log and the rest looked quite normal.

---

### Post by jeremytaylor on 2005-08-15
you can get rid of that error by commenting out the line

FontPath	"unix/:7100"	

in the files section of your xorg.conf.
Not sure whether this has any knockon effects though. Or if it even stops the crashes! It was suggested in [http://ubuntuforums.org/showthread.php?t=56602](http://ubuntuforums.org/showthread.php?t=56602)

jeremy

---

### Post by heimo on 2005-08-15
I'm guessing. Power management / interrupt problems or ati drivers. Possible workarounds: Use vesa driver instead of ati or use 
 ```
         Option         "NoAccel"               "true"

``` option in device section (xorg.conf) of your graphics card. Edit grub configuration, add new entries with acpi=off (or noacpi), apic=off (or noapic).

Grub:
[https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)

xorg.conf:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

Sorry for being so light on details, these are faint guesses, but something that I would try.

---

### Post by nawitus on 2005-08-15
I uncommented "FontPath "unix/:7100" but still had a crash. The logs were the same but without the last line ""Could not init font path element unix/:7100, removing from list! ", atleast that is fixed for now (I think). But before that I have bunch of warnings about fonts:

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

---

### Post by jeremytaylor on 2005-08-15
If I turn off apci and apic will the cpu frequency scaling still work? My laptop runs very hot so without that It's really not usable.
thanks
Jeremy

---

### Post by nawitus on 2005-08-15
I turned off 'apci and apic' and finally it seems stable (I'm not 100% sure though). So I think its driver issue? But now window dragging and the browsers etc seem pretty laggy :/

---

### Post by heimo on 2005-08-15
[QUOTE=jeremytaylor]If I turn off apci and apic will the cpu frequency scaling still work? My laptop runs very hot so without that It's really not usable.
thanks
Jeremy[/QUOTE]

Probably not,  I believe apm (old power management) cannot substitute ACPI for everything. But I'm not suggesting this as a final solution, just a workaround and a way to isolate the cause.

---

### Post by heimo on 2005-08-15
[QUOTE=nawitus]I turned off 'apci and apic' and finally it seems stable (I'm not 100% sure though). So I think its driver issue? But now window dragging and the browsers etc seem pretty laggy :/[/QUOTE]

Did you also make NoAccel change to xorg.conf? That could slow down graphics.

---

### Post by nawitus on 2005-08-15
[QUOTE=heimo]Did you also make NoAccel change to xorg.conf? That could slow down graphics.[/QUOTE]

Yeah I made the NoAccel change. Should I change it back and see if it doesnt crash?

---

### Post by tmasboa on 2005-08-15
I have the same problem with a:
Foxconn mobo(not sure what model)
Intel Celeron D 2.66 Ghz
**ATI Radeon 9250**(seems like everyone who has this prob has and ATI)
40GB Seagate HD

Could someone tell me exactly how to fix it? I am kind of a newbie.

---

### Post by nawitus on 2005-08-15
For me I got it working with heimo's advice. Turning off apci and apic and gfx acceleration.

And commenting the NoAccel line makes the crashing constant again  ](*,)  so I'm going to stick with quite laggy linux  :-|

---

### Post by jeremytaylor on 2005-08-15
does it make a difference if you just change the noaccel line and leave the acpi stuff as it is by default?

jeremy

---

### Post by RaF93 on 2005-08-15
k, tried the other variants - i.e. noacpi and noapic - and system kept locking up.
So really seems acceleration is the culprit here - or I hope it is, cause then my system should finally run stable now

---

### Post by jeremytaylor on 2005-08-17
hi there.
i turned off the graphics acceleration and it's still crashing! 
Going to try all turning off all the power management too will see if that helps.

It seems that the crashes generally happen on the first boot of the day... why would that be?

thanks

Jeremy

---

### Post by tseliot on 2005-08-17
Have you got an integrated graphic card?

---

### Post by jeremytaylor on 2005-08-17
Hi, 
it's an asus w3v laptop with a ati radeon x600 mobility card.
any suggestions?
Jeremy

---

### Post by tseliot on 2005-08-18
1) get to the bios and make sure your graphic card is set as active. I have 2 graphic cards 1 PCI (ATI X200P, integrated) and 1 PCI-E (Geforce 6200, not integrated). I was using the PCI-E card and the computer hanged randomly. I had to set the default graphic adapter to PCI-E (it was set to PCI by default). My computer is a Compaq Presario. Something like this could have happened to you computer.

So check if the graphic card is PCI, PCI-E or AGP and then make sure your bios settings match with it.


2) Can you tell me the brand and model of you hardisk(s)? My SATA Seagate (160gb) broke down and made my computer hang (I've read somewhere it is not well supported by Linux)

---

### Post by jeremytaylor on 2005-08-18
Well there isn't even a setting in the BIOS for agp or other graphics cards. So that's not it.

The hard drive appears to be an Hitachi travelstar 80GB.  I think the interface on this laptop is SATA but with an older ATA drive stuck in anyway... I don't think any SATA laptop harddrives are on sale yet?

It crashed again today. It always seems to be the first boot of the day which is rather suspect. I've got the acpi and apic turned off and the noaccel flag on in my xorg.conf.

thanks for any help
Jeremy

---

### Post by tseliot on 2005-08-18
Ok, let's see if it's the graphic card. Try this while in Ubuntu:

ctl-alt-f1 (so as to get to the command line)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf

Scroll down (with your keyboard) the text until you find this section (this is my configuration):

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "[COLOR=Red]ati[/COLOR]"
BusID "PCI:1:5:0"

Substitute the word in red with “vesa”, make it look like this:
Section "Device"
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "vesa"
BusID "PCI:1:5:0"

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

/etc/init.d/gdm start (or "kdm start" if you use KDE)

See if the system freezes now

---

### Post by RaF93 on 2005-08-18
not sure if it helps u....but my crashes stopped finally with that NvAgp option.

---

### Post by jeremytaylor on 2005-08-19
Well yet again on the first boot of the day the machine froze. I now have the vesa drivers and noapci noapic. I'm no longer convinced that it is anything to do with the graphics card, I've tried the vesa, the xorg ati and radeon and the official ati drivers and all had the same behaviour.

I think the NvAgp option is for agp nvidia cards right? Probably not going to help a pci-express ati card?

Any other suggestions?
Thanks for the help so far
Jeremy

---

### Post by jeremytaylor on 2005-09-01
Hi there,
I seemed to have sorted this problem. For some reason the slocate script in cron.daily was completely freezing my machine. I remember having problems with updatedb slowing anything down on an old pc but not slocate freezing everything permanently (no hard drive activity, hard reset required type of freeze) on a brand new machine!
Oh well, don't use it often so just removed it from my cron.daily. Still puzzled by it though.
Thanks
Jeremy

---

### Post by Maier on 2005-09-01
It seems, when reading forums on the net, that ATI cards and Xorg, dosent go along very well.. more ATI users have switched tt Xfree, and others have to put in the VESA option in the xorg.conf file, to get it to work...

The thing is, that these options arent that good, for people liking 3d gfx.. :)

My gfx card came yeasterdat (GF 6600 GT AGP), and everything went smoothly, even 3D games are running very well..

---

