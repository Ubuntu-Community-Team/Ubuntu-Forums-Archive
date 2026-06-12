---
title: "TeamSpeak2 with ARTS working with WoW"
date: 2006-11-17
forum: Gaming &amp; Leisure
---

### Post by JairunCaloth on 2006-11-17
FINALLY!!!! This problem has been plaguing me for months and months on end. Now there is a solution! (Well it works for me anyways)

I've seen tons of posts on here and everywhere else on the web, where people need to be able to use TeamSpeak while they play 'X' game. Note I have not tested this with any other games, but it's working great with WoW. I have full sound in WoW, and I'm able to use TS fully.

Poking around on the web today I ran across this little gem of a post that got it all working for me. [http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1705&forum=6](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1705&forum=6)

I skipped most of the info there because I already have WoW running with wine through AOSS, and I've got alsa working just fine. I did a sudo apt-get install arts. Next I ran arts -d (-d enables full duplex mode, otherwise you won't be able to talk, only listen)

Don't forget to edit the TS launcher to use ARTS: 

 your/install/dir/TeamSpeak2/TeamSpeak.bin $*

Changes to 

 artsdsp -m your/install/dir/TeamSpeak2/TeamSpeak.bin $*

Run TS and volia I have TS and sound in WoW

*note I'm running Xubuntu Edgy

---

### Post by frodon on 2006-11-17
Don't forget that if you have 10$ to spend just buy a soundblaster live on ebay for example, these cards include a component which mix the sound in hardware so you don't have any sound problems like with onboard soundcards ;)

---

### Post by JairunCaloth on 2006-11-23
does that include the audigy?

---

