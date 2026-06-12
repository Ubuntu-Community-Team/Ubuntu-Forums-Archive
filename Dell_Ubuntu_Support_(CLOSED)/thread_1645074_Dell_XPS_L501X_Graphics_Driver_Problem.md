---
title: "Dell XPS L501X Graphics Driver Problem"
date: 2010-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dragonss on 2010-12-14
Hello there,

I hav recently bought a dell XPS L501 and installed Ubuntu 10.10 on it.

It has i3 processor, a Nvidia GT420M Gfx card and 4gb of Ram.

When i install the graphics driver as recommended by  System > Administration > Additional Drivers
The system starts showing the console.

From where should i install the proper graphics driver for my system.

I am a complete newbie........I hav searched thru the forum and found out abt some Optimus technology issue of Dell systems........But don't really understand it.

Can somebody please show me some easier way?....

I wud be very gr8ful.......


Thanks

---

### Post by ibizatunes on 2010-12-14
welcome, I would suggest that you post next time in the absolute beginner bit
Did you install the x64 or x32 bit version, with 4gb of ram you should install x64 ubuntu

[http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

---

### Post by tylerwagler on 2010-12-16
This is a fairly legitimate problem. I spent most of last night trying to get the graphics driver to work. The new Dell XPS line does something weird with an intel and an nvidia adapter. lspci shows both. After installation of the driver, X won't start because its using the wrong PCI bus ID for the nvidia adapter. if you add "BUSID: "2:0:0" " following the Vendor section X will try to start. I can hear the sound ubuntu makes when the login screen shows, but the screen is frozen back at the command promt. By frozen, I mean frozen. Nothing moves, and you cannot type. The machine is still active though, because Ctrl+Alt+Delete works to reboot. From what I've gathered, this problem may be limited to the i5 versions of the new XPS's, but I cannot verify.
 
Dell XPS L501X
Intel Core i5-560M
6GB,DDR3,2 DIMM
NVIDIA GeForce GT 420M 1GB graphics with Optimus <--Problem child
 
Ubuntu 10.10 x64 all updates completed
 
I will post my lspci and xorg.conf when I get home.
 
Edit:  Scratch that.  After some reading on the nVidia linux support forums I have found that nvidia has no intention of ever supporting systems with optimus technology.  Looks like I just spent $1500 on a laptop I can't use linux on.  Yay!!
Post #2 is the winner: [http://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477](http://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477)

---

### Post by krunalpatel on 2010-12-16
The default driver works fine for me. I can watch 1080p movies and run compiz. To play games, I obviously dual boot with win 7 (which have the latest drivers). Until hybrid drivers are made for us, we can't do much really. I had the same exact problem you guys are having... not much u can do

---

### Post by Ju4n on 2011-01-01
It seems we all passed through that... I'm also dual-booting for gaming, for everything else in Ubuntu the Intel driver works fine, besides, you save battery life ^^

---

### Post by hansen55 on 2011-01-24
Since you cannot upgrade or change the graphics card of a laptop, you  cannot raise this score. New drivers might raise the score a bit, but  this is not very likely. Keep in mind though that this score does not  mean a thing really. It is currently only being used to determine if  your computer or laptop can display the Aero interface properly. Simply  ignore this score therefore. Improving this score will not make things  better, as your hardware itself will never change.

=============
[business opportunity](http://www.starscapes.com)
[orlando airport transportation](http://www.alwayssuperb.net)

---

### Post by svast on 2011-01-25
Since the usability of the onboard NVIDIA chip is unsupported, we can only rely on the Intel graphic adapter.

1) there is no way for the moment to switch off the nvidia chip, in order to save battery life

2) the fact is that this driver is not so good as it could be:
 - no correct support for external display with display-port output (it cannot display on higher resolution than the laptop native screen).
 - I could not enable the hdmi output.

Of course, this work out of the box with Windows7.

My config: XPS 15 L501X, 4GB RAM, 1366x768 screen res.
If i do connect a full-HD monitor (ACER V223HQ), the resolution is set at 1366x768, not 1920x1080 (not listed in the Screen section of the GUI tool).


Does anyone have better luck?

---

### Post by Teg_Navanis on 2011-01-26
Displayport works with the i5 L501X? This is huge news! I don't expect the Nvidia card to be supported anytime soon, and HDMI (and thus external monitors) not working made me regret my purchase. If I can use a Displayport-to-HDMI adapter as a workaround, this will hugely boost the usefulness of my machine.

I'll try getting an adapter today, and will report back. I have a 1920x1080 display built-in, so it may be useful for others to know what resolution I can get on the external monitor.

---

### Post by svast on 2011-01-26
Intel graphic driver: displayport do seem to work, I tried with a Displayport-to-VGA adapter.
My problem is on the display resolution which is not the external native.

And I did not know there is displayport-to-hdmi adapter on the market, very interested in hearing that's working!

---

### Post by Teg_Navanis on 2011-01-29
I just got my Mini DisplayPort to HDMI adapter today ([http://store.moshimonde.com/hdmi-adapter-1.html](http://store.moshimonde.com/hdmi-adapter-1.html)).

It works! and in FullHD! :)
I don't know if having a FullHD built-in display matters (it shouldn't), but the monitor is recognized in my monitor preferences, so the route over HDMI might be worth a try for you (or you could configure the display manually in your Xorg.conf).

---

### Post by rasos on 2011-10-26
The ubuntu community is now providing a suitable driver for NVIDIA optimus :smile:

To download, add the following repository:
> **[B]ppa:mj-casalogic/ironhide**[/B]reload all repositories:
> sudo apt-get updateinstall the driver:
> sudo apt-get install ironhideYou will be guided through the configuration. Select a template, then choose XV. 

Find all packages here: [https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/+packages")

--rasos

---

