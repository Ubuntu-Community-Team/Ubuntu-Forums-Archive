---
title: "Trouble installing drivers for Nvidia graphics card"
date: 2009-02-23
forum: General Help
---

### Post by Kilon on 2009-02-23
> **Ferrat said:**
> It wasn't anything but whine and a "oh everything else is so much better post" = troll 

Just saying your drivers wont do what you want and that makes Ubuntu flawed in development etc isn't something of value

[http://video.google.nl/videoplay?docid=-4216011961522818645](http://video.google.nl/videoplay?docid=-4216011961522818645)

might want to check that video out

I'll stop saying troll when you actually show that you have at least tried to debug the problem and asked for help before throwing your arms up in the air and shouting "I hate this, I quit, this sucks etc etc, you guys are doing it wrong and so on" and you leaving doesn't really help the problem now does it, if there is something wrong the devs need to know about it, the more they know the faster they can address it.

ok fair enough... I did not say  UBUNTU sucks, i just was abit pisseed that is all. 


I respect that for Other people UBUNTU rocks, and that is perfectly fine, I do not see them as trolls, why you see me as one ? 

I admire what the community has done with UBUNTU. And it is free so no complaints there. 


I have no doubts that with some hacking the problem will be solved. And I am going to solve it. LOL

Nahh I am not going to leave UBUNTU. Probably I was bit too pissed off. But probably avoid updating anything in the future. I will leaving these things to people with alot more free time. 

Sorry In my haste I posted it to wrong forum.

So guys anyone can help ?

how do i edit the configuration files to use the native UBUNTU drivers even with low graphics settings ? Any links will be appreciated .

---

### Post by Simian Man on 2009-02-23
I have never had to download nVidia drivers from their site.  Usually on Ubuntu the restricted driver manager would be able to find them.  Was that not the case?

As a general rule in Linux, you should *always* try the package manager before resorting to 3rd party downloads.  This is much different than on Windows.

---

### Post by aj_ on 2009-02-23
If you're not used to the terminal, don't install things like drivers from source. The official binaries might sometimes be quite outdated, but at least you'll know that nothing will break when you install with synaptic (same isn't true for many distros, sadly).

---

### Post by Ferrat on 2009-02-23
Sounds better Kilon :)

Well might wanna try a ```
sudo dpkg-reconfigure xserver-xorg
```

Also as Simian Man said use Ubuntus built in stuff 

installing after the reconfigre should just be 

System >> Administration >> Hardware Drivers 

and selecting the nvidia driver and activating it :)

that should activate and install your nvidia drivers with just a restart :)

---

### Post by Kilon on 2009-02-23
> **Simian Man said:**
> I have never had to download nVidia drivers from their site.  Usually on Ubuntu the restricted driver manager would be able to find them.  Was that not the case?

As a general rule in Linux, you should *always* try the package manager before resorting to 3rd party downloads.  This is much different than on Windows.

No I had problems , like failure to redraw the windows title bar, blender could not run in windowed mode , several crashes etc. 

I tried regular updating 

Synaptic

Envy

and downloading from nvidia

I suspect that compiling from source that the nvidia installer did created the problem. Another ubuntu user daviced me to unistall envy as it could create problems as well, but envy does not uninstall cause it is missing "interface.py" 

Oh well UBUNTU does not seem to like me... lol

---

### Post by Kilon on 2009-02-23
> **Ferrat said:**
> Sounds better Kilon :)

Well might wanna try a ```
sudo dpkg-reconfigure xserver-xorg
```

Also as Simian Man said use Ubuntus built in stuff 

installing after the reconfigre should just be 

System >> Administration >> Hardware Drivers 

and selecting the nvidia driver and activating it :)

that should activate and install your nvidia drivers with just a restart :)

Thanks ferrat , I will try it and post back the result. I hope it works because there is no GUI working at the moment only the terminal.

---

### Post by tad1073 on 2009-02-23
[http://ubuntuforums.org/showthread.php?t=1071283](http://ubuntuforums.org/showthread.php?t=1071283)

---

### Post by Kilon on 2009-02-23
I tried Ferret approach and tad1073 , but still no lack. UBUNTU is screwed. 

I manage to start the gui with "gdm start" but to my surprise there is no longer a net and internet capability, also the sound card has gone . But still no regular boot. Keyboard frozen even in recovery mode some times.

If I install UBUNTU on top of my old installation will I lose all the available configuration ?

---

### Post by overdrank on 2009-02-23
Moved to General Help

---

### Post by Can+~ on 2009-02-23
> **Kilon said:**
> Well I have nothing to lose, now .... as it is I cannot us Ubuntu at all.

You can backup some of the configuration files from the live-cd.

As a general rule of thumb with debian-based distros: stick to whatever is available in your repository.

---

### Post by Kilon on 2009-02-23
> **Can+~ said:**
> You can backup some of the configuration files from the live-cd.

As a general rule of thumb with debian-based distros: stick to whatever is available in your repository.

thanks mod, sorry mod... 

I saw that probably it is not possible to do what I want . Oh well, I will lose some hours from my life and install Ubuntu from scratch.

Yes Can , I have learned the hard way , no more updates and customization , will stick with only the basics.

---

### Post by stchman on 2009-02-23
> **Kilon said:**
> Tried to update my graphic card driver today. NVIDIA 6200 PCI, I went to nvidia website , downloaded the packed universal driver for linux, followed the ubuntu installation instructions, stoped the NVIDIA Server and entered the appropriate command the terminal that so much hate. 

The installation executed , downloaded the appropriate drivers , could not find binaries, compiled to source , assured that all went perfectly. And of course all went to hell!!!!

The next boot welcomed me with a dialog complaining that the configuration files of the graphics card are screwed and have to update. Problem is that everything is frozen, no mouse , no keyboard, ubuntu is dead . 

The only way to access terminal is via recovery boot , but of course i hate terminal and afterall UBUNTU has created so many more problems that it actually solved that besides viruses and spyware I do not see any other big advantage compared to windows. 

Of course there is no comparison between UBUNTU and my favourite OS , MACOS. UBUNTU developers should learn alot of thing from MACOS user friendlines, UBUNTU looks , but certain is not cool. Under the surface , is still too much terminal dependent and its installation/unistallation features may look more impressive than other OS but they are fundamentally lacking.

I am so sorry I have to leave the UBUNTU , I am a huge fan of open source and admire what people have done with their free time. But I cannot see any real benefit to make me switch from MACOS and Windows.  

May be I will be back one day that LINUX has really matured.

So enabling the Nvidia restricted driver did not work?  I have (3) Nvidia cards (8800GT, 7600GT, 5700 Ultra) and all work with the restricted driver enabled.

A little pop up tells you about it.  You don't need to download the latest driver as the 6200 card is pretty old.

---

### Post by makisupa123 on 2009-02-23
Not sure about your non-video related issues.  Unless you've done something to your machine not reported in this thread they are not related.

You need to make sure that the old version is properly removed.  From a tty do the following:

Stop GDM.
```
/etc/init.d/gdm stop
```

run envyng (-t) and make sure the driver from synaptic has been removed.
```
envyng -t
```  
If you end up removing it using envyng, you should prolly reboot.  Stop gdm again and run the installer you downloaded.  


This is, of course, unless you've already re-installed from scratch.

--Mak

---

### Post by Martje_001 on 2009-02-23
[SIZE="1"][Off-topic][/SIZE] Is it just me or is everyone here a bit rude? [SIZE="1"][/Off-topic][/SIZE]

You could try EnvyNG to install your graphic drivers. It's in the repository's. The package is called envyng-qt (since the gtk interface is disabled :().

---

### Post by stchman on 2009-02-23
> **Kilon said:**
> Tried to update my graphic card driver today. NVIDIA 6200 PCI, I went to nvidia website , downloaded the packed universal driver for linux, followed the ubuntu installation instructions, stoped the NVIDIA Server and entered the appropriate command the terminal that so much hate. 

The installation executed , downloaded the appropriate drivers , could not find binaries, compiled to source , assured that all went perfectly. And of course all went to hell!!!!

The next boot welcomed me with a dialog complaining that the configuration files of the graphics card are screwed and have to update. Problem is that everything is frozen, no mouse , no keyboard, ubuntu is dead . 

The only way to access terminal is via recovery boot , but of course i hate terminal and afterall UBUNTU has created so many more problems that it actually solved that besides viruses and spyware I do not see any other big advantage compared to windows. 

Of course there is no comparison between UBUNTU and my favourite OS , MACOS. UBUNTU developers should learn alot of thing from MACOS user friendlines, UBUNTU looks , but certain is not cool. Under the surface , is still too much terminal dependent and its installation/unistallation features may look more impressive than other OS but they are fundamentally lacking.

I am so sorry I have to leave the UBUNTU , I am a huge fan of open source and admire what people have done with their free time. But I cannot see any real benefit to make me switch from MACOS and Windows.  

May be I will be back one day that LINUX has really matured.

Enable the restricted driver.

---

### Post by stchman on 2009-02-23
Did you enable the restricted driver?  That is all you need for that card.

---

### Post by Kilon on 2009-02-24
Well I decided to say bye bye to UBUNTU without saying bye bye . How I will do that ?

Well easy, I will run via VM UBUNTU from inside WINDOWS and this way everyone is happy. 

Thanks sledge for the suggestion and yes I am a greek like you

---

### Post by Hallvor on 2009-02-24
It is a good idea to stick with the repositories. Downloading and installing packages from webpages on the internet may break your system. It is just as bad as running random .exe files from the internet on Windows. Sure, you might be lucky, but you`ll probably end up borking your install sooner or later.

Secondly, it is always a good idea to backup your system just in case. My main computer broke down last summer. Fortunately I had made a backup livecd that I was able to install on the new computer. It all took me about 15-20 minutes to install everything on the new computer. Setting up everything the way I wanted it all over again would have taken me hours.

---

### Post by Kilon on 2009-02-24
> **Hallvor said:**
> It is a good idea to stick with the repositories..

If I did I would be still working in a 800x600 resolution and lacking loads of absolutely necessary features.

---

### Post by Hallvor on 2009-02-24
> **Kilon said:**
> If I did I would be still working in a 800x600 resolution and lacking loads of absolutely necessary features.

That is pretty bad. Perhaps you`ll have more luck with a different distro. I don`t know. Use whatever that works for your hardware.

---

### Post by Kilon on 2009-02-24
> **Hallvor said:**
> That is pretty bad. Perhaps you`ll have more luck with a different distro. I don`t know. Use whatever that works for your hardware.


Hmm tried to install 8.10 UBUNTU via VM , thing are even worse here, cannot apply my usual hacks , resolution is locked at 800x 600. I will try to uninstall and install 8.04 . 

Anyone knows a distro that is graphic driver friendly ?

---

### Post by Kilon on 2009-02-24
> **stchman said:**
> Did you enable the restricted driver?  That is all you need for that card.


They cannot be enabled, probably because I run Ubuntu through VM. 

Is there a way to increase my resolution without them ?

---

### Post by makisupa123 on 2009-02-24
WAIT -- you're trying to install the nvidia drivers in an ubuntu install on a VM?

You can't do that.  You can't use the NVIDIA drivers and you can't use visual effects.  Visual effects require direct rendering.

--Mak

---

### Post by jbysmith on 2009-02-24
> **Kilon said:**
> Hmm tried to install 8.10 UBUNTU via VM , thing are even worse here, cannot apply my usual hacks , resolution is locked at 800x 600. I will try to uninstall and install 8.04 . 

Anyone knows a distro that is graphic driver friendly ?

Just out of curiosity, did you install the "guest additions" (IE drivers) for your particular VM?  It'll probably think it's a standard SVGA adapter otherwise.  You *should* be able to resize the resolution to anything you want if configured properly, get the "integrated mouse" and all that too.

Ubuntu's actually pretty easy on its proprietary drivers.. click and go unless you want bleeding edge from the manufacturer, then it gets a little trickier.  

If you're toying with a virtual machine, go distro-hopping a bit then, maybe find one that suits you better.  openSUSE is pretty easy to get going, PCLinuxOS, Fedora and Mandriva are other decent alternatives too. DistroWatch will have a full list, links to reviews, etc etc.  Arch is my distro of choice myself, but a lot more hands on.. but still dead easy to install drivers.  One pacman commmand and off you go.  (Thats their package manager) Give 'em a try, if you don't like, remove and move on to the next one.  Keep in mind the performance and drivers in a VM versus your real machine will differ wildly, but it'll give you a good idea what to expect anyway.

---

