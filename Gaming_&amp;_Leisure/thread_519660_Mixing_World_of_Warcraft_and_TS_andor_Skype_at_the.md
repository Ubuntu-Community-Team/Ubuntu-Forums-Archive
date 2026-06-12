---
title: "Mixing World of Warcraft and TS and/or Skype at the same time."
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Gunn3r on 2007-08-07
Greetings.
I've been using Ubuntu for 1 year (started with 6.06, use 7.04 atm), but I consider myself to be a total n00b regarding Linux.
I've tried to do a little research but to no avail.
My problem is this:

I play World of Warcraft (through WINE, of course) and I'd like to use Teamspeak and/or Skype to talk with my guild mates.

Here is what I tried so far:

1st - Wine is setup as default using OSS and WoW is running in opengl with only the wine /directory/wow folder/wow.exe. I start up TS or Skype and no sound on each of them.

2nd - I tried using "aoss wine (etc)" with WoW and the same with TS and Skype. It starts to lag WoW a LOT ! no chance of playing this way.

3rd - I thought about a bit and "let's try to put WoW using Alsa and TS using OSS and Skype using ALSA too".
      Wow runs fine, sound normal (with some normal quirks) and I fire up Skype... it works the phones !! but no mic sound. My girlfriend (who plays WoW with me) says that she can't hear a thing.
      I look at sound volume, mic volume, mic boost, try alsamixer from CLI and activate a lot of stuff that i think might be related. doesn't work. I can hear game and my girlfriend speaking thru skype, but I can't speak.
     Skype is properly configured using alsa.
Then i try the WoW(alsa) and TS(oss). Lots of lag. I can hear sound but with lots noise. one of my guildmates say my voice comes with a lot of echo. again, TS seems to be properly configured.


So, Skype and Wow using alsa seems to be the best bet, but I still don't have a working microphone.
Can anyone help me in this ? Like, with simply editing a config file or something equally simple ? I don't want to fiddle a lot with deep stuff. if it doesn't work, patience. It's my only computer and i don't want to mess it up.

My sound card is a Creative Audigy Player, works well with everything else.

Thank you for all the help.

---

### Post by cogadh on 2007-08-07
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

Scroll down the page most of the way, it will explain how to set up WoW with a voice chat application.

---

### Post by Gunn3r on 2007-08-07
Ok, will try that this night. Ty very much. I saw that page already several times, but didn't noticed that particular subject.

---

### Post by Sammi on 2007-08-07
I used to have exactly the same problem. But then I realised that the solution was kind of simple, only it wasn't documented very well. That's why I wrote that section, so other Linux rookies, would have an easier time :D

I really hope aoss it works. Otherwise getting a second PCI sound card is both a cheap and easy solution for stationary computers. Sadly it's not an option on laptops.

---

### Post by Gunn3r on 2007-08-08
Well, unfortunately, aoss didn't work.
I did it like the wowwiki stated... aoss wine /path/wow.exe (with wine using oss of course) and loaded "aoss teamspeak" from CLI.
When i did it (the teamspeak part), WoW became very slow and stuttering, totally unplayable.

On the other hand I went to skype again to give it another look, set it to alsa, then the same to wine and got it working ! I think it was the mic capture volume that was down or something. Missed that the 1st time...
WoW is stable using alsa (I read somewhere that it was safer to use oss for stability reasons) and Skype works as intended, with a clean sound and no interruptions.

so, only thing left is to get TS working... will try the DMIX hack tomorrow, but one thing I didn't get. The DMIX hack is done and after that what ? use alsa on wow and aoss on TS or use aoss on both again ?

If anyone has more suggentions, feel free to write.

TY !

---

### Post by Sammi on 2007-08-08
> **Gunn3r said:**
> Well, unfortunately, aoss didn't work.
I did it like the wowwiki stated... aoss wine /path/wow.exe (with wine using oss of course) and loaded "aoss teamspeak" from CLI.
When i did it (the teamspeak part), WoW became very slow and stuttering, totally unplayable.

On the other hand I went to skype again to give it another look, set it to alsa, then the same to wine and got it working ! I think it was the mic capture volume that was down or something. Missed that the 1st time...
WoW is stable using alsa (I read somewhere that it was safer to use oss for stability reasons) and Skype works as intended, with a clean sound and no interruptions.

so, only thing left is to get TS working... will try the DMIX hack tomorrow, but one thing I didn't get. The DMIX hack is done and after that what ? use alsa on wow and aoss on TS or use aoss on both again ?

If anyone has more suggentions, feel free to write.

TY !
You can always dream about TeamSpeak 3, which will use ALSA: [http://www.goteamspeak.com/index.php?page=blog](http://www.goteamspeak.com/index.php?page=blog)

If we're lucky they'll release it this year (yeah right).

---

