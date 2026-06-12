---
title: "3 problems i cant seem to fix..."
date: 2005-05-02
forum: Desktop Environments
---

### Post by Borrowed Lab Monkey on 2005-05-02
Im a windows user by nature, so im probibly not thinking this through in a logical linux way, so lets start with the most serious.
  Within Gnome, the horizontal hold on the monitor seems a tad off.  the screen narrows about an inch and quickly expands back to where it should be, repeating this cycle intermitantly, but constantly.  Its really hard to type this as im starting to get motion sick!  the monitor and video card isnt the issue, as it works fine within winXP.      Next is the issue with Nautilus opening the CD DVD-R creator when i put in a disc that has about 3 gigs woth of stuff on it.  I cant get to my files no matter what i try! I burnt the Disc using CDBurnerXP pro v 2.2.9 and left it open for multi session use, would this have anything to do with it?
And last but not least is the DVD playback using totem.  its a no-go. just tells me it cant read the disc regardless of what DVD i put in or which Drive i put it into.  Im stumped! (remember, Windows user?lol)

My Hardware config is as follows...
AMD Athlon XP 1800+
Gigabyte GA-7ZXE Motherboard (no onboard video)
786MB PC133 Ram
Saphire ATI 7500 w/128Mb DDR
SB Live 5.1 Platinum
3com 10/100 Nic
Avermedia PCI350 TV tuner card
SIL 640 IDE/PCI RAID 0+1 adapter
Benq 8x4x16 dvd+/- dual layer burner (connected to mobo ide)
Aopen 16x dvd Rom (connected to mobo ide)
Western Digital wdd200 (connected to mobo ide)
Western digital wdd400 (connected to PCI controllerin raid 0+1 array with samsung)
Samsung 40 gig (connected to PCI controller in Raid 0+1 array with WDD400)
and a patridge in a pear tree ;-)

---

### Post by shakin on 2005-05-02
"Next is the issue with Nautilus opening the CD DVD-R creator when i put in a disc that has about 3 gigs woth of stuff on it. I cant get to my files no matter what i try! I burnt the Disc using CDBurnerXP pro v 2.2.9 and left it open for multi session use, would this have anything to do with it?"

I'm guessing Nautilus opens with the folder burn:///. I use Nautilus in browser mode (more like Win explorer), but I assume 'spatial' mode also has a way to manually type the path. Your DVD disc would be /media/cdrom0 or /media/cdrom1 or something like that. If you type that path it should get you to your files. I might suggest filing a bug report with Gnome because there should be an obvious way to switch between burn mode and browse mode on multisession discs.

"And last but not least is the DVD playback using totem."

Yes, totem with gstreamer is broken or it sucks or something like that. A lot of people can't get it to work. Use Synaptic to install VLC (also wxvlc for a gui) and it will work much better than totem. You can also install the totem-xine package (which will remove the totem-gstreamer package) to use the xine movie player version, which works better than the gstreamer version.

---

### Post by tread on 2005-05-02
> Within Gnome, the horizontal hold on the monitor seems a tad off. the screen narrows about an inch and quickly expands back to where it should be, repeating this cycle intermitantly, but constantly. 

I'm sure I dont understand this! Could you elaborate? Also, if you are having display problems, its more likely an xserver problem, and not gnome.

Try looking at [http://ubuntuguide.org/](http://ubuntuguide.org/)  for some getting-started information.

---

### Post by cdhotfire on 2005-05-02
```

[Q: How to install DVD playback capability?]("http://Q:%20How%20to%20install%20DVD%20playback%20capability?")[url="http://Q:%20How%20to%20install%20DVD%20playback%20capability?%3Cbr%20/%3E"]
[/url] sudo apt-get install libdvdcss2

```

taken right off the unofficial guide. that should give your totem dvd powers.:)

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=Borrowed Lab Monkey]
  Within Gnome, the horizontal hold on the monitor seems a tad off.  the screen narrows about an inch and quickly expands back to where it should be, repeating this cycle intermitantly, but constantly.  Its really hard to type this as im starting to get motion sick!  the monitor and video card isnt the issue, as it works fine within winXP.     
My Hardware config is as follows...
AMD Athlon XP 1800+
Gigabyte GA-7ZXE Motherboard (no onboard video)
786MB PC133 Ram
Saphire ATI 7500 w/128Mb DDR
[/QUOTE]
This seems to be some serious problem with video drivers. For starters, you may switch to a command line terminal while fixing the problem - not so user-friendly, but at least no motion sickness :). You can do it by pressing Ctrl+Alt+F1 (to get back, press Ctrl+Alt+F7). 

Now: can you check if there are some error messages in one of the following files: 
~/.xsession-errors
/var/log/Xorg.0.log
(in command line terminal, you can use command "less" to print files to screen, or use emacs editor if you have it installed).

---

### Post by phen on 2005-06-08
regarding the dvd multisession problem: try to change the autostart settings for recordable CD/DVD, under System -> Settings -> Changeable media / harddisks

turn off the autostart things for recordable cd/dvd, and access your dvd via the normal nautilus explorer

note: i had to translate the menus from german, so maybe they are named differently (i am almost sure about it..)

---

