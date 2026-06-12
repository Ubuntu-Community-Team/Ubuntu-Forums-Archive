---
title: "How to enable special effects"
date: 2009-10-26
forum: Desktop Environments
---

### Post by Vignesh S on 2009-10-26
For some reason on my IBM Thinkpad R31, whenever I try to enable more special effects in the Appearance Manager, it says that "Desktop effects could not be enabled". I need to do this because I can't seem to make emerald themes work without them. I also can't enable anything in the advanced compiz config settings manager. I'm not interested in if it crashes or not, I just want to see if they can at least work, for I'm reinstalling it to 9.10 again anyway. On that, I'm doing this all in Ubuntu 9.10 RC. 

The point is, I just want emerald themes to work at the very least.

---

### Post by TenPlus1 on 2009-10-26
Try turning on the Composting feature in Metacity and then see if your emerald themes will work, here's how:

[http://ubuntu-tweak.com/2008/02/10/turn-on-the-compositing-feature-of-metacity.html](http://ubuntu-tweak.com/2008/02/10/turn-on-the-compositing-feature-of-metacity.html)

---

### Post by Vignesh S on 2009-10-27
Woudln't work. Tried re-enabling window manager, wouldn't load up again till I restarted it. Any other ideas out there?

---

### Post by raprap30 on 2009-10-27
Maybe its an error in the driver? Check your Xorg or try going to gconf-editor and enable "compositing-manager" in apps/metacity/general. You will get some compositing effects for your windows, transparency and other things. The "compositing-manager" might just work

---

### Post by Vignesh S on 2009-10-28
As I already said, I enabled compositioning effects in gconf-editor under /apps/metacity/general. And despite this, emerald themes are still not working. The strange thing is, the terminal and the two bars don't have a problem becoming transparent! I just don't get this at all. All I am asking here is how to get emerald themes working under a system that only has an intel i810G graphics chip (which in my experience, can't even handle powerpoint transitions in Vista :-( 

But just to make things clear to future responders, I have already done the gconf-editor thing, and emerald themes do not want to be enabled... :-(

EDIT: I might be onto something here. How would I start the CompizConfig icon in the start up applications? Seem very lost as to how I should do that since I have to find the start up file that does this, and I have no idea where it is

EDIT (again): Despite setting the window manager to Metacity and setting Emerald as default theme manager (and restarting the window manager), Emerald just won't load up its theme I have installed! Loading up Compiz Fusion icon won't do the job here, and I am still stuck at square 1 :-(

---

### Post by lrcaballero on 2009-10-28
Try this:

System
Preferences
CompizConfig. Settings Manager
Effects
Animations
Effects Settings (tab)

and make sure the ALL option is checked!!!!

This worked for me about 7 weeks ago, somehow I couldn't get the effects work until I tried the above!!!!!

Luis:D

---

### Post by murderslastcrow on 2009-10-28
You could always go to Hardware Drivers in System/Administration to make sure there isn't a video card driver available for installation.

To start emerald on startup, just make type the following command into a new startup applications entry.

emerald --replace

That should enable it on startup. If you still don't see the window borders, you may need to look into the drivers a bit more for your laptop.

---

### Post by Vignesh S on 2009-10-29
Right, lets get a couple of things ironed out here.

1. As I said, the graphics chip is an intel i810G. The drivers are already installed, and no, when I clicked on the "Hardware Drivers" icon, nothing showed up. Besides, the intel guys officially announced 5 years ago that they would halt support for that particular graphics chip, so I'm out of luck!

2. I went to the ccsm, and it worked to somewhat of a degree. That cool notification system now has a glassy effect when I mouse over it (AWESOME! Thanks for that :-D), but despite all, emerald themes just wouldn't work even after I reloaded the window manager!

3. I tried doing that emerald --replace thing, but still, emerald themes are not working :-(.

Surely, there has to be a way to get this to work...

---

### Post by Vignesh S on 2009-10-30
<bump> Surely there is a way?

---

### Post by Vignesh S on 2009-10-30
<bump> maybe there isn't ? :-(

---

### Post by Vignesh S on 2009-10-31
<bump> anyone know?

---

### Post by Castor68 on 2009-11-03
I have the same problem.

This is the output of **sudo lspci | grep VGA**

[COLOR="Blue"]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
01:0a.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
[/COLOR]

---

### Post by doppis on 2009-11-03
Did you remove your video drivers yet and reinstall them?

---

### Post by Castor68 on 2009-11-03
How?

Can I disable that Intel chipset?.

In the BIOS, the integrated videocard is disabled. 

Everything worked perfect with Hardy, but after I did a Karmic clean install, I can't enable those efects.

---

### Post by Castor68 on 2009-11-03
The accelerated proprietary graphics activated drive for the nVidia card is the 185.

---

### Post by Vignesh S on 2009-11-04
Well, I tried to force Compiz to work, but it crashed my lappy :-(. Had to reinstall Ubuntu 9.10 on it. Wouldn't boot into GNOME, even failsafe!

Is there anyway to get my themes to work via matacity?

---

### Post by Vignesh S on 2009-11-06
<bump> Surely there is a way to get emerald to work under metacity. I mean, awn works on this laptop without any hassles! It can't be that hard to get emerald to work can it? I mean, its just window decorations

---

### Post by Vignesh S on 2009-11-07
<bump> anyone? Surely, there has to be a way. Its just see through window borders here.

---

### Post by Vignesh S on 2009-11-11
Surely it can't be impossible. I mean, transparency worked with Google Gadgets (even the gadget adder had a translucent window border!)

EDIT: Now have a pic of my Desktop. You can see for yourselves that the Google Gadgets adder and my screenlets have no problem in transparency. Surely, it can't be that hard to add translucent window borders to my Desktop...

](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Vignesh S on 2009-11-11
The output of sudo lspci | grep VGA 

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

Matacity works perfectly fine on this thing. Surely, emerald can too...

And, the result of compiz --replace

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:3577' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by Vignesh S on 2009-11-11
Alright, that's it. I've given up on Emerald, since it most likely depends on Compiz, and that doesn't want to work. Rather, I've decided to focus on Metacity.

Anyone know any transparent/translucent gtk 2.x /Metacity themes out there?

---

### Post by Vignesh S on 2009-11-13
<bump>surely, there has to be a metacity theme out there that is translucent out there... I mean, the Google Gadgets adder didn't seem to have any problems with translucency...

---

### Post by Vignesh S on 2009-11-15
<bump>
Anyone.................

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Vignesh S on 2009-11-19
Oh well doesn't matter. I like my new GTK theme anyway :-D

---

### Post by Perturbed Penguin on 2009-11-20
As far as I am aware you must be running Compiz or Beryl to use Emerald themes... they will not work if you are running Metacity as your window manager... I think. As you have found I don't think enabling the Metacity compositing will help you any either. So if I am right about this then you would want to get things fixed up so that you can enable your desktop effects somehow - this would mean you would be using Compiz... unfortunately I don't have any suggestions as far as how to fix that issue you are having with your drivers or sounds like something like that. ...OR you could possibly look into installing the Beryl window manager which I believe is out of date since Beryl has merged back into Compiz. Nevertheless I THINK that if you can't get Compiz to work you MAY be able to get Beryl to work which should then allow you to use your Emerald themes. To sum up I recommend looking into how to install the 'Beryl window manager'. I'm sorry I can't be much more help in this area but there is a chance that looking into Beryl as an option may help you. Good luck! ;)

---

### Post by Vignesh S on 2009-12-15
Thanks for your advice, PerturbedPenguin. But I've got a newer and much better lappy  now, and that old IBM bugger isn't quite working anymore anyway.

But yeah, I prefer to stick to things that are current and not outdated, as I've learnt quite a few times the hard way. 

Thanks for your advice though. I'll keep that in mind when I come across an old computer which won't enable transparency as easily as newer hardware ;-)

---

### Post by Perturbed Penguin on 2009-12-18
Ah ditched ye olde 'top eh? lol Yeah I don't even know if Beryl is still functional on newer distros but certainly its an idea that I hope you won't ever HAVE to try. Cheers. ;)

---

