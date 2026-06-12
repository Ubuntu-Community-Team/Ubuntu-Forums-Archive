---
title: "Can i use beryl on this computer?"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Rick123 on 2007-03-30
Hi just wounder if this computer can handle beryl, i don`t know much about graphic cards so i just write down every thing about it, the only thing i know is, i don`t have Nvidia nor .............. , anyway I have an laptop computer, and here whats in it:

Processor intel(R) celeron(R) M processor 1,50GHz

Memory 507MB (232MB used)

Res 1024*768 pixels

Open GL renderer Mesa DRI intel(R) 915GM 20050225
And looked in windows too, to know what graphic card i got and its says:
Mobile intel(R) 915GM/GMS, 910ML Express Chipset Family. 
=) There you go... Do you think i can use beryl on this computer?

If so please make me an newbie guide or direct me to one that make easy steps to follow how to apply it, I don`t know about graphic driver, so i don`t know if Ubuntu installed one, or if i need to have a better one for my graphic card, anyway, if i can use beryl on this machine please guide me throughout the hole process. Thanks in regard!!  :guitar:

---

### Post by SendDerek on 2007-03-30
I'm no beryl-professional, but I've ran beryl on a system with similar specs as yours except the RAM.  He only had 256MB.  I was actually shocked to see it run so nicely.  Sometimes it skipped, but I'm sure that's expected with minimal RAM.

Short answer, I believe you'll be able to run beryl... yes.  

If it doesn't work out, just remove it.  No biggie.

---

### Post by Flying George on 2007-03-30
I think you could if your computer supports OpenGL, you might even be able to play some games, I say go for it. If its slow or anything, just un-install it.

F.Y.I. Having a 'mobile' Graphics Card, just means its integrated (its a chip on your motherboard, not a real 'card').

hope this helps.

---

### Post by Rick123 on 2007-03-30
Wow guys! thanks, i gonna go for it!
So does i just download some sort of installer and the rest does the installer or do i have to install it from the terminal? If so...  Were do i find  what i gonna write? 

Thanks again, much appreciated for your answers! :popcorn:

---

### Post by BarfBag on 2007-03-30
Intel Integrated Graphics have open source drivers, so you get a 3D desktop out-of-the-box.  From what I've heard, they run Beryl nice and smooth.  Here's a link to get you started.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

### Post by Flying George on 2007-03-30
:lolflag:  I just installed beryl on my PC, I'm still laughing, ITS AMAZING! here's a link to install beryl from the terminal:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by astrolabio on 2007-03-30
Look, beryl at the end of the day is just little more than a cube.

Shouldn't be such a big deal for almost any video card with 3d cababilities.

The problems usually pop up from its beta status (aka it's still under massive developping (aka lots of bugs)), from poor driver support (aka ATI) or some cool effect like trasparency (aka you can deactivate it anyway).

It's not such a big surprise that so many people managed to make it work even with crappy lappy videocard. Give it try and then report.

---

### Post by Rick123 on 2007-03-30
> How-to install Beryl with AIGLX on Edgy Eft
[edit]
Add repositories

Edit the sources.list file, e.g. by opening a terminal and typing:

sudo gedit /etc/apt/sources.list

Add this line:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

For the GPG key (to ensure that the packages are authentic):

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O - | sudo apt-key add -


For EXPERIMENTAL svn packages, which are UNSUPPORTED (although bug-reports are most welcome :) ):

# Treviño's Beryl-SVN Ubuntu Repository
 # GPG key: 81836EBF
 deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn


GPG key for Treviño's repository:

wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O - | sudo apt-key add -

Update the package list before installing

sudo apt-get update


So what is this all about? Beryl with AIGLX on Edgy Eft,  AIGLX??-whats that, so do i need to do this? Whats it for?


Or should i just stick to the, whats its look like the normal installation of beryl, thats look... even easy for me to do?
> 
Install Beryl

Simply type

sudo apt-get install beryl

That's too easy !

You'll also need themes for the decorations

sudo apt-get install emerald-themes

Beryl is a metapackage that will install all the dependencies (beryl-core, beryl-plugins, beryl-manager, beryl-settings) and also the decoration themes (emerald but not emerald-themes). Make sure you have all!

(or simply use:

sudo aptitude install beryl

since aptitude installs "recommended" packages as well as required and emerald-themes is recommended one of the other packages) 

---

### Post by SendDerek on 2007-03-30
As far as I know... AIGLX is the "program" meant specifically for intel and nvidia graphics chips. XGL is for ATI.  

In shorter:  AIGLX is what you want for Intel graphics chips.

---

### Post by Rick123 on 2007-03-30
Okay guys, thanks for all the help, i have now installed beryl and its works to some degree, not water effect and some other effects, but i can turn the cube =), 
Anyway, now i have tried the man the myth the concept.

BUT... =) i want to uninstall AIGLX and beryl now, so how do i do that??

Witch command should i write in the terminal?

i have installed beryl plus emerald theme and AIGLX if that is to any help to figure out what command i should write to uninstall it.

Thanks :guitar:

---

### Post by SendDerek on 2007-03-31
Generally, it's whatever steps you took to install it, reversed.

So, if you used sudo apt-get install beryl-manager, you'll need to do a sudo apt-get remove beryl-manager.

Give that a shot.  Again, I'm no beryl professional.

---

