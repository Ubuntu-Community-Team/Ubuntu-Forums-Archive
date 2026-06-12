---
title: "Playing media files over network"
date: 2006-02-09
forum: Desktop Environments
---

### Post by martymart on 2006-02-09
I have all of my music and movies on a windows file server. I can play the media over my network on a windows machine fine (no stuttering etc). On my ubuntu computer (totem) the movies will buffer for about 7 seconds then start to play but after about 15 seconds the movie catches up with the buffer, the movie then stops and buffers for 7 seconds before playing again and the cycle starts again; stop, start.
Is this something to do with the way they are mounted? I mount them using the connect to server gui tool.
Or is it something I need to set in totem or gnome, ,gstreamer etc?
Is there a media player more suited to this type of use?

Thanks for your time and help.

Martin

---

### Post by rado_london on 2006-02-09
I am not sure for the exact configuration structure for totem,but basically you need to set it up to cache the whole file before playing it. I use the same thing with MPlayer and I dont have any problems.

Good Luck

---

### Post by dickohead on 2006-02-09
I ahve samba mounted file shares on a 100mpbs cat5 network, I play DVD quality movies across the network and have never experienced lag of any kind, even when other users are using the same movie file! Perhaps your machines are connected with a hub rather than a switch? Or maybe you're only running 10mbps network cards?

---

### Post by martymart on 2006-02-10
Ok I got it sorted out now, thanks for the help. I simply had to mount the shared files using samba. I had to install samba and smfs using apt-get and followed the instructions at [http://ubuntuguide.org/](http://ubuntuguide.org/).

Now all my moves play like a dream over the network which consists of several 10mb wired comps (one of which is the windows file server) and a wireless one connected to the same router. The wireless comp is the one that I am streaming moves to, so the wired 10mb is fast enough and so is the 22mb wireless.

Thanks for the help 

Martin

---

### Post by joselin on 2006-02-10
Additionally you can stream all your media files through your browser. The main advantage is that you can use it in and out your network.  
  
This is only one program that allow you to do it. [http://www.jinzora.com/]("http://www.jinzora.com/")

---

### Post by chris2028 on 2008-02-13
i have similar issue here.
but I can't even play movie media over windows network.

i must have done something to it.
it seems is a network issue

when i play movie media over network using totem.
it come out an error message : There is no input plugin to handle the location of this movie 
if i use other media player, it simply just do nothing.

mp3 file, is fine... with Rhythmbox...

:(
but i can play those file after I copy it to my local drive.~!!!

---

### Post by KCPokes on 2008-02-13
> **joselin said:**
> Additionally you can stream all your media files through your browser. The main advantage is that you can use it in and out your network.  
  
This is only one program that allow you to do it. [http://www.jinzora.com/]("http://www.jinzora.com/")

For music only you can look into Ampache as well (ampache.org).  I find it far more stable then Jinzora, but doesn't handle videos.  Then again, I didn't find Jinzora stable enough to do movies anyway, unless I was on a local network.  At that point I'd just assume play them via network drives.  That said, it is a good idea using Jinzora or Ampache.  Both are great concepts.

---

### Post by KCPokes on 2008-02-13
> **chris2028 said:**
> i have similar issue here.
but I can't even play movie media over windows network.

i must have done something to it.
it seems is a network issue

when i play movie media over network using totem.
it come out an error message : There is no input plugin to handle the location of this movie 
if i use other media player, it simply just do nothing.

mp3 file, is fine... with Rhythmbox...

:(
but i can play those file after I copy it to my local drive.~!!!

You will need to have the samba share mounted, not just connected.  Most players will give you the error when trying to connect to a drive that is mounted with smb://.  Mount the drive using smbfs or cifs, and I believe that it'll resolve your issue.

---

### Post by chris2028 on 2008-02-13
> **KCPokes said:**
> You will need to have the samba share mounted, not just connected.  Most players will give you the error when trying to connect to a drive that is mounted with smb://.  Mount the drive using smbfs or cifs, and I believe that it'll resolve your issue.



I did the following HOW-TO ---------------- appear not working ........... somehow.
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I think i know why I am not able to mount the network drive........
because my share name has space on it.
therefore.... it keep giving me an error message....... location not found.

I am looking for more information on the net.
please refer me any~~!!

many thanks.

---

### Post by chris2028 on 2008-02-13
> **chris2028 said:**
> I did the following HOW-TO ---------------- appear not working ........... somehow.
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I think i know why I am not able to mount the network drive........
because my share name has space on it.
therefore.... it keep giving me an error message....... location not found.

I am looking for more information on the net.
please refer me any~~!!

many thanks.



O ye~~~!!

I did it.

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

---

### Post by s21825 on 2008-02-14
I was also having the problem of Totem not playing files of a smb mount. I installed smbfs and followed the instructions here:

[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

Now it plays videos perfectly over the network.

---

### Post by psypher on 2008-03-27
May I ask WHY totem cannot play media files over a smb share without mounting it? Linux will never be accepted as a easy to use desktop for non technical users if a simple thing as browsing a network share OR using the built in "Connect to server" function cannot do something as simple as play a media files seamlessly. I have other issues with mounting shares like when your network connection drops and you have to manually unmount ALL your samba shares and remount them or you won't be able to use nautilus till you do. Or the fact that your samba passwords have to sit unencrypted in a file somewhere on your machine. I'm sorry to say this but this is not acceptable. I researched this bug a little and it led me to ridiculous "bug reports" where the bugs were marked as fixed when there was no "fix" done at all. Is this problem totem related or ubuntu related? Also please don't tell me to use another media player. totem is an excelent media player, the shortcut keys and mouse controls are easy and intuitive, my laptop's media control button's seem to only work with totem out of the box, I LOVE the features of totem. And it's the default media player. I reckon it's the best media player I have ever used. I only use VLC or mplayer when I absolutely have to due to some weird codec which is only 1% of the time.

Why then does it not play media files when using smb:// or the "Connect to server" feature??

---

