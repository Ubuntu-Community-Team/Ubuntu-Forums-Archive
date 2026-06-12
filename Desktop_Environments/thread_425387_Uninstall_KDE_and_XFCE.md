---
title: "Uninstall KDE and XFCE"
date: 2007-04-27
forum: Desktop Environments
---

### Post by Vanaheim on 2007-04-27
[I]Hi all ^^

Iv been using Ubuntu for sometime now, used to use Dapper and recently moved on to Feisty. It really is better in so many ways, but well, since I'm in that phase of trying out everything i can and mess with the hole package and learning how to do things etc.. i followed a guide on how to install XFCE and KDE, i decided to install just to see how different the were from Gnome.

Well, after trying out both i decided that KDE simply uses too many resources and XFCE well..nothing against it but i just wanted to look at it not actually use it ^^

Well, i used these commands:

sudo aptitude install kubuntu-desktop

and 

sudo aptitude install xubuntu-desktop

Now, i don't know how to uninstall them, can anyone point me in the right direction?

I want to remove them and leave no traces of KDE or XFCE on the system, i actually never used them more then  minutes each, enough to take a peak.

Any help would be much appreciated ^^ thanks in advance!

Cheers[/I]

[COLOR="Red"]EDITED[/COLOR]:

Well after some experiments alone and some errors i found that 

sudo aptitude remove kubuntu-desktop

and 

sudo aptitude remove xubuntu-desktop

worked ^^ i was trying the wrong way and searching the wrong way on google as well, i was trying to 

sudo apt-get uninstall kde

but after searching on synaptic and looking at the original commands it was just a 1+1 situation ^^' 

Also Iv read that on Dapper and Edgy people were having allot of issues while uninstalling KDE along with the applications, well, on Feisty at least everything was removed and went back to how it was before ^^ quite cool!

Cheers

---

### Post by hellblade on 2007-04-28
I would like to inform you that by "removing" these metapackages, while the programs were removed some files remain on your system (configs in /etc etc.) and especially in your home.
If you want to completely remove all traces from your system (still not home) you can run aptitude (sudo aptitude), search for package (hit / once, type kubuntu-desktop and the return), select package (return) and then go in the "Depends" list. The grey packages that start with "c" are the ones that got uninstalled but left some files behind. You can purge them by selecting and pressing "_" (Shift+- usually). After purging them hit "g" twice to apply the changes.

Hope that helps a little.

---

