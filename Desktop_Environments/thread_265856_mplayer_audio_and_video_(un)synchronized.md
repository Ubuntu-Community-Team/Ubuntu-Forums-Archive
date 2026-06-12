---
title: "mplayer audio and video (un)synchronized"
date: 2006-09-26
forum: Desktop Environments
---

### Post by crash0 on 2006-09-26
Hello,

I have a problem with MPlayer: when I play some movies, the video part goes slower than the audio. Sometimes it's just a second or less difference, sometimes it's more than half a minute difference, sometimes it seems totaly synchronized.:-| 

My MPlayer history: when I installed MPlayer (with "Add/Remove") on my new Dapper Drake installation, this synchronization problem occoured when I'd watch any movie, and it was a large difference (video would be about 3-4 times slower than the audio). Then I uninstalled MPlayer with "Add/Remove" and tried to install it manually from SVG, as instructed from a tutorial on this forum. It didn't work, so I canceled that and installed MPlayer the same way I did it before.

Now, as I said, this unsync problem appears only when I watch some movies, it seems to me that it happens only when I watch Xvid movies and some Divx.

I tried to choose different audio and video codecs from the preferences, but only a few combinations work and they make no difference. What codecs should I choose?:-k 

Also, Totem works much worse than MPlayer, I can't use it to play almost anything... On my previous Ubuntu installation (Breezy), MPlayer worked just fine until a few days before I formated my disk. I'm not 100% sure, but I think that these problems started just after an updated.

Any help would be very appreciated :???:

---

### Post by doobit on 2006-09-26
> **crash0 said:**
> Hello,

I have a problem with MPlayer: when I play some movies, the video part goes slower than the audio. Sometimes it's just a second or less difference, sometimes it's more than half a minute difference, sometimes it seems totaly synchronized.:-| 

My MPlayer history: when I installed MPlayer (with "Add/Remove") on my new Dapper Drake installation, this synchronization problem occoured when I'd watch any movie, and it was a large difference (video would be about 3-4 times slower than the audio). Then I uninstalled MPlayer with "Add/Remove" and tried to install it manually from SVG, as instructed from a tutorial on this forum. It didn't work, so I canceled that and installed MPlayer the same way I did it before.

Now, as I said, this unsync problem appears only when I watch some movies, it seems to me that it happens only when I watch Xvid movies and some Divx.

I tried to choose different audio and video codecs from the preferences, but only a few combinations work and they make no difference. What codecs should I choose?:-k 

Also, Totem works much worse than MPlayer, I can't use it to play almost anything... On my previous Ubuntu installation (Breezy), MPlayer worked just fine until a few days before I formated my disk. I'm not 100% sure, but I think that these problems started just after an updated.

Any help would be very appreciated :???:

Video/audio playback is very resource intensive, and the different codecs handle their jobs in different ways. Choosing a different codec will make no difference on playback because the player can only use the codec to play back the video that was used to compress it when it was authored. The only thing you can do to improve performance is to try different players and try to give the player as much of your computer's resources to play back as possible. This means stopping any background processes, and other programs that you don't need when you play the video, making sure DMA is enabled on your hard drives, and that your hard drives are not too full, that you have sufficient memory (512 MB minimum) and swap space, and anything else you can think of to speed up the machine. Also, if the video file is very large and your CPU is very slow, then you may find it impossible to play back the video with much success.

---

### Post by Naegling23 on 2006-09-26
mplayer requires you to manually set the sync between audio and video, use the + and - keys to do this.  For my system its -200ms.  The problem is that you have to set this each and every time you start mplayer.  Very very annoying.  I found a simple work around that I have not seen posted anywhere, but seemed to work for me (after throwing a fit, banging my head against a wall, and yelling at forum people, I eventually figured it out).  Under your home/.mplayer directory are two text files.  One of these lets you add custom options for when mplayer starts up.  Unfortunatly Im at work right now, and I cant remember off the top of my head the exact command.  When I get home, I will try to post exactly what I wrote.  It is something like delay="-200" 
Once you add the command, you save it to the file and it will be set when mplayer starts up.  (bonus is that it will sync the audio and video in the firefox plugin as well!)  Hopefully this can solve your problem, it drove me to madness.

---

### Post by crash0 on 2006-09-27
thank you both for yor suggestions... 

@doobit: I have only 256 mb of memory, insufficient disk space and I don't know if DMA is enabled and how to enable it. Still, there are two things why I don't think this would change anything:
1. I had 256 mb of memory on Breezy (it's the same comp) and it worked.
2. Even when I had enough disk space (just after installing Dapper) it didn't work

@Naegling23: I'll try to find something regarding that on the net until you post it... Thanks

---

### Post by kwalo on 2006-09-27
Have you tried -framedrop option in mplayer? It should keep your audio and video synchronized. Try in command line```
mplayer -framedop <some movie>
```If it works, you can add```
framedrop=yes
```option to your ~/.mplayer/config file (create one, if it doesn't exist).

---

### Post by doobit on 2006-09-27
> **crash0 said:**
> thank you both for yor suggestions... 

@doobit: I have only 256 mb of memory, insufficient disk space and I don't know if DMA is enabled and how to enable it. Still, there are two things why I don't think this would change anything:
1. I had 256 mb of memory on Breezy (it's the same comp) and it worked.
2. Even when I had enough disk space (just after installing Dapper) it didn't work

@Naegling23: I'll try to find something regarding that on the net until you post it... Thanks

I wanted to respond to this for the benefit of others, so here goes.
What @Naegling23 recommended may help you because it compensates for whatever the latency difference is between your audio and video busses, which usually remains consistant - until you change something.

Breezy is somewhat lighter on system resources than Dapper is. There doesn't need to be much difference between a system that seems to run smoothly and one that doesn't. Disk space is only part of the equation and only affects EIDE drives as the seek speed slows as free drive space goes below 40% or so. The size of the video file you are trying to run, and the free memory, and the CPU speed will affect it too.

---

### Post by Naegling23 on 2006-09-27
After rereading your post, I dont think my technique is what you are looking for, it seems your system is struggling to keep up with the video, and is causing it to drop out of sync.  The framedrop might be what you need.

However, I'm going to post my answer anyway.  If someone is searching the forum, it might solve their problem (I wish I would have found it when I was searching)

/home/naegling23/.mplayer  (obviously replace naegling23 with your user name)

open the config file

It should say something like this along the top
# Write your default config options here!

add this line underneath

delay="-0.2"

for my system, I need a -200ms delay in the audio, put whatever you need for your system inside the " "

save the file and start up mplayer, if you hit + or -, it should be centered around your delay time.

---

### Post by crash0 on 2006-09-28
> **kwalo said:**
> Have you tried -framedrop option in mplayer? It should keep your audio and video synchronized. Try in command line```
mplayer -framedop <some movie>
```If it works, you can add```
framedrop=yes
```option to your ~/.mplayer/config file (create one, if it doesn't exist).

thanks, it works :D

it looks a bit buggy now, but it'll do... now i'll try to free some disk space and perhaps get more ram memory to make it a bit smoother...

---

