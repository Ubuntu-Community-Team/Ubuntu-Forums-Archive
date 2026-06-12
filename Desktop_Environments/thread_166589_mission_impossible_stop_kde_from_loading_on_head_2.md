---
title: "mission impossible? stop kde from loading on head 2"
date: 2006-04-26
forum: Desktop Environments
---

### Post by pelle.k on 2006-04-26
I can't for the life of me (i've been trying to accomplish this for a few nights by now) stop kde from loading on the second head (:0.1 wich is my tv-out that is).
Soon i'm going to put KDE where it doesn't belong if can't resolve this matter somehow. It's driving me nuts, really.
There seems to be zero/null information, i've been trying all thinkable combinations of keywords on google during a couple of hours now.

This is a dual-head config, no xinerama (doesn't fit my need), no tvinview (same here), newest nvidia drivers. KDE starts up two sessions. startkde have no apparent "--options". gnome-session does, and almost any half decent wm om this earth has but not startkde.
I want my tv-out to load ONLY xorg then freevo, or maybe twm then freevo, but what second wm to chose is not the issue. But KDE is, so here it goes:

How the **** do I stop KDE from loading on my second head?
Sorry bout the * but it fits my mood right now, wondering why something so easy must be so freakin hard...

---

### Post by Ensnared on 2006-04-27
I'd like to know this too. I have the exact same setup, and want to specify my media-player as being the "Window Manager" for the second display and not have KDE running on it (which should be possible by specifying that the media-player should be the last program to start if using the traditional .xinitrc/.Xclients-scripts).

I'd never heard of Freevo before reading this post though, and I've been using oxine for this purpose instead, but oxine's interface is extremely slow and choppy (it's only version 0.5 though, so not quite done yet). After trying out Freevo I've decided to switch, I just gotta figure out how to make it recognise playlists for video-files, but that's a topic for another thread ;)

I'm searching for a possible solution to this right now, but so far it unfortunately does not look promising. If I do find anything I'll post about it here.

---

### Post by pelle.k on 2006-04-27
How nice it is to know someone else feels the same way about this :)
So far i've been browsing in certain scripts and config files from kdm launching to kde starting up. I >think< either ksmserver, kcminit or kinit is responsible for this naughty behaviour, and i've also found out the enviroment variable KDE_MULTIHEAD=true is set. I have tried several attempts to setting this variable in vareity of config files, but it always resets to true after i've set it to false (when i start kde of course) :(

Babysteps, i guess. It still makes me kind of mad there's zero documentation on this matter.

---

### Post by Ensnared on 2006-04-27
I just posted to the main KDE mailing-list asking for help. If that doesn't get us an answer, I fear nothing will ;)

---

### Post by Ensnared on 2006-04-30
I've always used GDM as my display manager, but last night I decided to try KDM instead (for the first time in years). When I logged in, KDE only started on my primary screen, and my secondary screen was just the boring default black/white-speckled background for X, and my mouse-pointer (which could still move between them like usual) was the default X-pointer. Checking the process-list, I confirmed that KDE was indeed only running one instance.

So maybe that's all it took - and apparently, this is controlled by the display manager rather than KDE itself (I did not know that), which means it should indeed be doable to set it up to run a different WM on the second head. I have yet to figure out how though, but it's some progress atleast :)

Still no response on the KDE mailing list though, but I suppose these things may take time - devs are busy making KDE 4 I guess (and hope) ;)

---

### Post by morikaweb on 2006-09-23
Well if anyone figures this one out please fill me in. I'd love to know how to  set my own wm on the second head.

---

### Post by pelle.k on 2006-09-23
wow! this is an old thread :)
But anyway, i haven't tried this in a long time. I never got it to work though. Also it would be nice if i could do the same to gnome...

---

