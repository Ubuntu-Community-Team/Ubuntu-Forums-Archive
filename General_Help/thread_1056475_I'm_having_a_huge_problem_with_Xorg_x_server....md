---
title: "I'm having a huge problem with Xorg x server..."
date: 2009-01-31
forum: General Help
---

### Post by grndslm on 2009-01-31
After installing Intrepid on my laptop, I'm having a huge problem with my Xorg X server.  I'm pretty sure it comes after installing a huge list of packages.  I thought it was startupmanager and/or my usplash tweakings, but I haven't even installed startupmanager yet.  Here's the list of installed packages (packages which never affected earlier ubuntu releases):

> aptitude install ntp pessulus compizconfig-settings-manager fusion-icon emerald gsfonts-x11 msttcorefonts gtk-smooth-themes gnome-icon-theme-nuovo gnome-icon-theme-dlg-neu gpaint blender stellarium kstars gperiodic kalzium planner cream gparted slocate filelight smartmontools xclip unp unrar p7zip-full alien checkinstall f-spot k3b libk3b2-extracodecs vorbis-tools rezound alsa-oss libid3tag0 libcdaudio1 mp3gain easytag tagtool soundconverter amarok totem-xine xine-ui libxine1-gnome libxine1-plugins vlc vlc-plugin-ggi vlc-plugin-esd vlc-plugin-pulse vlc-plugin-sdl vlc-plugin-arts vlc-plugin-svgalib mplayer mplayer-doc mplayer-fonts mplayer-skins mozilla-mplayer ubuntu-restricted-extras flashplugin-nonfree w32codecs libdvdcss2 libdvdread3 libdvdnav4 libxvidcore4 liba52-0.7.4 libfame-0.9 gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame flac streamtuner streamripper audacity kino k9copy boxee devede winff jokosher miro sun-java6-jre qalculate abiword abiword-plugins lbreakout2 ghextris gtetrinet flobopuyo frozen-bubble armagetronad solarwolf barrage abuse-frabs abuse-sfx xchat mutt liferea pidgin-audacious pidgin-encryption pidgin-extprefs pidgin-hotkeys pidgin-libnotify pidgin-mpris pidgin-musictracker pidgin-otr pidgin-plugin-pack pidgin-themes ssh sshfs gmailfs fuseiso ipcheck rtorrent transmission pan gftp-gtk ntfsprogs sysv-rc-conf sysadmin-guide abs-guide cdbs subversion automake autoconf build-essential linux-image-generic linux-headers-generic linux-restricted-modules-generic linux-source-2.6.27

Many thanks for the help... I definitely need it on this one.

EDIT:  Doh!  Forgot to mention the problem.  At the start of GDM, I sometimes see "double vision", consistent vertical lines down the screen, a large vertical chunk missing out of the right side of the screen, or sometimes the left side of the screen looks 70% alright, but the last 30% is extra distorted.  WTF?

---

### Post by grndslm on 2009-02-01
Perhaps it's a Intel & Intrepid problem??

---

### Post by norwoods on 2009-02-01
maybe the horizontal frequency set on the video card is not compatible with the display.

---

### Post by grndslm on 2009-02-02
So I can't find anywhere online that shows what my horizontal frequency should be set at.  I read somewhere that I should replace the "Monitor" section in xorg.conf with this:

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
        HorizSync       60-70
        VertRefresh     70-160
EndSection

Didn't seem to help any at all.  Seems like almost every other time, Xorg will be all outta whack, or it'll be normal.  I just have to drop down to a virtual terminal and type sudo /etc/init.d/gdm restart in order to keep from getting in an endless loop by pressing Ctrl+Alt+Backspace too fast while trying to "clear up" Xorg.

I am also getting this error at boot, but I'm pretty sure it's network & not graphics related:

```

iwl3945: No space for Tx
iwl3945: Error sending REPLY_LEDS_CMD: iwl3945_enqueue_hcmd failed: -28

```

---

### Post by grndslm on 2009-02-12
Nobody knows what's going on??  Everything seems to work fine until I install the packages listed above (problem only happens on Intrepid & Jaunty; Hardy & before were fine), and then I get the wacky X server.  I don't understand what in my list of apps could be corrupting X like this.

---

### Post by lykwydchykyn on 2009-02-12
Sounds like a hardware/driver issue to me; here are some things you could post for us that might help diagnose the issue:

1. Make/model of the computer
2. output of "lspci"
3. output of this command (searches Xorg log for errors):
```

sudo cat /var/log/Xorg.0.log |grep (EE)

```
4. Photo of what the screen looks like?
5. BIOS version

---

