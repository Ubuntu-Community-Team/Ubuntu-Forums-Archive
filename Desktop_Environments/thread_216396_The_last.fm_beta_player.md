---
title: "The last.fm beta player"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Third Thoughts on 2006-07-15
Has any body on Dapper tried compiling and running the new beta player for last.fm. You can get the source by running
```

svn co svn://svn.audioscrobbler.net/LastFM_client/trunk/

```

If you've got svn installed. If not then install it from the repos. I followed the instructions that were in the readme. I already had Qt 4.1* installed so I...
```

cd ~/trunk/src
qmake
make

```

I got this error while compiling
```

/usr/bin/ld: cannot find -lLastFMTools
collect2: ld returned 1 exit status
make: *** [../bin/LastFM_debug] Error 1

```

I tried looking for answers on the last.fm forums, but there's no search function so finding anything on those forums is a matter of pure chance. Thought I'd post here and see if anyone else had run across the same problem.

~Andrew S.

---

### Post by Colonel Kilkenny on 2006-07-15
I tried to compile also, just out of curiosity. But I ran into same problem...  
I'm not expert but does that mean that it can't find library LastFMTools or something like that?
And that error comes in last stage of compiling, I think. Or at least it is dealing with those .o-files.. As I said, I'm not expert. Hopefully somebody (or official developers) will soon get it ready to download for linux also..

---

### Post by Third Thoughts on 2006-07-15
If you ran into the same problems its probably a Dapper wide issue. I was hoping that maybe I just had something tweaked weird on my system. I know that alot of Gentoo folks have been using it, but don't know about Ubunites, or even Debianites.

~Andrew S.

---

### Post by abbot on 2006-07-25
Good News.  They released a beta player for Linux available [HERE](http://www.last.fm/tools/downloads/).  All you have to do is double click the "lastfm" script in the downloaded directory and it will run.  I downloaded the QT4 stuff from the repositories, but I don't know if that's necessary.  It didn't make any menu entries for me or anything so I made my own.

---

### Post by jr.gotti on 2006-07-26
doesn't the last.fm player block your soundcard, making it unable to play local tracks, making it unable to "scrobble" your music, rendering last.fm useless?

...or is it just me?

[if this post confused you...say "I"]

---

### Post by gatiba on 2006-07-26
Me too... It crashes on trying to play tracks or streaming...

---

### Post by SishGupta on 2006-07-26
run qmake and make from /trunk/ not /trunk/src/.

also it doesnt seem like a good idea to run the precompiled binary. and it just flat out doesnt work anyway...so.yeah.

---

### Post by abbot on 2006-07-26
> also it doesnt seem like a good idea to run the precompiled binary. and it just flat out doesnt work anyway...so.yeah.

is that what that "lastfm" file in the downloaded folder is?  it works just fine for me.  even the tagging function which didn't work in the last local player.  i didn't do the whole qmake, make stuff.  if you double click the "lastfm" file in the downloaded directory it will open and just start working.  i just moved that whole folder to /usr/share/ and created my own application menu entry linking to that file.

the only problem is that firefox doesn't know to send that format to the last fm player if i click a radio link on the last fm webpage.  they used to have something in the faq that told you how to fix that because it was the same problem with the last version, but they neglected to put it back in the faq when they revamped the site recently and i've since re-installed my OS.  you can do that stuff from the player so this function isn't that necessary, but still.

---

### Post by ltmon on 2006-07-26
You also might want to get hold of the latest betas of Amarok (amarok.kde.org), or to compile Amarok from SVN source.

It has integrated last.fm capabilities which work quite well for me.

L.

---

### Post by ellion on 2006-08-03
hm, I have an even simplier question: Which package ships qmake for qt4? :/ for qt3 it is libqt3-dev-tools, but libqt4-dev-tools comes without any qmake :(

---

### Post by SishGupta on 2006-08-04
ellion: i just downloaded Qt4 from the website.

Also the last_fm binary loads, but doesnt play audio. it also doesnt work as well as the windows one did (obviously).

I tried several times to ./configure and make the lastfm source and that never worked.

I now use audacious with the last_fm plugin.

---

### Post by abbot on 2006-08-04
> **SishGupta said:**
> Also the last_fm binary loads, but doesnt play audio. it also doesnt work as well as the windows one did (obviously).


must be a fluke then because i'm listening to mine right now and i'm running it from the binary.

---

### Post by newagelink on 2006-08-04
> **abbot said:**
> All you have to do is double click the "lastfm" script in the downloaded directory and it will run.It loads -- I believe typing "./lastfm" does the same thing? -- but whenever it connects to a station, it immediately closes. Anyone else have this problem?

edit - I guess so: > **gatiba said:**
> Me too... It crashes on trying to play tracks or streaming...Also, has anyone tried [the Yamipod software]("http://www.yamipod.com/") they recommend?

---

### Post by linuxguiri on 2006-09-14
I can only get the [Last.fm 1.0.0 Beta player]("http://www.last.fm/tools/downloads/?showplatform=Linux") to work about every other time. 

Either the program opens and everything works fine, or it doesn't even open a window (though I can see a bin_LastFM and lastfm process running in my system monitor).

Anyone having the same problems? Find a solution?

EDIT: [This]("http://www.last.fm/forum/34905/_/137962/_/1671262") may have something to do with it: > someone commented earlier that killing the ESD processes gets the linux beta working and i can confirm that. it doesn't seem to recognize the soundcard with ESD running and can't engage Alsa.

---

### Post by linuxguiri on 2006-09-14
Yup, disabling ESD prior to running last.fm works. It just messes up sound for all my other applications. 

Anyone know why ESD and last.fm can't play well together?

---

### Post by gobbluth on 2006-09-19
> **newagelink said:**
> It loads -- I believe typing "./lastfm" does the same thing? -- but whenever it connects to a station, it immediately closes. Anyone else have this problem?

edit - I guess so: Also, has anyone tried [the Yamipod software]("http://www.yamipod.com/") they recommend?

I also have this problem, and I am running it straight from the binaries (Just typing ./lastfm after unzipping). When I tried to follow in the installation instructions in the readme, the command 'qmake' just output the --help explanation for qmake. Also, are you saying that amaroK integrates listening to last.fm custom stations, just like the player? If so, I may have to switch...

amaroK works fine with gnome right?

---

### Post by gamma on 2006-09-20
Ahh.. yep hopefully they fix the ESD issue..

---

### Post by puppy on 2006-09-21
Another vote for Amarok here - it has integrated LastFM functionality which works perfectly for me. Of course it also plays your music collection, shows album art, downloads your podcasts, makes your breakfast etc etc   :D

---

### Post by kline on 2006-09-21
> **puppy said:**
> Another vote for Amarok here - it has integrated LastFM functionality which works perfectly for me. Of course it also plays your music collection, shows album art, downloads your podcasts, makes your breakfast etc etc   :D

Can you clue me in on howto use last.fm with Amarok?  Of all the players, Amarok is my favorite, but I'm haing trouble with selecting external music sites.  Thanks!

---

### Post by linuxguiri on 2006-09-26
> **gamma said:**
> Ahh.. yep hopefully they fix the ESD issue..

is there a way to add a command to kill all esd processes in the launcher for the last.fm player? (so i don't have to manually kill the processes first and then run the last.fm player afterward.)

---

### Post by valke on 2007-01-13
ok so here is a question, will amarok work in gnome? sorry if this is supposed to be in another thread...

---

