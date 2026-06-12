---
title: "Changes to mozpluggerrc does not seem to take effect?"
date: 2009-03-08
forum: General Help
---

### Post by TurpoNieminen on 2009-03-08
I wasn't sure should i post this to multimedia or networkin or what so i post in general...

First i say that im new user to Ubuntu 8.10 and
Im trying to edit mozpluggerrc so it would open wmv streams with VLC player, so i changed the default part of application/x-mplayer2 mimetype in /etc/mozpluggerrc

```

application/x-mplayer2:*:Windows Media video
video/x-ms-asf:asf,asx:Windows Media video
video/x-ms-wm:wm:Windows Media video
video/x-ms-wmv:wmv:Windows Media video
	: vlc -vvv "$file"
video/x-ms-wvx:wvx:Windows Media video
video/x-ms-asf-plugin:*:Window Media video
	MP_VIDEO_PLAYLIST(%.asx)
	MP_VIDEO_STREAM()        
	TM_VIDEO_STREAM()

```

and deleted the home/profilename/.mozilla/firefox/95cvfcym.default/pluginreg.dat file

However there is no effect in Firefox.
Firefox still opens wmv streams with totem plugin. The reason i don't want to open them in the browser window
is that no plugin for ubuntu and firefox support seeking in wmv streams!? 

Can anyone help?

---

### Post by dcstar on 2009-03-09
> **TurpoNieminen said:**
> I wasn't sure should i post this to multimedia or networkin or what so i post in general...

First i say that im new user to Ubuntu 8.10 and
Im trying to edit mozpluggerrc so it would open wmv streams with VLC player, so i changed the default part of application/x-mplayer2 mimetype in /etc/mozpluggerrc

```

application/x-mplayer2:*:Windows Media video
video/x-ms-asf:asf,asx:Windows Media video
video/x-ms-wm:wm:Windows Media video
video/x-ms-wmv:wmv:Windows Media video
	: vlc -vvv "$file"
video/x-ms-wvx:wvx:Windows Media video
video/x-ms-asf-plugin:*:Window Media video
	MP_VIDEO_PLAYLIST(%.asx)
	MP_VIDEO_STREAM()        
	TM_VIDEO_STREAM()

```

and deleted the home/profilename/.mozilla/firefox/95cvfcym.default/pluginreg.dat file

However there is no effect in Firefox.
Firefox still opens wmv streams with totem plugin. The reason i don't want to open them in the browser window
is that no plugin for ubuntu and firefox support seeking in wmv streams!? 

Can anyone help?

Why not just change the Firefox application for that file type?

---

### Post by TurpoNieminen on 2009-03-09
> **dcstar said:**
> Why not just change the Firefox application for that file type?

If i change in Firefox -> Edit -> Preferences -> Applications -> Windows Media -video 
then "Use other..." i point to  /usr/bin/vlc
It changes to VLC but in browser there is no no effect, the video still plays in browser window (using totem-gstreamer plugin for mozilla i believe)

---

### Post by TurpoNieminen on 2009-03-11
Well i got this working now, sort of...

First i removed totem-mozilla plugin, (disabling that plugin in Firefox was not affecting anythin)

Then the videos started to play with mozilla-mplayer plugin, i removed that also.

Only then the mozplugger and VLC kicked in, this is strange because i had set Firefox application preferences to open Windows Media -video with mozplugger as default. (i think that was default even before i started to change any settings)

It seems that Firefoxes Preferences -> Applications settings and disabling plugins does not take effect for some reason. (didnt try to start Firefox with gksudo tough if this is related to user priviledges) 

I would like to get totem-plugin and/or mplayer plugin to work with other filetypes, so this really is not very good solution...

any ideas?

---

### Post by TPM on 2009-11-22
The solution is to do the following steps: 
  
   1. Edit your mozpluggerrc
   2. Exit Firefox (if running)
   3. Uninstall MozPlugger (or move mozplugger.so to some other dir)
   4. Start Firefox
   5. Stop Firefox
   6. Re-install/move back MozPlugger/mozplugger.so, make sure you don't overwrite your edited mozpluggerrc.
   7. Done, next time you start Firefox, it will recognize the changes.

---

