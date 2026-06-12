---
title: "Compare two WAV files???"
date: 2009-03-24
forum: General Help
---

### Post by u-slayer on 2009-03-24
I'm looking for a program that can compare to wav files and tell me if they sound similar. Maybe something to analyse volume peaks or something. Nothing fancy. 

I tried to install a speech-to-text program: julius, but I couldn't figure out the config options.

---

### Post by ibuclaw on 2009-03-24
I'm not sure this is all that possible due to the binary format audio is stored in. Although such things exist for images, which decodes the files for analysis. So it may be worth having a look around, but I wouldn't get my hopes high.

But as good as analyst software can get, nothing can beat the comparison of your own ears, in my personal opinion ;)

Regards
Iain

---

### Post by u-slayer on 2009-03-24
> **tinivole said:**
> But as good as analyst software can get, nothing can beat the comparison of your own ears, in my personal opinion ;)

This script is meant to be fully automated. Also, im not looking for anything to tell me what sounds best. I just want to know if do wav files contain the same audio. Should be pretty simple really.

---

### Post by rolandrock on 2009-03-24
Mr slayer,

I agree with Iain that the format of wav files is such that there is no way of simply comparing them and determing if content is similar.

One idea would be to pull apart the source code for audacity.  Find the algorithms that render the graphical representation of the audio.  Build up a system of criteria for determining what is 'similar'.  Then _simply_ write it yourself.

You will of course need to be proficient in C and have pretty good statistical analysis skills.

There may be applications for these techniques in oil/mining indsutries as well as medicine so you could make a fortune and save the world.  I'm going to lean back, stare at the ceiling and go glassy-eyed for ten minutes.  Ahhhh.

Regards
Paul

---

### Post by HavocXphere on 2009-03-24
> **u-slayer said:**
> Should be pretty simple really.
Hell no. "Understanding" audio  is one of those things that computers just don't do well. Its right up there with asking a computer to work out which painting is more beautiful.

Its not quite clear what we're dealing with here: Music or spoken text. 

Mainly Beat detection is used. Neural networks to a lesser extent.

Or invert the phase of the first one, mix with second one. If the result is near zero then they are the same. If the one is offset/remixed/normalized though then it screws everything.

If its a music collection then you can try something like magic mp3 tagger.

> **u-slayer said:**
> anything to tell me what sounds best.
Aside from bitrate and format, there is no easy way for a computer to work this out. "sounds best" is very subjective. Computers don't do subjective.

---

### Post by u-slayer on 2009-03-24
> **HavocXphere said:**
> Its not quite clear what we're dealing with here: Music or spoken text.

I've got two sound tracks from a dvd, one in 6 channel ac3 and one in 2-channel ac3. I use mplayer to convert the both to a one channel wav sample and normalize the audio. Now how can the script tell if they have the same audio?

> **HavocXphere said:**
> 
Mainly Beat detection is used. Or invert the phase of the first one, mix with second one. If the result is near zero then they are the same. If the one is offset/remixed/normalized though then it screws everything. Interesting, what software can do this?


> **HavocXphere said:**
> Aside from bitrate and format, there is no easy way for a computer to work this out. "sounds best" is very subjective. Computers don't do subjective.

Try reading the full sentence again:
[QUOTE=U-Slayer]
Also, im **[COLOR="Red"][SIZE="5"]not[/SIZE][/COLOR]** looking for anything to tell me what sounds best. I just want to know if do wav files contain the same audio.[/QUOTE]

---

### Post by unutbu on 2009-03-24
What you want to do is possible, but I don't know of a Linux program that does it out-of-the-box. That doesn't mean it doesn't exist -- I only started looking after reading your first post.

Here is a windows program that claims to be able to find similar sound files: [http://www.music-similarity.com/](http://www.music-similarity.com/) based on (correlation of?) FFT or wavelet decompositions.

And here are two discussions of how it can be done. 
[http://www.dsprelated.com/showmessage/103820/1.php](http://www.dsprelated.com/showmessage/103820/1.php)
[http://www.perlmonks.org/?node_id=169641](http://www.perlmonks.org/?node_id=169641)

---

### Post by uwalt on 2009-08-28
> **u-slayer said:**
> I'm looking for a program that can compare to wav files and tell me if they sound similar. Maybe something to analyse volume peaks or something. Nothing fancy. 

I tried to install a speech-to-text program: julius, but I couldn't figure out the config options.

Hi,

I found this software that can do the job:

[http://www.sevana.fi/voice_quality_testing_measurement_analysis.php](http://www.sevana.fi/voice_quality_testing_measurement_analysis.php)

if you like to compare music files then the Wideband version is for you. As a matter of fact it's available for Linux and Windows (I contacted the company). For my tasks I used the demo version and it worked quite fine.

I would greately appreciate if anybody could point me to similar resources. TIA!

---

### Post by sevana on 2010-08-27
Thank you for mentioning our product! We would like to give more details and information about AQuA and NIQA, so please find materials attached to this post.

Don't hesitate to contact us, we are happy to talk to you!

Best Regards,
Sevana Oy

> **uwalt said:**
> Hi,

I found this software that can do the job:

[http://www.sevana.fi/voice_quality_testing_measurement_analysis.php](http://www.sevana.fi/voice_quality_testing_measurement_analysis.php)

if you like to compare music files then the Wideband version is for you. As a matter of fact it's available for Linux and Windows (I contacted the company). For my tasks I used the demo version and it worked quite fine.

I would greately appreciate if anybody could point me to similar resources. TIA!

---

