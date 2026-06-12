---
title: "Live Radio Stream Problem Help"
date: 2009-02-24
forum: General Help
---

### Post by Hr_Birnbaum on 2009-02-24
I don't know if this has been discussed before, but I have been encountering streaming problems while trying to listen to live radio streams.  The stream always had interruptions after around 10 minutes.  I increased the cache, that didn't work, but then it hit me!  I switched from one of the pre-installed "graphic generated" screensavers to the "slide show" Cosmos screensaver, and now the problem seems to have been solved.  Just a small recommendation.

By the way, is there a possibility to import my Windows .m3u stream playlists to a Ubuntu/Linux player and my Firefox Windows bookmarks to Firefox Ubuntu/Linux?  Which simple yet efficient Ubuntu/Linux Media player would you recommend for Internet radio streaming?

p.s.  I am a complete amateur to computers in general, so please bear with me. :-)

---

### Post by Lunx on 2009-02-24
>  Which simple yet efficient Ubuntu/Linux Media player would you recommend for Internet radio streaming?

I stream my radio with Rythmbox and have no problem with Windows streams (.asx file) or Realplayer (.ram files). Simply popped the address of the stream in as a new radio station and then was advised it couldn't play the stream as it needed missing plugins. I let the app search for the missing gstreamer plugins, installed them and now have no problems.

I do have an issue with one ram stream however, asked a question [[COLOR="DarkOrchid"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1068388") a while back but received no answer as yet. Problem persists, but not sure whether it is a OS issue, or something about that stream in particular.

---

### Post by roccivic on 2009-02-24
I use MPlayer and a homemade script to listen to internet radio.
If you would like to try open terminal and type:

```
sudo apt-get install mplayer -y
```

Once installed type:

```
mplayer http://someradiostation.something:port/
```

for example:

```
mplayer http://radio.bigupradio.com:8005/
```

to import a playlist, just open it with gedit, copy the URL and paste in terminal as above.

Enjoy

---

