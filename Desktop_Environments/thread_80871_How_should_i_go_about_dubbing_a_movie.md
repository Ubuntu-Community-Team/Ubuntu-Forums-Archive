---
title: "How should i go about dubbing a movie?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by pizzach on 2005-10-23
This last summer I was playing around with redubbing Anime all by myself.  (Managed an episode and a half.)  It was actually a lot of fun.  But that was on my Mac.  I need to figure out a new workflow.  Now that the mic is working on my lappy with breezy and a freshly complied alsa driver I think I am ready to start setting up camp.

Recorded and edited audio files with Audacity before so no change now.

I mixed audio streams in iMovie on my mac. Mixing them in audacity is not an option because the video is required for some kind of syncing and decent acting. I tried kino, but didn't notice any places for audio import/muxing.  That and I don't know how I would import movie into it yet since it is for dv (but then iMovie is technically too.)

Last I need a good program for exporting around the file so I can compress it good.  I could use ffmpeg on my Mac......but that version had a gui with it.

Any help would be appreciated.  I didn't think I did a bad job on my previous dub.  I had only meant to spend a day on it but ended up spending 3.  I actually liked my acting better than the real episode of Excel Saga.  I couldn't believe I managed to play ALL of the characters without it sounding horrible  :).  iMovie is a good program, but I did have to fight with it because it wasn't made for dubbing something in mind.  Not to mention I ran into some bugs in the program that screwed up my audio twice.

thanks in advance,
zach

---

### Post by Ampersand on 2005-10-23
You could try Cinelerra ([http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)). It's not in the repositories, but there's a .deb on the site.

---

### Post by kaput on 2005-10-23
Another app to keep on the radar is Diva, but it's not quite ready yet. It's a Mono-based app focused on a blend of usefulness and usability and is being compared to iMovie (and for once, rightfully so in my opinion). You can watch a demo [here]("http://forge.novell.com/modules/xfcontent/private.php/diva/demo_4.zip"), but be forewarned, it's **28** megabytes. As this app matures, I'll definitely be watching because what I see so far is superb.

More info at the coder's [blog]("http://diva.mdk.org.pl/").

---

### Post by pizzach on 2005-10-23
Diva looks good.  From the movie I can already tell it does what I need it to do.  It just doesn't appear to be released yet.  Agh! :)

Finally got Cinelerra to compile and install.  The rpms on the site didn't appear to be for x686.  I can not for the life of me figure out how to superimpose two audio effects in Cinelerra which is essential for dubbing.  Being the humungoid program it is and the fact that it can do video compositing makes me think it has to be possible.  But I can't even find any helpful documentation or tutorials pertaining to my needs.

I suppose all I'm looking for in the end is an application that can mix different audio streams together.  Simplest example would be taking and ogg music file and putting it againt me talking.

I may just have to just try another way and think outside the box a bit more.  I suppose it's entirely possible to align audio by listening to the japanese speakers when they start and stop talking in audacity with no visual cues.  And for the actual encording I just have to open up mplayer next to audacity and try to speak against the movie.  It will probably work better than I think.  Then I can just combine my own audiotrack with the vidio in Cinelerra.

Actually, that doesn't sound so bad now that I think about it.  Probably still less painful than how iMovie got super slow when audio inserts piled up.  Yeah, I got caught thinking in the box.  Sorry peoples.  :mad: It really is true that the first way you learn to do something effects you learning how to do it on other things.  Also reminds me of how my english tends to still leading my japanese speaking around in how I do sentence structure too.  First language effects second language because of an implanted way of thinking.

Thanks again peoples.  If someone does think of a better way for me to do this, I'm all ears still. :)

---

### Post by reuben on 2005-12-09
Try Main Actor. Costs $$s, but awesome. There's a free download (deb) demo.

---

