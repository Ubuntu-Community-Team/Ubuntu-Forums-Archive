---
title: "Music Server Drive Swap (upcoming)"
date: 2009-01-05
forum: General Help
---

### Post by jamesisin on 2009-01-05
Howdy,

I am building a music server on my network.  For reasons of convenience I would like to start building the drive on one of my desktop machine and then move the drive into the server where it will perform its duties.

I was planning to format the drive in ext3 and load all the CD's in my collection as wave files.  What I would like pre-assistance with is cautions about what is to come.

Will there be issues in moving the drive from my desktop machine to my music server?  I do this in Windows all the time, but that's a different world.  Permissions, maybe?

Is ext3 the best file system for this kind of storage and access?


Thanks in advance,

James

---

### Post by TransitMan on 2009-01-05
Are there going to be a mix of Operating Systems accessing this drive from the server?
If so, you may want to think about either FAT32 or NTFS, preferably the later if any Windows system is not older that Windows 2000.
If a MAC system is going to access it, then FAT32 will be your only option here.
I have a similar server setup here at home and it is formatted in NTFS, because of the mix of OSes. (No MACs involved.)

Moving it to another box may not be a problem. Once there, you'll have to assign and place file sharing permissions through that computers OS setup. And then test to make sure it functions from another computer other than your own. If it works, you're good to go. If not, a little more configuring.

Good luck.

---

### Post by jamesisin on 2009-01-05
Yeah, I was thinking about the cross-platform issues.  I believe I can get what's needed for the Mac to mount ext3 if I need to do that.  Less certain about Windows.

However, if I use MPD (Music Player Daemon) I think I can send the signal to any machine which has a viable client (and I further believe those clients are available).  Though I am not already an expert in this area--read: rank amateur.

I do have all three OS's (Mac, Windows, and Unix) and I have considered FAT32.  There is some problem with larger drives, but usually once they are correctly formatted they can be seen and accessed by Mac and Windows:

[http://www.soundunreason.com/InkWell/?p=39](http://www.soundunreason.com/InkWell/?p=39)

Primarily though I am concerned with using Linux boxes to get the music from the server.

(My Mac is a laptop connected to wireless (different subnet) and rarely connected to wired.  I have a Windows server and my recording studio machine is Vista--neither of which will be playing music from the music server.)

---

### Post by jamesisin on 2009-01-05
Well, we have arrived at snag number one.

For whatever reason, Rhythmbox will encode my CD's as .wav files but they are just static and it will fail to add them to its library (GStreamer error).  Is this normal?

I've added a host of codecs to my system but none of my audio applications is able to play these waves (but other waves made on other systems--recordings--are working fine).

I opened Sound Juicer and extracted a CD as both .wav (wrong bit rate I noticed) and .flac.  The waves produce a GStreamer error in Totem and Rhythmbox (same as those produced by RB) while the flacs play fine.

Why won't RB (& company) encode these waves?

(I confirmed that VLC on Vista and my Mac will play them, but they are nothing but static.  Clearly that's an encoding problem more than a playback problem.)

This is especially a pain because I can't use flac on my ipod, can I?

=========================

Thread addressing this encoding problem:

[http://ubuntuforums.org/showthread.php?p=6501861](http://ubuntuforums.org/showthread.php?p=6501861)

---

### Post by TransitMan on 2009-01-05
Your ripping and encoding a CD as a CD.
You need to rip and encode as .mp3, m4a (AAC) or .ogg.
If you need to go with .mp3, then convert from .ogg to .mp3.
However, if you can rip and encode in AAC (.m4a), it will be read by your I-Pod.

---

### Post by jamesisin on 2009-01-06
I usually rip CD's as waves (.cda to .wav) using iTunes on my Mac or my Windows machine.

My iPod plays wave files just fine.  Bummer it doesn't play flac though.

Is that what you were meaning?

---

### Post by TransitMan on 2009-01-06
> **jamesisin said:**
> I usually rip CD's as waves (.cda to .wav) using iTunes on my Mac or my Windows machine.

My iPod plays wave files just fine.  Bummer it doesn't play flac though.

Is that what you were meaning?

Yes it is.

Try and rip them in ACC (.m4a) which is Apples codec.

---

### Post by mcduck on 2009-01-06
> **jamesisin said:**
> Yeah, I was thinking about the cross-platform issues.  I believe I can get what's needed for the Mac to mount ext3 if I need to do that.  Less certain about Windows.

However, if I use MPD (Music Player Daemon) I think I can send the signal to any machine which has a viable client (and I further believe those clients are available).  Though I am not already an expert in this area--read: rank amateur.

I do have all three OS's (Mac, Windows, and Unix) and I have considered FAT32.  There is some problem with larger drives, but usually once they are correctly formatted they can be seen and accessed by Mac and Windows:

[http://www.soundunreason.com/InkWell/?p=39](http://www.soundunreason.com/InkWell/?p=39)

Primarily though I am concerned with using Linux boxes to get the music from the server.

(My Mac is a laptop connected to wireless (different subnet) and rarely connected to wired.  I have a Windows server and my recording studio machine is Vista--neither of which will be playing music from the music server.)

That's not how MPD works, its not a streaming server.. With MPD the server is the machine playing the music, all the other can only connect to tell the server which songs to play. So with MPD you won't get any sound out of the other machines, only from the server. (of course you can use Pulseadio or Icecast or some other way to handle the audio streaming..)

Ext2/3 drivers are available for both Mac and Windows, I have both working although the Mac driver requires mounting the drives from command line, the GUI that came with the driver fails to work.

Also, I recommend using FLAC as the format instead of WAV, you'll save half of the disk space that way without losing anything in quality (as FLAC uses lossless compresssion).

There are MPD clients for both Mac and Windows, but, like I said, the clients are used to control MPD, not to play music.

---

### Post by jamesisin on 2009-01-06
mcduck - Hmmm... what you say about streaming is interesting.  I was involved in a thread here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6458815#post6458815](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6458815#post6458815)

I was under the impression it would be possible to use mpd to route a signal to another machine.  Perhaps through an intermediary?  If not, do you have a recommended solution?

As to flac, the trouble I run into then is my iPod(s) won't be able to decode them (to my knowledge).  I already run waves on them.

I'm less concerned with size now than I once was.  I can store my entire collection on a half-terabyte drive (more than 600 CD's) as waves, probably.  Surely though on a TB.  Regardless, I can be less concerned.  I think the buffer problem can be overcome on my local network (I wouldn't try streaming waves across the net just yet).

I will do a comparison of flac to wave file size here.


TransitMan - I would rather avoid any compression.  Doesn't seem to be any need for it any more.

---

### Post by mcduck on 2009-01-06
Yeah, MPD itself won't do what you want but Pulseaudio alows streaming audio between different Linux machines. And Pulseaudio is available for windows, at least, so that's something you could try.

The other alternative I mentioned is to use Icecast, which is basically internet radio server. That would allow you to use any music player app that supports web radio streams to listen to your music.

One important thing here is which ever way you go, when using MPD all machines will play the _same_ song at the same time. You can of course use any MPD client app to control what's playing but you can't play different songs on different computers (since the whole idea is that MPD is the player, the clients are just interfaces to control the player).

If you want each machine to be able to access same music library but play different songs, and to play the sound on that machine, not the server, some DLNA server would most likely be better for you. If playing the same song is OK for you then MPD combined with some solution to stream the audio  should work just fine.

---

### Post by jamesisin on 2009-01-06
> **mcduck said:**
> ...MPD itself won't do what you want but Pulseaudio alows streaming audio between different Linux machines. And Pulseaudio is available for windows...which ever way you go, when using MPD all machines will play the _same_ song at the same time.

If you want each machine to be able to access same music library but play different songs, and to play the sound on that machine, not the server, some DLNA server would most likely be better for you. If playing the same song is OK for you then MPD combined with some solution to stream the audio  should work just fine.

Ok, so MPD must then be combined with a streaming solution?  I guess that's one option.  I'm not clear why I couldn't have two instances of MPD running with each playing a different song (seems plausable), but I really don't mind since this is just about my local network (home) and I'm not likely to require more.

I found this (seemingly partial) list of possible candidates:

[http://www.rbgrn.net/blog/2007/08/how-to-choose-dlna-media-server-software-in-windows-mac-os-x-or-linux.html](http://www.rbgrn.net/blog/2007/08/how-to-choose-dlna-media-server-software-in-windows-mac-os-x-or-linux.html)

I recognized a couple of them.

Don't know anything about Icecast.  I suppose Rhythmbox could intercept an Icecast stream then?

---

### Post by mcduck on 2009-01-06
Yeah, Rhythmbox and pretty much any music player on any OS is able to listen to Icecast streams. It's commonly used for web radios.

Here's a short howto for MPD+Icecast2 on Ubuntu: [http://gashcrumb.homelinux.org/logahead/2008/09/04/mpd_and_icecast2_streaming_mini_howto]("http://gashcrumb.homelinux.org/logahead/2008/09/04/mpd_and_icecast2_streaming_mini_howto")

To get separate streams for each client machine with MPD would require not only running multiple instances of MPD, but you'd also need multiple instances of Icecast, and on every machine used for listening you'd need both MPD client running (to control the music) and some other music player (to listen to the stream).

With a file share, you'd only need the file sharing service running on the server, and any music player on the clients.

The purpose of MPD is pretty much opposite of this, playing music on a single machine but being able to control it remotely. Combining this with streaming makes sense, you get a web radio with remote control, but using it to play separate music for each client is simply making the task harder than what it really is when a simple file share would give you the same result.

edit: This solution might be closer to what you are looking for.. Music streaming server with web-based interface. Run something like this on the server, and on the clients you only need to open the servers address in any web browser and you can select what music to play and Edna will stream it to that computer like any internet radio. [http://edna.sourceforge.net/]("http://edna.sourceforge.net/")

---

### Post by jamesisin on 2009-01-06
Yes, my first thought was to simply create a file share / network drive on which to house the collection.  Maybe that's my best option after all.

The only issue I see with using a file server (and large wave files) would be buffer size.

---

### Post by jamesisin on 2009-01-07
Ok, I have now unsnagged number one (can't encode wave files for usual playback):

[http://ubuntuforums.org/showthread.php?p=6508604](http://ubuntuforums.org/showthread.php?p=6508604)

The whole thread has some very good conversations about encoding if that interests you (just start from the beginning).  Otherwise, the above link is the solution instructions.

---

### Post by jamesisin on 2009-01-09
mcduck - Well, I took a look at Icecast and did a sort of cursory review of the whole streaming media thing.  It seems to me that streams are compressed and using this method for local distribution won't fit my needs (though it'll probably come in handy when I decide to stream outside my network).  So I guess I'm back to using a simple network drive / file sharing option.

What did you download to access ext3 on Mac?  On Windows?  Do you recommend them?

---

### Post by jamesisin on 2009-01-09
Ok, we have run into snag number two:

[http://ubuntuforums.org/showthread.php?t=1035494](http://ubuntuforums.org/showthread.php?t=1035494)

I formatted a 500gb drive as ext3 and it has disappeared from the /dev directory.

---

### Post by jamesisin on 2009-01-09
Snag number two solved.  In the end it was a jumper problem.  Read about it at the link in my last post.

---

### Post by jamesisin on 2009-01-10
When Sound Juicer rips files, it places all the files for an album or boxset within a folder named after that album or boxset:

/MusicLocation/Artist/Album/

This works fine when it is a single album.  But when you are dealing with a double album or a boxset this creates a mess.

I wrote a script to help me rename the subsequent files in the following format:

D#.T# Song Title.flac

You can find my write-up (including the script) here:

[http://www.soundunreason.com/InkWell/?p=594](http://www.soundunreason.com/InkWell/?p=594)

---

### Post by mcduck on 2009-01-11
> **jamesisin said:**
> mcduck - Well, I took a look at Icecast and did a sort of cursory review of the whole streaming media thing.  It seems to me that streams are compressed and using this method for local distribution won't fit my needs (though it'll probably come in handy when I decide to stream outside my network).  So I guess I'm back to using a simple network drive / file sharing option.

What did you download to access ext3 on Mac?  On Windows?  Do you recommend them?

In windows I use this: [http://www.fs-driver.org/]("http://www.fs-driver.org/"). and on Mac I think it's this one: [http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/") although I'm not absolutely sure.

The Windows driver has worked great with no problems, so I can definitely recommend that one if you need to access Ext drives from windows. The mac driver kind of works but it's GUI doesn't so I need to mount the drives from terminal, not something you'd expect on OS X.. So it works but it's not great.

But you shouldn't need the ability to read Ext2/3 on client machines, the server does that for you even if you choose to go with simple file sharing. Just use a normal "windows" SMB share and all your machines should be access it without having to install any extra software.

---

