---
title: "Recording internet audio"
date: 2005-05-27
forum: Desktop Environments
---

### Post by spencer on 2005-05-27
Hi,

Just wondering, In OS X I use WireTap to record internet audio. Is there such an app for linux?   

-spencer

---

### Post by jobezone on 2005-05-27
I use streamtuner to listen to streams, which then can use streamripper to record them.
I think both are in Universe.

---

### Post by word_virus on 2005-05-27
[QUOTE=spencer]Hi,

Just wondering, In OS X I use WireTap to record internet audio. Is there such an app for linux?   

-spencer[/QUOTE]

apt-get install audacity

Open it in the Programs menu

Select "Stereo Mix" from the input selector (It's the drop-down box next to the mic 
volume fader) and press the "Record" button.  You can capture any sound that goes through your soundcard this way, then edit it, convert it to ogg or mp3, add effects, whatever.  I use this method all the time.

---

### Post by Majlo on 2005-05-27
Or try this howto

[http://www.ubuntuforums.org/showthread.php?t=28356](http://www.ubuntuforums.org/showthread.php?t=28356)

---

### Post by flaming_monkey on 2005-05-27
mplayer to the rescue.

download radio link

$ wget [http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/hitchhikers.ram](http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/hitchhikers.ram)

then rip the stream

$ mplayer -dumpstream `cat hitchhikers.ram`

convert it to a wav

$ mplayer stream.dump -ao pcm -aofile ripped_audio.wav 

finally, convert that to ogg or mp3

$ lame ripped_audio.wav ripped_audio.mp3

---

### Post by GazaM on 2005-05-27
What app do you use to listen to internet radio? If you use XMMS or Beep Media Player you can record streaming Internet Radio by going into 'preferences', then 'plugins' then select the MPEG Audio plugin (also known as mpg123) and go into it's preferences. Now go to the 'Streaming' tab and tick the box 'Save stream to disk'. This will record any SHOUTcast or Icecast (pretty much ALL mp3 internet radio) as mp3 to the path you selected. I'm surprised nobody suggested this as it is far less hassle than any other suggestion on this page. Hope this helped.

---

### Post by spencer on 2005-05-27
Thanks for sharing your comments on this everyone, these apps are just what I was looking for. I'll try em' out and see which one works best for me, Thanks.

-spencer

---

### Post by spencer on 2005-05-27
[QUOTE=word_virus]apt-get install audacity

Open it in the Programs menu

Select "Stereo Mix" from the input selector (It's the drop-down box next to the mic 
volume fader) and press the "Record" button.  You can capture any sound that goes through your soundcard this way, then edit it, convert it to ogg or mp3, add effects, whatever.  I use this method all the time.[/QUOTE]

word_virus,

This is the first method I tried, and it works great!  Haven't yet tried the others, For now I'll stick with Audacity. Thanks. :-) 

-spencer

---

### Post by stepore on 2005-05-30
[QUOTE=word_virus]apt-get install audacity

Open it in the Programs menu

Select "Stereo Mix" from the input selector (It's the drop-down box next to the mic 
volume fader) and press the "Record" button.  You can capture any sound that goes through your soundcard this way, then edit it, convert it to ogg or mp3, add effects, whatever.  I use this method all the time.[/QUOTE]
 i don't see a "stereo mix" on my audacity. all i see is:
vol
line
mic
cd
lin1
phoneIn
phoneOut
video

any tips?

---

### Post by word_virus on 2005-05-31
[QUOTE=stepore]i don't see a "stereo mix" on my audacity. all i see is:
vol
line
mic
cd
lin1
phoneIn
phoneOut
video

any tips?[/QUOTE]

Mm, phoneOut just as a guess.  You can test this really easily by playing something in, say, XMMS, pressing record in Audacity, then changing the input until you notice the soundwave change.

Hope this helps!

---

### Post by bigzak on 2005-05-31
I prefer vsound. It works by wrapping access to the soundcard and capturing it, and then optionally passing it through (the -d option). You can record, say, a realplayer stream like this:

vsound -d realplayer [http://url.of/stream.ram](http://url.of/stream.ram)

When you quit realplayer you will have vsound.wav in your home directory, containing ONLY the sound played by the app *when it had the soundcard open*. This is cool because you could have 10 minutes messing about before you click play and it still only records the actual sound - no huge silences to get rid of.

---

### Post by stepore on 2005-06-02
[QUOTE=word_virus]Mm, phoneOut just as a guess.  You can test this really easily by playing something in, say, XMMS, pressing record in Audacity, then changing the input until you notice the soundwave change.

Hope this helps![/QUOTE]
 yup - phoneOut got it. cheers.
do you know how to control or change what audacity sees there? i've got ubuntu on another system, granted i had a hard time getting the sound to work (old compaq deskpro with onboard sound), but on that pc i have absolutely nothing in that drop-down list. not even mic.

---

### Post by waverave on 2006-05-04
[QUOTE=GazaM]What app do you use to listen to internet radio? If you use XMMS or Beep Media Player you can record streaming Internet Radio by going into 'preferences', then 'plugins' then select the MPEG Audio plugin (also known as mpg123) and go into it's preferences. Now go to the 'Streaming' tab and tick the box 'Save stream to disk'. This will record any SHOUTcast or Icecast (pretty much ALL mp3 internet radio) as mp3 to the path you selected. I'm surprised nobody suggested this as it is far less hassle than any other suggestion on this page. Hope this helped.[/QUOTE]

Is there a way to save the id3 info of the stream? tnx

---

### Post by NT4.0 on 2006-08-25
I have been trying to record Internet radio. I have never been able to do it in Windows, so I presumed Linux would cope better. :) I followed the instructions on Audacity but never got the sound wave change. Moreover, if I started Audacity AFTER I started the audio stream (in Totem), Audacity says in can't open the sound device as it is busy. I have an on-board Intel sound card. Can it be so that my hardware just won't let me record Internet radio stream? I heard it's better to buy a separate sound card for better sound quality, so I wonder if it is because of my card's being an on-board device.

---

