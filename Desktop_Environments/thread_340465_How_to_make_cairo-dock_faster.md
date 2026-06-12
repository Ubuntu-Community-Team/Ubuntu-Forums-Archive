---
title: "How to make cairo-dock faster?"
date: 2007-01-17
forum: Desktop Environments
---

### Post by JedTheHead on 2007-01-17
Anyone know how to make cario-dock faster?  It seems a bit sluggish on all my machines and I'm NOT a developer so I can't determine if this speed is the result of settings in the code, or if its just a slow app.  I'd really like to see it respond more quickly and smoothly when moused over, etc.

Just curious...

Thanks!

---

### Post by hihihi on 2008-05-19
yeah, good question!
i find cairo-dock on my system too slow:
running xubuntu hardy 64bit with compiz on nvidia 8400 gs, latest drivers, compiz runs top,
thx in advance

---

### Post by fabounet on 2008-05-21
try to determine if it's not an applet that is slowing the dock.
if not, then you can try to set up some CPU options in the "system" tab
also, try to reduce the zoom or the icons' size.
if you have too much icons into your dock, consider grouping applis together in the taskbar  and/or grouping applis with launchers and/or grouping launchers in some sub-docks.

But the ultimate solution is to enable the hardware acceleration into your dock. You have to compil it with Glitz, and the result is impressive.
see the wiki in [http://cairo-dock.org]("http://cairo-dock.org")

---

### Post by hihihi on 2008-06-21
Thanks, you are right, in the meantime I found a good solution,
actually on the french cairo-dock site:
is installing cairo-dock with glitz support and than running 
$ cairo-dock --glitz

all the deatils here:
[http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en)

$ sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1 dbus libdbus-1-3 libdbus-glib-1-2 libvte9 libxxf86vm1 libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libbonoboui2-0


	$ cd /opt
	$ sudo mkdir cairo-dock_svn
	$ cd cairo-dock_svn/
	$ sudo wget [http://cairo-dock.vef.fr/cairo-dock_svn.sh](http://cairo-dock.vef.fr/cairo-dock_svn.sh) 

	$ sudo chmod u+x cairo-dock_svn.sh
	$ sudo ./cairo-dock_svn.sh &#8211;enable-glitz


Thanks to all.

---

### Post by sc00ter on 2008-06-27
The version of cairo etc. this downloads appears to break sub-pixel rendering, consequently making all fonts look awful on a laptop display.

The only way to recover is to back out the installation and remove the library files (cairo, pixman and glitz) it installs under /usr/local/lib

It may appear that these 3 libraries that the installer downloads do not have the necessary patch files applied for Ubuntu and lcd filtering.

Any idea how to install the hardware accelerated version without upsetting the font rendering?

---

### Post by hihihi on 2008-06-28
i saw this, too, you are right!
but it is not all the fonts.
just the fonts in the mozilla-browser...
it has something to do with pango, witch is enabled with the cairo-installation-link posted by me above.
there is a way to disable pango in firefox:
[http://ubuntuforums.org/showpost.php?p=807322&postcount=28](http://ubuntuforums.org/showpost.php?p=807322&postcount=28)
works great.
a general way to make your fonts look better on the whole system (exclud. firefox-pango stuff)
is to open terminal
$ sudo gedit ~/.fonts.conf
paste this and save:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>

voila, your fonts look better than ever :)

---

### Post by Maharifu on 2008-06-30
Hi.
I installed cairo-dock_svn with the hardware acceleration using the script you mentioned. It runs faster and smoother when using the --glitz option, but the sub-docks are all buggy. The text in the sub-docks never show and sometimes not all the icons will show.
It all works good without the --glitz option, but i would like to use hardware acceleration.
Anyone had this bug and knows how to solve it?!

---

### Post by fabounet on 2008-06-30
It is known that in the parabolic view, text is not displayed properly with glitz, for some unknown reason.
otherwise, it seems to work fine and smooth.

By the way, the script installs cairo/pixman/glitz in /usr/local/lib, so it shouldn't interfere with your system at all, except if you have the path "/usr/local/lib" in your $LD_LIBRARY_PATH.

---

### Post by Maharifu on 2008-06-30
But, in my case, it's not just the text that is not displayed properly, the icons aren't either. Some times i don't see any icon until i hover the area where they should be with my mouse. Other times i see half an icon and when i hover it i see them all.

I do have the LD_LIBRARY_PATH variable set to /usr/local/lib. Am i suppose to?!

Oh, and i'm using ubuntu x64, don't know if that makes a difference.

And yes, i'm an ubuntu noob.. :P

---

### Post by hihihi on 2008-07-01
--glitz works fine on mine,
xubuntu hardy 64bit, nvidia 8400 gt m, prop.-drivers

but tell us more:
what graphic-card do you have?

---

### Post by Maharifu on 2008-07-01
I have a 8400M GS, using prop drivers. I'm on a laptop, Compal FT00. Using Ubuntu Hardy 64bits.

---

### Post by hihihi on 2008-07-08
seems like in the meantime some things changed and that auto-remote-installation is not going so well, it moans about mozilla-gtkmozembed not being there...
anyone has a solution here? ah, and i do not speak french...

Installation du plug-in nVidia

Erreur

Installation du plug-in weblets

Erreur

Installation des themes

Vérification de l'intégrité de l'installation
checking for PACKAGE... configure: error: Package requirements (cairo-dock mozilla-gtkmozembed) were not met:

Des erreurs ont été détéctées lors de l'installation.
Veuillez consulter le fichier log.txt pour plus d'informations et vous rendre sur le forum de cairo-dock pour reporter l'erreur dans la section "Version SVN"

---

### Post by hihihi on 2008-07-08
ok, to have gtkmozembed, you need to install xulrunner1.9-dev.

later it stopped because of the nVidia plugin.
i solved it by editing the install-script "cairo-dock_svn.sh", commenting out the script itself not to be renewed by SVN-update, and deleting "nVidia" from the plugin list.
installation successfully, cairo-dock --glitz works nice.

---

