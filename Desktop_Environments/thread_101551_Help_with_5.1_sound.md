---
title: "Help with 5.1 sound"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Plankman on 2005-12-10
Hi. I hope someone can help me. About a month ago I bought a Cmedia 8738 7.1 sound card. I have a 5.1 speaker system, but I can't get my surround to work. Without setting anything, the back speakers just copy the front output, and my subwoofer doens't work. I've tried to change settings in ALSA, but then only my front speakers work.

Thanks
Jason

---

### Post by 0okami on 2005-12-10
well, i know im not much help at the moment, but when i was trying to get 5.1 working, this command really helped trouble shoot: 

terminal: 
speaker-test -c6 -D plug:surround51

then if you look up manhole fansubs, they have a video which uses 5.1 and prompts each speaker with sound as well (good for testing in your media player)
*looking for the file my self at the moment* i will post it once i come across it.

---

### Post by 0okami on 2005-12-11
ok, found the file. it was in my old backup :) 

mkv video format... 
[http://65.189.185.5/test5.1.mkv](http://65.189.185.5/test5.1.mkv)

incase the top link dont work right...
[http://65.189.185.5/test5.1.mkv.tar.gz](http://65.189.185.5/test5.1.mkv.tar.gz)
then extract and play it back.

came in handy when i was playing around with my 5.1

---

### Post by Plankman on 2005-12-11
Thanks

The speaker test worked ok. I'm just downloading the video to try it. I've got MP3's playing, but I can't get it to use my surround and subwoofer. Any ideas? I think it's something to do with ALSA

Thanks

Jason

---

### Post by 0okami on 2005-12-11
when i set up my surround, all i did was double click on the sound icon on the application launcher bar, or  (applications->sound & video->Volumen control)

this loaded the sound mixer... i there, i selected Edit->pref. I checked everything in there to make it visible on the mixer. 

Then, i started unmutting all the channels that were muted by default, that included LFE (subwoffer) Surround channels and such. they were muted by default for some odd reason. 

I'll edit this later if its not too clear. Im runningn late for work :(

---

### Post by Plankman on 2005-12-16
HI, I tried that, but now I only get sound from my two front speakers, I tried to pu it all back how it was, but only get sound from the two front speakers. That 5.1 speaker test worked though. I guess I'll just wait till Dapper and hope that will work.

Thank
Jason

---

### Post by tanari on 2005-12-16
I have SBLive + 5.1 speaker system. I setup speakers very easy, just open volume control and setup **Wave center** (center speaker) channel and **Wave surrond** (rear speakers), thats all. 
Don't know how it helps you, but if helps will be good :)

---

