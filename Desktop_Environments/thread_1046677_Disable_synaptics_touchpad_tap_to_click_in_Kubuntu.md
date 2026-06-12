---
title: "Disable synaptics touchpad tap to click in Kubuntu."
date: 2009-01-21
forum: Desktop Environments
---

### Post by ScottyDelicious on 2009-01-21
I have been using Ubuntu and gnome for a while (6.10 - 8.10) and this past week I decided to give KDE a try. 

In Ubuntu's Gnome, I select System > Preferences > Mouse, and there is a trackpad configuration GUI. I simply unchecked the option to click with trackpad taps and I was good to go.

In Kubuntu's KDE, there is no GUI config for this (also, there is no GUI config for the trackpad in Fedora 10's Gnome).

Digging around in xorg.conf, I found a very sparse config file. No mention at all about synaptics or input devices. Now I have to dig into HAL fdi XML files (which I will admit, I am not that familiar with yet). Long story short, I had to make a synaptics options fdi.
```
sudo kate /etc/hal/fdi/policy/11-synaptics-options.fdi
```

Put this in the file, save it, and log out then back in to restart X.
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
     <match key="input.x11_driver" contains="synaptics">
         <merge key="input.x11_options.SHMConfig" type="string">On</merge>
         <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
       </match>
    </device>
</deviceinfo>
```

I am hoping someone can correct me and show me that there is in fact a gui control to do this in KDE 4.

I feel really comfortable with administering Linux based systems from the command line (more so Debian and Red Hat based systems than others), and I feel right at home in Gnome, but I am cursed with forever having to tinker with my system and learn new ways to do things, so here's to hoping I can get more familiar with KDE :)... Just for the fun of learning.

---

### Post by Bat on 2009-01-31
Thank you, Doctor, for that answer.  I had to work it out myself on an earlier installation, but I'd forgotten it all by the time I got to this one.

In answer you your plea for a GUI interface: it looks like the sad-sacks who are "maintaining" KDE4 don't care much to have it used by real people, because this is exactly the sort of thing they haven't bothered to port from KDE3 where it worked perfectly well.  Is it any wonder Linus Torvalds gave up on them and moved to Gnome?  I'm just hoping KDE 4.2 will prove minimally usable; otherwise I'm upgrading my new 8.10 installation to the far superior and better-supported 8.04, where it will stay for a year or two until these guys get some clue.

---

### Post by elyboy on 2009-04-25
I installed kubuntu 9.04 64bit. It seems that a GUI for disabling touchpad is not yet available.

---

### Post by fatboab on 2009-05-03
This issue has been really frustrating me over the last month since I finally totally ditched windows. Thanks for the solution, it worked like a charm.

Cheers,

-- 
Bob.

---

### Post by TitanTiger on 2009-05-05
Oh, thank the sweet Baby Jesus I found this thread.  It worked and now I can type normally.  

Thanks for the solution!

---

### Post by Zorael on 2009-05-06
Yeah, there is no KDE4 tool to configure touchpads currently. Perhaps that's worthy of a KDE bugtracker wishlist report.

I think you can install the **gsynaptics** package and use the GNOME standalone utility, though it's been discontinued. And I'm not sure that's what GNOME is currently using. There used to be a ksynaptics package (and a qsynaptics one), but I think they went missing in Hardy.

From [http://qsynaptics.sourceforge.net:](http://qsynaptics.sourceforge.net:)
> **12/01/08** *(read: January last year)*

[SIZE="4"]TouchFreeze for Linux pre 0.2 and annoucing end of {q/k}synaptics[/SIZE]
First the rant, then the grant ;)

You all know that {k,q}synaptics development had been rather slow lately.
I even will stop it completely now, and I will explain you why:

You might have noticed that the latest ksynaptics version does not work any more once again.
As you know your touch pad in X can be accessed if you use the synaptics driver. Since its interface had been subject of change I developed libsynaptics to encapsulate the functionality across different driver versions.
Something happened short time ago and the driver got accepted into the XOrg tree (is that right?).
But now again the interface is changing and nobody cared to update the version numbering the driver reports. Besides there does not seem to be much attention to what would be needed to have a clean interface to access and configure the driver.

Strictly spoken, there's not much I can do about it! So I decided to copy the functionality of TouchFreeze for Windows (a GoS Project) to create something which is much easier to maintain but similary useful nevertheless!
First I tried to use something like Xevie to catch native events but it is both insecure and buggy. Hence, a no-go.
So I finally basically copied the functionality of 'syndaemon' into a Qt4 tray applet which can be used with KDE3/4 and Gnome.

I know it is still a hack, but it took me only a few hours and works for me (Ubuntu, with synaptics driver shm access enabled) which is awesome compared to the ongoing troubles I faced during the maintenance of ksynaptics.

So, please, download it and be happy or even enhance the code, there is still a lot of small improvements to be done...

I'd like to thank all people that helped me during development, it has been fun working with you, and maybe sb wants to grab up the work and integrate it in KDE4 (that would be nice, even platform independence seems possible)

Facts:
# works for me on KUbuntu
# needs /usr/bin/synclient
# needs synaptics driver shm access enabled

Put the binary in your ~/.kde/Autostart or whatever - that should do the trick!

Yeah, and happy new year, of course :)

Googling around, I find [http://gsynaptics.sourceforge.jp](http://gsynaptics.sourceforge.jp).
> [SIZE="4"]Announce[/SIZE]

GSynaptics will be obsolete. Please try [GPointing Device Settings](http://live.gnome.org/GPointingDeviceSettings).
There are no packages that match gpoint* in the repositories, though perhaps it's a core GNOME component. With {q,k,g}synaptics discontinued, perhaps that's what it's using now?

See [http://blog.fekw.de/2008/09/22/kubuntu-howto-configure-synaptic-touchpad](http://blog.fekw.de/2008/09/22/kubuntu-howto-configure-synaptic-touchpad) for a guide on how to install touchfreeze.

Alternatively, of course, configure it via HAL or xorg.conf.

---

### Post by squaregoldfish on 2009-05-14
Just as a note for followers of the OP's excellent advice: I found that I had to reboot to get the HAL config change to take effect instead of just restarting X.

Steve.

---

### Post by nicafyl on 2009-07-14
Thank you, gracias. I have read "how to do this" in 10 other places, all of them wrong.

It sucks that there is nothing in the GUI to do this but, at least it is done.

---

### Post by krazyd on 2009-07-15
It's very easy to disable the tap-to-click while typing in KDE4.

Go to System Settings > Advanced > Autostart > Add Program... and enter:
```
syndaemon -d -t
```
This will disable your touchpad tap-to-click functionality for 2 seconds after you stop typing and makes my laptop much more usable.

---

### Post by 7x1x on 2009-08-19
Adding this to /etc/hal/fdi/policy/11-x11-synaptics.fdi will disable tapping.

```

<merge key="input.x11_options.TapButton1" type="string">0</merge>
<merge key="input.x11_options.TapButton2" type="string">0</merge>
<merge key="input.x11_options.TapButton3" type="string">0</merge>

```TapButton1 is a one finger tap, TapButton2 is a two finger tap, TapButton3 is a three finger tap. Multi finger tapping only works if your hardware supports it.

0 disables tap, 1 is left click, 2 is middle click, 3 is right click.

---

### Post by Detroit_Bad_Boy on 2009-09-27
**[SOLVED]**> **ScottyDelicious said:**
> I have been using Ubuntu and gnome for a while (6.10 - 8.10) and this past week I decided to give KDE a try. 

In Ubuntu's Gnome, I select System > Preferences > Mouse, and there is a trackpad configuration GUI. I simply unchecked the option to click with trackpad taps and I was good to go.

In Kubuntu's KDE, there is no GUI config for this (also, there is no GUI config for the trackpad in Fedora 10's Gnome).

Digging around in xorg.conf, I found a very sparse config file. No mention at all about synaptics or input devices. Now I have to dig into HAL fdi XML files (which I will admit, I am not that familiar with yet). Long story short, I had to make a synaptics options fdi.
```
sudo kate /etc/hal/fdi/policy/11-synaptics-options.fdi
```Put this in the file, save it, and log out then back in to restart X.
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
     <match key="input.x11_driver" contains="synaptics">
         <merge key="input.x11_options.SHMConfig" type="string">On</merge>
         <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
       </match>
    </device>
</deviceinfo>
```I am hoping someone can correct me and show me that there is in fact a gui control to do this in KDE 4.

I feel really comfortable with administering Linux based systems from the command line (more so Debian and Red Hat based systems than others), and I feel right at home in Gnome, but I am cursed with forever having to tinker with my system and learn new ways to do things, so here's to hoping I can get more familiar with KDE :)... Just for the fun of learning.


Thank You VERY much for this!! I was going NUTS trying to type without hitting the touch pad. It worked like a charm!! 
Good on you!!!!

---

### Post by Strongman332 on 2009-11-01
> **ScottyDelicious said:**
> I have been using Ubuntu and gnome for a while (6.10 - 8.10) and this past week I decided to give KDE a try. 

In Ubuntu's Gnome, I select System > Preferences > Mouse, and there is a trackpad configuration GUI. I simply unchecked the option to click with trackpad taps and I was good to go.

In Kubuntu's KDE, there is no GUI config for this (also, there is no GUI config for the trackpad in Fedora 10's Gnome).

Digging around in xorg.conf, I found a very sparse config file. No mention at all about synaptics or input devices. Now I have to dig into HAL fdi XML files (which I will admit, I am not that familiar with yet). Long story short, I had to make a synaptics options fdi.
```
sudo kate /etc/hal/fdi/policy/11-synaptics-options.fdi
```

Put this in the file, save it, and log out then back in to restart X.
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
     <match key="input.x11_driver" contains="synaptics">
         <merge key="input.x11_options.SHMConfig" type="string">On</merge>
         <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
       </match>
    </device>
</deviceinfo>
```

I am hoping someone can correct me and show me that there is in fact a gui control to do this in KDE 4.

I feel really comfortable with administering Linux based systems from the command line (more so Debian and Red Hat based systems than others), and I feel right at home in Gnome, but I am cursed with forever having to tinker with my system and learn new ways to do things, so here's to hoping I can get more familiar with KDE :)... Just for the fun of learning.

this no longer works in 9.10

---

### Post by Zorael on 2009-11-01
> **Strongman332 said:**
> this no longer works in 9.10

You can do something like what's explained in [this post](http://ubuntuforums.org/showpost.php?p=7643273&postcount=2), or use synclient. See 'synclient -l' for a listing of available settings. As for xinput;
```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0 0 0 0 0 0 0
```

---

### Post by commonplace on 2009-11-01
> **Zorael said:**
> You can do something like what's explained in [this post](http://ubuntuforums.org/showpost.php?p=7643273&postcount=2), or use synclient. See 'synclient -l' for a listing of available settings. As for xinput;
```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0 0 0 0 0 0 0
```

Two things:

1. How on earth can there STILL not be a GUI for this? This is beyond basic.

2. If I use the command you gave (the xinput one), is that persistent across reboots? Do I just type that in once and then it's set for good? Or do I need to put that in startup somehow/somewhere?

Thanks for this!

/Kevin

---

### Post by danzvash on 2009-11-03
Ok, stop press. 

I too was at a loss for why KDE/Kubuntu don't have a GUI disable the touchpad clicking. AFAIK, no KDE distro has it by default.

All the other responses in this thread may work, at least to begin with, but they are ALL hacks and not the way to maintain a well-ordered system.

A guy called Micha&#322; &#379;ar&#322;ok has written the GUI, as a module for the KDE control center. It's called kcm_touchpad and you can [see the KDE-APPS page here.]("http://www.kde-apps.org/content/show.php/kcm_touchpad?content=113335&PHPSESSID=106d176a58d010794536f3e960124d1e")

To add kcm_touchpad, see [Michal's PPA page.]("https://launchpad.net/~mishaaq/+archive/ppa/")

Or if you wanna do this quickly (so you can have this working in 2 minutes), open a console and do this:

Add these 2 lines to your /etc/apt/sources.list (use sudo vi/nano/kate editor you want) :
[I]deb [http://ppa.launchpad.net/mishaaq/ppa/ubuntu](http://ppa.launchpad.net/mishaaq/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/mishaaq/ppa/ubuntu](http://ppa.launchpad.net/mishaaq/ppa/ubuntu) jaunty main 
[/I]
Get the key for Michal's PPA repo:
# wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2D483981C80D1CD6" -O- | sudo apt-key add -

and update your package list
# sudo apt-get update

Install the bits
# sudo apt-get install kcmtouchpad libsynaptics0

Restart KDE control center, click the Keyboard & Mouse icon and hey presto: you now have a new Touchpad section with loads of options.

So - why has KDE4 not got this by default?

---

### Post by commonplace on 2009-11-03
> **danzvash said:**
> Ok, stop press. 

I too was at a loss for why KDE/Kubuntu don't have a GUI disable the touchpad clicking. AFAIK, no KDE distro has it by default.

All the other responses in this thread may work, at least to begin with, but they are ALL hacks and not the way to maintain a well-ordered system.

A guy called Micha&#322; &#379;ar&#322;ok has written the GUI, as a module for the KDE control center. It's called kcm_touchpad and you can [see the KDE-APPS page here.]("http://www.kde-apps.org/content/show.php/kcm_touchpad?content=113335&PHPSESSID=106d176a58d010794536f3e960124d1e")

To add kcm_touchpad, see [Michal's PPA page.]("https://launchpad.net/~mishaaq/+archive/ppa/")

Or if you wanna do this quickly (so you can have this working in 2 minutes), open a console and do this:

Add these 2 lines to your /etc/apt/sources.list (use sudo vi/nano/kate editor you want) :
[I]deb [http://ppa.launchpad.net/mishaaq/ppa/ubuntu](http://ppa.launchpad.net/mishaaq/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/mishaaq/ppa/ubuntu](http://ppa.launchpad.net/mishaaq/ppa/ubuntu) jaunty main 
[/I]
Get the key for Michal's PPA repo:
# wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x2D483981C80D1CD6" -O- | sudo apt-key add -

and update your package list
# sudo apt-get update

Install the bits
# sudo apt-get install kcmtouchpad libsynaptics0

Restart KDE control center, click the Keyboard & Mouse icon and hey presto: you now have a new Touchpad section with loads of options.

So - why has KDE4 not got this by default?

I tried that repo but it didn't work. Maybe because I'm using Karmic (9.10) and not Jaunty (9.04)? Or maybe because I'm 64-bit? Not sure, but I couldn't get it to work. When I did the sudo apt-get update, I got this:

```
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/mishaaq/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas? (Thanks for your help, btw!)

/Kevin

---

### Post by Zorael on 2009-11-06
> **commonplace said:**
> I tried that repo but it didn't work. Maybe because I'm using Karmic (9.10) and not Jaunty (9.04)? Or maybe because I'm 64-bit? Not sure, but I couldn't get it to work. When I did the sudo apt-get update, I got this:

```
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/mishaaq/ppa/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas? (Thanks for your help, btw!)

/Kevin
Yes, if you check the link ([https://launchpad.net/~mishaaq/+archive/ppa/+packages](https://launchpad.net/~mishaaq/+archive/ppa/+packages)) you'll see there are only packages compiled for jaunty in there.

You could add it as a jaunty repo though.

---

### Post by agim on 2009-11-08
Has anyone found a fix for this on Kubuntu 9.10? I would like to disable the mouse clicks capability entirely.

---

### Post by dylan66 on 2009-11-22
yes, this is very frustrating ... i tried the kcm touchpad option but
while it does install in my kubuntu 9.10 the touchpad tapping
section is blanked out ....

---

### Post by wilee-nilee on 2009-11-22
Is touchfreeze in kubuntu?

If it's not you can download it.
[http://linux.softpedia.com/get/Utilities/TouchFreeze-28533.shtml](http://linux.softpedia.com/get/Utilities/TouchFreeze-28533.shtml)

---

### Post by justbill6942 on 2010-01-15
If you just download the .deb from this link.  Then double click the deb and use the installer you should be good.  This link is for the 64bit version.

[https://launchpad.net/~mishaaq/+archive/ppa/+files/kcmtouchpad_0.3.0-1_amd64.deb]("https://launchpad.net/~mishaaq/+archive/ppa/+files/kcmtouchpad_0.3.0-1_amd64.deb")

---

### Post by will_in_houston on 2010-02-06
I'm not using kubuntu, but found that the option to disable taps on the touchpad in ubuntu 9.10 mostly worked -- but it still left in place the ability to do a "right-click" on the touch pad by tapping in the lower right corner.

Not that I'd intentionally be tapping there, but sometimes (often -- all the time really) it would happen accidentally while typing.

Selecting "disable touchpad while typing" in the gnome GUI mouse config app did nothing.

But, thankfully, you're fix worked.  Now I can type away and not have random right-clicks doing all sorts of things (like creating new folders on the desktop, closing the window I was typing in, and otherwise just being so annoying that I couldn't do anything).

Now I'm all happy.  Thanks.

Will

---

### Post by jtGohan on 2010-07-04
> **ScottyDelicious said:**
> 
In Kubuntu's KDE, there is no GUI config for this (also, there is no GUI config for the trackpad in Fedora 10's Gnome).

Digging around in xorg.conf, I found a very sparse config file. No mention at all about synaptics or input devices. Now I have to dig into HAL fdi XML files (which I will admit, I am not that familiar with yet). Long story short, I had to make a synaptics options fdi.
```
sudo kate /etc/hal/fdi/policy/11-synaptics-options.fdi
```Put this in the file, save it, and log out then back in to restart X.
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
    <device>
     <match key="input.x11_driver" contains="synaptics">
         <merge key="input.x11_options.SHMConfig" type="string">On</merge>
         <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
       </match>
    </device>
</deviceinfo>
```I am hoping someone can correct me and show me that there is in fact a gui control to do this in KDE 4.

I feel really comfortable with administering Linux based systems from the command line (more so Debian and Red Hat based systems than others), and I feel right at home in Gnome, but I am cursed with forever having to tinker with my system and learn new ways to do things, so here's to hoping I can get more familiar with KDE :)... Just for the fun of learning.

I can confirm that this method works for me in karmic kubuntu on my hp dv6000 laptop.  I agree there needs to be a gui in system settings for touchpads.  For a while I would just just use the disable touchpad button on my laptop when using a usb mouse.  But when not using a usb mouse this became really annoying when typing since I would always accidentally touch the touchpad and have the cursor move to random places. But now there is no need for the disable touchpad button.  Hopefully it works for lucid when upgrade to it next year or so.

---

