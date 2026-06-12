---
title: "Yahoo Games:Chess (Not Working)"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by timo1023 on 2008-05-18
I am trying to load up Yahoo Chess, but I'm getting an error:
Link: [http://games.yahoo.com/games/login2?page=ch](http://games.yahoo.com/games/login2?page=ch)
Error:
"You have an old version of the client in your cache. You will need to restart you browser and come back to retrieve the current version. If restarting does not work, manually clearing your browser's cache should fix the problem."

Clearing the cache does not fix the problem. I am running Hardy, Firefox 3 Beta 5, and Flash/Java were install with the ubuntu-restricted-extras package.

Can someone else reproduce/solve this?

---

### Post by frogitts on 2008-05-18
Yeah, I can reproduce that on 8.04 with Firefox 2. My only guess is that it's reading the old client from my Windows partition, but I can't find anything with the words "yahoo" or "chess" on my windows partition. Looks like it may actually be an ubuntu/firefox thing.

---

### Post by Monicker on 2008-05-18
Judging from what I read in the Yahoo message boards, this is an issue with their site.  People have complained about it happening with IE on Windows too.  I got that error myself when trying to access it from my wife's computer, using Internet Explorer on Windows XP.

---

### Post by timo1023 on 2008-05-30
Looks like you have to downgrade to Flash 7 from the current Flash 9, but I haven't tried that yet.

---

### Post by pyan on 2008-06-04
hello,
I faced the same problem..
I have 3 browser.(firefox 3,firefox 2 and swiftfox)
I can play chess with swiftfox only.swiftfox is 32 bit browser that I've installed in fiestyfawn.Now I in hardy heron.Firefox 3 and firefox 2 will give the error:
"You have an old version of the client in your cache. You will need to restart you browser and come back to retrieve the current version. If restarting does not work, manually clearing your browser's cache should fix the problem."

It's look like that we can run yahoo chess with the first installed browser only....

---

### Post by grossaffe on 2008-06-04
for me, yahoo chess just takes about 15+ minutes to load (no exaggeration)

---

### Post by twizler on 2008-06-10
I am also not able to play yahoo chess -- get the cache problem... .

:confused:

---

### Post by twizler on 2008-06-11
No yahoo games Hardy 8.04 - new install from scratch for 8.04 Ubuntu and yahoo chess will not work ... have tried removing java totally out of system did a new install of java from a sun.com  tar.gz file -- NOTHING has worked so far. 

if i go to a java enabled page it tells me everything works and i have removed the ice java version. 

if you have the fix please update your answer. -- i think people that did an upgrade to hard hv gotten yahoo games to work -- but doing a blank install ... NO LUCK. 

HELP needed:?:

---

### Post by opend0wn on 2008-07-01
2 things 
1 make sure your firewall allows outgoing 11999 port 
2 downgrade flashplayer here is one that works for me [http://opendown.homeunix.com:88/install_flash_player_9_linux.tar.gz](http://opendown.homeunix.com:88/install_flash_player_9_linux.tar.gz)

tar -zxf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer

---

### Post by twizler on 2008-07-02
OK so yahoo chess is now all the sudden working ?? maybe they made a change on the yahoo server?? Only thing i have done different lately was installing XMMS the old one.

---

### Post by timo1023 on 2008-07-05
I can confirm that Yahoo Chess is now working (without having to downgrade Flash).

---

### Post by buntu_hugenewbie11 on 2008-10-28
I find that it is still not working.
I am using Hardy 64 bit and have Shockwave Flash 10.0 r12
What are you all using to get it working?
Which Java plugins are you using?

---

