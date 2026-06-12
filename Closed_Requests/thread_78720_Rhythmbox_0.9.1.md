---
title: "Rhythmbox 0.9.1"
date: 2005-10-18
forum: Closed Requests
---

### Post by idn on 2005-10-18
Maybe we could put this in the breezy backports repos when they are up. It has just been released - I'm sure many people would welcome this update. There are many new features / fixes:

Overview of Changes in Rhythmbox 0.9.1
======================================

* Add DAAP (iTunes' music sharing) support [Charles Schmidt]
* Notification bubble from tray icon [Colin Walters]
* Minimise to tray rather than exiting when close is used [Colin Walters]
* Allow sources to form a tree, for child playlists [Charles Schmidt]
* Add removable media framework and port ipod code [James Livingston]
* Support HAL >= 0.5 as well as > 0.2 [Ronald Bultje]
* Much improved automatic playlists, including more criteria options and
  sorting [James Livingston:132566]
* Use a proper GTK status bar [William Jon McCann]
* Better drag-n-drop support: drag from browsers to source list, from browsers
  or track list to other apps and re-order playlists [Jonathan Matthew: 147337]
* Update DBus support to version 0.35, general DBUS improvements and drop
  command-line arguments for DBus [Colin Walters]
* Add "limit by time" option to playlists [James Livingston: 159227]
* Display hours if a song is longer than 60 minutes [Jonathan Matthew: 313311]
* Use new volume widget, same as in Totem [Ronald S. Bultje: 300867]
* Focus entry view when enter is pressed in search box [Paolo Borelli: 128110]
* Show source list when playlist os created [James Livingston: 161935]
* Disable rather then hide seek bar [James Livingston: 139102]
* Improved error handling in RBPlayer [Colin Walters]
* Remove dashboard support [Colin Walters]
* Many HIG and UI improvements [Dennis Cranston and Paolo Borelli]
* Use last.fm instead of allofmusic.com for links [Colin Walters]
* Remove autorating of tracks [Colin Walters]
* Fix header synchronisation [Raphael Slinckx]
* Fix some window state issues [James Livingston: 313893 and 137068]
* Add "Date Added" column [Ernst Persson]
* Better playlist loading [James Livingston, Bastien Nocera, Colin Walters]
* Make playing source bold, rather than using an icon [Colin Walters]
* Allow library-derived sources to override behaviour [James Livingston]
* Correctly update status bar and don't use useless info [James Livingston]
* Add support for building API docs with gnome-doc-utils [Raphael Slinckx]
* Update the default radio stations [Ali Akcaagac:129285]
* Remove a heap of old code, and use stock art instead of custom art
* Many rhythmdb improvements
* Fix more memory leaks
* Many bug fixes and minor improvements

Updated Translations:
* ca (Josep Puigdemont i CasamajÃ³)
* cs (Miloslav Trmac)
* da (Morten Brix Pedersen, Ole Laursen)
* de (Hendrik Brandt)
* el (Kostas Papadimas)
* en_CA (Adam Weinberger)
* es (Francisco Javier F. Serrador)
* fi (Ilkka Tuohela)
* fr (Stephane Raimbault)
* gl (Ignacio Casal Quinteiro)
* hu (Gabor Kelemen)
* lt (Å½ygimantas BeruÄka)
* ne (Pawan Chitrakar)
* nl (Tino Meinen)
* pt_BR (Raphael Higino, Afonso Celso Medina)
* vi (Clytie Siddall)
* zh_CN (Funda Wang)

---

### Post by idn on 2005-10-20
* bump *

I think this would be really awesome to add into backports for breezy

---

### Post by Reb on 2005-10-26
It's very easy to build this for anyone inclined... just "sudo apt-get build-dep rhythmbox". You'll probably need to install most of the libavahi-*-dev, the avahi-daemon and avahi-dnsconf packages, as well as the libsoup-dev packages (these if you want DAAP - iTunes sharing, otherwise just build-dep rhythmbox will do). I had to install many packages for this, some of which may have been unnecessary.  Then download the sources, extract them, do ./configure --prefix=/usr [--enable-daap if you want it also - I'm on a campus with a ton of iTunes sharers], make, sudo make install and you've got it. It's nice!

---

### Post by Kyral on 2005-10-26
Wait for it to hit Dapper ;P

---

### Post by Reb on 2005-10-26
However, DAAP sharing doesn't seem to work...

---

### Post by macmasterxiv on 2005-10-29
Well, for anyone interested, I created a deb of 0.9.1 w/ daap enabled. You can get it [here.]("http://jm.homeunix.org/rhythmbox_0.9.1-1_i386.deb")

---

### Post by RSX311 on 2005-10-29
[QUOTE=macmasterxiv]Well, for anyone interested, I created a deb of 0.9.1 w/ daap enabled. You can get it [here.]("http://jm.homeunix.org/rhythmbox_0.9.1-1_i386.deb")[/QUOTE]


link doesn't work :(

---

### Post by idn on 2005-10-29
did for me :)

---

### Post by RSX311 on 2005-10-29
ahh, link works now, thanks!

---

### Post by idn on 2005-10-29
Pretty nice, like the notification area telling you wahat song is playing, also the close button minimizing to the system trya.

BTW you cant jsut install the deb, you have to install a few other depndancies. If you open the deb and see what you want you can get them from synaptic. Everything works fine then.

---

### Post by zachtib on 2005-10-30
actually, the easy thing to do is to install the deb normally, with a 
sudo dpkg -i nameoffile.deb
then dpkg will complain about dependencies, but open up synaptic and do 
Edit >> Fix Broken Packages
then hit apply, and the deb will have installed fine

now, does RhythmBox's DAAP sharing allow more than 5 users daily? Im on a college campus with lots of sharers, and the 5 a day limit gets very annoying

---

### Post by macmasterxiv on 2005-10-30
It shouldn't have that limit since Apple added that to iTunes to limit potential downloading from shares.

---

### Post by zachtib on 2005-10-30
OK, one thing that im noticing, is that when i access my windows pc over DAAP, the playlists are backwards (the last track on the list appears first on RB)

---

### Post by merlyn on 2005-10-31
[quote=macmasterxiv]Well, for anyone interested, I created a deb of 0.9.1 w/ daap enabled. You can get it [here.]("http://jm.homeunix.org/rhythmbox_0.9.1-1_i386.deb")[/quote] 
Thankyou, thankyou, thankyou!

Oh and by the way did I say thankyou!

---

### Post by zachtib on 2005-11-01
Another question about DAAP:  how does it work with aac and ogg files?
for example, if my linux box's music is in ogg format, could a windows pc running iTunes listen to it, whihc doesn't support ogg, and vice-versa.

---

### Post by doclivingston on 2005-11-01
[QUOTE=zachtib]Another question about DAAP:  how does it work with aac and ogg files?
for example, if my linux box's music is in ogg format, could a windows pc running iTunes listen to it, whihc doesn't support ogg, and vice-versa.[/QUOTE]

DAAP just sends the files as-is, and the client has to deal with them. That means that the windows pc will complain if you don't have an ogg vorbis codec installed, and Rhythmbox will complain if you don't have the aac codec (gstreamer-faad) installed.

---

### Post by zachtib on 2005-11-01
[QUOTE=doclivingston]DAAP just sends the files as-is, and the client has to deal with them. That means that the windows pc will complain if you don't have an ogg vorbis codec installed, and Rhythmbox will complain if you don't have the aac codec (gstreamer-faad) installed.[/QUOTE]

wow, i didnt know know it was even possible to play aac files on linux
*opens up synaptec*
and, go figure, i already had it installed

---

### Post by duffman25 on 2005-11-10
[QUOTE=zachtib]wow, i didnt know know it was even possible to play aac files on linux
*opens up synaptec*
and, go figure, i already had it installed[/QUOTE]

*bump*
Is this a valid backport?

---

### Post by Kyral on 2005-11-10
Only packages made by the Backport Team can be considered official Backports

---

### Post by duffman25 on 2005-11-11
[QUOTE=Kyral]Only packages made by the Backport Team can be considered official Backports[/QUOTE]
I wasn't refering to the deb in here, but to the new rhythmbox in dapper being backported. Does it build cleanly?

---

### Post by doclivingston on 2005-11-11
It should build fine, since some of the Rhythmbox developers (myself included) use Breezy. It should also be back-portable to Hoary, if Totem 1.2 if installed.

---

### Post by jdong on 2005-11-11
Working on a backport....

---

### Post by fosk on 2005-11-11
[QUOTE=jdong]Working on a backport....[/QUOTE]

Cool!!!
Looking forward it!!

Thank you so much to every backports people!

---

### Post by jdong on 2005-11-11
Works, build queued to James.

---

### Post by potrick on 2005-11-26
sorry to bother you, but it looks like the link to the .deb is broken again. Does anybody out there have it? I'd really like to play with the DAAP.

never mind, I figured it out. I learned about backports today. Sorry for wasting forum space.

---

### Post by daveg on 2005-11-28
Its a shame that it isn't built with DAAP support :-(

---

### Post by duffman25 on 2005-11-28
[QUOTE=daveg]Its a shame that it isn't built with DAAP support :-([/QUOTE]

I have a small bug with this backport, but I don't know if it's only me:
When I launch rhythmbox (and therefore the main window is visible) the tray icon item that says "Show music player" is un-ticked. When I minimise the main windows, that item becomes ticked. I should expect the behaviour to be the other way round. Anyone can confirm this?

---

### Post by doclivingston on 2005-11-28
[QUOTE=duffman25]I have a small bug with this backport, but I don't know if it's only me:
When I launch rhythmbox (and therefore the main window is visible) the tray icon item that says "Show music player" is un-ticked. When I minimise the main windows, that item becomes ticked. I should expect the behaviour to be the other way round. Anyone can confirm this?[/QUOTE]

That's a known bug, which got fixed after 0.9.1.

---

### Post by duffman25 on 2005-11-28
[QUOTE=doclivingston]That's a known bug, which got fixed after 0.9.1.[/QUOTE]

Ok, thanxs for answering

---

### Post by flickerfly on 2005-11-28
I installed 0.9.1 using the package mentioned here. I have 2 networks connected to this machine with shares on both sides. 

> Could not start browsing for music servers on your network.  Rhythmbox will continue to function, without this feature.  Check your Avahi installation

Any idea what this means? I do see some music shares, but I have found music to play on one side of the network (eth0). I see another share that I'm not sure which side it is on. I'd expect, if it was catching the network on eth1, that it would have found a lot more networks.

Also of interest, though probably a Rhythmbox issue, when I restart avahi, Rhythmbox crashes.

---

### Post by trickie on 2005-11-29
Any chance of Rhythmbox getting rebuilt with DAAP support?

---

### Post by jdong on 2005-11-29
Those kinds of changes to the source packages can only be done by a Ubuntu developer with main repository upload rights... Contact #ubuntu-devel on freenode if you want to get in contact with those who can make these decisions... Backports is powerless for those kinds of changes.

---

### Post by doclivingston on 2005-11-29
I wouldn't advise building packages with DAAP support yet. It's marked as "experimental" because there are a couple of potentially nasty bugs (some of which can't be fixed within Rhythmbox itself). In particular, if you use the version of libsoup that shipped with breezy, Rhythmbox will start chewing all your cpu as soon as any connects to you share and does anything apart from playing entire songs (e.g. pausing or skipping).

---

### Post by trickie on 2005-11-30
Thanks for the tip on the process jdong.

And doclivingston i just built my own package and see what you mean! Not very stable at all.

---

### Post by shekhark on 2006-01-02
The link to the deb doesn't work for me. I would really love to be able to share my iTunes Music Library sitting on my Powerbook (and connected to a Firewire disk which I cannot plug into my Ubuntu Thinkpad directly) using DAAP and Rhythmbox. Please let me know when the deb is back online.

---

### Post by gsmith on 2006-02-01
That deb seems pretty cool to me, but it crashes when I go to edit -> preferences.  Anyone experience anything similiar?

---

### Post by stanz on 2006-03-15
Hi All,
I'm happy with ubuntu & rythembox...thing is- for the radio part- the buffer gets stuck or whatever happening there-
I get a short blast of some good tunes~ and thats it ?
I'ld say- it might even 'hang'...but not for long.
any settings to change?  adjustments here or there?
thanks in advance!!
---------------
no 'edit' crash here...even while tunes r blaring.  :)
--------------
jus' thought to update the tunes thing:: I went thru XMMS, with streamtuner and its the kewlest!

---

