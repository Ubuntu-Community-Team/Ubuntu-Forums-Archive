---
title: "Cannot play CDs / DVDs in KDE"
date: 2005-12-16
forum: Desktop Environments
---

### Post by bulldogzerofive on 2005-12-16
I am confused.

I have been using Ubuntu for a while and it is great.  I switched to Kubuntu because i have always prefered KDE  to Gnome... it just looks nicer.  I installed via kubuntu-desktop in synaptic.

The problem is playing CDs and DVDs.  They work fine in Gnome.  In KDE however neither of them work.  I can mount them and browse the contents fine, but they will not play.  For DVDs Kaffeine gives the error message: "Could not read title information for DVD," while totem says "the specified movie could not be found"  For regular CDs,   most media players can play them, but KsCD cannot.  Still, when they play the drive seems to be spinning at max... at any rate it is way louder than under Gnome.  I am not sure what the deal is. 

Anybody got any thoughts?

thanks, 
mat

---

### Post by stuporglue on 2005-12-16
Did you install kde-base, or kubuntu-desktop? Make sure it was kubuntu-desktop.

---

### Post by bulldogzerofive on 2005-12-21
Yes it was kubuntu-desktop.

Please, i really would like to be able to watch DVDs.  If someody out there has an inkling of what the problem might be but i have not provided enough information, please tell me what you need.

Like i said, everything works in Gnome.

What i have discovered is that if i put the DVD in the drive and type:

umount /dev/hdc
mount /dev/hdc
totem /dev/hdc

it will play (i would really like to do this from the gui, though), but with the following error messages in the terminal:

> 
sysadmin@localhost:~$ totem /dev/hdc

(totem:27575): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:27575): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdnav: Using dvdnav version 1.0.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: LOTR_TWO_TOWERS_D1
libdvdnav: DVD Serial Number: 2EA86922
libdvdnav: DVD Title (Alternative): LOTR_TWO_TOWERS_D1
libdvdnav: Unable to find map file '/home/sysadmin/.dvdnav/LOTR_TWO_TOWERS_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000174d0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001757c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000285e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003cf2c4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003cf2c9
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff

** (totem:27575): WARNING **: Failed to load '/usr/share/xml/iso-codes/iso_639.xml': Failed to open file '/usr/share/xml/iso-codes/iso_639.xml': No such file or directory


with kaffeine it will not play.  Error output:
> 
sysadmin@localhost:~$ kaffeine /dev/hdc
DVB 0 : No such file or directory
DVB 1 : No such file or directory
DVB 2 : No such file or directory
DVB 3 : No such file or directory
kaffeine: No DVB device found.
kaffeine: Window manager: KWin found
kaffeine: Kaffeine:: Try to load service: gstreamer_part
kaffeine: This is a KMediaPart...
kaffeine: GStreamerPart: Load config
kaffeine: GStreamerPart: Found GStreamer version 0.8.11
kaffeine:
kaffeine: GStreamerPart: Using audio driver: alsasink
kaffeine: GStreamerPart: Using video driver: xvimagesink
kaffeine: GStreamerPart: Using visualization plugin: goom
kaffeine: GStreamerPart: Creating video window
kaffeine: GStreamerPart: Set volume to 1
kaffeine: GStreamerPart: Found logo animation:
kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for kaffeine/noatun/m3u/pls/asx playlist
kaffeine: PlayList: Try loading kaffeine playlist
kaffeine: PlaylistImport: kaffeine: /home/sysadmin/.kde/share/apps/kaffeine/playlists/NEW.kaffeine
kaffeine: PlayList: add 1 items to playlist
kaffeine: GStreamerPart: New gstreamer state: READY
kaffeine: GStreamerPart::openURL(): /dev/hdc
kaffeine: GStreamerPart: Got single track
kaffeine: Kaffeine: Set screensaver timeout to: 2 min
sysadmin@localhost:~$ kaffeine: GStreamerPart: play URL: file:///dev/hdc
kaffeine: GStreamerPart: Using source sink: GstFileSrc
kaffeine: Kaffeine: destructor


with mplayer it will not play.  it just hangs on Cache fill:  0.00%

could this have something to do with the way KDE mounts things and passes addresses to media players?

oh, buy the way kscd will not play anything from the command line or otherwise.

---

### Post by bulldogzerofive on 2005-12-22
well, for DVDs i worked aroud the problem by writing a little script to mount, ask if i want to play, and then open the DVD with totem and then associating this script with actions to take on DVDs. Still,  am really curious as to why it won't play.  It turns out, from the desktop i can not even mount it... that freezes the desktop every time.  

Is anyone else having this issue?  Is it a bug?

---

### Post by byourg on 2005-12-25
install kaffeine-xine, then start kaffeine and go to settings, player engine and select kaffeine, not the kaffeine gstreamer, for the engine. I had to do this to get DVD playback. Hope this helps?

---

### Post by bulldogzerofive on 2005-12-27
That is probably part of the problem:  I have xine installed and not Gstreamer.

Reconfiguring kaffeine to use xine as the engine worked... thank you.  Do you have any idea what engine kscd uses by default and where to change that? I suppose i can look it up on google, actually...

The problem that i have to mount and unmount DVDs on the command line is still there, though.  If i try to mount/unmount with the right-click on the desktop it feezes for varying amounts of time that seem to approach a complete stop... "killall kdesktop; kdesktop" is at times the only way to get things moving again.  I have to get around it with that script i mentioned earlier.  This is not a problem for me but my spouse will not touch the computer if something does not work exactly as expected; then i get an earful that i broke the computer again.  I would like to fix it but am not sure how to get further.:confused: 

I think that this mount/unmount thing is the real problem i am having...

If anyone has any ideas?

Thanks

---

### Post by Lord Illidan on 2005-12-27
Can you give us your /etc/fstab ?

Is automounting on?

---

### Post by Sp@z on 2006-01-02
[QUOTE=byourg]install kaffeine-xine, then start kaffeine and go to settings, player engine and select kaffeine, not the kaffeine gstreamer, for the engine. I had to do this to get DVD playback. Hope this helps?[/QUOTE]

Thank you this helped me! Wierd how it works in Gnome not KDE out of the box. But it works now again thank you.

---

### Post by bulldogzerofive on 2006-01-04
OK everything is working just fine now.  Thank you to everyone who helped, especially byuorg.

Just a synopsis:

**Problem:**

Used Synaptic to install kubuntu-desktop on an already functional ubuntu installation, including functioning multimedia.  Multimedia continues to function in Gnome, but under KDE media players will not play CDs or DVDs.  Worse, the desktop appears to freeze for different periods of time when inserting or mounting DVDs.

**Solution(s):**  

_Kaffeine:_  Installed kaffeine-xine.  Set it to use the xine engine instead of Gstreamer.  Found playback was jumpy.  Went to the configure engine options and played with them until I found a mix that works on my computer.  Plays perfectly now.

_Amarok:_  Installed amarok-xine.  Use the xine engine.  Everything plays nicely.

_KsCD:_  It turns out KsCD tries to use a CDROM's built in ability to function as a regular CD player to send audio information directly to the audio card, which saves CPU.  In my case, there is no cable running from the player to the card, so obviously this does not work.  Under KsCD there is an option under extras to use direct digital, which then causes KsCD to send the audio information over the CPU, and it works now.

_Totem:_  Still doesn't work right but i get more functionality out of Kaffeine anyway (playlists and such) so i don't care.

_Desktop freezing:_I think the desktop was locking up when i put stuff in the drive because it was trying to open the media with multiple programs at once.  I am not sure that was the problem, but at any rate it went away by going to konqueror settings:/ then components then file associations and associating all video (including DVD and VCD) to play with Kaffeine and all audio (including CD) to play with amaroK.

---

### Post by YourSurrogateGod on 2006-01-27
[QUOTE=bulldogzerofive]_Kaffeine:_  Installed kaffeine-xine.  Set it to use the xine engine instead of Gstreamer.  Found playback was jumpy.  Went to the configure engine options and played with them until I found a mix that works on my computer.  Plays perfectly now.[/quote]
How did you set it to use the xine engine instead of gstreamer?
[quote=bulldogzerofive]_Amarok:_  Installed amarok-xine.  Use the xine engine.  Everything plays nicely.[/quote]
Just curious, but why did you install amarok?
[quote=bulldogzerofive]_Desktop freezing:_I think the desktop was locking up when i put stuff in the drive because it was trying to open the media with multiple programs at once.  I am not sure that was the problem, but at any rate it went away by going to konqueror settings:/ then components then file associations and associating all video (including DVD and VCD) to play with Kaffeine and all audio (including CD) to play with amaroK.[/QUOTE]
Where are those settings specifically? I can't seem to find them on the desktop. I tried right-clicking on the desktop in order to find what you've described... maybe I missed something.

---

### Post by Neo Ex on 2006-01-27
[QUOTE=YourSurrogateGod]How did you set it to use the xine engine instead of gstreamer?[/QUOTE]
Open Kaffeine, then Settings -> Playback engine -> Kaffeine (I think in English this would be like so).

> 
[...]
Where are those settings specifically? I can't seem to find them on the desktop. I tried right-clicking on the desktop in order to find what you've described... maybe I missed something.
KControl -> KDE Components -> File associations (or Konqueror -> settings:/ (in the location bar) -> KDE Components -> File associations).

---

### Post by YourSurrogateGod on 2006-01-27
[QUOTE=Neo Ex]Open Kaffeine, then Settings -> Playback engine -> Kaffeine (I think in English this would be like so).[/quote]
What do I do then? It leads me to a window that has a few basic options (open file, playlist, etc.) I see nothing with regard to changing from gstream to xine.

---

### Post by YourSurrogateGod on 2006-01-27
[QUOTE=bulldogzerofive]_Kaffeine:_  Installed kaffeine-xine.  Set it to use the xine engine instead of Gstreamer.  Found playback was jumpy.  Went to the configure engine options and played with them until I found a mix that works on my computer.  Plays perfectly now.[/QUOTE]
What options did you alter?

---

### Post by Neo Ex on 2006-01-28
[QUOTE=YourSurrogateGod]What do I do then? It leads me to a window that has a few basic options (open file, playlist, etc.) I see nothing with regard to changing from gstream to xine.[/QUOTE]
I mean this:
[[IMG]http://img78.imageshack.us/img78/9204/schermata61yq.th.png[/IMG]](http://img78.imageshack.us/my.php?image=schermata61yq.png)

Note that 'Kaffeine' is the Xine engine.

---

### Post by YourSurrogateGod on 2006-01-28
Ok, it seems to be working, but the video is somewhat choppy and irregular. As you watch a scene where a camera pans across (a field for example), one can notice that the picture stops for a split second (very short period of time) and then continues.

---

### Post by N8K99 on 2006-01-29
Hey thanks for solving this issue. I can now listen to CDs on my Ti Powerbook running Kubuntu! Awesome!:)

---

### Post by tadashi on 2006-02-20
I managed to get Kaffeine-xine installed but it still will not play DVDs.

I tried the totem workaround and it seems to always crash on me.  It pops open for about 1 sec.

The error I now get in KsCD is CD-ROM read or access error.  Please make sure you have access permissions to: /dev/hdb

I am able to get Kaffiene to play the CD but I get a intermitent static when I play the CD (this seems to be a hardware issue, hopefully, driver related).

---

### Post by SkyNet2029 on 2006-06-30
> Originally Posted by byourg
install kaffeine-xine, then start kaffeine and go to settings, player engine and select kaffeine, not the kaffeine gstreamer, for the engine. I had to do this to get DVD playback. Hope this helps?

Oh Man Oh Man! Dude, you saved me from just wiping my drive and going back to gnome (which I do not enjoy) but now that I can chill and kick back with Terminator3/War of the Worlds (ya, the new one), I am happy as pie with my KDE and DVD. You rock.

---

