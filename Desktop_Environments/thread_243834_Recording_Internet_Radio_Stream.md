---
title: "Recording Internet Radio Stream"
date: 2006-08-25
forum: Desktop Environments
---

### Post by NT4.0 on 2006-08-25
I have been trying to record Internet radio. I have never been able to do it in Windows, so I presumed Linux would cope better. :) I followed the instructions on Audacity found in this forum for an older release of Ubuntu but never got the sound wave change. Moreover, if I started Audacity AFTER I started the audio stream (in Totem), Audacity says in can't open the sound device as it is busy. I have an on-board Intel sound card. Can it be so that my hardware just won't let me record Internet radio stream? I heard it's better to buy a separate sound card for better sound quality, so I wonder if it is because of my card's being an on-board device.

---

### Post by latebeat on 2006-08-25
Do you know the URL of the audio stream ?

---

### Post by NT4.0 on 2006-08-26
Here is the content of the *.asx file which I play with Totem to get the stream:

<ASX VERSION="3.0">

 <ENTRY>

  <REF HREF="mms://a1785.l2187543784.c21875.g.lm.akamaistream.net/D/1785/21875/v0001/reflector:43784" />

 </ENTRY>

</ASX>

---

### Post by mdurham on 2006-08-26
I'd really like to know how to do this too.

---

### Post by joep on 2006-08-26
Hi I use Streamtuner which includes a ripper to record radio,  I them use Audacity to edit the tracks I want to keep. I'm a newbie to Linux and it is possible but awkward to explain.

---

### Post by mdurham on 2006-08-26
thanks joep, but I don't think Streamtuner will do BBC links.

---

### Post by neko18 on 2006-08-26
Do you have mplayer installed?
If not, run this
```
sudo aptitude update && sudo aptitude install mplayer
```

Then run this to rip the stream:
```
mplayer -dumpstream mms://a1785.l2187543784.c21875.g.lm.akamaistream.net/D/1785/21875/v0001/reflector:43784
```
Edit: This command will take a while -- it takes the same amount of time it takes to play the video or music or whatever it is.

It should work, if it doesn't, report back with the error.

---

### Post by neko18 on 2006-08-26
Oh, and if you want to stop the recording, you can hit Control-C at the terminal.

---

### Post by mdurham on 2006-08-26
neko18, it didn't work. See below:
> mike@station1:~$ mplayer -dumpstream mms://a1785.l2187543784.c21875.g.lm.akamaistream.net/D/1785/21875/v0001/reflector:43784
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Xeon Nocona (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing mms://a1785.l2187543784.c21875.g.lm.akamaistream.net/D/1785/21875/v0001/reflector:43784.
STREAM_ASF, URL: mms://a1785.l2187543784.c21875.g.lm.akamaistream.net/D/1785/21875/v0001/reflector:43784
Resolving a1785.l2187543784.c21875.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a1785.l2187543784.c21875.g.lm.akamaistream.net
Resolving a1785.l2187543784.c21875.g.lm.akamaistream.net for AF_INET...
Connecting to server a1785.l2187543784.c21875.g.lm.akamaistream.net[64.86.142.181]: 1755...
Connected
Unknown object
File object, packet length = 1516 (1516)
Unknown object
Stream object, stream id: 1
Stream object, stream id: 2
Unknown object
Unknown object
Data object
mmst packet_length = 1516
Cache size set to 64 KBytes
Stream not seekable!



---

### Post by neko18 on 2006-08-26
And it just stayed at "Stream not seekable?" That's what it should be doing. It means it's recording the stream ;)

There should be a file called stream.dump in your home folder that contains the recording.

---

### Post by mdurham on 2006-08-26
thanks neko18, I see the file now that you mention it.
Cheers, Mike

---

### Post by neko18 on 2006-08-26
No problem

---

### Post by kimara on 2006-08-26
There's a program called streamripper, [http://streamripper.sourceforge.net/](http://streamripper.sourceforge.net/).

---

### Post by NT4.0 on 2006-08-26
Is it possible to do that with Audacity? The fact is that I never found an acceptable setting (Line/PhoneOut/Video etc) to choose for recording. I Windows programs, the necessary item just didn't show up, so I was wondering if it is my sound card that prevents me from recording streams. For those who succeeded with mplayer, does it work with Audacity too?

---

### Post by mwob on 2006-08-28
Hi all,

I'm trying to do the same thing but with BBC "Listen again" links, which just look like this:

[http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu](http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu)

When I try to "mplayer" it, I get this error:

91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing [http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu](http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu).
STREAM_HTTP(1), URL: [http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu](http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/sequence_thu)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.bbc.co.uk](www.bbc.co.uk)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET...
Connecting to server [www.bbc.co.uk](www.bbc.co.uk)[212.58.224.114]: 80...
Cache size set to 320 KBytes
Cache fill:  0.34% (1103 bytes)
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Is there anything I can do?

Thanks!

---

### Post by Edward The Bonobo on 2006-08-28
I've covered this in a HowTo on the Ubuntu wiki pages: [https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3](https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3)

This also covers how to extract URLs, which stations try to hide in media container files.

On that page, I've also got a link to a page where I'm compiling a list of URLs for favourite/random stations.  I've already listed the main, national BBC live feeds.  Please feel free to suggest others.

---

### Post by Edward The Bonobo on 2006-08-28
It occurs to me...maybe the title of the HowTo isn't user-friendly enough.  Should I re-title as "How to record internet radio streams"?

---

### Post by mdurham on 2006-08-28
yes, it's a good idea

---

### Post by mdurham on 2006-08-28
Someone has already done the hard work of finding the .ra urls. See link below
It's great!
[http://dave.org.uk/streams/Radio%204.html]("http://dave.org.uk/streams/Radio%204.html")

---

### Post by mwob on 2006-08-28
Thanks for all the info.. I think I am getting nearer but I can't seem to find the proper URL's (the .ra file)..

I want to record some "listen again" stuff from BBC 6music, all I am offered from the bbc page is a .shtml page. I tried saving that to disk and looking inside it, but it contains no URL for a ram file. That pre-compiled list also just gives the URL of the shtml file... This is the URL I am trying to record:

[http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/6m_lamacq_mon](http://www.bbc.co.uk/radio/aod/6music_aod.shtml?6music/6m_lamacq_mon)

I tried it with vsound just to see what happens, and this is the ouput:

About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: line 177: [http://www.bbc.co.uk/radio/aod/networks/6music/aod.shtml?6music/6m_lamacq_mon:](http://www.bbc.co.uk/radio/aod/networks/6music/aod.shtml?6music/6m_lamacq_mon:) No such file or directory
Missing file ./vsound8474.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

So I guess thats basically it complaining about the URL I am passing, right?

Heres the contents of the shtml file:

[HTML]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head lang="en">
<title>BBC Radio Player - 6 Music</title>
<script src="/radio/aod/javascript/framescheck.js" type="text/javascript"></script>
<meta name="robots" content="noindex" />
</head>
<frameset cols="272,*" framespacing="0" frameborder="no" border="0">
<frame name="bbcplayer" title="Audio controls and information." src="/radio/aod/networks/6music/aod.shtml?6music/6m_lamacq_mon" marginwidth="0" marginheight="0" scrolling="auto" frameborder="0" />
<frameset rows="40,*" framespacing="0" frameborder="no" border="0">
<frame name="dropnav" title="Navigate to other radio stations or types of music." src="/radio/aod/static/dropnav.shtml" marginwidth="0" marginheight="0" scrolling="auto" frameborder="0" />
<frame name="channel" title="Choose something to listen to." src="/radio/aod/networks/6music/channel.shtml" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" />
</frameset>
</frameset>
<noframes>
<body><a href="/radio/aod/networks/6music/audiolist.shtml">No frames version</a></body>
</noframes>
</html>
[/HTML]

---

### Post by mwob on 2006-08-28
Googling this subject some more reveals this page:

[http://www.nenie.org/misc/bbcradio/index.html](http://www.nenie.org/misc/bbcradio/index.html)

Which gives some good ideas, but none of which work!! I cannot view the frame URL because no such option exists in firefox, all I can do is view page source which is no help :-(

---

### Post by Edward The Bonobo on 2006-08-29
The Steve Lamacq page...It looks like what you've got is the .shtml for the frames.  Various other .shtml files are embedded in these...and one of these will most likely have a suitable url in it.

(Can't experiment right now, but I'll have a look from my Lx machine @ home)

I'm really not sure why stations don't just release their stream URLs.

---

### Post by potion magique on 2007-11-23
This is not really a reply, it is a parallel request.

Having recently moved from Windows to Ubuntu, I am delighted t oreport that everything works like a dream, EXCEPT that I like listening to the BBC during the working day, and I simply cannot find a way of recording anything through Audacity.

Audacity shows a flat line for recording, in fact, Audacity shows a flat line for recording whether I am trying to record from the BBC radio or from a CD.

The radio player works perfectly, but I'm not what sure which bit of software is running it!

Can anyone help?

---

### Post by mister_p_1998 on 2007-11-23
For a start, if you are wanting to record from Audacity an audio stream, you'll never do it with an onboard sound card, theyre NOT Duplex. E.G. a Duplex card can record and play audio at the same time. No onboard sound Ive ever seen can do this, theyre all cheap ****. you need to get a soundblaster clone pci card before you can even start to sort the software out. Having said that, the easiest way to record online streaming (Not Realplayer on the BBC) is with the above mentioned Mplayer hack, that records most other non-real streams really well. Ive given up trying to rip realplayer streams, I too get the audio device in use error. Someone wrote a long howto on getting your duplex soundcard working in a duplex manner on Ubuntu, but it looked rather complicated, and looked to me like it might kill all your sound entirely. Try doing a search for recording streams or something.
Steve

---

