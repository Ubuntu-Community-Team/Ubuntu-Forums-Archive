---
title: "totem plugin and the totem dummy package"
date: 2005-03-22
forum: Desktop Environments
---

### Post by Knome_fan on 2005-03-22
Seeing that totem-1.0.1 had been released and that it claimed to have an improved mozilla plugin, I apt-geted the source for totem and rebuild the package to include the mozilla plugin. This is fairly easy, all you have to do is add --enable-mozilla to the configure lines in debian/rules.

All works well and I now have a working totem plugin for firefox (I had to link the plugin files from /usr/lib/mozilla/plugins to /usr/lib/mozilla-firefox/plugins to get it working btw., if anyone wants to try it).

However, now the totem dummy package is borked. If I bump the version of totem-xine with dch -i, the dummy package reports as broken, if I don't bump the version, it insists on installing the totem-xine package from hoary. 

I know this is probably an easy to solve situation for someone knowing his way around debian, but I simply can't figure out how to rebuild the dummy package in a way that makes it depend on my selfcompiled version.

Any hints on what to do?

Edit:
Doh, figured it out, google is indeed my friend.
Simply using equivs-build with the control file in totem-1.0.1/debian/totem/DEBIAN build the dummy package.

---

### Post by dangparker on 2005-03-23
Great work!  Any chance you could elaborate a bit?  i.e. how does one "apt-get the totem source" and what's all this about the dummy package?  Very confused....

Thanks
Daniel

---

### Post by Knome_fan on 2005-03-23
[QUOTE=dangparker]Great work!  Any chance you could elaborate a bit?  i.e. how does one "apt-get the totem source" and what's all this about the dummy package?  Very confused....

Thanks
Daniel[/QUOTE]

I'll try. Note though that the totem plugin doesn't do very much right now except play the content, that is the position slider and the settings button don't work. Also note that I'm quite new to anything debian, so I'm probably doing some very stupid things here, so corrections are welcome.

So in order to get the totem plugin I did the following:
1. Install the tools I used:
sudo apt-get install fakeroot devscripts equivs

2. Install the build dependencies for totem
sudo apt-get build-dep totem

3. Get the totem sources
apt-get source totem

Note, you don't have to be root to do this.
This will give you three files:
totem_1.0.1-0ubuntu1.dsc
totem_1.0.1-0ubuntu1.diff.gz
totem_1.0.1.orig.tar.gz
and create the directory totem-1.0.1 

4. Change the version number of the package to build:
cd totem-1.0.1
dch -i
This will open up your editor, so that you can edit the file debian/changelog.dch
Give some information about what you are doing after the * and save the file

5. Change the file debian/rules, so that the plugin gets compiled
In the totem-1.0.1 directory: vi debian/rules
Now look for the following line under build-xine: build-xine-stamp:
./configure --prefix=/usr --sysconfdir=/etc --mandir=\$${prefix}/share/man --libexecdir=\$${prefix}/lib/totem

and add --enable-mozilla to it:
./configure --prefix=/usr --enable-mozilla --sysconfdir=/etc --mandir=\$${prefix}/share/man --libexecdir=\$${prefix}/lib/totem

Do the same thing for the coresponding line under build-gstreamer: build-gstreamer-stamp, if you also want to build totem-gstreamer with the plugin.

Now save the file.

6. Now we are ready to compile the packages:
In the totem-1.0.1 directory do:
dpkg-buildpackage -rfakeroot -uc -us

That's about it, now you should have to .debs in the parent directory of totem-1.0.1,  totem-xine_1.0.1-0ubuntu2_i386.deb and totem-gstreamer_1.0.1-0ubuntu2_i386.deb
(again, not in the totem-1.0.1 directory, but one directory above it)
You can now install either of them and the plugin files will get install in /usr/lib/mozilla/plugins

Note: There might be some build-dependencies that the plugin needs that weren't installed with sudo apt-get build-dep totem but that I had previously installed so that I didn't get any error message. For example, mozilla-dev could be needed. If you get an error, just install the missing packages.

7. In order to get them to work with firefox, I had to link them to the firefox plugin directory:
sudo ln -s /usr/lib/mozilla/plugins/libtotem_mozilla.* /usr/lib/mozilla-firefox/plugins/

But wait: Enter the dummy package
If you open up synaptic and search for totem you'll find three packages: totem-xine, totem-gstreamer and totem.
The last one is a dummy package, that is, its sole purpose is to depend on either totem-xine or totem-gstreamer. As the version of these packages has now changed, synaptic will complaing that totem is broken.

And here's where google was my friend.
So in order to create a dummy package yourself, that depends on the packages you just build yourself, you'll just have to do the following:
cd totem-1.0.1/debian/totem/DEBIAN/

here you'll find a file called control.
Now all there is to do is to use equivs to build a dummy package using this file:
equivs-build control

This will create totem_1.0.1-0ubuntu2_all.deb in the current directory. Simply install it and enjoy a package system that doesn't complain and a working totem plugin.

Have fun.

---

### Post by Nis on 2005-04-13
This is very cool.  I will say you do need mozilla-dev otherwise the plugin will not be compiled and the package will be no different from the standard Hoary totem packages.

---

### Post by JDay on 2005-04-13
Anyone know how to do this with totem 1.1.1 in breezy? --enable-mozilla is already in debian/rules in that version but i don't get any plugin when I compile (yes, it works for me in the hoary version).

---

### Post by RastaMahata on 2005-04-13
could you upload the deb package? :P (could it work in my system as it is?)

---

### Post by JDay on 2005-04-13
[QUOTE=RastaMahata]could you upload the deb package? :P (could it work in my system as it is?)[/QUOTE]
I don't have a place to upload to, but I can email it or something if you want.

---

### Post by JDay on 2005-04-14
Ok, I got the Breezy version to compile with the plugin (included by default  :)) after the big auto-sync last night. Didn't notice the "major enhancements to the experimental mozilla plugin." as mentioned in the changelog. Works pretty well with quicktime, though (although nothing else) and for some reason only the source is available as yet.

---

### Post by RastaMahata on 2005-04-14
sent you a pm

---

### Post by RastaMahata on 2005-04-14
I have found only to things that bother me:
1. If I load a part of the movie, im not allowed to browse it.
2. If the movie ends, I cant play it again from cache. If I reload the site, I have to download the whole movie again :(

---

