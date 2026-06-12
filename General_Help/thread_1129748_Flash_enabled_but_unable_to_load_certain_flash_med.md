---
title: "Flash enabled but unable to load certain flash media"
date: 2009-04-19
forum: General Help
---

### Post by Chrono Reaper on 2009-04-19
I go on screwattack.com most of the time and I found out that even though flash is installed on my computer and I can view media on Youtube and other sites the videos on Screw Attack will not load the flah video. 

Is there a certain plugin that I may have to install for this certain type of media to work? 

I have Ubuntu Jaunty Jackalobe installed on my Dell XPS M1730.

---

### Post by labinnsw on 2009-04-19
If you have compiz enabled, disable it and see it that makes any difference.

If that works you may want to file a compiz bug. (I think if should have been filed already)

Here's another solution if mine did not help [Re: upgraded to 9.04 problems with flash player]("http://ubuntuforums.org/showthread.php?p=7086141"). See the whole thing but entry # 5 in particular

---

### Post by Chrono Reaper on 2009-04-19
I did that, the only two flash plugins i have installed via synaptic is the adobe-flashplugin and the flashplugin-installer.

---

### Post by codeseer on 2009-04-19
Those are what I refer to as 'fake flash'; you need the real official flash to view some things. Are you 32-bit or 64-bit?

---

### Post by acimmarusti on 2009-04-19
to get all codecs and plugins you might need including flash do this:

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by codeseer on 2009-04-19
> **acimmarusti said:**
> to get all codecs and plugins you might need including flash do this:

```

sudo apt-get install ubuntu-restricted-extras

```

What you get in that is still 'fake flash'. I don't know why, but it just will not work on some sites.

---

### Post by Chrono Reaper on 2009-04-19
im a 32 bit

---

### Post by codeseer on 2009-04-19
> **Chrono Reaper said:**
> im a 32 bit

Ok, download the .deb from here: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

Close Firefox. Completely remove those two flash packages you mentioned in the previous post, using Synaptic. Then do the following, exactly, in a terminal window:

```

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```

Then, execute the official .deb package and install it.

---

### Post by Chrono Reaper on 2009-04-19
ok i did everything u said and i got this:

```
chrono@chrono-laptop:~$ sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 kdebase-runtime-data-common
  libxine1-misc-plugins libxcb-xv0 xdotool libboost-thread1.34.1
  kde-icons-oxygen libxine1-bin libexiv2-5 libboost-date-time1.34.1 librasqal1
  libsoprano4 redland-utils libxcb-shape0 libpq5 exiv2 libxcb-shm0
  soprano-daemon kdebase-runtime-data libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
chrono@chrono-laptop:~$ sudo rm -f /usr/lib/mozilla/plugins/*flash*
chrono@chrono-laptop:~$ sudo rm -f ~/.mozilla/plugins/*flash*
chrono@chrono-laptop:~$ sudo rm -f /usr/lib/firefox/plugins/*flash*
chrono@chrono-laptop:~$ sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
chrono@chrono-laptop:~$ sudo rm -rfd /usr/lib/nspluginwrapper

```

And then installed the.deb

Youtube and all the other flash media on the site that i fgo on still work, and yet the flash player that is used on [http://screwattack.com](http://screwattack.com) is still not able to load the video...I only get the flash video box and thats all.

---

### Post by codeseer on 2009-04-19
Let me investigate. Give me a direct link to a page you're trying to view; something that actually has flash on it.

---

### Post by codeseer on 2009-04-19
I see what you mean. That's because they wrap it in a custom player; which benefits nobody. If you'll take that embed tag it gives you at the bottom of the movies like this one:

```
<object width="425" height="355"><param name="movie" value="http://v.giantrealm
.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2Zj
djYg==&from=aHR0cDovL3NjcmV3YXR0YWNrLmNvbS9Pb3RCL2JyZW50YWxmbG9zcw==" type="applicati
on/x-shockwave-flash"></param><param name="allowfullscreen" value="true"></param><par
am name="wmode" value="transparent"></param><embed src="http://v.giantrealm.com/embed
/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==&rom
=aHR0cDovL3NjcmV3YXR0YWNrLmNvbS9Pb3RCL2JyZW50YWxmbG9zcw==" type="application/x-shockw
ave-flash" width="425" height="355" allowfullscreen="true" wmode="transparent"></embe
d></object>
```

...and strip everything before 'http' and everything after the '==' that comes before the '&from=', it will play.

For instance: [http://v.giantrealm.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==]("http://v.giantrealm.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==")

---

### Post by Chrono Reaper on 2009-04-19
> **codeseer said:**
> I see what you mean. That's because they wrap it in a custom player; which benefits nobody. If you'll take that embed tag it gives you at the bottom of the movies like this one:

```
<object width="425" height="355"><param name="movie" value="http://v.giantrealm
.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2Zj
djYg==&from=aHR0cDovL3NjcmV3YXR0YWNrLmNvbS9Pb3RCL2JyZW50YWxmbG9zcw==" type="applicati
on/x-shockwave-flash"></param><param name="allowfullscreen" value="true"></param><par
am name="wmode" value="transparent"></param><embed src="http://v.giantrealm.com/embed
/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==&rom
=aHR0cDovL3NjcmV3YXR0YWNrLmNvbS9Pb3RCL2JyZW50YWxmbG9zcw==" type="application/x-shockw
ave-flash" width="425" height="355" allowfullscreen="true" wmode="transparent"></embe
d></object>
```

...and strip everything before 'http' and everything after the '==' that comes before the '&from=', it will play.

For instance: [http://v.giantrealm.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==]("http://v.giantrealm.com/embed/publisher_id=10&file_id=NTdhYmY4MGMwYWUwOTYwYmU3ZWE2ZTAwZjFkMDM2ZjFjNTQ2ZjdjYg==")

EDIt:

Ahh...thats why...Think ubuntu might come up with a flash update to overcome this?

---

### Post by codeseer on 2009-04-19
Eh, well it's generally broken stuff to begin with, because it provides no real benefit. Consider yourself lucky that they give you that embed tag and the content isn't DRM'ed or Windows-Only in a number of other ways. ABC and CWTV are the two big losers in my book for having players like this that do not work unless they are under a real install of Windows; they won't even work in a VirtualBox installation or Wine. That's the only reason I still have a Vista install.

If I were you, I'd complain to the website people and tell them there's no reason to have that player when the standard flash player is just fine. Their website is pretty horrible in my opinion. I broke through like 15 things in my Firefox security to just see that there was some flash on the page; it's poor programming.

---

### Post by Chrono Reaper on 2009-04-19
I know how you feel too, I have a vista install for college use. Thanx for the help.

---

### Post by rusyear04 on 2009-04-22
i can recommend post #8. it did the trick for me!

thanx to codeseer!

---

### Post by Zaff on 2009-04-23
Okay so I had the same problem because apparently, upgrading to Jaunty installed swfdec-mozilla as part of the gnome package. So I still had the flash plugin but it would load swfdec in firefox instead.
Which doesn't work on some videos.
So I did remove the swfdec-mozilla package and now it works fine, the only problem is that it also removed the gnome metapackage and now I have this :

```
The following packages were automatically installed and are no longer required:
  menu-xdg desktop-base menu planner gthumb gnome-desktop-environment
  gnome-games-extra-data python-gnome2-extras gnome-network-admin libgfortran3
  hardinfo gthumb-data gnome-office python-lxml swfdec-gnome gnumeric-common
  libsoup2.2-8 gnumeric-doc dasher p7zip gnome-themes-extras gdm-themes
  python-numpy arj python-4suite-doc gnome-backgrounds dasher-data gok
  libwmf-bin libswfdec-0.8-0 python-uniconvertor libblas3gf liblapack3gf
  liferea python-4suite-xml gnumeric gnome-accessibility perlmagick inkscape
  libgdl-1-0 serpentine libgdl-1-common gnome-vfs-obexftp
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now I am NOT autoremoving these for obvious reasons, but it is annoying. Is there anyway to get rid of swfdec without removing the gnome metapackage as well ? I understand why they would want to include a free alternative in gnome by default, but I should be able to go back to the adobe plugin if I'm not satisfied with the current solution without having breaking my system.
Granted it's not really broken. Everything still seems to work but I don't like it.
Maybe I'm just being silly.

Anyway if there's another way please let me know.

---

### Post by Jompa on 2009-04-24
I had the same problem, where many flash players wouldn't work, and Youtube was buggy, but post #8 worked for me as well.

---

