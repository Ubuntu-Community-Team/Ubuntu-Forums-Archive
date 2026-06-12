---
title: "Loading str subtitles with mplayer"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-08
I can't load succesfully str subtitles for a movie with mplayer

I open the mplayer, then the movie and then I do:

right click -> open -> load subtitle

The movie continue to play but the subtitles are not loaded

What I'm doing wrong?

---

### Post by Tsukasa on 2006-07-08
Try the commandline version and do something like:
$ mplayer myfile.avi -sub mysub.srt

By default you can cycle through the available subtitles by pressing "j".
Gmplayer doesn't really play nice for me either but this way it works :) .

---

### Post by Dearhell on 2006-07-09
You are right, in that way it works fine, thx

---

### Post by john_markh on 2006-07-17
It also worked for me... but why it doesn't work with gmplayer ?
](*,)

---

### Post by john_markh on 2006-07-17
I did it!
:-D 
All I had to do is to change subtitles encoding to "None" (it was "Unicode" on my machine as default).

---

### Post by revoltism on 2007-03-04
in my case in works... only problem is when i want to use arabic subtile it shows jidderish.. i guess it is only to change the encoding to unicode or something but then it says "Can't load subtitles" and no subtitle shows only the movie plays.

---

