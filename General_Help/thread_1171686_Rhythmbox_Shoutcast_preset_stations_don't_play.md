---
title: "Rhythmbox Shoutcast preset stations don't play"
date: 2009-05-27
forum: General Help
---

### Post by puzzledinmn on 2009-05-27
I have just started using Rhythmbox and I have 5 preset radio stations that play and 2076 shoutcast stations that don't.  What is the trick to getting all the preset shoutcast stations working?  I mostly get a Couldn't Start Playback message with Service Temporarily Unavailable. Thanks.

---

### Post by puzzledinmn on 2009-06-01
My brother in law helped me somewhat.  You have to click on "Configure default player" in the upper right hand corner of the Shoutcast web site, then select "Play in your Default Media Player" and save.  Then when you first tune in a station you can select /usr/bin/rhythmbox as your player.  I got 23 mirror entries for the first station I tuned in and added to Rhythmbox.

But I still can't play any of the 2000+ preset Shoutcast stations.  Why were they loaded with the 9.04 install if they don't work?

---

### Post by karatedog on 2010-02-08
I'm baffled. 
I have added a Shoutcast radio "http://77.105.228.100:9000" as a new internet radio (kawaii-radio). First it didn't accepted it, no errors, just blank nothing. I supposed the problem was the URL. So I stripped ":9000".
Adding "http://77.105.228.100" was fine, then I could edit the string to add back ":9000".
Then, it wouldn't play the d@mn radio, telling me various errors of missing GStreamer plugins, or text/html converters. I installed a gazillion packages based on information around the internet, to no avail.

I was about to throw the whole thing out (Exaile plays Shoutcast URLs out-of-the-box), when - hit by a sudden idea - I added only "77.105.228.100:9000" as a new internet radio. Lo-and-behold, it now accepted ":9000" and flawlessly played the channel.
As for added "magick", Rhythmbox immediately added "http://" before this new URL, so now I have 2 exactly same URL in my list, one of them is unplayable.

---

### Post by rbaleksandar on 2010-05-24
I have an even worse problem. :) Icecast loads pretty good. But Shoutcast doesn't at all. When I double click on the folder, Rhythmbox starts reloading the whole radio-thing. And again I get 0 entries in the Shoutcast-folder. Also I tried repeating this a couple of times and Rhythmbox suddenly crashed...

---

### Post by arthalion7 on 2010-07-11
> **rbaleksandar said:**
> I have an even worse problem. :) Icecast loads pretty good. But Shoutcast doesn't at all. When I double click on the folder, Rhythmbox starts reloading the whole radio-thing. And again I get 0 entries in the Shoutcast-folder. Also I tried repeating this a couple of times and Rhythmbox suddenly crashed...

the same behavior on my linuxbox :(

---

