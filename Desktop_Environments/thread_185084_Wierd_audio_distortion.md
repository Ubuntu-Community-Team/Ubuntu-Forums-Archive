---
title: "Wierd audio distortion"
date: 2006-05-31
forum: Desktop Environments
---

### Post by | MM | on 2006-05-31
Hello,

I'm getting wierd distortion playing certain audio files, either .mp3 or .wma through rhythmbox or and/or totem.

The distortion or low popping sounds, that vary in volume during the extent of the track, is only evident when played through rhythmbox or totem. Distortion IS NOT present when the file is played through mplayer.  :-k

Any thoughts?

---

### Post by jalonsom on 2006-05-31
Try lowering the PCM volume.

I have noticed that after a recent upgrade that involved alsa stuff, all volumes were set to 100%

This is OK for master volume, because 100% does not amplify sound.
The problem is that 100% in PCM volume means amplification, and this causes distortion in high volume audio files.

So open the audio mixer and set PCM volume around 80%, which seems to correspond to unity gain (no amplification). Maybe this solves your problem.

I filed [bug #42043]("https://launchpad.net/distros/ubuntu/+source/gnome-alsamixer/+bug/42043") on this unconsistent behaviour a long time ago, but got no answer. If this is your problem, please add a comment to get some attention.

I think it is an important bug, as many newcomers are going to think that sound does not work, and PCM volume is quite hidden.

---

### Post by | MM | on 2006-06-01
No, the PCM volume was at 80% i even tried lowering it further.  Its affecting rhythmbox and totem ... and not mplayer.  So it must be something that is common to both of those apps and is not present in mplayer that is making the difference.

Could it be to do with how the codecs are being handled?

Hrmm i guess ill get the Release version of Dapper and give that a try at some point to see if that makes a difference.

---

### Post by smack on 2006-06-01
Try running gstreamer-properties and changing your default output pluggin to alsa instead of Autodetect. That fixed it for me. The popping was about to make me commit hari-kari.

---

### Post by | MM | on 2006-06-03
hrmm so i did as smack said, as well im now on a fresh install of dapper.  Its really wierd, like its just certain files, like some play right, some play with the distortion, regardless of format.  Perhaps bitrate but i dunno easily how to tell the bitrate as rhythmbox just says unknown.

But the files that play wierd i totem and rhythmbox play right in mplayer, and they all play fine in windows.

---

### Post by whitemage12380 on 2006-06-26
Well, you helped me out a bunch. Thanks!

---

### Post by dougfir on 2006-07-08
> **| MM | said:**
> hrmm so i did as smack said, as well im now on a fresh install of dapper.  Its really wierd, like its just certain files, like some play right, some play with the distortion, regardless of format.  Perhaps bitrate but i dunno easily how to tell the bitrate as rhythmbox just says unknown.

But the files that play wierd i totem and rhythmbox play right in mplayer, and they all play fine in windows.

I'm experiencing the same thing!  I'm using an SB live value here.  Setting the PCM volume to 80% doesn't work.

And yea, the distortion is only during some songs.  It's kind of like underwater sounds.

---

### Post by Cody8417 on 2006-08-28
i'm experiencing this as well with an audigy 2.  get the popping sounds in rhythmbox and songbird, but not in xmms or vlc or under windows.

still looking for a fix

---

### Post by cbudden on 2006-08-29
I am using an Intel HDA laptop audio chip, and I also get the strange underwater sounds in Rhythmbox, a little using Beep but not at all using Mplayer.  Very odd.  Glad its not affecting all software though.

---

### Post by cbudden on 2006-08-29
> **Cody8417 said:**
> i'm experiencing this as well with an audigy 2.  get the popping sounds in rhythmbox and songbird, but not in xmms or vlc or under windows.

still looking for a fix

> **cbudden said:**
> I am using an Intel HDA laptop audio chip, and I also get the strange underwater sounds in Rhythmbox, a little using Beep but not at all using Mplayer.  Very odd.  Glad its not affecting all software though.

Ok, here is how I fixed the underwater problem.  (With HUGE help from #gstreamer on freenode and #rhythmbox on irc.gnome.org)

```

sudo apt-get remove gstreamer0.10-fluendo-mp3

```

Then install 

```

sudo apt-get install gstreamer0.10-plugins-ugly

```

Worked for me!

---

### Post by saracen on 2006-09-01
> **cbudden said:**
> ```

sudo apt-get remove gstreamer0.10-fluendo-mp3

```

Then install 

```

sudo apt-get install gstreamer0.10-plugins-ugly

```

Yup!  This worked for me as well!  If that plugin is bad then why do they keep it around?

---

### Post by Seryozha on 2006-09-08
> **saracen said:**
> Yup!  This worked for me as well!  If that plugin is bad then why do they keep it around?

just tried this out... Hope it works *fingers crossed*

---

### Post by Seryozha on 2006-09-08
> **Seryozha said:**
> just tried this out... Hope it works *fingers crossed*

Nope :( no luck.  it seemd like it was fixed last night but now its doing the same thing.  everyonce in a while it just sounds really tinny and hollow. if i pause the song and restart it it works fine again or if i leave it usually after 30 sec or so it will fix itself.  it does this with MP3's, in WOW, with OGG.... any ideas?  oh look there it is again.. it dosent like being talked about.

---

### Post by | MM | on 2006-09-10
Hey ...  woohoo this worked, evil fluendo!
Forgot about this problem for edgy, had to return here after a long time, but yay good to know there is a fix!

This is pretty anecdotal, but i think there is a correlation between where files are ripped.  For instance i *_think_* that all the files with the underwater sound were ripped on my friends computer in wmp.

But files ripped on my computer in wmp are fine, regardless of the output compression format (.mp3 or .wma).  Quite bizarre!

---

### Post by Glint on 2006-11-10
Thanks.  Worked a treat for me.

---

### Post by Dr_Faustivius on 2006-11-25
This worked for me in Dapper, I had already installed the gstreamer-plugins-ugly, but fluendo seems to be whats causing the evil low pops. I've noticed that it's most prevalent in distorted or overdriven music (Such as Tool, Kittie, or Slipknot) My Vivaldi didn't have this problem though...

Interesting.

---

### Post by Chachee on 2006-12-26
I still have the distortion and don't have gstreamer0.10-fluendo-mp3 installed.  For the most part it's only when the CD spins up/down/eject.

It also happens when I'm ripping CDs, which I would assume is connected with the CD drive changing it's spinning.

Any clues?

JT

---

