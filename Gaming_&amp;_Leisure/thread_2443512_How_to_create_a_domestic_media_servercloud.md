---
title: "How to create a domestic media server/cloud"
date: 2020-05-16
forum: Gaming &amp; Leisure
---

### Post by xeon-88 on 2020-05-16
Hi everybody!
Thanks to the pandemic I have way too many time to spend and I was thinking of doing something for my family. We discussed many times in the past how inconvenient it is to have all the various media (CDs, DVDs, ...) around the house and since I'm the "computer expert" in the family they asked me many times if there is way to share all that material in our private network. I tried to look around, but didn't find anything ready to use that satisfies my requisites, so I thought of setting up my own media server (I'm not even sure that's its correct name). Maybe you can point me towards the right direction. It's highly probable that the whole thing will require many different programs, so if you have only a partial solution, that would help nonetheless.

At the moment I managed to get my hands on an old computer, that should be just enough for what I have in mind. I just need to install Linux on it and configure it. And that's the first problem: which flavor should should I choose, based on the requisites below? I usually use Ubuntu MATE, but for this project I suspect Ubuntu Server would be better.

This is what I'm looking for:

[LIST]
[*]I should be able to upload files to the media server from my computer when I'm connected to the domestic network. Being able to do the same from outside is a plus, but it has to be secure. Uploading files should require authentication in any case.
[*]Every device connected to the local network should be able to see the list of shared files easily and either download them or receive them as an audio or video stream. It should be able to stream different files to different devices.
[/LIST]

Our network contains Linux, Windows and Mac computers, as well as smart TVs, smart DVD players and Android and iOS devices, so whatever comes up should be compatible at least with computers and smart TVs.
As I said I'm a "computer expert", not a computer expert, that means that I sort of know where to put my hands and how to use the terminal, but I don't know Linux that intimately.

Thanks a lot in advance for your interest and your help!
Xeon

---

### Post by SeijiSensei on 2020-05-16
There are a variety of ways to distribute media files, but the most widely supported is called DLNA.  Most "smart" devices like TVs know how to connect to a DLNA server.  I use the bog-simple **[minidlna]("https://help.ubuntu.com/community/MiniDLNA")** program, available in the repositories.  You need to edit one file, /etc/minidlna.conf, to point to the directories where the various types of media are stored.  It can handle music, video, and photos separately.  Android devices can use the Bubble UPnP client and MXPlayer to access files shared by minidlna.

Now on to your other concerns.

There's nothing fundamentally different between desktop and server versions of Ubuntu except the software that is shipped with each flavor.  The server edition has no GUI so you have to be comfortable handling everything from the command line.  If you're used to MATE, then I'd use that, and just install any extra software you need like minidlna.

You can share files with other machines using either NFS (for Linux/Macs) or Samba (for Windows).  Servers can run both an NFS and a Samba server simultaneously.  I do that so I can see my home directories on my server from either Linux or Windows.

I'd hold off on any sort of external connections until you have things running locally and have thought through the security implications of remote access.

---

### Post by QIII on 2020-05-16
I would echo the advice about external access until you move from "computer expert" to *computer expert.*

:)

---

### Post by ajgreeny on 2020-05-16
Just to add to what SeijiSensei said about minidlna, if you would prefer something with a GUI to configure and manage your media have a look at [Plexmediaserver]("https://www.plex.tv/media-server-downloads/") which I used until fairly recently and also [Emby Mediaserver]("https://emby.media/download.html") which I am now using and prefer over Plex.

Client apps for you to use will be more graphical with both Plex and Emby but not all platforms have client apps for those two servers, whereas DLNA clients are just about available on all platforms in one form or another; I tended to use VLC which has been my media player choice for a very long time, but I imagine there are many other choices available, it's just that I never bothered to search.

I never bothered to look into external access as I did not want to leave my computer running when not at home, but security is the most important factor to consider if you choose to go down that road.

---

### Post by xeon-88 on 2020-05-16
Wow, thanks everybody for the quick answers!

@SeijiSensei: DLNA was one of the keywords I was missing. Minidlna seems promising, easy to configure and to maintain, I'll give it a try tomorrow.
As for the server version, I thought it would be better because it should be already oriented for this kind of situations, and should be lighter on the computer, since it lacks the GUI, and more stable. I suspect the installation will be the most complicated part, but I'm sure it's such a standard process it's full of tutorials out there.

@QIII: I'm aware that an external connection can be dangerous, that's why that's why I want to be extremely sure it's safe before I try to implement it. But that's something that can wait, luckily. I won't need it in the near future.

@ajgreeny: I'll look into these two programs too. I'm not sure I need a GUI, since it seems VLC can handle the DLNA protocol so well, but it may be easier for the rest of the family.

One last question (I hope): Is there a way to access the server from my computer, via the terminal? I plan to leave the server without monitor, keyboard and mouse near the router, so being able to do some maintenance remotely would be wonderful (mainly periodic updates). I can assign the server a fixed IP address, if necessary. I think SSH is what I'm looking for, but I'm not sure how to use it and how to configure the server in order to accept my connection.

---

### Post by CatKiller on 2020-05-16
> **xeon-88 said:**
> One last question (I hope): Is there a way to access the server from my computer, via the terminal? I plan to leave the server without monitor, keyboard and mouse near the router, so being able to do some maintenance remotely would be wonderful (mainly periodic updates). I can assign the server a fixed IP address, if necessary. I think SSH is what I'm looking for, but I'm not sure how to use it and how to configure the server in order to accept my connection.

You're right that SSH is what you're after. By default all ports are open but no services are listening, so you shouldn't need to do anything apart from installing openssh-server. You may need to forward ports in your hardware firewall for access from outside your network. You may also want to do key exchange for verification rather than use a password. About half of my computers are headless and managed over SSH. JuiceSSH is good if you want to SSH from a phone.

---

### Post by xeon-88 on 2020-05-17
Thanks CatKiller, I'll look into key exchange.

I have a doubt on the various DLNA software suggested above. Where are audio and video codecs needed, on the server or on the clients? That can be a major problem particularly on smart TVs, that seem to be stuck at mp3 and avi formats. That would create a bit of a problem, since I have already converted part of our multimedia collection to more modern formats, mainly flac and mkv, and I'm not sure they can be read on every smart device.

---

### Post by Tadaen_Sylvermane on 2020-05-17
There are a number of ways to accomplish this. I use straight NFS shares with central mariadb databases and Kodi as my front end. Main server is Ubuntu 18.04 running headless right now. It is very easy to navigate with a 10 foot interface that you can use an app on your phone to control. Currently have 4 machines in use regularly. As I understand it you can use Firetv sticks for this, but I use older low power machines for my clients. I don't do anything > 1080p though. If you have 4k stuff then your clients will need to be able to run it. Wired networking a plus. The nice part about this method is you can use it as a linux desktop as needed with a wireless mouse & keyboard. My wife uses the living room tv to play minecraft all the time.

---

### Post by CatKiller on 2020-05-17
> **Tadaen_Sylvermane said:**
> It is very easy to navigate with a 10 foot interface that you can use an app on your phone to control.

If you have the right hardware you can use your TV remote control to navigate it, too, through HDMI-CEC. Kodi is great.

---

### Post by xeon-88 on 2020-05-17
> **Tadaen_Sylvermane said:**
> I use older low power machines for my clients.
That would be complicated at the moment. In general I'd like to avoid installing specialized hardware or software on the devices, except for phones and tablets. Everybody should already have VLC, so computers should work fine. I'm concerned about TVs, I've had really bad experiences with how they handle audio and video formats.

---

### Post by CatKiller on 2020-05-17
> **xeon-88 said:**
> I have a doubt on the various DLNA software suggested above. Where are audio and video codecs needed, on the server or on the clients? That can be a major problem particularly on smart TVs, that seem to be stuck at mp3 and avi formats. That would create a bit of a problem, since I have already converted part of our multimedia collection to more modern formats, mainly flac and mkv, and I'm not sure they can be read on every smart device.

Part of the DLNA specification is negotiation of capabilities, so both ends of the connection will say which formats they can do. If the player can handle the file as it is, the server will stream it over the network; otherwise, the server can transcode the stream to something else. Transcoding means that the stream will need more bandwidth, and will put more load on the server, but is generally painless: my PS3, which barely followed the specification, was the only thing I've used that was finicky about formats.

AVI and MKV are just container formats: the important part is how the stream is encoded; widespread encodings like those used for DVDs, Blu-Ray, and YouTube, tend to be hardware-accelerated in consumer hardware, so those are generally easiest to get working without transcoding.

---

### Post by SeijiSensei on 2020-05-17
My LG TV supports MKV files, and my Roku supports MKV file with ASS subtitles as well.  (I complained about subtitle support to Roku, and sometime thereafter suppot for ASS files was improved.)  They show up in the closed-captioning box with no font stylings.

Not all TVs are as forgiving. Sony's seem limited to files in the MP4 container with AAC or MP3 audio.  I've converted (with ffmpeg) a few shows to that format to share them with friends who just want to plug in a USB stick and start watching.

Tried checking to see if my TV supported FLAC.  It does fine with music tracks in that format, but all my video files that use FLAC use other technologies that aren't supported (H.265, 10-bit color, etc.).  It also seems to barf at 1080p BD rips, but handles 720p rips fine.

Most of the time, though, I watch files on my server over the network on a computer that's connected to my TV.  I simply mount the video and music shares with NFS, then run appropriate software on the client computer like SMPlayer + mpv.

---

