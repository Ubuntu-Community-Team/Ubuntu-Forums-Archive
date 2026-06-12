---
title: "Ubuntu GIMPShop Packages for i386/amd64!"
date: 2006-08-19
forum: Desktop Environments
---

### Post by xtknight on 2006-08-19
I, along with a 32-bit-user friend, have just completed the compilation of GIMPShop (a package that contains a new GIMP with a Photoshop style GUI) and would like to share our .debs.  Enjoy. 

Note: these packages were not compiled with gutenprint.  You can use other image programs to print your pictures.

Configure option used was: ./configure --prefix=/usr --disable-print

**Dapper GIMPShop 2.2.11 i386 packages:**

[gimpshop_2.2.11-1_i386.deb]("http://www.lurkmore.com/pow/Packages/Ubuntu/i386/GimpShop/gimpshop_2.2.11-1_i386.deb")
[libgimp2.0_2.2.11-gimpshop1_i386.deb]("http://www.lurkmore.com/pow/Packages/Ubuntu/i386/GimpShop/libgimp2.0_2.2.11-gimpshop1_i386.deb")
[Mirror: gimpshop_2.2.11-1_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/gimpshop_2.2.11-1_i386.deb")
[Mirror: libgimp2.0_2.2.11-gimpshop1_i386.deb]("http://xtknight.atothosting.com/ubuntu/dapper/i386/libgimp2.0_2.2.11-gimpshop1_i386.deb")

**Dapper GIMPShop 2.2.11 amd64 packages:**

[gimpshop_2.2.11-1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/gimpshop_2.2.11-1_amd64.deb")
[libgimp2.0_2.2.11-gimpshop1_amd64.deb]("http://xtknight.atothosting.com/ubuntu/dapper/amd64/libgimp2.0_2.2.11-gimpshop1_amd64.deb")
[Mirror: gimpshop_2.2.11-1_amd64.deb]("http://www.lurkmore.com/pow/Packages/Ubuntu/Amd64/GimpShop/gimpshop_2.2.11-1_amd64.deb")
[Mirror: libgimp2.0_2.2.11-gimpshop1_amd64.deb]("http://www.lurkmore.com/pow/Packages/Ubuntu/Amd64/GimpShop/libgimp2.0_2.2.11-gimpshop1_amd64.deb")


Download these to your Home directory (or anywhere for experienced users).

**_Easy Install_**

**1. Remove all previous GIMP components**

First, open a terminal.  Go to Applications->Accessories->Terminal.

$ sudo apt-get remove xsane gimp-svg gimp-dbg libgimp2.0-dev gimp gimp-print gimp-helpbrowser mrwtoppm-gimp libgimp-perl gtkam-gimp gimp-ufraw gimp-texturize gimp-dimage-color gimp-dcraw gimp-cbmplugs gimp-data libgimp2.0

**2. Install GIMPShop package (libgimp2.0 is more a pseudo package to prevent programs that require 'libgimp2.0' from breaking)**

Replace *arch* with your Ubuntu installation's architecture.  This will either be *i386* or *amd64*.

$ cd ~/
$ sudo dpkg -i gimpshop_2.2.11-1_*arch*.deb
$ sudo dpkg --force-all -i libgimp2.0_2.2.11-gimpshop1_*arch*.deb

You can ignore any warnings resulting from the libgimp2.0 package.

**3. Tell Synaptic not to update libgimp2.0 to a repository version**

Go in Synaptic, find libgimp2.0, and go to Package->Lock Version.

**4. Enjoy GIMPshop**

Run GIMPshop by selecting Applications->Graphics->_The GIMP_.



**_Change the Shortcut Name_**

If you wish to rename _The GIMP_ under the Applications->Graphics menu to _GIMPShop_, you can do the following:

**1. Install alacarte (if you already have alacarte installed, skip this step)**

$ sudo apt-get install alacarte

**2. Run alacarte from terminal**

$ alacarte

**3. Select Graphics, look for _The GIMP_.**

**4. On _The GIMP_, right click and choose properties.  Where it says name, change it to _GIMPShop_.**

**5. Press Close to exit out of the dialog.**

The next time you go to Applications->Graphics, it will say _GIMPShop_.  You can reinstall xsane and such that we removed in the first step.  (Don't install any packages that require the **gimp** package or things will get screwed up.)  xsane, etc. were just going to conflict with our new libgimp2.0, until we told Synaptic to lock it.

---

### Post by sabitha on 2006-08-19
whats a diferent betwen gimp and gimpshop, i dont see the different

---

### Post by xtknight on 2006-08-19
> **sabitha said:**
> whats a diferent betwen gimp and gimpshop, i dont see the different

One difference is the new Adjustments menu under Image.

---

### Post by Robstero on 2006-08-19
Great job  - thanks a million! Just started my first freelance project since I began using linux so this is a godsend. 

For some reason I had a gimp-related folder that seemed to be stopping the installation from completing. So I just had to do this:

sudo rm -r /etc/gimp

after the "remove all previous gimp components" step above to get rid of the offending folder. Sorted!

---

### Post by powder22 on 2006-08-19
Difference between The Gimp and GimpShop can be found at the following links.
 
GimpShop:

[http://www.gimpshop.net/]("http://www.gimpshop.net/")

The Gimp:

[http://www.gimp.org/]("http://www.gimp.org/")

---

### Post by Dubbayoo on 2006-08-19
sounds very promising.

---

### Post by jsully1 on 2006-08-19
Thank you very much - worked great!

---

### Post by petersjm on 2006-08-19
Wasn't there already a deb for this? Can't remember the link now. Is this any different to the GIMPShop from the existing deb?

---

### Post by xtknight on 2006-08-19
> **petersjm said:**
> Wasn't there already a deb for this? Can't remember the link now. Is this any different to the GIMPShop from the existing deb?

I've never seen a deb for it so I'm unsure of the difference.  It's probably the same.

---

### Post by machia on 2006-08-20
Man thx alot! This is sooo much better :)

---

### Post by zodwallop on 2006-08-20
There is a .deb of an older version of GIMPShop floating around.  It's for version 2.2.8.  I have it installed and for some reason cant get it UN-installed to install this newer version.  When I follow the above posted instructions all seems to go well, but GIMPShop 2.2.8 still loads up instead of 2.2.11.  Please excuse my ignorance as I'm still a n00b when it comes to all things Linux.  Any ideas on how to completely remove The GIMP and the old version of GIMPShop so I can get the new one working properly?  Thanks!

---

### Post by xtknight on 2006-08-20
I'm glad the packages are working for everyone.  :p 

> **zodwallop said:**
> There is a .deb of an older version of GIMPShop floating around.  It's for version 2.2.8.  I have it installed and for some reason cant get it UN-installed to install this newer version.  When I follow the above posted instructions all seems to go well, but GIMPShop 2.2.8 still loads up instead of 2.2.11.  Please excuse my ignorance as I'm still a n00b when it comes to all things Linux.  Any ideas on how to completely remove The GIMP and the old version of GIMPShop so I can get the new one working properly?  Thanks!

Try to find the package name of the old deb and then dpkg -r it.  For instance:

$ dpkg -S /usr/bin/gimp
oldgimpshoppkg: /usr/bin/gimp

$ sudo dpkg -r oldgimpshoppkg

And then follow the instructions in the original post.  If that doesn't work, find out what path the GIMP shortcut points to and then dpkg -S that to find out what package is associated with it.  Then remove the package with dpkg -r.

---

### Post by petersjm on 2006-08-20
> **xtknight said:**
> I've never seen a deb for it so I'm unsure of the difference.  It's probably the same.

Cool. I didn't mean to sound snappy - hope I didn't. Anyway, I just checked what version I have installed - it's 2.2.11. No idea where I got it from! LOL

---

### Post by vrahokipos on 2006-08-25
Another deb version by Suramya
[http://www.suramya.com/blog/2006/06/25/gimpshop-debian-installer-ver-2211-port-available/](http://www.suramya.com/blog/2006/06/25/gimpshop-debian-installer-ver-2211-port-available/)
but i tried to install it 2 days now without something good (except from learning compiling from the source;))

Thanks a lot, with your package everything go fine!

---

### Post by mayamaniac on 2006-08-28
I ran:
> sudo dpkg -i gimpshop_2.2.11-1_i386.deb

and got this error:
> (Reading database ... 84633 files and directories currently installed.)
Unpacking gimpshop (from gimpshop_2.2.11-1_i386.deb) ...
dpkg: error processing gimpshop_2.2.11-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gimp-2.2', which is also in package gimp
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gimpshop_2.2.11-1_i386.deb

Now gimp wont load. Any ideas?

---

### Post by xprlt on 2006-08-28
yep, I got that too, and then nothing installs.

---

### Post by ozPATT on 2006-10-06
i got that too. :( now i have no gimp... :s i was kind of looking forward to checking out gimpshop... sounds like just what i need

now i have no gimp :( just tried installing the other but to no avail ](*,)

---

### Post by leif3d on 2006-10-08
WOW! this is great man...thanks a lot for all your effort!

---

### Post by -::Bas::- on 2006-11-12
Really appreciate this. This was the last thing I needed to finally being able to completely migrate from Windoze to Linux/Ubuntu. Just in time for not having to experience Vista.

---

### Post by dotsi on 2006-11-14
I removed GIMP and installed GIMPShop as instructed but now I get GIMPShop splash screen and GIMP user interface. Any ideas what went wrong and how to fix it?

EDIT: Nevermind, the difference seems to be in the menus with processing an image file. My bad :) Is there any way to make it a single-window app like Photoshop?

---

### Post by MightyMag on 2007-07-12
This guide works great in 7.04 also.

---

### Post by jfg69 on 2007-08-14
Whats the latest on this? Is it a worthwhile change over from the standard Gimp? I'm (probably obviously) a *nix noob trying to migrate from XP and really use PSCS3 a lot.

---

### Post by bogolisk on 2007-08-15
Unless you really want the gimpshop menus and keystrokes, I'd recommend to learn gimp. gimp 2.4 will apparently have optional single-window mode.


[https://lists.xcf.berkeley.edu/lists/gimp-user/2007-July/010449.html](https://lists.xcf.berkeley.edu/lists/gimp-user/2007-July/010449.html)
> 
...It's a forked version and the person who did that fork refuses to work with the GIMP developers...


[http://wiki.gimp.org/gimp/GimpShop](http://wiki.gimp.org/gimp/GimpShop)
> 
...Support for GIMPshop must come from the GIMPshop developers. Please avoid asking questions specific to GIMPshop on the GIMP mailing lists, because the differences between both programs usually cause a lot of confusion...


---

### Post by jfg69 on 2007-08-15
> **bogolisk said:**
> Unless you really want the gimpshop menus and keystrokes, I'd recommend to learn gimp. gimp 2.4 will apparently have optional single-window mode.


[https://lists.xcf.berkeley.edu/lists/gimp-user/2007-July/010449.html](https://lists.xcf.berkeley.edu/lists/gimp-user/2007-July/010449.html)


[http://wiki.gimp.org/gimp/GimpShop](http://wiki.gimp.org/gimp/GimpShop)

I was afraid you'd say that! Oh well, I dont really care for Gimp at this point, I have been using PS for years, have had formal trining in it and I am STILL learning. The last thing I want to do is learn another new prog! But I guess I'll have to give in at some point if I want to continue on *nix and completely dump XP.
I guess I'll keep bangin away at Gimp and see how 2.4 looks when it comes out. Hopefully it will make it into the repo quickly.

---

### Post by bogolisk on 2007-08-15
> **jfg69 said:**
> I was afraid you'd say that! Oh well, I dont really care for Gimp at this point, I have been using PS for years, have had formal trining in it and I am STILL learning. The last thing I want to do is learn another new prog! But I guess I'll have to give in at some point if I want to continue on *nix and completely dump XP.
I guess I'll keep bangin away at Gimp and see how 2.4 looks when it comes out. Hopefully it will make it into the repo quickly.

My points are:
[list]
[*] gimpshop is just gimp (with all its limitations) with modified menus and keystrokes. it will not and simply cannot turn gimp into photoshop. Because photoshop and gimp are not in the same league.
[*] for me, none of that matter, because I *do* like gimp's UI and gimp is already more than enough for home users like me!
[*] there's an alternative path: trying to run PS under wine! Apparently PS 7.0 runs very well under wine and CS3 doesn't like wine. I managed to run CS2 under wine 0.9.41 (badly under wine 0.9.42 and 0.9.43) using a *portable* edition and in Desktop-mode (vs window mode.)
[/list]

---

### Post by jfg69 on 2007-08-15
> **bogolisk said:**
> My points are:
[list]
[*] gimpshop is just gimp (with all its limitations) with modified menus and keystrokes. it will not and simply cannot turn gimp into photoshop. Because photoshop and gimp are not in the same league.
[*] for me, none of that matter, because I *do* like gimp's UI and gimp is already more than enough for home users like me!
[*] there's an alternative path: trying to run PS under wine! Apparently PS 7.0 runs very well under wine and CS3 doesn't like wine. I managed to run CS2 under wine 0.9.41 (badly under wine 0.9.42 and 0.9.43) using a *portable* edition and in Desktop-mode (vs window mode.)
[/list]

I was thinking about trying it under wine. I just read a tutorial the other day on running Dreamweaver under Wine. Gonna dig up my old copy old DW8 and see how THAT goes, and work from there. These are probably the only 2 programs that are stopping me right now from a full swing over from XP.
I'm sure if I keep reading thru stuff I find on Gimp, I'll figure it out well enough to use regularly, but I'd just rather have PS.

Thanks!

j

---

### Post by era86 on 2007-08-15
Finally, something I can use as default for my image editing.  Thanks much!

---

### Post by HaXiT on 2008-03-19
Didin't work for me. I did everything.

1) Gimp doesn't show up in the menu
2) When I open gimp from terminal, it opens up with the GimpShop Splash but there is not GimpShop interface.

Any help? Ideas?

Thanks

---

### Post by Punkristo on 2008-04-18
I installed it and it looks exactly the same as Gimp. It says its gimpshop on synaptic so I dont know whats wrong

---

### Post by neptho on 2008-05-22
> **Punkristo said:**
> I installed it and it looks exactly the same as Gimp. It says its gimpshop on synaptic so I dont know whats wrong

/usr/local/bin/gimp ~= gimpshop.
/usr/bin/gimp ~= gimp

---

### Post by honkey on 2008-06-26
i installe dgimpshop
but there isnt any menu shortcut
if i run teh GIMP 
there is the GIMP splash
and the GIMP interface
NO GIMPSHOP
GIMPSHOP
AAAAAAAAAAAAAAAAAAAAAAH

---

### Post by jfg69 on 2008-06-26
Is GimpShop any longer being supported? I thought it was a dead dog?

---

