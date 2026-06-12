---
title: "How do I install sound in FreeCiv 2?"
date: 2005-05-05
forum: Gaming &amp; Leisure
---

### Post by mostwanted on 2005-05-05
a backport.

I get this message > simon@ubuntu:~ $ civclient
1: Kunne ikke finde lydopsætning i filen "stdsounds".
1: For at få lyd skal du installere en lydopsætning.
1: Lydopsætning kan hentes hjem fra <ftp://ftp.freeciv.org/freeciv/contrib/sounds/sets>. 

Which means "Couldn't find sound setup, to get sound you need a sound setup, download sound setup from <ftp://ftp.freeciv.org/freeciv/contrib/sounds/sets>".

So I go there, and download an archive, but where do I extract it to?

---

### Post by Equanimity on 2005-05-06
FreeCiv 2.0.0 is located at **/usr/share/games/freeciv/** 

The "stdsounds" directory is placed in this folder, alongwith the soundspec file. However, it appears that /dev/sequencer is needed for the sounds to play correctly, and that device doesn't exist on my machine. I havn't investigated a solution for this issue yet (it may be as simple as a symlink).

---

### Post by Keith_Beef on 2006-05-23
I'm having problems with this, too...

```
$ civclient -v
Freeciv version 2.0.2 gui-gtk-2.0
$ civclient -t trident
Audio File Library: 'data/stdsounds/foot3.ogg': unrecognized audio file format [error 0]
1: Error while caching sample <-1>: confirm value != samples[].id

Audio File Library: 'data/stdsounds/woodbrk.ogg': unrecognized audio file format [error 0]
Audio File Library: 'data/stdsounds/wall01.ogg': unrecognized audio file format [error 0]
1: last message repeated 2 times
Audio File Library: 'data/stdsounds/metbrk.ogg': unrecognized audio file format [error 0]
```

So civclient is finding the soundset, but can't play it.

I tried linking the existing sequencer like this:

```
# ln -s /dev/.static/dev/sequencer /dev/sequencer
```

but that didn't cure the problem...

Using Totem or Beep, I can play OGG files that I have ripped from my CD collection.

Beef.

---

### Post by Snowball on 2008-07-12
I am having the same problem.

I managed to get sounds in freeciv in Ubuntu 6.? (the previous version). But today I upgraded to 7.04 and now it doesn't work anymore.

---

### Post by NovruzeliH on 2008-07-12
so u guys downloaded the soruce code huh ??? well do u try it with wine or not yet ?

---

### Post by Snowball on 2008-07-12
I am not that much experienced that I know what 'wine' is. I saw it a couple of times though. I will figure that out.
By the way: here is my shell output:

1: Error calling Mix_OpenAudio
1: Plugin sdl found but can't be initialized.
2: No real audio subsystem managed to initialize!
2: Perhaps there is some misconfiguration or bad permissions
2: Proceeding with sound support disabled

---

### Post by NovruzeliH on 2008-07-12
well there is something really messed up there, wherever u installed the game, try downloading the sound files and putting it into the folder "/usr/share/games/freeciv/ " just like Equanimity said :p give it a try, if not, try downloading and installing wine, then download the windows version of the game , and install it with wine, if that wont help then i dont know whats wrong 
sorry

---

### Post by Snowball on 2008-07-12
So 'wine' can execute windows program under Ubuntu. That would be nice for a lot of things, so I may be trying that soon.

But my problem is that Freeciv worked, truely in Ubunty, in my previous version. I looked it up and I am further than I thought I was. I upgraded to 8.04 today (Hardy Heron). I came from Gutsy Gibbon. Before my upgrade, everything was OK. Now I have no sound in freeciv.

Does anybody know how I can fix this?

---

### Post by Snowball on 2008-07-12
I spent some investigating as well. My sound settings are all OK. I managed to get sound now in Hardy Heron too.

In my folder /usr/share/games/freeciv I have a folder made named 'stdsounds' and it contains the following files:

foot3.ogg   LrgExpl.ogg  MgBar1.ogg   Mortar.ogg   THover.ogg  woodbrk.ogg
inh2o.ogg   MedCan.ogg   MgBar2.ogg   SmlExpl.ogg  Tread.ogg
LrgCan.ogg  metbrk.ogg   MgHeavy.ogg  Splash.ogg   wall01.ogg

I downloaded these files as described on the standard website of freeciv.

My problem however was that I couldn't get sound anymore after I upgraded to Hardy Heron. It seems that 'Mix_OpenAudio' (which I think is some kind of program that is used by several other programs) can only work with one program at the time. I was playing music when I started freeciv, so the 'Mix_OpenAudio' was 'occupied'. If I start freeciv without any music playing, everything is allright and I do get sounds when playing. However, if I start some music player (rhythmbox) and try to get music after having started freeciv, then the music player doesn't give me sound.

So the situation is far from perfect, but I do have sounds in my freeciv now.

---

### Post by NovruzeliH on 2008-07-12
hmm try making ur sound trhorugh ALAS i guess if that dont work, then im not sure man, and yeah i dont use Ubuntu 8.04 i use xubuntu 8.04 :P

---

### Post by Snowball on 2008-07-13
That would be too much for me. If one doesn't even know what 'wine' is (let alone have it working on my computer) it certainly is not a good idea to change the way programs work with sounds...

But thanks anyway. I hope future Ubuntu releases will solve this problem.

---

### Post by NovruzeliH on 2008-07-13
well Snowball there is one way you can play in, by installing virtual box, and then installing xp or any other windows on it, just put the space like 20 GB, and install few games that you need and start playing it :p

---

### Post by Snowball on 2008-07-17
Thanks again. I really appreciate all your suggestions. But as a Ubuntu-user, it somehow feels like a defeat to be forced to use Windows for these kind of problems. Even if it's within Ubuntu. It just shouldn't be that way. It's not a copyright thing that we're dealing with here. Why is it suddenly not possible anymore to use two sound-producing programs at the same time? Makes me wanna go back to my old version. And that should not be the case with new versions.

By the way, I used XMMS before. But that is now not available anymore. Very curious... Maybe I will switch back to the older version.

---

