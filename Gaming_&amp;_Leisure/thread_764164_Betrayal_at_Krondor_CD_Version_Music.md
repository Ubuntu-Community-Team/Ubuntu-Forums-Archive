---
title: "Betrayal at Krondor CD Version Music"
date: 2008-04-23
forum: Gaming &amp; Leisure
---

### Post by captainjorge on 2008-04-23
Hi everyone,

I've been searching the 'net for a few days now trying to find an answer to this with no luck. Maybe one of you could shed insight on this problem...

I'm trying to run an old DOS classic - Betrayal at Krondor - through the DosBox emulator under Ubuntu 7.10. The game runs fine, but not the CD Audio. The game's music is played from the CD (Redbook Audio), the CD is a mixed mode disc. The data portion is only needed once for the install, but the music part is always needed. I've accomplished this setup successfully in windows by mounting the cd in dosbox like so:

mount d d:/ -t cdrom

Or something like that at least. 

My question is this: How can I accomplish this in Ubuntu? 

I know it works in Windows because both parts of the mixed mode disc are accessible to the operating system, and mounting in dosbox picks them up both. When I pop the CD in Ubuntu, I'm asked if I want to browse data or play audio, the play audio option just takes me to the 'sound juicer' ripping app. Is there a way to mount the audio part of the disc? I need the audio part present in a way that can talk to dosbox. Making an iso or some type of image would be even better, but as far as I know .iso does not support mixed mode. 

The game is a favorite of mine and the music is truly great, otherwise I wouldn't go through so much trouble. Any help would be greatly appreciated.

---

### Post by happyhamster on 2008-04-23
Try downloading the game (it's freeware now). More info (including a download link) is here:
[http://linuxappfinder.com/blog/rediscovering_betrayal_at_krondor_using_dosbox](http://linuxappfinder.com/blog/rediscovering_betrayal_at_krondor_using_dosbox)

And also see:
[http://en.wikipedia.org/wiki/Betrayal_at_Krondor](http://en.wikipedia.org/wiki/Betrayal_at_Krondor)

---

### Post by captainjorge on 2008-04-23
Thank you for the reply. I took at link at your links. The freeware version comes without the cd music it uses midi instead. The cd version which I have will default to midi if no cd is present. My project is getting linux to recognize the audio portion in some kind of mountable format so that other programs can see the audio files. I'm doing some research on cdfs, I may be able to use that to extract the audio content and mount it as an image.

---

### Post by Grishka on 2008-04-23
DOSBox can be configured to mount CDs. try DBGL for a nice frontend to DOSBox. there's an option there to mount a CD under DOS.

---

### Post by captainjorge on 2008-04-23
Cool. I didn't know about the frontend. I'll check it out.:cool:

---

### Post by captainjorge on 2008-04-26
Solved it!

A different approach was required. DosBox supports mounting of bin/cue images for mixed mode cds. I created an bin/cue of my cd, and mounted it in DosBox with the imgmount command:

imgmount [driveletter] [file system parameters]

in my case it was:
imgmount  g bak.cue -t iso -fs iso

Works flawlessly, now I have Betrayal at Krondor working in Linux with the cd music!

---

### Post by happyhamster on 2008-04-26
Funny thing is, I also still have that cd (a SierraOriginals from way back). I have played the game a lot (the puzzles were great!), but I can't remember hearing the cd music ever. It must have defaulted to midi for me always. (Perhaps because of the old hardware.)

Anyway, I tried your solution, and it worked perfectly. First time I'm hearing the cd music (and it only took ~10 years, ubuntu and dosbox to pull it off). :lolflag:

---

### Post by captainjorge on 2008-04-26
Glad to hear it! Enjoy the excellent music!

---

### Post by gifted a55a55in on 2010-01-10
> **happyhamster said:**
> Funny thing is, I also still have that cd (a SierraOriginals from way back). I have played the game a lot (the puzzles were great!), but I can't remember hearing the cd music ever. It must have defaulted to midi for me always. (Perhaps because of the old hardware.)

Anyway, I tried your solution, and it worked perfectly. First time I'm hearing the cd music (and it only took ~10 years, ubuntu and dosbox to pull it off). :lolflag:

It's been almost a decade since I first played BaK. And I absolutely loved the music--even my late grandfather once heard the music when I was in Krondor and said it was great. Funny thing is just using the "Install.exe" option you can make it play in 3 different ways!

But only recently (a couple years back) I found out that the AWESOME music that I've been hearing isn't even the original "CD Music" and that it was even better! I've tried but all the downloadable versions as well as the device driver CD on which I had found the game (among some demo versions of "better" games) contain only the MIDI version.

So I'd like to know: How much megabytes is this cd? Can anyone upload an image and send it to me by e-mail? Any help with how to play it on Win XP would also be welcome.

---

