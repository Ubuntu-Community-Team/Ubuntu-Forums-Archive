---
title: "Can't get throught DVD menus."
date: 2009-04-03
forum: General Help
---

### Post by Marlonsm on 2009-04-03
I've just tested how Ubuntu would play DVDs and the first one I tried, The Insider, opened normally. But I just couldn't select/click anything on the menus, so I'm stuck in the language selection:

[IMG]http://img222.imageshack.us/img222/737/screenshot1h.png[/IMG]

What can I do?

---

### Post by 3Miro on 2009-04-03
Hm, this looks like Totem. I have never tied playing DVDs in totem, but I have some videos that give me codec issues. I sometimes need to use mplayer. Go to add/remove and search all apps for GNOME Mplayer. I don't know is it will work, but it might.

---

### Post by tominto on 2009-04-03
maybe try xine?

---

### Post by trlkly on 2009-04-04
@OP:

totem-gstreamer is notorious for being bad with DVD menus. You may want to install totem-xine and uninstall totem-gstreamer in synaptic. (You can have both installed, but this is simpler.)

(Synaptic is in System > Administration. Search for totem to find the packages)

@Everyone else:

I find that gmplayer won't even show all the menus, and gxine has a clumsy DVD interface. That's why I recommend totem-xine, It's either that or VLC.

---

### Post by mb_webguy on 2009-04-04
I prefer to use VLC as my default media player, and I've never had a problem playing DVDs.

---

### Post by andrew.46 on 2009-04-04
Hi trlkly,

> **trlkly said:**
> I find that gmplayer won't even show all the menus,

Support for dvd menus is slowly maturing in MPlayer but support or gmplayer has been unofficially dropped some time ago and I believe would be best abandoned by most users. I attach a screenshot of the latest svn MPlayer utilising a dvd menu, just to show that full support is almost there :-).

All the best,

Andrew

---

### Post by LoloftheRings on 2009-04-04
Do you have ubuntu-restriced-extras installed? It contains some proprietary software, like flash player, mp3 support and also DVD playback support.
```

sudo apt-get install ubuntu-restriced-extras

```

---

### Post by coffeecat on 2009-04-04
Do you have libdvdcss2 installed? You need this for encrypted commercial DVDs, otherwise they won't play. Perhaps the menu on this one is unencrypted and the rest encrypted.

You need the [medibuntu]("http://www.medibuntu.org/") repository enabled. And [this is how]("https://help.ubuntu.com/community/Medibuntu").

Once you've done that, install libdvdcss2 and see if that helps. Also install VLC, which comes from medibuntu. It's quite the best multimedia player and plays DVD menus fine.

---

### Post by Marlonsm on 2009-04-04
Thx for replies.

I'm downloading the ubuntu-restricted-extras now, might take some 20min to finish, if it doesn't work, I'll install totem-xine...
And I do have Medibuntu, I'll also get the libdvdcss2, if I need it.

---

### Post by DeMus on 2009-04-04
> **Marlonsm said:**
> I've just tested how Ubuntu would play DVDs and the first one I tried, The Insider, opened normally. But I just couldn't select/click anything on the menus, so I'm stuck in the language selection:

[IMG]http://img222.imageshack.us/img222/737/screenshot1h.png[/IMG]

What can I do?


I use VLC and have no problems. What I do is this:
[LIST=1][*]Start VLC
[*]Start Nautilus and surf to the right folder which is the one with the video_ts folder.
[*]Select and hold down the mouse key on the video-ts folder.
[*]Drag the folder to the bottom panel and hover above the VLC button.
[*]VLC will open.
[*]Drag the mouse to the VLC screen and release the mouse button.
[/LIST]

Now the video will start in the menu and the items are clickable.

Have fun

---

### Post by Marlonsm on 2009-04-04
I'm still downloading ubuntu-restricted-extras, my internet is extremely slow today.
But I think I'll try VLC too. Is there a way to set is as default video player? so always I click a video file or put a DVD it would open.

EDIT: I tried another movie (Forrest Gump) and it didn't even got the the menu, maybe coffecat is right about the menu in The Insider being the only unencrypted part.

Also, I couldn't install the ubuntu-restricted-extras, all packs have finished downloading but one (w32 codecs), that downloads until 22% and restarts.

I'll try VLC now.

EDIT2: VLC is not working, I click to open the movie, the VLC window resizes for a sec, but then it comes back and nothing happens.

EDIT3: Solved. Mplayer and Totem(xine) could open it.
I'll now uninstall Totem(gstreamer) and VLC

---

### Post by trlkly on 2009-04-18
> **andrew.46 said:**
> Hi trlkly,

Support for dvd menus is slowly maturing in MPlayer but support or gmplayer has been unofficially dropped some time ago and I believe would be best abandoned by most users. I attach a screenshot of the latest svn MPlayer utilising a dvd menu, just to show that full support is almost there :-).

All the best,

Andrew

Huh. I thought gmplayer was just a GNOME wrapper around Mplayer, and thus was being updated alongside mplayer.

Maybe it's just me, but I like to have a GUI for my graphical applications.

---

### Post by andrew.46 on 2009-04-22
Hi trlkly,

> **trlkly said:**
> Huh. I thought gmplayer was just a GNOME wrapper around Mplayer, and thus was being updated alongside mplayer.

No gmplayer is the default gui that was originally developed by the MPlayer team itself and it has become something of an embarrassment for the current MPlayer. 

> Maybe it's just me, but I like to have a GUI for my graphical applications.

Fair enough, I note that newer versions of SMPlayer have support for dvd menus although RVM calls it '*experimental*' at this stage. I am running SMPlayer 0.6.7 with the current svn MPlayer and I personally have had no trouble with dvd menus and SMPlayer. I attach another screenshot of Lola and SMPlayer :-).

Andrew

---

