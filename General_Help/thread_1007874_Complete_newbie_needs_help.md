---
title: "Complete newbie needs help"
date: 2008-12-10
forum: General Help
---

### Post by z0mfgkyroN on 2008-12-10
Hi,
sorry if i'm going to sound like a complete idiot,
but at the moment I have no clue about Ubuntu or any other linux based operating systems,
I am an IT technician so as you can expect all my knowledge is on hardware and windows based OS,
Ubuntu has always really interested me and i've always wanted to install it but never had compatible hardware,
but the other day I upgraded and as far as I can see I am fine compatibility wise now,
My only real fear of installing is getting the drivers,
and when people talk about "ah just chuck this command into the console" and i'm like o.O

So could someone possibly walk me through getting it on to my system and when i've got it on I can hopefully increase my knowledge on the subject,
and when I mean walk, I mean baby steps

thanks in advance,
hope someone can help :(

PS. I have dual 22" monitors both 1680x1050, I suppose this is going to be hard to set up?

PPS. System Specs:

Q6600 3.2
P5Q-PRO 775
8800GTX 768MB
150GB Raptor HDD

---

### Post by PocketDog on 2008-12-10
If somebody puts a code to be entered in a ```
code box like this
``` it's usually meant to be copied as-is, and pasted straight into a terminal window, nothing to be afraid of ;-). If you grab an Ubuntu .iso and burn it to CD or DVD - or order one through the post for free - you can run it live straight from the disc without having to install it first. That'll give you a taste, and throw up any hardware incompatibility issues, if any. If you like what you see you can choose to install it from the same disc.

---

### Post by abn91c on 2008-12-10
run ubuntu from a live cd, if it finds all your hardware without problems most likely it will install Ok, in the menu bars, top of the screen select system>administration>hardware drivers to see if it autodetects your hardware, if you dont need any propietary drivers the window will be empty, otherwise it will list the recommended drivers for you system
You can get a free factory burned ubuntu cd form here [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by 2handband on 2008-12-10
I was in your shoes only three weeks ago. It's not as frightening as you think. even the command line is starting to get easy. Just go for it... what's the worst that can happen?

---

### Post by soro2005 on 2008-12-10
Chances are you never need to go on the hunt for a driver. You have an Nvidia graphics card, which should be supported out of the box, and you can install the proprietary Nvidia driver with the click of the mouse button (see abn91c). So just pop in the Live CD, and it looks to me like you're going to see sheer magic.

Once you've installed it and are running on the proprietary Nvidia driver, make sure you install the package nvidia-settings (System --> Administration --> Synaptic Package Manager; in Synaptic, open Settings --> Repositories and make sure that all the options are checked in the first tab "Ubuntu Software", then search for "nvidia-settings" and install it). That is the configuration utility for the Nvidia cards, and it will let you set up your twinview with a very intuitive graphical interface. Once you've installed it, it's in System --> Adminstration --> Nvidia X Server Settings

---

### Post by z0mfgkyroN on 2008-12-10
Looks like I have one problem,
I can't seem to connect network-wise,
which i'm assuming is the reason the search for "nvidia-settings" is failing

Any ideas?

I've heard once or twice while searching that ubuntu will not find drivers for the p5q motherboards network-wise and you need to go out and buy a network card

PS. I forgot to choose AHCI over IDE in the BIOS which I heard effects this motherboard,
would this effect the network connection?

---

### Post by 2handband on 2008-12-10
Nvidia is your graphics card, not your network. Are you using Ethernet or wireless?

---

### Post by adult swim on 2008-12-10
i just did a quick search on your problem and enabling ahci seems to be beneficial to finding the network controller on your p5q. if you are dual booting youll need to remember to switch back to ide before running windows.  while i have no experience with it people reported windows didnt play nice whith ahci.

---

### Post by z0mfgkyroN on 2008-12-10
Hahaa, I know it's not my network, but I need to be connected to do this search to get my dual monitors to work.

I'm connected via ethernet,
also i'm booting to the 8.04 release if that helps

UPDATE:

After switching the SATA configuration from IDE to AHCI, the network connection still doesn't work :(

---

### Post by 2handband on 2008-12-11
odd, ethernet usually isn't a prob. what's your network card?

---

### Post by 2handband on 2008-12-11
odd, ethernet usually isn't a prob. what's your network card?

---

### Post by z0mfgkyroN on 2008-12-11
Onboard (Atheros)

---

### Post by Twitch6000 on 2008-12-11
> **z0mfgkyroN said:**
> Onboard (Atheros)

Oh... Atheros....

Yeah you might want to Use Ubuntu 8.10 for better Atheros support.

There are ways to make 8.04 work with it,but it takes time :(.

Ofcourse there is problem more then one answer to this problem aswell so you might want to wait for another answer before jumping to the next version ;).

---

### Post by z0mfgkyroN on 2008-12-11
I was just readin through some stuff and found a post on this forum related to Atheros and the 8.10 release:

"Hello,
In the betas of ubuntu 8.10 there were warnings for people using the above mobo and integrated ethernet to NOT install the betas because it would whipe the ROM of the ethernet on the mobo... thus destroying it.

Fortunatly I read that on the release page of the betas so I didnt try it."

So could anyone confirm that it is safe to use?
and if it will actually fix this problem?

UPDATE:

I just finished downloading 8.10, i'm going to boot to live cd in a bit, i'll tell you how I get on

UPDATE:

Runs perfect off the Live CD, no problems what so ever,
so i'm going to go ahead and install it

---

### Post by z0mfgkyroN on 2008-12-11
After installing the X server it hits me with this when opening:

You do not appear to be using the nvidia x driver
Please edit your x configuration file
Just run 'nvidia-xconfig' as root

Any help?

---

### Post by eBoxNet on 2008-12-11
try ```
sudo nvidia-xconfig
``` in a terminal window

---

