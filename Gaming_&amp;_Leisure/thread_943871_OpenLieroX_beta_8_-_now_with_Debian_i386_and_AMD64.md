---
title: "OpenLieroX beta 8 - now with Debian i386 and AMD64 release"
date: 2008-10-10
forum: Gaming &amp; Leisure
---

### Post by albertz on 2008-10-10
Hi,

We just made a new release: OpenLieroX 0.58 beta9

I don't know if you have heard of the game, it's basically a Liero clone (Liero is kind of realtime Worms), based on Liero Extreme.

If you know of OpenLieroX, the 0.58 branch has many new features and is a major new version.

Most important updates of 0.58:

- Hide & Seek, Capture The Flag, Race / Team Race gamemodes
- infinite maps
- game size factor (you can make everything bigger or smaller)
- possibility to disable minimap
- support for Commander Keen 1-3 levels
- air jumping as an optional feature
- worm speed/damage/shield/friction factor and projectile friction factor
- ingame console can be used everywhere, also in menu and is much more advanced, many new commands, better autocompletion
- IRC support (for global chatting)
- new game options dialog
- dedicated server becomes useable
- improved connect-during-game
- more stable network (CChannel3)
- hit/damage yourself/teammembers can be enabled/disabled (aka friendly fire on/off)
- and, as usual, many further fixes which I don't want to list here
More details: [http://www.openlierox.net/forum/index.php/topic,12642.0.html](http://www.openlierox.net/forum/index.php/topic,12642.0.html)


Most important updates of 0.57 beta6-8: (since Beta5)
- Game-speed multiplicator
- connect during game support
- Force random weapon selection (with the extensions to have the same weapon for all players)
- Show player online/chatting/away status
- Chatbox has HTML and copy&paste support
- better synchronisation for shooting, that should also fix the self-shooting problem
- Auto-completion for chat commands
- Options editable from everywhere in the game
- Notify application window on events when application is in background

Please look at our homepage for more details:
[http://openlierox.net/](http://openlierox.net/)

We have again a Debian/Ubuntu package for you, this time for both i386 and AMD64. It would be nice to get some response from you about these packages.

Beside the Debian packages, we have the source tarball, a Win32 package and a MacOSX package. We also provide a Gentoo ebuild.

All the downloads are here:
[http://openlierox.net/downloads/](http://openlierox.net/downloads/)

As an addition, if you have any problems with that 0.58 beta version, there is also a more stable update to 0.57. Look at the [homepage]("http://openlierox.net") for more information.

Greetings,
Albert

---

### Post by Perfect Storm on 2008-10-11
Nice, going to try.
I'll see if it's something the kids wanna play.

---

### Post by GlaciesHun on 2009-05-26
Its a very good game, I've played it since 2007. But the new versions get slower and slower. Can you make it more optimized? I've got a laptop with 2.13 Ghz CPU, but the FPS is about 10-15 (maybe another physical engine?).

But its still a great game, I suggest everybody to try it.

---

### Post by albertz on 2009-05-26
> **GlaciesHun said:**
> Its a very good game, I've played it since 2007. But the new versions get slower and slower. Can you make it more optimized? I've got a laptop with 2.13 Ghz CPU, but the FPS is about 10-15 (maybe another physical engine?).

But its still a great game, I suggest everybody to try it.

That is indeed very low. I have 2.16GHz but I can have up to 160 FPS (in beta8).

What GFX settings are you using? With OpenGL or without? 32/24/16 bits per pixel? Fullscreen or not? Esp. fullscreen can increase the FPS a lot.

Are you using Compiz (graphics effects on desktop)? I have seen cases where OLX was incredibly slow with Compiz; but I am not sure if this is the fault of OLX. Try perhaps disabling Compiz and see how fast it is then.

---

### Post by GlaciesHun on 2009-05-26
Oh. thank you very much.
I didn't try fullscreen, and OpenGL rendering, because I've got bad experiences in 8.10. Neither worked correctly (Intel driver problem).

Now its OK (with, and without compiz, and with all color depths) - Thank you for the help. You've made a very good game.

---

### Post by albertz on 2009-05-26
Good to know that it works ok with OpenGL for you.

Perhaps I will just activate OpenGL by default in the next release. (OLX anyway fallsback to non-OpenGL if it detects any problems.)

Is here anyone who can tell me what in general what would be the best option for an Ubuntu system? On my other Linux system, I don't see much differences in performance with and without OpenGL, and some users reported that it's faster for them without OpenGL.

Probably not everybody will try so far in the game to try enable/disable OpenGL when the performance is bad - so we could loose some users because of this which is a bid sad.

---

### Post by GlaciesHun on 2009-05-27
I saw that OLX works better with OpenGL in Ubuntu, and Xubuntu (I didn't try in other distributions), but in windows, its faster without OpenGL: on my laptop the game shows 200-300 FPS.

Why don't you make a first-run test to the game, which select the better option when the user starts the game first time? I've seen it in some (bigger) games.

---

### Post by albertz on 2009-10-11
Heya,

Just want to note you about the new major 0.58 version. It took over a year to make this new version and finally, it's there. Still beta (whereby 0.57 was most of the time also only beta) but I think it's already very promising and as far as I know works for most people (in most cases even better than any earlier version).

Though, if there are any problems, we also made a small stability update to 0.57.

Here the changelog of 0.58:

- Hide & Seek, Capture The Flag, Race / Team Race gamemodes
- infinite maps
- game size factor (you can make everything bigger or smaller)
- possibility to disable minimap
- support for Commander Keen 1-3 levels
- air jumping as an optional feature
- worm speed/damage/shield/friction factor and projectile friction factor
- ingame console can be used everywhere, also in menu and is much more advanced, many new commands, better autocompletion
- IRC support (for global chatting)
- background music by Corentin Larsen
- new game options dialog
- dedicated server becomes useable
- improved connect-during-game
- more stable network (CChannel3)
- hit/damage yourself/teammembers can be enabled/disabled (aka friendly fire on/off)
- and, as usual, many further fixes which I don't want to list here
More details: [http://www.openlierox.net/forum/inde...c,12642.0.html](http://www.openlierox.net/forum/inde...c,12642.0.html)

As usual, there are packages for Debian/Ubuntu i386 and amd64, MacOSX, Windows, the source package and a Gentoo ebuild. All packages:

[https://sourceforge.net/projects/openlierox/files/openlierox/OpenLieroX%200.58%20beta4/](https://sourceforge.net/projects/openlierox/files/openlierox/OpenLieroX%200.58%20beta4/)

Would be nice to get some report if that works for you. Thanks for testing already in advance!

Edit: Btw., is there a way to rename this thread? Or would it make more sense to create a new thread for a new release?

---

### Post by albertz on 2009-10-30
And some more releases. :) We released beta5, beta6, beta7 and yesterday, beta8.

Mostly smaller fixes. Here a short changelog:

0.58 beta5

This took some more work, I worked almost non-stop 5 days on that for the initial support. The outcome is Google Breakpad support. Most probably, you wont notice that at all. :) And even if there would be something to notice (like at least some message or so), I hope that you still will not notice it.

Google Breakpad is a very advanced crash reporting system. It's the same that is also used by Firefox. Though, the inclusion in OLX the way we did it made it even more complicated than it is in Firefox. Anyway, I hope it works on most systems and if not, you can easily disable it.

So for all people who had any crashes, please try out 0.58 beta5. Even if it still does not work for you, it will greatly help us in fixing the problems.

Despite the Breakpad support, some smaller fixes (default setting for iLives was wrong, CTF will drop the flag if a flagholder disconnects, ...).

0.58 beta6

- Some problems with the new crash reporter were fixed (only related to the actuall reporting).
- Colorised damage pop-ups crash was fixed.
- If game is hanging in some unusual situation, please don't quit it and leave it running for 1 minute. It will quit automatically then and the crashhandler will collect usefull debugging information for us to fix that problem.
- Some weird negative scores right at gamestart should be fixed.

0.58 beta7

* Fixed some more cases when "strange problems with auxlib" error occured.
* CrashHandler improvements. Also restarts OLX now in case of a crash.
* Filehandling fixes. IRC, this should also fix your problem.
* Fixed when Http client (used for newspage & serverregistering) blocks whole OLX.
* Hopefully fixed all crashes in player profiles.

0.58 beta8

- Fixed strange ceiling friction.
- New option: Network.ForceMinVersion: forces minimum version ingame
- New option: Network.ForceCompatibleConnect: if client is too old, i.e. not compatible (or ForceMinVersion is set), client even cannot connect at all
- Automatically download map when you connect to server ingame or when server starts game and you don't have the map.
- Some crash fixes.
- More crashhandler fixes (again only under the hood, i.e. the difference is only for us, not for you).

---

### Post by Garyu on 2009-11-01
OMG, we had so many laughs with Liero and the other one that's almost exactly the same but can't remember its name now... EDIT: Molez!

Sitting 3 guys at the same keyboard blasting eachother is some of the best fun I've had...ever. :D

Will definitely take a look at this when I get a few moments to spare.

---

### Post by albertz on 2009-11-01
3 guys at the same keyboard? :o

But two guys on the same keyboard is possible in OLX. :)

And/or playing over network of course.

---

### Post by DrMelon on 2009-11-01
Wow, it's pretty cool to load some of the old Commander Keen levels and then blow my friends to bits on them. Lends a very interesting angle to the nostalgia!

---

### Post by albertz on 2009-11-01
I even got the idea to go a bit further with the Commander Keen support in OLX. :)

Like, to play through the whole Commander Keen 1 - 3 games but Liero-style. :P We would have to add some possibilities to OLX (like doors & items (keys)) ...

Commander Keen 1 files are free to download/redistribute, for CK2+CK3 you need to pay. ( [http://www.3drealms.com/keen1/index.html](http://www.3drealms.com/keen1/index.html) )

---

### Post by albertz on 2009-11-27
A new release: 0.58 beta9

- WormGroundFriction feature
- merge duplicate servers in serverlist
- fixed possible crash at quit
- better performance for DNS resolving
- better performance for textboxes
- fixed upload speed test
- fixed possible crash when downloading map in game
- fixed crash when trying to select weapons in lobby
- save config also in case that OLX crashes at exit
- fixed clicking on buttons (for example when you click start in hostlobby and it quits)
- removing music (many crashes related to that)
- loads LX56-style options.cfg config file
- fixed possible crashed under Unix/Linux with X11
- small physics fix where you gluing too much on ceiling
- fixed shooting in race gamemode
- and many more smaller fixes

---

