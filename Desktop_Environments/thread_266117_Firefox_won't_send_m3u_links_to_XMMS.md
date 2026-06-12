---
title: "Firefox won't send m3u links to XMMS"
date: 2006-09-26
forum: Desktop Environments
---

### Post by thoughts on 2006-09-26
For as long as I've been using Ubuntu, when I click on a link to an m3u file (an MP3 playlist) in Firefox, it would pop up the open/save dialog, where I would select "Open with XMMS."  Then XMMS would play the playlist.

Today I installed the last week's worth of Ubuntu auto-updates, and now when I click on m3u links, Firefox plays them internally using the mplayer plugin.  Ugh!  Terrible.

How can I revert to the old behavior?  I don't see any settings in Firefox's preferences that allow me to choose open/save instead of plugin.  And I've had the mplayer plugin for a long time now, so it's not like it just got installed so now it's taking over m3u.  (Though perhaps it just got updated, and the updated version takes m3u automatically?  Even so, I should get to choose!)  And I don't want to remove the mplayer plugin; it is useful in some cases.

Here's an example m3u link:

[http://magnatune.com/artists/albums/magnacomp-sxsw/hifi.m3u](http://magnatune.com/artists/albums/magnacomp-sxsw/hifi.m3u)

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by yaddoshi on 2006-09-27
I have a similar problem, although I'm trying to get VLC to work.  The problem also seems to affect *.ram and *.asx type files.  Before the update when I clicked one of these links mplayer would be listed as the default player but I would have the option to switch to something else (and then I would have to browse to /usr/bin/vlc to start the player).  That option no longer appears, and whatever file type I try to open automatically opens in the browser in Mplayer.  ](*,) 

I even went a step further and made a backup of my .mozilla directory and deleted it, allowing Firefox to create a new one.  The problem remained.  It does not appear to be a user config issue, but something goofy with this latest Firefox update.  Does anyone know a way around it?  :confused: 

Thanks in advance!

---

### Post by yaddoshi on 2006-09-27
Found a solution!

In the addressbar of Firefox type "about:config" (without the quotes), then press enter.  In the filter: box at the top of the page type "plugin.disable" (again without quotes).

Under Value double-click on whatever is printed there (in mine it said audio/basic) which will allow you to add to the string.  I then made the entire string as follows:

```
audio/basic,audio/mpegurl,audio/x-mpegurl
```

If that doesn't work, open your terminal, type in "grep m3u /etc/mime.types " (without quotes) and you will get a response with the correct mime-type you should be placing into the string field.

Good luck!  :mrgreen:

EDIT:
Oh yeah I almost forgot - restart Firefox after you make the changes!

---

### Post by Jose Catre-Vandis on 2006-10-21
Hmmm, no "plugin.disable" in my list? (again without quotes, lol)

Can I add this setting to config?

[EDIT]

Found the answer here:

[http://linuxweblog.com/firefox-download-actions](http://linuxweblog.com/firefox-download-actions)

As follows:

   1. Type "about:config" on the address bar to get to firefox config settings.
   2. Do a filter search for "hide_plugins" and double click on "browser.download.hide_plugins_without_extensions" to change the settings value to "false".
   3. Open up "Edit > Preferences", go to the "Downloads" area and click on "View & Edit Actions".
   4. It should now list all the "File Type". Do a search for audio and change the "MP3 audio (streamed)" to open up in the external xmms player.

---

### Post by Jose Catre-Vandis on 2006-10-28
And this is all well and good until you upgrade to Edgy and Firefox 2. I like to enqueue files from gnump3d on my home server, so set xmms to enqueue for m3u files in nautilus. this is great under FF 1.7, but in FF 2 you just get play, so you cannot build a playlist from single links on a web page. :-(

---

### Post by Gerard Barberi on 2006-11-03
I just had the same problem, except I'm on Edgy Eft with Firefox 2.0.

I tried everything here, but no luck.  I did eventually fix it another way.

Edit --> Preferences --> Content Tab

Under "File Types", clicked 'Manage'.  

All of Firefox's File associations were here.

---

### Post by meltingrobot on 2006-12-21
Thanks, this helped a lot.  I was getting ready to just remove the mplayer plugin, but I'm happy to have it around for quicktime trailers.  It's nice to not have it try to monopolize playing every single media file the net throws at me though.

---

### Post by kernel scurry on 2007-03-01
I just had to bump this and say thank you.

Toggling browser.download.hide_plugins_without_extensions to false made it so I was able to actually see the actions for each file after clicking manage on the content tab of the prefs.

---

### Post by homerj742 on 2007-04-14
> **Jose Catre-Vandis said:**
> And this is all well and good until you upgrade to Edgy and Firefox 2. I like to enqueue files from gnump3d on my home server, so set xmms to enqueue for m3u files in nautilus. this is great under FF 1.7, but in FF 2 you just get play, so you cannot build a playlist from single links on a web page. :-(


I'm having the same issue. Windows just opened up windows media, or I could just the winamp.exe file. 

I don't know how to replicate something similar in Ubuntu.

---

