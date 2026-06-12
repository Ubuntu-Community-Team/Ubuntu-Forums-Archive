---
title: "Music players using new notify-osd"
date: 2009-06-18
forum: Desktop Environments
---

### Post by Onion Avenger on 2009-06-18
Hi,

I'm trying to find a music player that uses notify-osd.  I'm used to the behavior in the OSD plugin in Audacious where I can show popups not only when I change songs, but also when I pause and resume.

So far, the closest match that I've found is Banshee.  It will popup the song title using notify-osd but only when it skips to the next track in the playlist.  This is a good start, however I would like it also to show popups when I pause and resume.  I've tried Exaile, Audacious (has its own OSD system but I would like it integrated with notify-osd), Amarok (similar behavior to Audacious--which I like--but no notify-osd support), Rhythmbox (nothing), and several others. 

Is nothing available yet?  Does somebody need to write a plugin or something?

---

### Post by Onion Avenger on 2009-06-19
I decided to take matters into my own hands.  I downloaded the Banshee source and created a hack to do exactly this.  Here is the bug I filed with the Banshee team, my patch is attached to it.

[http://bugzilla.gnome.org/show_bug.cgi?id=586333](http://bugzilla.gnome.org/show_bug.cgi?id=586333)

I guess other music players would need similar modifications.

---

### Post by svD on 2009-08-22
long time ago, but thanks for your "patch"... thats a feature i missed, to. i will test it now...

edit: can you give me a little "howTo" install? :)

---

### Post by Onion Avenger on 2009-08-23
> **svD said:**
> long time ago, but thanks for your "patch"... thats a feature i missed, to. i will test it now...

edit: can you give me a little "howTo" install? :)

Sure, it's been awhile so I'm a little rusty.  Hope you're not afraid to get your hands a little dirty though, I haven't made a .deb or anything from this.

First you need to get banshee's development sources.  I pulled off a copy of the git trunk back in June when I made the patch.  I assume that things haven't changed so much since then that the patch no longer applies.

Follow the steps here: [http://banshee-project.org/download/development/](http://banshee-project.org/download/development/) to get the source.

Next, download my patch (see the bug report in my earlier post).

Now, you need to apply the patch.  This page:
[http://banshee-project.org/contribute/write-code/](http://banshee-project.org/contribute/write-code/) refers to this page: [http://live.gnome.org/Git/Developers](http://live.gnome.org/Git/Developers), which has some pointers on applying the patch.

Finally, compile it (use the steps in [http://banshee-project.org/contribute/write-code/](http://banshee-project.org/contribute/write-code/)) and run it.  I didn't install it to any system directories, I just left a copy in my home directory that I run.

That should help. Lemme know if you have any other questions.  If I had more time I would make the patch a bit better.  Right now it's really just an ugly hack to get things working.  I really wish we had this feature on more media players.  It appears that not everyone thinks it's important or even needed (see the comments on the upstream bug report I filed).

---

### Post by svD on 2009-08-23
Thanks for your detailed explanation!

...coming from windows and foobar2k this is a must-have-feature... pausing the audioplayer und coming back and know what's playing... why not?

is their an easier way than recompile the whole sourcecode, e.g. editing a settings-file of the plugin? as a like newbie i like software installed "regularly".

---

### Post by Onion Avenger on 2009-08-23
> **svD said:**
> Thanks for your detailed explanation!

is their an easier way than recompile the whole sourcecode, e.g. editing a settings-file of the plugin? as a like newbie i like software installed "regularly".

Unfortunately, the only way with Banshee (that I can tell) is with this patch.  If you're just coming from windows I recognize that all those steps must be very confusing.  Here, I'll create a .deb that you can install that will have this Banshee functionality.  It'll make things easier for you and it'll be good practice for me. :)

I'll post it here later today.

---

### Post by Onion Avenger on 2009-08-23
Alright svD, here you go.  I compiled this on my laptop and my pause/resume notification ability works.  If your system is drastically different than mine, then it may not work.  Assuming it works, just download the .deb file and open it up to install it.  I don't think that the file has the right dependency stuff, so I think the best option is to first make sure you banshee already installed, THEN install my version.  It'll overwrite your version and you should get the pause/resume notifications.  Keep in mind that the notifications only show up when Banshee is not focused.  So either minimize it or switch to another application, then do your pausing and resuming to see it in action.

The forums won't let me upload a .deb bigger than a meg, so here's a link for you:

[http://dl.getdropbox.com/u/131441/banshee_1.5.1-1_i386.deb](http://dl.getdropbox.com/u/131441/banshee_1.5.1-1_i386.deb)

Good luck!

---

### Post by svD on 2009-08-24
At first a big thank you! That's much more work than I assumed.
But unfortunately the .deb-file doesn't work for me (my architecture is amd64). I forced to install it, but this ****** up my whole banshee installation ^^
I think i had to wait for a plugin or similar for this feature.

again thanks for efforts

---

### Post by Onion Avenger on 2009-08-24
> **svD said:**
> But unfortunately the .deb-file doesn't work for me (my architecture is amd64). I forced to install it, but this ****** up my whole banshee installation ^^
I think i had to wait for a plugin or similar for this feature.

Sorry that messed up your banshee installation.  Did you fix it?  

It's not a big deal for me, I can find an amd64 system in the next couple of days to compile on and get you an amd64 version.  The discussion on the patch on Banshee's site seems to have stalled.  I dunno if they'll ever implement it.  In the meantime, I suggest trying out audacious.  It's similar to Winamp (classic version) and you can configure pause/resume notifications in the Audacious OSD plugin, although it uses its own notification system, not the new Ubuntu one.

---

### Post by svD on 2009-08-24
Yeah, i fixed it, no problem.

A amd64-deb would be cool, but don't go after it to hard...
I haven't tried Audacious until now, but when it's similar to Winamp... i don't give a try ;)
I'll stick to banshee - for very big and sorted archives it's much better.
regards from germany

---

### Post by joey-elijah on 2009-08-24
Rhythmbox uses notify-OSD, btw.

---

### Post by Onion Avenger on 2009-08-25
> **joey-elijah said:**
> Rhythmbox uses notify-OSD, btw.

Yeah, it does, but it doesn't use it when you pause or resume the player.  Neither does Banshee.  I'm used to Amarok (classic) and Audacious doing this and wish Banshee (and other players) had this support.  Please let us know if you find any players that fit this description!

> **svD said:**
> A amd64-deb would be cool, but don't go after it to hard...

Not a problem.  Here it is:
[http://dl.getdropbox.com/u/131441/banshee_1.5.1-1_amd64.deb](http://dl.getdropbox.com/u/131441/banshee_1.5.1-1_amd64.deb)

---

### Post by pixelot on 2009-10-13
Thanks so much for making the .deb! I'm just switching to Banshee from Audacious, and this is just what I need. :guitar:

---

### Post by svD on 2009-10-13
Yeah, also THANK YOU for the .deb-file!
I think I hadn't recognized it when you posted it, but now (because of pixelot's post) I do.
I've just installed it and it works! Also with "paused/resumed" shown up... very nice!
It would be nice to see this in the official release, but I think you already gave a try for this.

---

### Post by JCoster on 2010-02-01
Sorry to resurrect an old thread but for those of you with Amarok looking to integrate it with NotifyOSD, I've written a script.

All information relating to the script can be found at my website:
[http://www.blue-shift.net](http://www.blue-shift.net)

Don't worry- there's no advertising and it's all devoted to the script development.

If you have any questions regarding it though then PM me or contact me on this thread.

It's tested under Karmic with Amarok 2.2.0.

Cheers,
JC

---

