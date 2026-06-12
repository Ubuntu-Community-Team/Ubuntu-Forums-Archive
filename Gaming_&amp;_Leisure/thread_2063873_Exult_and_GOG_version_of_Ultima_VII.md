---
title: "Exult and GOG version of Ultima VII"
date: 2012-09-28
forum: Gaming &amp; Leisure
---

### Post by Unotforme on 2012-09-28
Has anyone installed Ultima VII the complete collection from gog.com?
I don't know how to make this work with exult, as the Ultima download is a .exe which (to me) means I have to run it in Wine, which doesn't do me any good.

I ran through the forums at exult and here and couldn't find any install instructions that relate to this version.

---

### Post by oldrocker99 on 2012-09-28
Use Wine to "install" the game. Then move the U7 and SI folers to your home directory in a U7 folder. Install Exult, and point to those folders. It should work.

---

### Post by Unotforme on 2012-09-28
I've never used Wine, so I'm not sure how to do this.
How do I access the virtual drive of wine, so I can copy the files?

---

### Post by oldrocker99 on 2012-09-29
First, install wine from the Software Center, Synaptic, or the terminal:

sudo apt-get install wine

Install Ultima VII by using

wine /path-to/setup-ultima_7-complete.exe

You'll see the GOG installation window. 

Now you can install Exult. No real need to copy the files. When it installs, it'll ask for the path to Ultima VII and Serpent Isle. Tell it:

"~/.wine/drive_c/GOG.com/The Complete Ultima VII/Ultima7" for Ultima 7 (obviously), and

"~/.wine/drive_c/GOG.com/The Complete Ultima VII/Serpent" for Serpent Isle.

~/, by the way is the shortcut for your /home directory, and .wine is a hidden folder (all files with a dot in front are hidden and can be viewed in a file manager by hitting CTRL-H or View/Show Hidden Files. The quotation marks are for the spaces, as you probably already know.

Good luck and let me know if it works. It's still one of the best RPGs ever.

---

### Post by Unotforme on 2012-10-01
No go yet. When I started Exult it said cant find the data files, please edit the config file and set the path.

So here's the start of my exult.cfg config file, using the path you suggested:

```

<config>
 <disk>
  <game>
   <blackgate>
    <title>
    blackgate
    </title>
    <path>
    ~/.wine/drive_c/GOG.com/The Complete Ultima VII/UltimaVII
    </path>
    <gamedat_path>
    /home/larry/.exult/blackgate/gamedat
    </gamedat_path>
    <savegame_path>
    /home/larry/.exult/blackgate
    </savegame_path>
   </blackgate>
   <serpentisle>
    <title>
    serpentisle
    </title>
    <path>
    ~/.wine/drive_c/GOG.com/The Complete Ultima VII/Serpent
    </path>
    <gamedat_path>
    /home/larry/.exult/serpentisle/gamedat
    </gamedat_path>
    <savegame_path>
    /home/larry/.exult/serpentisle
    </savegame_path>
   </serpentisle>
  </game>

```

I also tried /home/larry instead of ~/
The /home/larry for savegame path and gamedat path were already in there.

---

### Post by Unotforme on 2012-10-02
Got it to work. Did a little tweaking and now I've got all my pathnames right, so good to go.

Thanks for your help.

:guitar:

---

### Post by Unotforme on 2012-10-02
I'm not quite there after all...

I can get get Exult to load and play Ultima VII, but I have no sound.
I've tried every setting that comes up under sound setup (both at startup and in game), but nothing.

I do have Timidity++ installed, but can't locate it with Exult, assuming I need it.

---

### Post by oldrocker99 on 2012-10-03
Hmmm...that's one I haven't heard about. Exult does use Timidity; I haven't heard about Timidity++. 

Try this:

locate timidity

and post the results.

---

### Post by Unotforme on 2012-10-03
Here are the results:

```
/etc/timidity
/etc/default/timidity
/etc/init.d/timidity
/etc/rc0.d/K01timidity
/etc/rc1.d/K01timidity
/etc/rc2.d/S99timidity
/etc/rc3.d/S99timidity
/etc/rc4.d/S99timidity
/etc/rc5.d/S99timidity
/etc/rc6.d/K01timidity
/etc/timidity/freepats.cfg
/etc/timidity/timidity.cfg
/etc/timidity/timidity.cfg~
/etc/timidity/timidity_backup.cfg
/home/larry/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,reviews,filter,en,ubuntu,oneiric,any,timidity-interfaces-extra,page,1,,a1c92839c93f23e68fe290f8d3c103ee
/usr/bin/timidity
/usr/lib/timidity
/usr/lib/timidity/bitmaps
/usr/lib/timidity/browser.tcl
/usr/lib/timidity/interface_T.so
/usr/lib/timidity/interface_T.txt
/usr/lib/timidity/interface_g.so
/usr/lib/timidity/interface_g.txt
/usr/lib/timidity/interface_i.so
/usr/lib/timidity/interface_i.txt
/usr/lib/timidity/interface_k.so
/usr/lib/timidity/interface_k.txt
/usr/lib/timidity/interface_s.so
/usr/lib/timidity/interface_s.txt
/usr/lib/timidity/misc.tcl
/usr/lib/timidity/tclIndex
/usr/lib/timidity/tkmidity.tcl
/usr/lib/timidity/tkpanel.tcl
/usr/lib/timidity/bitmaps/back.xbm
/usr/lib/timidity/bitmaps/fwrd.xbm
/usr/lib/timidity/bitmaps/next.xbm
/usr/lib/timidity/bitmaps/pause.xbm
/usr/lib/timidity/bitmaps/play.xbm
/usr/lib/timidity/bitmaps/prev.xbm
/usr/lib/timidity/bitmaps/quit.xbm
/usr/lib/timidity/bitmaps/random.xbm
/usr/lib/timidity/bitmaps/repeat.xbm
/usr/lib/timidity/bitmaps/stop.xbm
/usr/lib/timidity/bitmaps/timidity.xbm
/usr/share/app-install/desktop/timidity-interfaces-extra:timidity-interfaces-extra.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_timidity.png
/usr/share/applications/timidity-interfaces-extra.desktop
/usr/share/doc/timidity
/usr/share/doc/timidity-daemon
/usr/share/doc/timidity-interfaces-extra
/usr/share/doc/timidity/AUTHORS
/usr/share/doc/timidity/NEWS.gz
/usr/share/doc/timidity/README
/usr/share/doc/timidity/README.Debian
/usr/share/doc/timidity/README.alsaseq.gz
/usr/share/doc/timidity/README.dl
/usr/share/doc/timidity/README.m2m.gz
/usr/share/doc/timidity/README.mts.gz
/usr/share/doc/timidity/README.sf
/usr/share/doc/timidity/README.tk
/usr/share/doc/timidity/README.w32.gz
/usr/share/doc/timidity/README.xaw.gz
/usr/share/doc/timidity/README.xskin
/usr/share/doc/timidity/TODO.Debian
/usr/share/doc/timidity/changelog.Debian.gz
/usr/share/doc/timidity/copyright
/usr/share/doc/timidity-daemon/changelog.Debian.gz
/usr/share/doc/timidity-daemon/copyright
/usr/share/doc/timidity-interfaces-extra/changelog.Debian.gz
/usr/share/doc/timidity-interfaces-extra/copyright
/usr/share/lintian/overrides/timidity
/usr/share/man/ja/man1/timidity.1.gz
/usr/share/man/ja/man5/timidity.cfg.5.gz
/usr/share/man/man1/timidity.1.gz
/usr/share/man/man5/timidity.cfg.5.gz
/usr/share/menu/timidity
/usr/share/pixmaps/timidity.xpm
/var/lib/dpkg/info/timidity-daemon.conffiles
/var/lib/dpkg/info/timidity-daemon.list
/var/lib/dpkg/info/timidity-daemon.md5sums
/var/lib/dpkg/info/timidity-daemon.postinst
/var/lib/dpkg/info/timidity-daemon.postrm
/var/lib/dpkg/info/timidity-daemon.preinst
/var/lib/dpkg/info/timidity-daemon.prerm
/var/lib/dpkg/info/timidity-interfaces-extra.list
/var/lib/dpkg/info/timidity-interfaces-extra.md5sums
/var/lib/dpkg/info/timidity.conffiles
/var/lib/dpkg/info/timidity.list
/var/lib/dpkg/info/timidity.md5sums
/var/lib/dpkg/info/timidity.postinst
/var/lib/dpkg/info/timidity.postrm
/var/lib/dpkg/info/timidity.preinst
/var/lib/dpkg/info/timidity.prerm
/var/lib/update-rc.d/timidity

```

I see there is an 'all-in one' audio file at the exult webpage, though it says not required. Here's the link:
[HTML]http://exult.sourceforge.net/download.php[/HTML]
Is that something I need as a seperate download? I have downloaded it, but it needs to go in a folder I can't access (probably have to do it in terminal.

---

### Post by oldrocker99 on 2012-10-06
You can sudo cp the "music" folder to where exult is; it made no difference in my in-game sounds.

---

### Post by Unotforme on 2012-10-07
Funny thing.

I downloaded and installed the all-in-one sound pack in the exult data folder.

Ran the game, still no sound, so I resigned myself to playing wthout sound.

Today, after about 4-5 game sessions, the sound just suddenly worked!?

Anyways, all seems to be good, and now I get to enjoy this gaming classic!

Thanks for your help along the way.

---

### Post by oldrocker99 on 2012-10-07
I'm glad you finally got the sound working....sometimes, the magic works!

Enjoy this total winner, then have a crack at Planescapt:Torment, which (it says here) is playable with the GemRB engine, not that I've gotten it running (yet). An amazing game with arguably the best story of any CRPG.

---

### Post by oldrocker99 on 2012-12-16
BTW, for the next 12 hours as I type, GOG.com is selling Ultima VII for a rock-bottom price of $2.99. Hopefully, the preceding thread will be enough help to any retro gamer interested in the 90's very best RPG.

---

