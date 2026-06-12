---
title: "Ubuntu (GNOME) sound theme not playing ?"
date: 2009-01-29
forum: General Help
---

### Post by Smjork on 2009-01-29
I can hear sounds. I can play all kinds of sounds in Amarok or any player.
I can hear the movie sounds in video files.
I can hear every event sound of the Ubuntu default (and only) sound theme
if I click on each of them.

But when I login/logout nothing happens and sounds never "sound" on events.

I do have some other user accounts made on the same computer. I made these accounts just for gaming/testing purposes.

Well, on those accounts the sound events are the same but I CAN HEAR them :-)

I don't know where to check for any differences ...

---

### Post by dcstar on 2009-01-29
> **Smjork said:**
> I can hear sounds. I can play all kinds of sounds in Amarok or any player.
I can hear the movie sounds in video files.
I can hear every event sound of the Ubuntu default (and only) sound theme
if I click on each of them.

But when I login/logout nothing happens and sounds never "sound" on events.

I do have some other user accounts made on the same computer. I made these accounts just for gaming/testing purposes.

Well, on those accounts the sound events are the same but I CAN HEAR them :-)

I don't know where to check for any differences ...

System-Preferences-Sound-Sounds-Play system sounds

---

### Post by Smjork on 2009-01-30
It seems I didn't make myself very clear:

The events/sounds ARE ENABLED.
I can hear the sounds if I press the small "play" button right to each and evry sound.
Sound is also working on music, movies, etc.

BUT EVEN IF I ENABLED SOUND EVENTS, THEY SIMPLY DON'T WORK.
I log on to my account and the "login" sound never plays (or at least I don't hear it)
I log out and the "logout" sound never plays (or at least I don't hear it)
And so on...

If I log onto a different account, having the exact same settings, they work. I hear all the sounds related to events.

So ...

---

### Post by Yellow Pasque on 2009-01-30
Is the GNOME Login sound enabled for that account (check System -> Preferences -> Session)?

Edit: I guess it could also be a permissions issue. Look in the /etc/group file to see if your non-working account has different permissions than the ones that work.

---

### Post by Pidgin on 2009-01-30
That's the same problem with me. I have never heard any sound effect except for logging in since I use Ubuntu.
[http://ubuntuforums.org/showthread.php?t=1042928]("http://ubuntuforums.org/showthread.php?t=1042928")

---

### Post by Smjork on 2009-02-14
The account that DOES NOT work is the MAIN account, the 1st account made on that machine, the one I currently use. It is like the "admin" account on that machine (of course, not "root" :-) ...)

The accounts that DO WORK are secondaty accounts, made just for testing purposes, but not very different than the main one. All of them run GNOME but use different themes. I use one for games so I disabled Compiz on it. The other one just has a Mac OS X theme on it.

So again... the problem is still open.

---

