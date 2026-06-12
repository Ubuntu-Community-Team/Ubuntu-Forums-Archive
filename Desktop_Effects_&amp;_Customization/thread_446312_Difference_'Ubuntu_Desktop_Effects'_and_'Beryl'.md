---
title: "Difference 'Ubuntu Desktop Effects' and 'Beryl?'"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by Chamelion on 2007-05-16
I am using the Ubuntu Desktop Effects in Feisty. They are working OK except that I loose the bottom panel on ocasion when I use the desktop switcher Instead of dragging with alt ctrl and the mouse. (A reboot normally sets things right.)
I would like to know where Beryl comes in here. What are the advantages and what are the dangers in installing it. I just have Feisty running very well and am very cautious. 
How would I go about the installation considering I already have the Desktop Effects enabled. 
I am in new territory here and would appreciate any advice I can get.:)
Thank you

---

### Post by chamberlain2006 on 2007-05-16
Beryl is similar to Compiz (they used to be the same).  It has more effects, but is also known to be less stable.  It is harder to install and configure for a basic user.  Soon, though, Compiz and Beryl are going to rejoin.  Personally, I think you'll want to stick with Compiz unless you're particularly ambitiooous.

---

### Post by Ziox on 2007-05-16
> **chamberlain2006 said:**
> Beryl is similar to Compiz (they used to be the same).  It has more effects, but is also known to be less stable.  It is harder to install and configure for a basic user.  Soon, though, Compiz and Beryl are going to rejoin.  Personally, I think you'll want to stick with Compiz unless you're particularly ambitiooous.

Actually, from my personal experience, Beryl had been amazingly stable, and since the packages are now in Ubuntu repositories, installation is as easy as installing...say amarok or any other standard package.

sudo aptitude install beryl emerald

---

### Post by chamberlain2006 on 2007-05-16
But remember, Beryl doesn't run on top of Gnome like Compiz does, it replaces it (not permanently, of course).  Also, don't you need to install/enable XGL?

---

### Post by Ziox on 2007-05-16
Compiz also replaces the Windows Manager.  But beryl is more obvious because of its ambitious nature (more effects and cooler borders).  You need to install XGL or enable nVidia or AIGLX for BOTH compiz and beryl.  And XGL is only needed if you have an ATI card.  Other cards, such as Intel cards use the natively supported AIGLX method.  For nVidia card users, the binary nvidia driver natively supports composite overlay.  In other words, Beryl looks better than Compiz, and a bit less stable, but other than that, there is no difference (to the end user).

---

### Post by Chamelion on 2007-05-16
Are the Ubuntu Desktop Effects Compiz then? I was not aware. I will take your advice Chamberlain 2006. It is that damn curiosity that got me into serious trouble many times.:lolflag:
Thanx

---

### Post by chamberlain2006 on 2007-05-16
Well I only talk from experience.  I have tried installing Beryl and was not happy to have to revert to command line to fix the stuff I broke.  From my experience, I have found the provided desktop effects through compiz to be enough.  Also, you may want to install all of the packages in the repositories concerning "compiz".  This will give you a lot more configurable options, and more features.  Good luck though!

PS to Ziox: I'm not sure about the all of the stuff concerning installing beryl/compiz, but I do know from experience thatberyl can cause some major hassle for a new/unexperienced user.

---

### Post by icechen1 on 2007-05-16
I am using Beryl,it is like Compiz but more effects.I heard Compiz and Beryl are going to merge soon

---

### Post by Chamelion on 2007-05-16
I just installed 3rd Party Plugins For Compiz (Synaptic). Lost my 3d and 3 of my desktops. :lolflag:
Lucky there is a command in another spot of this forum to get it back.
Problem now is, where are the plugins?
Everything is a OK again, but nothing has changed at all. I do not seem to be able to find anything I just have installed. :confused:

---

### Post by chamberlain2006 on 2007-05-16
Ther eshould be an option in System>Preferences called GL Desktop with more options.

---

### Post by Ziox on 2007-05-16
Soon, we don't have to worry about Compiz or Beryl: here's the official words:

[http://compiz.blogspot.com/2007/04/official-announcement-of-merge.html](http://compiz.blogspot.com/2007/04/official-announcement-of-merge.html)

---

### Post by Chamelion on 2007-05-16
GL Desktop is not there. I think I am missing a plug in. Linux is Great, but it does drive me nuts on occasion.:lol:

---

### Post by Ziox on 2007-05-16
sudo aptitude install gnome-compiz-manager

if that's already installed, then perhaps you need to reboot.

---

### Post by Chamelion on 2007-05-17
Thank you Ziox. I have got it.:)

---

