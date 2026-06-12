---
title: "DarkPhear : classic Phantasy Star-like RPG"
date: 2009-08-07
forum: Gaming &amp; Leisure
---

### Post by landeel on 2009-08-07
[[IMG]http://img40.imageshack.us/img40/9933/darkphearscreen1.th.jpg[/IMG]](http://img40.imageshack.us/i/darkphearscreen1.jpg/)[[IMG]http://img212.imageshack.us/img212/8873/darkphearscreen2.th.jpg[/IMG]](http://img212.imageshack.us/i/darkphearscreen2.jpg/)[[IMG]http://img40.imageshack.us/img40/324/darkphearscreen3.th.jpg[/IMG]](http://img40.imageshack.us/i/darkphearscreen3.jpg/)

DarkPhear is an old-school style RPG, programmed by me.

It was originally released for DOS, back in 2001. Thanks to [FreeBASIC]("http://www.freebasic.net"), it's now ported to Linux and Windows.

The game is freeware, and the code is released under the GPL.

It's available for download [here]("http://www.darkphear.com").

---

### Post by Grishka on 2009-08-07
cool. about inclusion in Ubuntu repos: the whole process is awfully bureaucratic, and it will probably take some time before all formalities are done. look [here](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages). you're, however, advised to request inclusion of your package in Debian. this way it'll eventually appear in Ubuntu as well. look [here](https://wiki.ubuntu.com/Debian/ForUbuntuDevelopers?action=show&redirect=ContributingToDebian).

edit: ah, I've read the license now. I'm afraid it's incompatible with Debian licensing policy, so it's a no-no. the engine's GPL is ok, but the media license will not be accepted by Debian. you may be able to include it in Ubuntu's multiverse repo, though I don't think it's likely. maybe contact [getdeb](http://www.getdeb.net/) guys, they're lax with licensing.

---

### Post by rCXer on 2009-08-07
Thanks I'll have to try it soon :popcorn:

---

### Post by landeel on 2009-08-09
I could change the license of my media. But I have lost contact with the guy who wrote the music, and I can't talk for him. Well, I will try it on getdeb.net.

Just made a .deb package.

---

### Post by farrell2k on 2009-08-09
Really Nice!  Who did the artwork?

---

### Post by Hire on 2009-08-10
Wow, fantastic, I will try it now!


Nah, I am kidding.

---

### Post by hetx on 2009-08-10
I don't get the joke.

---

### Post by landeel on 2009-08-10
> Really Nice! Who did the artwork?

Me, ten years ago! :guitar:

---

### Post by rCXer on 2009-08-12
I just installed it using the deb and I like the music. You might want to have the installer create a shortcut on the Applications/Games menu (with a cool icon of course :popcorn:)

---

### Post by landeel on 2009-08-12
It does create a menu shortcut for me (/usr/share/applnk/Games/RPG/DarkPhear.desktop). But I'm using KDE (Kubuntu).
How can I make it work with Gnome?

---

### Post by rCXer on 2009-08-12
I see what you're saying. Have it create a file called "/usr/share/applications/DarkPhear.desktop" with this in it:

```

[Desktop Entry]
Name = DarkPhear
Comment = DarkPhear
Exec = darkphear
Icon = /usr/share/darkphear/darkphear-icon.png
Terminal = false
Type = Application
Categories = Application;Game;

```

This is what It looks like:

---

### Post by wingnux on 2009-08-12
Sound doesn't work on OSSv4.

---

### Post by landeel on 2009-08-12
> Sound doesn't work on OSSv4.

DarkPhear uses SDL_mixer for sound. Try replacing the SDL libs in /usr/share/darkphear/lib32/ for a version that works for you.
If you already have 32-bit libSDL and libSDL_mixer installed, you can just remove this directory, and the game will use the ones from your system.
Please tell me if it works.

@rCXer : Thanks! It will be on the next release.

---

### Post by oldrocker99 on 2009-08-13
I've never played a console-type RPG, but this is a nice bit o' fun. Thanks!!

:guitar:

---

### Post by landeel on 2009-09-15
DarkPhear is updated.

-Improved scaler speed
-Animations should play more smoothly now
-Added some savegame sanity check
-Added automatic savegame backups
-Fixed the .DEB (debian) package file permissions
-Fixed the .DEB (debian) package shortcut creation

Game should be fully playable now.

The download link is in the first post.

[edit] Just spotted (and fixed) a couple of regressions. Uploading a new update. [/edit]

---

### Post by mister_playboy on 2009-09-19
Looks cool... I'll check it out. :)

---

### Post by imag1narynumber on 2010-01-12
I just tried to run it for the first time, and it crashes rather than starts.  Thoughts?

---

### Post by rCXer on 2010-01-12
Open a terminal and enter...
```
darkphear
```
...and post the results.  If something's wrong, an error is usually printed.

---

### Post by boriskarloffinablender on 2010-01-13
this doesn't even look as good as ps1 :(

---

### Post by landeel on 2010-01-19
> I just tried to run it for the first time, and it crashes rather than starts. Thoughts?

It seems the included libSDL.so will segfault with Ubuntu karmic. Also, even if you remove it, the game will look for libSDL.so and not for libSDL-1.2.so. I'll fix it in the next update. But for now replace the libSDL.so file with one that works for you. Attention: it must be the 32-bit version.

> this doesn't even look as good as ps1 :(

Of course it doesn't. Ps1 was Sega's greatest project at the time. Sega have invested hiring many many developers, musicians, playtesters and artists in the process of developing ps1. And then it sold many thousands of copies, making Sega even more rich. If ps1 was a movie, it could be compared to a hollywood superproduction. :popcorn:

DarkPhear was developed mostly by one teenager guy in his garage. And it was released for free. It could be compared to a well-succeded homemade short-film.
But well, I'm honored just to get a comparison. :D

---

### Post by landeel on 2010-02-10
Version 1.1.5 is out.

Bugs fixed:

-A couple of maps would not load on case sensitive filesystems. Many thanks to Michael Fridkin for spotting the bug and helping me fix it.

-Game would segfault on Ubuntu Karmic (due to SDL). I still need testers.

---

### Post by landeel on 2010-09-11
Version 1.1.6 is out

· a few bugs fixed
· improved stability
· improved libSDL and libSDL_mixer detection
· added Scale2X and Eagle pixel scalers

---

### Post by landeel on 2011-01-19
DarkPhear version 1.1.8 released
- Restored original MIDI music. OGG music is now optional, distributed as a separate music pack.
- Fixed a bug related to wine compatibility and write access.
- A few small fixes.

---

### Post by landeel on 2011-01-19
DarkPhear version 1.1.8 released
- Restored original MIDI music. OGG music is now optional, distributed as a separate music pack.
- Fixed a bug related to wine compatibility and write access.
- A few small fixes.

---

