---
title: "Installed Warzone 2100, receiving error on run"
date: 2006-06-17
forum: Gaming &amp; Leisure
---

### Post by eqisow on 2006-06-17
I just installed Warzone 2100 0.2.2 via the .run file. When I attempt to run the game with 'warzone', I get the following error:

```
NETinitAudioCapture
./warzone.bin: symbol lookup error: ./warzone.bin: undefined symbol: alutLoadWAVMemory
```

Does anybody know what that might be about? Thanks in advance. :)

---

### Post by Schalken on 2006-07-07
I have this problem as well, only in Ubuntu (6.06). Much like this guy: [http://www.forumplanet.com/strategyplanet/warzone2100/topic.asp?fid=5995&tid=1907381](http://www.forumplanet.com/strategyplanet/warzone2100/topic.asp?fid=5995&tid=1907381)

Just before it closes because of the error, you see the first frame of what looks like an intro video, just to annoy me. :( Looks like a good game.

Please I would like to know if anyone has and how to solve this problem.

I am using a geforce 6200 with 256mb vram btw.

---

### Post by Hairy_Palms on 2006-07-08
im running it fine,
try sudo apt-get install libalut0

---

### Post by eqisow on 2006-07-08
libalut0 is installed and the newest version. Still a no go on Warzone. I guess a might give the w32 version a try in Wine, though it will be a damn shame if the Windows version runs and the Linux version doesn't.

Btw, I'm on Dapper as well.

Edit: The game doesn't seem to work in WIne or Cedega either.

---

### Post by Schalken on 2006-07-12
BUMP

I think it's important we at least find the *cause* of the error, to determine whether or not the problem is fixable.

---

### Post by shugie on 2006-07-13
I also have the same problem. I installed libalut0 and still get the error. Is there another package where alutLoadWAVMemory would be, that we are missing?

---

### Post by Hairy_Palms on 2006-07-16
think i might have found what u need, try installing 
libopenal0
libopenal0a

---

### Post by viciouslime on 2006-07-18
Since so many people are having problms with this game, I have made some deb files. They are available on my site ([http://www.viciouslime.co.uk/]("http://www.viciouslime.co.uk/") under downloads/linux/games. You'll need both warzone2100 and warzone 2100 -data.

Please let me know if they work for you.

---

