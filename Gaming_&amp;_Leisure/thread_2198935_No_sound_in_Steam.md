---
title: "No sound in Steam"
date: 2014-01-11
forum: Gaming &amp; Leisure
---

### Post by Kymus on 2014-01-11
I recently noticed that none of my games in Steam are getting any sound. This is an issue in both the Linux client as well as WINE (1.7.10). 

I've tested sound elsewhere (youtube, XBMC, VLC) and it works perfectly fine. I tried contacting Steam and all they told me was that they don't offer support for 3rd party games (uh.. it's a game-neutral issue).

I'm running Ubuntu 13.10.

---

### Post by dannyboy79 on 2014-01-11
can you launch steam from the terminal and then copy and paste all the output at pastebin and then post that link here so we can see

---

### Post by Kymus on 2014-01-11
Certainly. Should I include output for both clients (Linux and WINE)?

---

### Post by Kymus on 2014-01-11
I've added two pastes:

[Running Steam (Linux)]("http://pastebin.com/QFTLgZHH")

[Running a game]("http://pastebin.com/mXNeVnuw")
(there's some overlap since I wasn't entirely certain as to when the game was initialized)

I experimented and found that within the steam client itself, there is sound (video from games in the store get audio fine), but still, no sound in-game.

I didn't post the output for WINE since I get the error "wine: cannot find L"C:\\windows\\system32\\steam.exe".

---

### Post by Kymus on 2014-01-15
bump.

---

### Post by dannyboy79 on 2014-01-15
ok, so you're getting sound within steam?, next i'll need you to launch a game and watch the output in the terminal so we can see why there's no sound from your steam games.

---

### Post by Kymus on 2014-01-15
> **dannyboy79 said:**
> ok, so you're getting sound within steam?, next i'll need you to launch a game and watch the output in the terminal so we can see why there's no sound from your steam games.

Didn't I do that with [this paste]("http://pastebin.com/mXNeVnuw")? Or do you mean run the game direct from the terminal as apposed to through the steam UI?

---

### Post by dannyboy79 on 2014-01-16
> **Kymus said:**
> Didn't I do that with [this paste]("http://pastebin.com/mXNeVnuw")? Or do you mean run the game direct from the terminal as apposed to through the steam UI?looking at the terminal steam output, i don't see any game being launched. did you try to launch a game?

---

### Post by Kymus on 2014-01-16
I did it in a round-about way. That may be why. Instead of launching a game direct from the terminal, I launched steam from the terminal, and then launched a game through the Steam UI. There's likely some overlap in my paste. 

Anyway, if it would be easier, I can launch something from the terminal directly, but I will need a little assistance. I know (*think* I know..) the command is 

> **$**wine steam/(some path here)/(game ID)

I know how to get the game ID, but I'm not certain on the path.

When I try to do ***$**wine steam* I get the error "*wine: cannot find L"C:\\windows\\system32\\steam.exe"*". AFAIK, it's not installed anywhere funny.

---

### Post by dannyboy79 on 2014-01-16
i don't use wine so i can't help with that. i'll attempt to help with linux steam. what game don't you have sound in? have you checked pulseaudio control to ensure the game audio channel is turned up?

---

### Post by Kymus on 2014-01-16
Sorry Danny, at some point I got confused and threw WINE in there even though that wasn't in my original paste >_<.

I installed pavucontrol  and checked the pulseaudio settings. System volume was set to 0, so I set it to 100% and then there wan an extra output device listed which I disabled (I'm just using 1 HDMI input)

I ran a few games and everything seems to be good now, thank!

---

