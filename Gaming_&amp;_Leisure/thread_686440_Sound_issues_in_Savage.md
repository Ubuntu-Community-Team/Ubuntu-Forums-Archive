---
title: "Sound issues in Savage"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by blaise69 on 2008-02-03
Hi there,

I'm experience an issue where sound will be poor quality when I load the game Savage, and them randomly during gameplay (usually within 5-10 minutes) I will lose sound completely, restarting will bring sound back (for 5-10 minutes).

I've searched about and it seems that other people have had this issue, but I've never seen a fix. in fact, most people have said that they've changed nothing but all of a sudden it works perfectly.

It may be to do with having to use ASLA drivers or something, but I don't know too  much about them, when I go into the options screen I have a choice of drivers for sound, but the choices are rather random, things like, front, backl, backr, surround, port, etc.

I have also trued using the alsa-oss package as a wrapper, but the same problem is there.

Any help would be really appreciated.

Cheers,

Blaise.

---

### Post by blaise69 on 2008-02-05
I'm suprised nobody has anything to say on this matter, as I certainly found examples of other people with this issue.

I found that if I have my music player opened before I use Savage, then sound will never work, even if I close my music player fully before executing Savage.  I find this strange, but imagine it's something to do with the sound driver, perhaps ALSA, being set to other software still.

---

### Post by Hooloovooloo on 2008-02-05
Yee, i found a fix for this then i was playing Savage. Forgot how to fix it tho. Check the newerth forums, i think i posted it there. Has to do with Alsa or something like that.

---

### Post by blaise69 on 2008-02-06
Hi Hooloovooloo,

Interesting, is [this]("http://www.newerth.com/smf/index.php/topic,2771.0.html") the thread you are talking about?

I have some questions there then, will downloading alsa-oss have any affect on my other programs/games?  I am slightly concerned here that I could mess things up for other programs in trying to finx something for one, will I always have a choice what driver is used for my applications?

Cheers,

Blaise.

---

### Post by blaise69 on 2008-02-06
Ok interesting,

I already had the alsa wrapper, and followed the instructions before-hand but they didn't work for me.

What I did do though was set my sound_output to oss and ran savage normally, "sh savage.sh", this worked!

Strange, I still get the feeling things will break again soon though :S

---

