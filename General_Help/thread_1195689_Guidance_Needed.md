---
title: "Guidance Needed"
date: 2009-06-24
forum: General Help
---

### Post by MadsaltyRe-Registered on 2009-06-24
Hey,

It's been a long time since i've used these forums and indeed ubuntu (hence the username).

My installation of XP has finally given up the ghost on my old PC and i've decided that over the next few months i'd like to learn more about linux as it will be usefull to have a stable, safe and dependable OS.

On previous installations of Linux i've never really embraced it as i've only been able to do basic things and use the in-built software that comes with a distribution. I'd like to be able to take control of this and actually install things this time.

Also i'd like it to be functional as a little studio computer. Is it possible to have functional audio recording software on linux?

Also i seem to remember a program which installed everything you needed at once?

Can anybody help?

Kind Regards,
Mad

---

### Post by Soul-Sing on 2009-06-24
Some linkages: [www.ubuntustudio.org](www.ubuntustudio.org) 
: [www.64studio.com](www.64studio.com)
: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) 
program: Ardour
: [http://eracks.com/products/Quiet%20Systems/config?sku=STUDIO](http://eracks.com/products/Quiet%20Systems/config?sku=STUDIO)
ERACKS-studio

---

### Post by Bucky Ball on 2009-06-24
I installed Xubuntu (slimline, fast) and then added the UbuntuStudio applications (only: no desktop or artwork) through the Synaptic Package Manager for my studio box. I use the Long Term Release 8.04 LTS, not 9.04.

[http://ubuntustudio.org/](http://ubuntustudio.org/)

Whatever you decide, try out the LIVE version from the installation CD first to see how your hardware deals with it. If everything's fine, and you can get online, you're good to go. 

Good luck with it.

---

### Post by t0p on 2009-06-24
> **MadsaltyRe-Registered said:**
> Hey,

It's been a long time since i've used these forums and indeed ubuntu (hence the username)

[...]

On previous installations of Linux i've never really embraced it as i've only been able to do basic things and use the in-built software that comes with a distribution. I'd like to be able to take control of this and actually install things this time


You've always been able to install software on Ubuntu (I'm using "you" generally, I'm not necessarily referring to *you*).  You can install a huge amount of software from online repositories with the Synaptic Package Manager.  If you fancy using something that's not available from the repos, you can get compatible packages from [www.getdeb.net]("http://www.getdeb.net") or [you can compile from source]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by MadsaltyRe-Registered on 2009-06-24
Well the good news is i'm currently posting this from a brand new fresh install of Ubuntu 9.04! And i'm pleased to report it's as good as i remember.

I'm having trouble getting firefox working correctly. I need the bits and bobs such as flash etc. but i simply don't know where to start. The synaptic package manager looks a bit scary.

EDIT: Quick trip to adobe website and a few clicks later downloaded and installed. This is alot more user friendly than last time!

---

### Post by Soul-Sing on 2009-06-24
MadsaltyRe-Registered: ubuntu-restricted-extra via synaptic package manager.

---

### Post by MadsaltyRe-Registered on 2009-06-24
> **leoquant said:**
> MadsaltyRe-Registered: ubuntu-restricted-extra via synaptic package manager.

Great! I'm starting to get the hang of this! thanks.

---

### Post by ajgreeny on 2009-06-24
And consider enabling the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos as well, they are great for a number of multimedia apps.

---

### Post by MadsaltyRe-Registered on 2009-06-24
Ok i've come unstuck trying to compile source code. I've downloaded the ardour source "ardour-2.8.taz.bz2" but i can't seem to get any further. I've extracted the files and tried to follow the link show earlier but i'm struggling. Is there an easier walkthrough?

---

### Post by Soul-Sing on 2009-06-24
.deb (ubuntu packages)for Ardour: [https://www.scimmia.net/code/wiki/DebianRepository](https://www.scimmia.net/code/wiki/DebianRepository)

---

### Post by Cheesemill on 2009-06-24
If you install the ubuntu-studio package it will automatically install Ardour as well as a whole range of other audio production apps

---

### Post by Soul-Sing on 2009-06-24
> **Cheesemill said:**
> If you install the ubuntu-studio package it will automatically install Ardour as well as a whole range of other audio production apps

Thats indeed the first thing to suggest. And has been suggested.(To take a look)

edit:I think(not sure though) ubuntu-studio has a more specialized forum?

---

### Post by Bucky Ball on 2009-06-24
> **leoquant said:**
> edit:I think(not sure though) ubuntu-studio has a more specialized forum?

Nope this is it. Fire away.

You can install the Ubuntu Studio apps by copy/pasting this command into a terminal (Applications->Accessories):

```

sudo apt-get update && sudo apt-get install **ubuntustudio-desktop** ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```I omitted the item in bold because I don't like the UStudio desktop or artwork much. If you want the choice in your themes and backgrounds menus, leave it in. Likewise, if you never do video, omit 'ubuntustudio-video'. You'll eventually have your regular Ubuntu with the Studio elements you've selected showing in your Applications drop-down menu (including Ardour). It could change the order around there a bit.

One peculiarity/bug for now, and this may be fixed: this installs the rt (real time) kernel (final item). UStudio apps will work without it (do experiment) but it works just dandy ...  _BUT_ there is a conflict with Nvidia drivers and the rt kernel. Bummer. So if you have an Nvidia graphics card and want to use the driver, boot using your regular kernel. If you don't, rt it is.

... and as mentioned, the Medibuntu repo will fix up just about all third-party codec related problemos. How long since you've used Ubuntu? Sounds like you might like it a little more this time around. :)

---

### Post by MadsaltyRe-Registered on 2009-06-24
I'm downloading ubuntu studio as we speak, but i've actually mamaged to get compiled and installed! thanks.

---

### Post by Bucky Ball on 2009-06-24
Wonder if you will read my last post #13 before you install Ubuntu Studio? We might have passed each other in the freeway there! :-k

Hey, MadSalty, it has only been ten posts and already you probably understand what I meant in post #3! Keep going, you're on a roll. :)

---

