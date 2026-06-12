---
title: "Sound Rip"
date: 2006-07-13
forum: Desktop Environments
---

### Post by sparty2809 on 2006-07-13
Does anyone know of a way to rip sound?  Like if I play something off the web, is there a way to rip a sound clip?

---

### Post by oldmanstan on 2006-07-14
i take it you mean you want to record the audio coming out of your speakers? yes, you can do that with "sound recorder" under the "sound and video" submenu under "applications"

you probably want to set the "record from input" drop down list to "wave" but it might be something else for your system, play around with it, the rest should be pretty easy to pick up

---

### Post by jordilin on 2006-07-14
You can just type:
arecord -f cd -t raw | lame -x - out.mp3 and you will record directly to an mp3 file any sound that goes through your computer. You can pipe to the ogg encoder as well substituting lame to oggenc. If you use oggenc the options change. Do a man oggenc. Previously you have to set the recording channel by typiing alsamixer.

---

### Post by jordilin on 2006-07-14
You can use streamripper to rip shoutcast streaming mp3 audio

---

### Post by oldmanstan on 2006-07-14
jordilin subscribes to the command line school of doing everything :) hehe, but if you are familiar at all with how to use the command line it is a much more elegant way

if you are not (you don't know what he meant by "pipe") and would like to become more familiar (you enjoy programs that run fast, clean and smooth), try googling "bash tutorial"

---

### Post by sparty2809 on 2006-07-15
Thanks for the replies.

I tried both options and it records but no audio.  

Any ideas why?

---

### Post by jordilin on 2006-07-15
Well, run alsamixer and you'll see plenty of columns. Select capture to see the available recording channels. There should be a column whose name is capture. Set the channel with the space tab and record with the command arecord -f cd -t raw | lame -x - out.mp3

---

### Post by grizzly on 2006-07-16
this is what I did > in konsole > alasmixer > F4 ( to reach capture controls > selected line . I am pretty sure this is the correct way to select the channel.

Recording with arecord -f cd -t raw | lame -x - out.mp3 
gives gibberesh sound no matter which channel is selected (Mic, line, Cd)

Recording with arecord  -f cd -t wav ww.wav 
still records from the microphone , no matter which channel is selected :/

I am gettign a feeling that my method of channel selection is screwed .

---

### Post by christhemonkey on 2006-07-16
Line will record anything that comes into your sound card from your line in.
So the microphone jack.
You should select wave or pcm to record what comes out of your speakers.

---

### Post by grizzly on 2006-07-16
There isn't a wave/pcm channel :(

---

### Post by christhemonkey on 2006-07-16
What is their then?
Please list all the recording channels:

---

### Post by grizzly on 2006-07-16
here in [in capture(F4) mode]("http://h1.ripway.com/chesss/alsa.png")

---

### Post by jordilin on 2006-07-16
> here in in capture(F4) mode
Select the capture column by typiing the space tab. It will appear the word CAPTUR under the column capture. Try again

---

### Post by grizzly on 2006-07-16
Urgh, I feel stupid, the reason for the gibberish sound was that I was playing a mp3 file with aplay ](*,) 

Anyways here is the final method for recording sound directly from the sound card.
1. open konsole > type alsamixer , enter
2. Press F4 , use arrow keys to highlight Captur , press space bar as required ( till you can see L & R ) 
3. Now you need to select another channel, (again use arrow keys,space bar) , the channel that worked for me was 'mix' . So first try by highlighting 'mix' , press spacebar.
4. Now simply use jordilin command to record

Phew... that lessens the guilt, 
and heres a song for you helpful ppl ;) [http://d.turboupload.com/d/785363/mayeri_phir_dhoom.mp3.html](http://d.turboupload.com/d/785363/mayeri_phir_dhoom.mp3.html) . Its in hindi( India) , but is a really kickass song. Oh btw the first 40 seconds of the song, may come in as a cultural shock, so just fast forward.

Thanks

---

### Post by stanz on 2006-07-16
Well....maybe I'll mention, ~ that the song isn't in english, but sounds nice...and after the yahoo intrusion and delay...I'd not go there.

---

