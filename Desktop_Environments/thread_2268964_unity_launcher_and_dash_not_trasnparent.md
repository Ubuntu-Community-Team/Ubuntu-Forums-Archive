---
title: "unity launcher and dash not trasnparent"
date: 2015-03-12
forum: Desktop Environments
---

### Post by Moofus on 2015-03-12
I installed ubuntu 14.04 UEFI off an external usb 3.0 dvd drive, and everything went fine, until i booted it up and noticed the launcher and dash werent transparent.  I googled and found another post that said to install compiz config settings manager and enable the ubuntu unity plugin.  i did, and after i enabled it, it enabled lots of other stuff like compositor and whatever else.  Then i closed it and wondered if i needed to log out and back in for it to reset.  I did that, and it still wasnt transparent, i looked in unity tweak tools to see if it was set to be transparent, and it was, but still wasnt doing it. since then ive rebooted at least three times and installed updates, and it still hasn't become transparent.  i dont think its worth a reinstall to fix it, but it would be nice if i could get it working.  can anyone help?

---

### Post by bonzo2 on 2015-03-14
Hi Moofus,
I not sure that this is the answer you're looking for, but I found your question while trying to solve one of my own, and thought I'd mention Unity Tweak Tool.  You may be able to address your transparency issues in Unity Tweak Tool here: Overview > Unity > Additional > Search > Background blur. 
Bonzo2

---

### Post by deadflowr on 2015-03-14
If you were running unity, I see no reason why you would need to enable it.(?)
(Since it would already be enabled.)

But the place you looked in (compizconfig-settings-manager) is where you could have set the transparency levels of the dash and the panel.
I think for 14.04 it falls under the general and launchers sections in the unity plugin's window; 

For a transparent panel, lower the number that is set in Panel Opacity. (should be set at 1.00)
The launcher setting should be similar in the launchers tab.

---

### Post by bonzo2 on 2015-03-15
Moofus, 
could you please update us on whether you had luck adjusting the transparency via DeadFlowr's method.  My CompizConfig does not contain an option for panel opacity/transparency in General/Launchers or anywhere else I can see.  I'm using 14.04 LTS.
Thanks

---

### Post by deadflowr on 2015-03-15
> **bonzo2 said:**
> Matt, 
could you please update us on whether you had luck adjusting the transparency via DeadFlowr's method.  My CompizConfig does not contain an option for panel opacity/transparency in General/Launchers or anywhere else I can see.  I'm using 14.04 LTS.
Thanks

Inside the unity plugin?
Open ccsm >> the click on and open the Ubuntu unity plugin.
Inside the Ubuntu unity plugin's window should be tabs for general, decorations, launcher,menus, and switcher.

---

### Post by bonzo2 on 2015-03-15
Hi DeadFlowr:

Thanks for replying. (Didn't mean to hijack your thread, Moofus, but our issues seem related. :-)

I was hoping to make the Dash search page completely opaque so that when the search screen with the message "Search your computer and online sources" appears, I do not see pages open in the background.  For example, right now I can see this Ubuntu Forums thread when use the Dash search.  I do not see the option to do obscure background images by increasing opacity.

However, inside the Unity plug-in, I do see the tabs you mention. Am I overlooking an obvious setting?

Thanks for your time. :-)



> **deadflowr said:**
> Inside the unity plugin?
Open ccsm >> the click on and open the Ubuntu unity plugin.
Inside the Ubuntu unity plugin's window should be tabs for general, decorations, launcher,menus, and switcher.

---

### Post by deadflowr on 2015-03-15
I think the dash and the launcher are some what tied into one another, so you need to adjust the background color and change the alpha setting.
(You can change the alpha setting in the color by moving the slider in the color settings box; if that makes sense at all)
The more checkered-board the color looks, the more transparent it will be, also, if that makes sense.

---

### Post by mc4man on 2015-03-15
By default the unity panel, launcher & Dash are colored from an average of the desktop background. The panel & launcher have their own opacity setting in the Unity plugin settings. (all settings for panel, laucher & Dash are in the unity plugin settings
The Dash is also colored  from the average & actively blurred with no additional opacity. 

To make the Dash completely transparent one would switch to the "No Blur " option.  

To make the Dash opaque then one needs to raise the opacity of the Background Color option by clicking on it & moving the slider in pop up.
However - as soon as the Opacity of the Background Color is raised from 0 then one starts using a custom background color vs. the average of the Desktop background image.
The default color is black & depending on taste it's the best one as the custom color chosen  will be used for not only the Dash but also the launcher & panel & can get real ugly, real fast.

Also once the Dash is given opacity via the Background Color option then it wrongly will affect the opacity of the unity panel. (an open bug that likely won't be fixed - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1171658](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1171658)
So the panel's opacity will be affected by both it's own opacity setting & the one for a custom color (Background Color option

Here I use no blur, set the launcher opacity, use a custom color of black with fairly high opacity & then adjust the panel's opacity to get close to the launcher.

---

### Post by bonzo2 on 2015-03-15
mc4man

That bug report explains why I've been unsuccessful in adjustments I've tried.  Thanks for that and your settings tip: I finally have the opaque background I wanted while searching in the dash. 

Cheers,
Bonzo2

---

### Post by Moofus on 2015-03-16
yeah ive tried adjusting the alpha settings (it was at 1, i set it at .5) in unity plugin in ccsm, but nothing happened.  I also changed the opacity of the custom background color im using, but it only made it lighter, not transparent! i also set it to Based On Wallpaper to see if it would work, but that didn't either.

---

### Post by mc4man on 2015-03-16
> **Moofus said:**
> yeah ive tried adjusting the alpha settings (it was at 1, i set it at .5) in unity plugin in ccsm, but nothing happened.  I also changed the opacity of the custom background color im using, but it only made it lighter, not transparent! i also set it to Based On Wallpaper to see if it would work, but that didn't either. No clue by what you mean by alpha - 
The closet you'll get to 'transparent' is - 
no blur
background color of #000000, opacity of 2
panel opacity at 0.0000
launcher opacity at 0.0000

You can note that the Dash is shaded, the more sections available the more shading applied. Also transparent obviously doesn't mean uncolored or unshaded. If you mean like a piece of clear glass then maybe in 12.04

---

### Post by Moofus on 2015-03-16
by alpha i meant transparency.
And what i mean by "launcher and dash  not transparent" is it is entirely opaque.  when i open dash, i cannot  see any of my windows or desktop or anything behind it, which you should be able to see, blurred or unblurred.

i also don't know what u mean by shading.

---

### Post by mc4man on 2015-03-16
> **Moofus said:**
> by alpha i meant transparency.
And what i mean by "launcher and dash  not transparent" is it is entirely opaque.  when i open dash, i cannot  see any of my windows or desktop or anything behind it, which you should be able to see, blurred or unblurred.

i also don't know what u mean by shading.
By shading I mean like in screen, 3 sections, each shaded

Looking at your orig. post a bit closer - 
> I installed ubuntu 14.04 UEFI ....
I googled and found another post that said to install compiz config settings manager and enable the ubuntu unity plugin. i did, and after i enabled it, it enabled lots of other stuff like compositor and whatever else


What did you actually install? 14.04 Ubuntu would already have unity installed & enabled. Maybe you installed [Ubuntu Gnome]("http://cdimage.ubuntu.com/ubuntu-gnome/releases/14.04/release/") & have added unity to it??

---

### Post by Moofus on 2015-03-17
no, ubuntu with unity *didn't* actually have the unity plugin enabled.  i have no idea why.

---

### Post by deadflowr on 2015-03-17
Hmm. A shot in the dark, but post the output for
```
/usr/lib/nux/unity_support_test -p
```
This will tell us if unity is properly running on your system.
And if not, why it's not running properly, hopefully.

All the behaviors I see remind me of what happens when you would have run unity2d in 12.04.
But, alas, 14.04 has no unity2d.

Like I started, a shot in dark...

---

### Post by Moofus on 2015-03-17
ok heres the output:

[FONT=courier new]matt@huntress:~$ /usr/lib/nux/unity_support_test -p[/FONT]
[FONT=courier new]OpenGL vendor string:   VMware, Inc.[/FONT]
[FONT=courier new]OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)[/FONT]
[FONT=courier new]OpenGL version string:  2.1 Mesa 10.1.3[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Not software rendered:    no[/FONT]
[FONT=courier new]Not blacklisted:          yes[/FONT]
[FONT=courier new]GLX fbconfig:             yes[/FONT]
[FONT=courier new]GLX texture from pixmap:  yes[/FONT]
[FONT=courier new]GL npot or rect textures: yes[/FONT]
[FONT=courier new]GL vertex program:        yes[/FONT]
[FONT=courier new]GL fragment program:      yes[/FONT]
[FONT=courier new]GL vertex buffer object:  yes[/FONT]
[FONT=courier new]GL framebuffer object:    yes[/FONT]
[FONT=courier new]GL version is 1.4+:       yes[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Unity 3D supported:       no[/FONT]

i assume its bad that unity 3d isnt supported?

---

### Post by CantankRus on 2015-03-17
Your dislpay is being software rendered.
Install inxi (small download, just a system information bash script)...
```
sudo apt-get install inxi
```
and post the output of the terminal command...
```
inxi -b
```

---

### Post by Moofus on 2015-03-18
ok:
[FONT=courier new]matt@huntress:~$ inxi -b[/FONT]
[FONT=courier new]System:    Host: huntress Kernel: 3.13.0-46-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty[/FONT]
[FONT=courier new]Machine:   Mobo: ASUSTeK model: M5A99FX PRO R2.0 version: Rev 1.xx Bios: American Megatrends version: 1903 date: 07/11/2013[/FONT]
[FONT=courier new]CPU:       Hexa core AMD FX-6300 Six-Core (-MCP-) clocked at 1400.00 MHz [/FONT]
[FONT=courier new]Graphics:  Card: NVIDIA GM107 [GeForce GTX 750 Ti] [/FONT]
[FONT=courier new]           X.Org: 1.15.1 drivers: vesa FAILED: fbdev,nouveau Resolution: 1920x1080@0.0hz [/FONT]
[FONT=courier new]           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.3[/FONT]
[FONT=courier new]Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 [/FONT]
[FONT=courier new]           Card-2: Ralink RT2870/RT3070 Wireless Adapter [/FONT]
[FONT=courier new]Drives:    HDD Total Size: 448.1GB (9.0% used)[/FONT]
[FONT=courier new]Info:      Processes: 219 Uptime: 1:13 Memory: 1626.7/7885.5MB Client: Shell (bash) inxi: 1.9.17 [/FONT]

um, why does it say my fx6300 is at 1.4 GHZ? is it just on idle or something?

---

### Post by CantankRus on 2015-03-18
Are you able to install a proprietary nvidia driver for your gfx card?
```
software-properties-gtk --open-tab 4
```

Clockspeed is variable depending on load.
Try running **inxi -b** while playing a video and with system monitor open.
eg
```
System:    Host: Trusty Kernel: 3.16.0-31-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at [COLOR="#FF0000"]3800.00 MHz[/COLOR] 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (12.8% used)
Info:      Processes: 289 Uptime: 13:45 Memory: 2828.7/3934.9MB Client: Shell (bash) inxi: 1.9.17
```

Ps If you put the copied output of inxi in code blocks it is more readable.
ie highlight the pasted content and press the # icon.

---

### Post by Moofus on 2015-03-18
it says no additional drivers available. should i get one from nvidia website?

and btw thanx! i never could figure out how people put that code in there!

---

### Post by CantankRus on 2015-03-18
For your card you would probably need to follow [**_[COLOR="#B22222"]this guide[/COLOR]_**]("http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/") to install the latest drivers from the  xorg-edgers ppa.
Read the [**_[COLOR="#B22222"]ppa warning[/COLOR]_**]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa") before installing.
Install ppa-purge and make yourself familiar with using it.
ppa-purge - disables a PPA and reverts to official packages  
[**_[COLOR="#B22222"]Using ppa-purge[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2264416&p=13224880#post13224880")

I have used this ppa before to test out recent drivers with no major problems.

Backup your home folder so if you encounter problems you can't fix, simply reinstall. (takes less than half an hour)

---

### Post by Moofus on 2015-03-18
the guide said something about having synaptic.  does the additional drivers thing (jockey) need synaptic installed to work?

---

### Post by CantankRus on 2015-03-18
> **Moofus said:**
> the guide said something about having synaptic.  does the additional drivers thing (jockey) need synaptic installed to work?
No, synaptic is just a package manager used before the Ubuntu software centre and was installed by default.
Installing will do no harm and more advanced users prefer to use.

---

### Post by CantankRus on 2015-03-18
I just used that guide to install the nvidia-346 driver from xorg-edgers.
I have a **GeForce GTX 550 Ti** gfx card.

After adding xorg-edgers and updating I simply ran in the terminal....
```
sudo apt-get install nvidia-346
```
and restarted once finished installing.

---

### Post by Moofus on 2015-03-20
YES! it worked! now everything looks right and the graphics are much faster! Thanx CantankRus!

---

### Post by CantankRus on 2015-03-20
Ok good. 
You can disable the ppa now if you like.
It says you should update all the packages in the ppa but just using the nvidia driver should be ok.
What I normally do after adding a ppa and installing the package I want is to disable it
unless I'm expecting frequent updates to the ppa.
Open software & updates...
```
software-properties-gtk --open-tab 1
```
Find the xorg-edgers ppa.
You will see two entries.
The entry that ends in "**(Source Code)**" you only use if you intend to download and compile yourself,
so you can remove that one.

With the other one just disable by unticking so you can re-enable later if you need to purge the ppa.
In any case before upgrading to a new Ubuntu release any third party ppas should be purged.

---

