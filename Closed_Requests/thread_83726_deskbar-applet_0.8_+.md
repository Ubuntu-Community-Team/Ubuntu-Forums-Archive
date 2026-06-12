---
title: "deskbar-applet 0.8 +"
date: 2005-10-29
forum: Closed Requests
---

### Post by magnusbb on 2005-10-29
Hello,

I really love the deskbar-applet, sitting on my panel. But the version bundled with Ubuntu is "old". Is it possible to get binary packages for 0.8+ (0.8.2 latest release).

I've tried compiling it myself, but ran into serious dependency problems.

---

### Post by poptones on 2005-10-29
That's the reason. The newer deskbar requires several packages from the latest gnome. It would be cool if the latest gnome got backported to hoary (I had serious problems with breezy) but I doubt that's gonna happen.

---

### Post by crypto178 on 2005-10-29
I compiled it this morning, what dependancies problems do you have exactly (I had to install a bunch of dev packages from synaptic, but none were too hard to figure out)?

---

### Post by magnusbb on 2005-10-29
Would it be possible for you to make a package of your installation using checkinstall, and then publish it?

That would be really nice.

---

### Post by crypto178 on 2005-10-30
I've never done that before but I'll try to look for some documentation.

---

### Post by crypto178 on 2005-10-30
[http://hlqg.free.fr/deb/deskbar-applet-0.8.2_0.8.2-1_i386.deb](http://hlqg.free.fr/deb/deskbar-applet-0.8.2_0.8.2-1_i386.deb) (has beagle and evolution support)

Tell me how it goes!

EDIT : I think that you have to remove the hidden deskbar folder in your home before running the new version, there are changes in the config files.


PS: It won't work if the deskbar applet in the repos is already installed.

---

### Post by 23meg on 2005-10-30
I'll be happy if you can post a Tomboy 0.33 package; I've been trying to compile it without any success.

Note: AFAIK deb files made with checkinstall do not contain dependency info so they're not guaranteed to work in systems where required dependencies can't be found.

---

### Post by crypto178 on 2005-10-30
[http://hlqg.free.fr/deb/tomboy-0.3.3_0.3.3-1_i386.deb](http://hlqg.free.fr/deb/tomboy-0.3.3_0.3.3-1_i386.deb)

built using the same method, hope it works

---

### Post by 23meg on 2005-10-30
Deskbar working nicely, Tomboy failing here. At the first try it appeared in the "Add to panel" dialog with no icon, and when I tried to add it an error message was displayed with an option to remove it from the list, and I removed it (shouldn't have?). The bad thing is, I cannot add the old Tomboy there either now; tried "killall gnome-panel", no luck. Maybe I have to tweak the list of apps that can be added to the panel; I wonder where that is..

---

### Post by crypto178 on 2005-10-30
Maybe there's something I missed during the compilation. On my desktop, tomboy doesn't show up either in the list of applets, but I always used tomboy as a regular program (alt+f2 'tomboy') so I didn't notice before you told me. 
Maybe there's an extra step involved in getting it to work as a true applet?

---

### Post by 23meg on 2005-10-30
Don't know that step, but a standard install should put it into the applets list. Does entering the "tomboy" command put it in your notification area?

---

### Post by crypto178 on 2005-10-30
> Does entering the "tomboy" command put it in your notification area?
yes, it does. 

But I'll try to tinker a bit with this applet problem
the panel compilation generates a lot of warnings :
[http://pastebin.com/411363](http://pastebin.com/411363)
maybe not the right version of the required lib *shrug*

---

### Post by magnusbb on 2005-10-30
Thank you very much, crypto178!

The latest version of deskbar-applet that you compiled, works great. Every Ubuntu user ought to try this fantastic tool.

---

### Post by crypto178 on 2005-10-31
0.8.3 is there ([changelog](http://sourceforge.net/project/shownotes.php?release_id=367197))

[http://hlqg.free.fr/deb/deskbar-applet-0.8.3_0.8.3-1_i386.deb](http://hlqg.free.fr/deb/deskbar-applet-0.8.3_0.8.3-1_i386.deb)

---

### Post by cowlip on 2005-10-31
THanks for that :D

---

### Post by crypto178 on 2005-11-01
Another bugfix release : 0.8.4 ([changelog](http://sourceforge.net/project/shownotes.php?release_id=367518))

[http://hlqg.free.fr/deb/deskbar-applet-0.8.4_0.8.4-1_i386.deb](http://hlqg.free.fr/deb/deskbar-applet-0.8.4_0.8.4-1_i386.deb)

---

### Post by 23meg on 2005-11-01
Anyone using deskbar with xcompmgr? In my use it stops responding whenever xcompmgr crashes.

---

### Post by crypto178 on 2005-11-05
I just did a fresh breezy reinstall so I wrote down the dependancies needed to compile the deskbar applet :

build-essential
libxml-perl
python-dev
python-gtk2-dev
python-gnome2-dev
python-gnome2-extras-dev
evolution-dev                        ** somehow enables beagle support
evolution-data-server-dev    ** enables evolution support

then use the usual commands:

./configure --prefix /usr
make

Then you have the choice between :
sudo make install 
or:
sudo apt-get install checkinstall  
sudo checkinstall -D make install  (to produce .deb package)
Type Deskbar Applet as description (so that it overrides breezy repositories version). ** I didn't do that in the packages I provided, my bad.


PS : For tomboy, I needed the following (you may need some from the deskbar applet dependancies too)

mono-mcs
libpanel-applet2-dev
libgtkspell-dev
gtk-sharp2

Still no tomboy in the applet list though

---

### Post by jdong on 2005-11-11
It's not in Dapper yet....

---

### Post by naked on 2005-11-15
crypto:  Can you provide us with the 8.5 deb you have made?

Thanks

L

---

### Post by bugmenot on 2005-11-18
me too, please. my own CVS compiles always crash on loading...

---

### Post by crypto178 on 2005-11-20
I switched to ubuntu amd64-bit recently, so I can't provide x86 debs anymore, sorry! 
I just tried to compile the 0.8.5 version, and it seems that dependancies have changed, I'll try to investigate the matter.

EDIT: 
There is one extra dependancy needed for the 0.8.5 version, libgnome-desktop-dev.
Other than that, it's just like before, download the source from the following link and see my previous post for instructions on how to compile it : [http://prdownloads.sourceforge.net/browserbookapp/deskbar-applet-0.8.5.tar.gz?download](http://prdownloads.sourceforge.net/browserbookapp/deskbar-applet-0.8.5.tar.gz?download)

EDIT2:
The amd64 build (don't use on ubuntu i386) is here : [http://hlqg.free.fr/deb/deskbar-applet_0.8.5-1_amd64.deb](http://hlqg.free.fr/deb/deskbar-applet_0.8.5-1_amd64.deb)

---

### Post by AgenT on 2005-11-22
Since this has made it into Dapper can it now be backported (0.8.5)?

---

### Post by jdong on 2005-11-22
yes, approved :)

---

### Post by jdong on 2005-11-23
done.

---

### Post by AgenT on 2005-11-23
WOW! jdong you sure are fast!

The deb is in the repositories but the index has yet to be updated (and hence apt-get does not know about it). How long does it take for it to update the index with the new additions?

---

### Post by Omer on 2005-12-11
0.8.6 builds up fine on breezy.

---

### Post by AgenT on 2005-12-20
Anyone know if it is possible to assign a shortcut to have the cursor appear on deskbar-applet like ctrl+l inside Firefox for the address bar?

---

