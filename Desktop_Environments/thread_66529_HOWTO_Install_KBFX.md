---
title: "HOWTO: Install KBFX"
date: 2005-09-17
forum: Desktop Environments
---

### Post by ojpd on 2005-09-17
This is Kind of like a Howto I guess..  :razz:

You could download the deb package here --->

[http://l1nux.free.fr/index.php?&direction=0&order=&directory=Debian/Utilities](http://l1nux.free.fr/index.php?&direction=0&order=&directory=Debian/Utilities)

It's kbfx_0.4.4-1_i386.deb to be specific... just download it through your browser and then open a terminal... go to where you downloaded it ex: /home/YOURNAME/ type: sudo dpkg -i *packagename*.deb

then after installation right click on your panel.. choose applet.. then choose kbfx..
remove your default kde menu button then move the kbfx button to where your default kde menu button was.
 
If you wanna change the background of your kicker you right click on your panel --> configure panel --> under "appearance" -- panel background -- go to the directory where you stored your theme and manually choose the background png file of any kbfx theme you downloaded.. usually it's the file named with a "kicker" text.. then click apply!

To change the Menu button you just open the directory (I use konquerer) where your downloaded kbfx theme files are at.. then you just choose which one you like as a menu button then drag it to the kbfx button.. it'll automatically change into the one you chose.. 

It would also be smart to adjust the size of your panel to make it look good with whatever kicker background and kbfx menu button theme u use..

Sounds simple enough... (I think)

Proven to work on Ubuntu Hoary running KDE 3.4.2

---

### Post by vassalle on 2005-09-17
[QUOTE=ojpd]This is Kind of like a Howto I guess..  :razz:

You could download the deb package here --->

[http://l1nux.free.fr/index.php?&direction=0&order=&directory=Debian/Utilities](http://l1nux.free.fr/index.php?&direction=0&order=&directory=Debian/Utilities)

It's kbfx_0.4.4-1_i386.deb to be specific... just download it through your browser and then open a terminal... go to where you downloaded it ex: /home/YOURNAME/ type: sudo dpkg -i *packagename*.deb

then after installation right click on your panel.. choose applet.. then choose kbfx..
remove your default kde menu button then move the kbfx button to where your default kde menu button was.
 
If you wanna change the background of your kicker you right click on your panel --> configure panel --> under "appearance" -- panel background -- go to the directory where you stored your theme and manually choose the background png file of any kbfx theme you downloaded.. usually it's the file named with a "kicker" text.. then click apply!

To change the Menu button you just open the directory (I use konquerer) where your downloaded kbfx theme files are at.. then you just choose which one you like as a menu button then drag it to the kbfx button.. it'll automatically change into the one you chose.. 

It would also be smart to adjust the size of your panel to make it look good with whatever kicker background and kbfx menu button theme u use..

Sounds simple enough... (I think)

Proven to work on Ubuntu Hoary running KDE 3.4.2[/QUOTE]
 where can i find themes for this ? 

edit: found it! thanks for the tip.. been meaning to replace the kmenu icon for a quite a while.

---

### Post by Takis on 2005-09-18
Please do not advise users to download Debian-specific packages. They are NOT designed with Ubuntu in mind and may very well break things. I advise you to edit your post so that the how-to walks you through the compilation from source procedure rather than using dpkg.

---

### Post by ojpd on 2005-09-19
[QUOTE=Takis]Please do not advise users to download Debian-specific packages. They are NOT designed with Ubuntu in mind and may very well break things. I advise you to edit your post so that the how-to walks you through the compilation from source procedure rather than using dpkg.[/QUOTE]



Dude, Ok Im really sorry if this post is'nt about the real deal in how to install kbfx from the source package and I must admit you are right about most debian specific packages not working in ubuntu and not designed for ubuntu.. HOWEVER this one (this post) is merely for the noobs out there and the newly converted ones from bill's windoze.. or for people having a really difficult time using the real app sources.. The people who cant seem to find a way to get it to work. This is somehow one of the easiest way to install kbfx in ubuntu.. SO FAR as in base on the posts about installing kbfx here in the forums. Newbies and the ones who cant get the real app sources to install and work have no choice at all.. if how to successfully install kbfx from the source package cant be found in this forum and if the most helpful people from the IRC Channel are mostly people who easily get irritated by newbies (The kind that just started using ubuntu for the first time) asking questions or asking for help..  what other choice do they have if they really really want to install kbfx??or any other app that they couldnt get to work.

I have installed this one on 9 machines now. all running hoary 5.04 with kde 3.4.2 installed.. I havent found anything wrong that this .deb package of kbfx has caused.. nor has it broken any of the beasts I have used this package with... Peace!!  ;-)

---

### Post by Takis on 2005-09-20
[QUOTE=ojpd]I have installed this one on 9 machines now. all running hoary 5.04 with kde 3.4.2 installed.. I havent found anything wrong that this .deb package of kbfx has caused.. nor has it broken any of the beasts I have used this package with... Peace!!  ;-)[/QUOTE]
Fair enough, but you may like to consider how long it takes bugs to appear (e.g. patches for programs that have been out for years). I'm a bit of a stickler for this so forgive me, but you may like to have a warning at the top that using Debian packages on Ubuntu may break people's systems. Of course, the next thing you say is that it doesn't seem to, but that the principle stands.

It's up to you, of course.

---

### Post by f1dave on 2005-09-21
Hear, hear.

For those who don't know, you may also wish to explain just what KBFX is :)

---

### Post by ojpd on 2005-09-21
[QUOTE=Takis]Fair enough, but you may like to consider how long it takes bugs to appear (e.g. patches for programs that have been out for years). I'm a bit of a stickler for this so forgive me, but you may like to have a warning at the top that using Debian packages on Ubuntu may break people's systems. Of course, the next thing you say is that it doesn't seem to, but that the principle stands.

It's up to you, of course.[/QUOTE]



Okies cookies dude,

You have a clear point there too dude... For everbody out there who downloaded and installed this Debian Package... A warning...

---> USE AT YOUR OWN RISK  <---   hehehe there u go!

If anybody wants to uninstall.. U can do it through synaptic, make a search.. search for KBFX... and then just mark it for complete removal.. click apply.. then, right click on you panel then Add the default KDE Menu again...  :-)

---

### Post by ojpd on 2005-09-21
[QUOTE=f1dave]Hear, hear.

For those who don't know, you may also wish to explain just what KBFX is :)[/QUOTE]


KBFX  =  An applet/program that can replace the default KDE Menu button, and at the same time "some" themes also offer a skin for the Kicker itself.. .. Check the author's page out -->  [www.linuxlots.com/~siraj/kde/plugin/home/index.php](www.linuxlots.com/~siraj/kde/plugin/home/index.php)   <--- or you can go --> to [www.kde-look.org](www.kde-look.org) <--- make a search for KBFX... there are already a number of downloadable themes with lots of screenshots over there... Hope this helps explain it to you.

---

