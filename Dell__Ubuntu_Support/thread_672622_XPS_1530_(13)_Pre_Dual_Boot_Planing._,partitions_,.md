---
title: "XPS 1530 (13??) Pre Dual Boot Planing. ,partitions ,installing"
date: 2008-01-19
forum: Dell  Ubuntu Support
---

### Post by Omnios on 2008-01-19
Hi I have read some other posts pertaining to Dual booting DElls XPS Laptops, From what I have read so far it seems to be fairly easy except for some self destruct warnings. Anyways I am not at that stage yet and going to do some really in depth pre Vista / K/Ubuntu planning. 

1:  K I have 2Gigs of ram and am wondering if there are any advantages to having a swap partition with this amount of ram. 

2:I have a 160 Gig hard drive and there is a 10Gig recovery partition within the 160G

3: Wanted and or needed partitions.
 : First as I am new to Visa I carefully need to know how much space I need for Vista as it seems a bit way off compared to XP.  Its already got 39Gigs on without a lot stuff installed. On the other hand Vista will just be sitting there for IE and for gaming. 

4: I also need to calculate how much space I need for the Ubuntu / mount as I intend to install a lot of stuff like music samplers, graphics and cad stuff.

5: I am planning on making a large ext3 partition to mount as home and also to act as the mount point for My Documents with  iExt2IFS,exe in Vista. I also want to try another trick if it will work. Being that the /home, My Documents is shared I want to put fake drive for wine there and also have it so I can run the files in Vista. This is mainly for upgrading as there are some broken upgrade features and this would bypass this. For example to play Anarchy line and upgrade it you currently have to run it in windows, upgrade it and copy it to the wine directory.

6: looking into swaping the 10G recovery to an external. I have a unused 40G drive lying around and thinking of slapping it into a external encloser if this is possible.

7: As for the media direct button I have read you can hack it to do something else so I might change it to launch Myth TV or some media stuff.

 Also I have my old P4-1.6Gz tower which has 512megs ram right now. It also have a ATI TV wonder pro with remote in it. I did a little researching and found out that with Myth you can use the tower with the tuner as a server and install a client in another computer to watch it remotely. I am also playing around with using the tower as a file and media server. I can currently play music on the laptop that is on the tower with no problem. I have not tried video yet but will give that a go. I am also looking into streaming if it has any advantages as compared to playing the file from the server. 

 I found a music management program called Cactus Jukebox witch manages the music with a data base and this is supposed to be really quick and have a low load on the system even with huge music storage. Just have to figure out how to use it as a remote. 
 
 I did a lot of thinking and think it will be better to use the old tower as a media and file server as apposed to putting all my files on the laptop. 

 I am also looking into a remote download server so I can use the file server to download programs and burn DVD's etc so I can still use my laptop while doing so. Sort of like a Nicotine remote downloader so I can say play a game while it does its work. 

 Anyone have any suggestions.

 Ps my lappy came with Media Center and I am not impressed.

---

### Post by jerrylin on 2008-01-20
1. The swap partition allows your operating system to extend the working memory. So if you load 3gb of data, 1gb or more will be sitting on the swap partition. I not sure your linux computer would work if you don't have one (never tried!)

---

### Post by Omnios on 2008-01-20
> **jerrylin said:**
> 1. The swap partition allows your operating system to extend the working memory. So if you load 3gb of data, 1gb or more will be sitting on the swap partition. I not sure your linux computer would work if you don't have one (never tried!)

 Hi from what I have read if you have a lot of ram you can go without a swap section. But wondering if there can be problems. Better safe than sorry.

 K forgot to ask something. I have a 160Gig drive that has a 10G recovery partition on it. I am wondering if it is possible to swap this partitions contents to either a external drive as I have an old 40G I can slap into a external box. Also thinking of putting it on my future file server but if I need it will I be able to use it as such. Another option might be to swap it to a large external usb bootable. I really want to free up this 10G partition,

---

### Post by kesomir on 2008-01-20
I have run ubuntu since 6.06, debian, suse and fedora on both desktop and server machines with between 1gb and 8gb RAM without any SWAP.

Never had a problem doing so.

It's my opinion that SWAP (slow as it is) is only useful for very short term use. Not having the swap means that everything in ram is fast ofc. If a server hits swap as a necessity,it's my experience that it'll thrash itself to death in short order.

I think that SWAP may be used to offload things from ram that are not being accessed currently, but with gnome / kde desktop using ~200mb of ram. I've only ever filled 2gb on a desktop when doing  intensive hard drive writes (file copies).

For desktop application use - I usually sit around 600MB running gnome and a few applications.

I run mostly apache - gimp - openoffice.... have run blender too. No probs without swap.

YMMV.

---

### Post by jerrylin on 2008-01-20
By having a swap partition, you are not slowing down your system. As far as I know, linux will only go to swap if it has to (and keeps data in RAM if it can).

After looking at how linux deals with this... it does indeed seem better to NOT use a swap partition. When your ram fills linux 2.6+ will actually utilize swap files in your active partition (which are more versatile).

---

### Post by T-MAN3000 on 2008-01-21
For the music management, I suggest you take a look at mpd. It's, like the name says, a Music Player Daemon, it also uses a database, and the good thing is, you can choose from a multitude of front-ends. That includes windows and mac and even web-based ones. The frontend I use atm is Sonata. 
In this way you play your music from the fileserver, so you don't have to stream or transfer them to your laptop everytime you want to play them. 
btw, MPD can also output as an icecast or shoutcast stream. 

Unfortunately there is no daemonized version of Nicotine, so you either you could try X over ssh (although I didn't manage to get it working...) or you could run Nicotine local and have the share/incoming directories mounted with sshfs or nfs.
For bittorrent or the emule network you have wide choice of daemonized clients.

As for your space requirements: even if you plan to install a lot of apps, 10G should be more than enough if you have a separate home partition. I very much recommend that, because in that way you can keep your settings when you reinstall your system.

Your recovery partition: why don't you wipe it altogether? Probably it will completely destroy your ubuntu installation when you use it, negating the intended purpose: a quick restore when things go awry.

That's all, hope it's useful to you

---

### Post by Omnios on 2008-01-21
> Your recovery partition: why don't you wipe it altogether? Probably it will completely destroy your ubuntu installation when you use it, negating the intended purpose: a quick restore when things go awry.

That's all, hope it's useful to you

 This is a 10G partition and currently there is about 5 Gigs used. The win backup is probably a problem. How ever Dell shares this partition with win backups and also dome dell recovery stuff which looks about 3G or so. I am thinking it might be possible to swap it to a 4gig booteble usb stick and have that ability in case every gets fraged aka vista etc.

---

### Post by ArtDeco on 2008-01-21
Not sure where to post this, but I Installed fiesty from live cd on a cheap new Dell 1501 with nothing but vista and some ads on it  and I accidentally wiped out windows vista during the install - I really wanted to make a dual boot pc - is it too late to install windows once unbuntu is installed and running?


:(

---

### Post by Omnios on 2008-03-01
> **ArtDeco said:**
> Not sure where to post this, but I Installed fiesty from live cd on a cheap new Dell 1501 with nothing but vista and some ads on it  and I accidentally wiped out windows vista during the install - I really wanted to make a dual boot pc - is it too late to install windows once unbuntu is installed and running?


:(
 The problem is not Ubuntu the problem is grub so if you reinstall Windows it will write to mbr and you will not have grub installed. I tried manually reinstalling grub with the alternative installer and ended up nuking my Ubuntu install once and have not played with that after that. (was following a how to lol)

---

### Post by Omnios on 2008-03-01
K played around with the Ubuntu Live CD and also the Kubuntu live CD. I think I am going to be using Kubuntu in the laptop as its more tweekable for the 1280 res. Getting a better feel of what space is needed. Read that the min partition for xps dual set up should be 40G  as per a how to. That how to stated that media direct was working on his system.  

 K serious question. What the hell is media direct and if it uses windows media center I do not want it lol. Myth TV would be nice though.

---

### Post by Omnios on 2008-03-14
Hi k still thinking and planning and right now am looking into installing a old xp-home oem upgrade I had on my old tower and dual booting with that. I found a lot of games will not play on vista such as the Delta Force series. 
 
 The big point here though is I have been trimming vista here and there and got it down to about 32gigs with a few games and demos and about 2 gigs for backup. 
 
 The bit thing here is with XP 30gigs would would be with a hole lot of stuff installed as I intent to use a seperate /home partition also for documents.  So generally I would be able to make a Xp partition about 20Gigs with a hole lot of stuff loaded.
 
 If I could install games to the /home partition within wine virtual drive things will be even better. 
 
 I could also possibly do the same with vista but I think its still to bloated to be sitting there jsut to play games.
 
 Any suggestions?

---

