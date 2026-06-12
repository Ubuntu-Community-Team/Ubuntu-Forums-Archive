---
title: "Music sharing issues"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Kashirigi on 2006-09-22
I'd ideally like to share my music from my desktop computer to my laptop. To whit, I've installed banshee (+daap) (and rhythmbox)  avahi-daemon, avahi-discover, zeroconf,libnss-mdns, avahi-dnsconfd and probably some more.

I'm almost there. I can now see the share names, but I can't see the songs themselves (similarly when the desktop is running iTunes in windows). I've configured ports 5353 and 3689 (but this happens even when I disable the firewall(or, at least turn of guarddog, which may not be the same thing, I suppose)). I can, however, see the songs when, say, I have Rhythmbox and Banshee open on the same machine.

I'm at a loss, and I'm tired of banging my dead against my desk.

I would be eternally grateful for any help you can provide (and I'm sure it would also help with my Samba problem, which is similar.

---

### Post by mc79 on 2006-09-24
I am having the same problem.  I would be interested if you have found a solution.

In Rhythmbox, I can see shared libraries, but I cannot see the tracks shared within them.

I can also share my library, but on my Windows machine, I see the share, but not the tracks.

This also seems to be the case with Banshee.

---

### Post by compuguy1088 on 2006-09-25
What version of iTunes are you using, because apparently, with the release of iTunes 7.0, they changed the DAAP standard slightly, making it impossible for a 3rd party client to connect to a iTunes Share [http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol]("http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol")

---

### Post by mc79 on 2006-09-25
Oh, ok, I'm using iTunes 7.  That makes sense.  thanks for the info.
As soon as someone finds a workaround, please pass it along.

---

### Post by Kashirigi on 2006-09-26
> **mc79 said:**
> Oh, ok, I'm using iTunes 7.  That makes sense.  thanks for the info.
As soon as someone finds a workaround, please pass it along.

However, I'm not using iTunes -- I'm using Banshee (and or rhythbox or tangerine or whatever) between two Dapper machines. I still can't see any songs, although I can see the shares. It doesn't matter if my firewall is up or down.

If anyone has any hints, however tenuous, as to where I should be looking, please feel free to suggest them.

This is such an irritating problem because as far as I can tell I'm the only person who has this problem. No error messages, no nothing. It's almost enough for me to switch back to Windows. I'm sick to death of "install banshee-daap and it just works" when clearly it doesnt.

---

### Post by Kashirigi on 2006-09-26
Now here's more. . .

When I try to ping my laptop, I get this, which is clearly nothing:


ping Gernsback.local
PING Gernsback.local (172.16.1.20) 56(84) bytes of data.

--- Gernsback.local ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10030ms


Something (everything) is not getting through, although I can obviously resolve by name. Any ideas on where I could look to find out what's happening?

---

### Post by amoore on 2006-09-27
Howto RhythmBox 0.95 Album Art & Daap (share songs)

[http://www.ubuntuforums.org/showthread.php?t=201362]("http://www.ubuntuforums.org/showthread.php?t=201362")

---

### Post by Kashirigi on 2006-09-28
It turned out that my problems had very little to do with avahi and everything to do with firewall configuration. I was using guarddog, and had opened all the ports (theoretically) required, or so I thought. I purged my iptables, installed firestarter, reconfigured, and I was off and running.

As far as I can tell, I opened the same ports using guarddog and firestarter, but one works and one doesn't. Such is life, I suppose.

Of course, switching to firestarter screwed up my VPN, but that's subject best left to my HOWTO!

---

### Post by mc79 on 2006-12-17
I'm still having some sharing problems.  
To recap:  I have a WinXP box running iTunes 7 with sharing on.
I have an Ubuntu Box running Rhythmbox that can see the share on the XP box, but does not see any of the tracks within that share.

If I share tracks from Rhythmbox, I can see them in iTunes. 

Seems strange that it's working in one direction, and not the other.  Any ideas on this?  I believe I've disabled any firewalls in the way.

---

### Post by Falcorian on 2006-12-21
iTunes 7 will not share with anything but iTunes 7. It will read fine from other sources, but it won't allow others to read from it.

Just Apple telling you how to use your computer. ;)

---

### Post by mc79 on 2006-12-23
Has anyone tried getting around this with [Firefly]("http://www.rokulabs.com/support_sb_dwnld_firefly.php")?

---

### Post by cam_tram on 2007-01-28
Firefly (mt-daapd) works for me, it just doesn't share copy protected music.

---

### Post by MaXqUE on 2007-02-11
> **compuguy1088 said:**
> What version of iTunes are you using, because apparently, with the release of iTunes 7.0, they changed the DAAP standard slightly, making it impossible for a 3rd party client to connect to a iTunes Share [http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol]("http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol")

Most of these complaints are about music purchased in the iTunes store and so are bound ccontractually by the agreements Apple has with the Major Lables. I've not made the mistake of purchasing any music from any online music store other than mail order CD's.

Time and again Apple is blamed for the requirements placed on them by the Major Lables. Sometimes I wish Apple would simply close the iTunes store and be done with it. Apple is taking far to much heat for the evil imposed by the likes of the RIAA.

iTunes is not a streaming music server, it is a music jukebox meant for use on a personal computer.

There are free and open source streaming music servers available already. Why aren't people using those?

I used to use a second mac to share my own iTunes library until I realised there as really no need for the second iTunes application. All I had to do was add the remote tracks to my own iTunes library locally and iTunes would fetch the tracks over the network. That way iTunes would have no idea how many other iTunes clients were also accessing the tracks.

Cheers,
MaXqUE

---

### Post by shagnthings on 2007-02-18
This is strange.  I'm able to see my banshee music files in itunes 7, but not able to see my library in banshee??  Because I can see the share name I don't think it has anything to do with the firewall....I think it's itunes.  consensus?

---

### Post by MaXqUE on 2007-02-22
hello again:

There's one thing that isn't clear to me here; that is are you expecting to see the actual files the songs have been encoded to or are you expecting to see what iTunes tells you is in the music library?

I have despensed with using iTunes to see remote song libraries even when I am using plain 'ole OS X with iTunes. I simply add the files to my iTunes library locally.

Other programs should do the same. I mount the remote share and let iTunes or Banshee or Rhythmbox think they are local files. Since this is a LAN whicih you have complete control oif .. the only questions are networking ones. Can you mount the remote share, can you read and write to the shares when you need to?

The only other thing it could possibly be is that somehow the file type with its extension are being rendered invisible by one or the other operating systems.

BTW... I have done this myself. I've put .m4a files on a Linux box with Netalk runing and used those shared files in iTunes with no problem at all. The only problems I ran  into were with Netatalk.

Cheers,
MaXqUE

---

### Post by mc79 on 2007-02-22
I am reasonably content using Firefly to share my iTunes library.  It won't work for DRM stuff, but I can deal with that for now.

Thanks for all your help.

---

