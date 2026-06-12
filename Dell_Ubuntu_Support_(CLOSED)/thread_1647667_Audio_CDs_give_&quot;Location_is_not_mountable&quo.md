---
title: "Audio CDs give &quot;Location is not mountable&quot; error"
date: 2010-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yacinkov on 2010-12-17
I am very new to Lubuntu, and relatively new to Ubuntu. On an old Dell Dimension XPS T500 I installed Lubuntu 10.10. All works well, except that when I insert an audio CD I get a window with the error message "Location is not mountable". 

In the file manager PCManFM when I click on the Audio CD I get the same error message. Aqualung cannot play the CD either.

Data CDs work fine, and the optical drive and CD work well when I boot from Windows. (I have 2 hard disks, and in Setup I set from where I want to boot.)

I am a software developer and know how to run commands in the terminal.

Thanks much for any insights you could throw my way.

---

### Post by cavalier911 on 2010-12-17
AudioCD's are not mountable,the digital stream is read into the buffer and either converted into analog by a chip in the drive and sent by a small cable to an analog input on the soundcard or with a plugin in the software player. 

Aqualung click the MS button so the Music Store window is open,expand out the CD Audio track info and add to the playlist.Settings/CD Audio/check auto add/remove CDs to playlist.
 
Gnome Mplayer/File/Disc/Open Audio CD

or from terminal

```
mplayer cdda://
```

Add **cache=5000 ** to .mplayer/config to increase buffer.

---

### Post by yacinkov on 2010-12-18
Thanks Cavalier911. Aqualung now plays my CDs thanks to your recommendations. :)

However, I would still like to get rid of the "Location is not mountable" error message that comes up right after I insert an audio CD in my optical drive.  I added cache=5000 to .mplayer/config in my home directory. And I also ran on the terminal the mplayer cdda command as you suggested.

What is this supposed to do exactly?
mplayer cdda://

Thanks again for your help. I greatly appreciate it.

---

### Post by cavalier911 on 2010-12-19
> What is this supposed to do exactly?
mplayer cdda://
Put an Audio CD in your drive. 
Execute the command in terminal.
mplayer should play the Audio CD

> I would still like to get rid of the "Location is not mountable" error message that comes up right after I insert an audio CD in my optical drive.
 
This is a bug in Lubuntu 10.10 without a fix:
[http://askubuntu.com/questions/17252/audio-cds-are-not-playing-because-of-dbus-error](http://askubuntu.com/questions/17252/audio-cds-are-not-playing-because-of-dbus-error)

Lubuntu 10.04 LTS doesn't have this problem,most of the bug's have been fixed.

When it comes to software,the newest release is not a good choice.
I suggest not upgrading/installing the newest version of lubuntu/ubuntu or any distro when it comes out.Wait at least 3 month's,a new version of ubuntu is released every 6 month's with new problems. 

I use LTS version's which are only released every 2 years with point releases in between and supported with security updates for 3 years.

---

### Post by andrew.46 on 2010-12-19
Hi yacinkov,

Depending on how your copy of MPlayer has been configured the following will not only play your audio cd but will also perform a CDDB search for you:

```

mplayer cddb://

```

I give an example below with an old classic:

```

andrew@skamandros~$ mplayer cddb://
MPlayer SVN-r32718-4.3.3 (C) 2000-2010 MPlayer Team

Playing cddb://.
Found audio CD with 9 tracks.
================ CD INFO === start =========
 artist=[Pink Floyd]
 album=[The Dark Side Of The Moon]
 genre=[Psychedelic Rock]
 nb_tracks=9
 length= 42:57.20
  # 1  4:00.41 @     182	[Speak To Me/Breathe] 
  # 2  3:32.74 @   18222	[On The Run] 
  # 3  7:06.38 @   34195	[Time] 
  # 4  4:44.04 @   66182	[The Great Gig In The Sky] 
  # 5  6:32.01 @   87485	[Money] 
  # 6  7:40.61 @  116885	[Us And Them] 
  # 7  3:25.46 @  151445	[Any Colour You Like] 
  # 8  3:50.41 @  166865	[Brain Damage] 
  # 9  2:04.23 @  184155	[Eclipse] 
================ CD INFO ===  end  =========

On The Run
rawaudio file format detected.

Speak To Me/Breathe
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  30.6 (30.6) of 2577.7 (42:57.6) 11.5% 

```

MPlayer has so many possibilities :)

Andrew

---

### Post by yacinkov on 2010-12-21
Thanks much Cavalier911. You explain things very well. I will install Lubuntu 10.04. I agree that with software it is always best to not be on the bleeding edge and be one version behind.
 
Thanks Andrew, for teaching me a bit about mplayer. One always learns lots by posting in these forums.
 
A much appreciative Yacinkov :D

---

### Post by Swaphead on 2010-12-31
Thanks to Cavalier911, not only for explaining the workaround, but for helping to clarify what "mounting" entails. (I'm still very fuzzy about it).
I have only been using Linux for about a year.
I switched from Ubuntu to Lubuntu 10.04 for its speed, but I went to 10.10 as soon as it was released because 10.04 did not automatically show when updates were available and 10.10 did.

What I can't get my head around is this:
The bug has only recently occurred: the last time I played an audio CD in AQUALUNG I didn't get the "Not Mountable" message and the tracklist appeared automatically.
Does this mean it was caused by something else being "fixed"?

Cheers
Geoff

---

### Post by baracuda68 on 2011-01-22
As I found elsewhere,(Cant find the link) for 10.10,
You need to 
sudo apt-get install gvfs-backends

Worked for me...

---

