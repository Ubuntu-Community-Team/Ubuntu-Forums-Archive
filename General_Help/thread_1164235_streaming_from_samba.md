---
title: "streaming from samba"
date: 2009-05-19
forum: General Help
---

### Post by c0nfusedami on 2009-05-19
I just installed samba so that i could share my files over my local network and was wondering if it was possible to play video files directly off of the network without transferring it over. When I tried doing this it seemed to freeze up and wouldn't play the file. Is this me or samba?

---

### Post by Psycho.mario on 2009-05-19
Did the video freeze up or the actual computer?

---

### Post by c0nfusedami on 2009-05-19
I got the video to run on the computer I was streaming it to for about 2 seconds then it froze

---

### Post by Psycho.mario on 2009-05-19
That's your internet connection, if you were streaming something like a movie, your OS was probably downloading to the local computer so it could be played faster. I don't think samba is the best for streaming video. Maybe mythtv or something? Im not really sure though, iv only tried streaming with samba and the same happened to me that happened to you.
Well, thats what i think, Im sure some Ubuntu guru will prove me wrong.

---

### Post by c0nfusedami on 2009-05-19
I haven't really played around with mythtv because I thought it was more like a specialized os meant to record and play back video on a tv not to stream it.

---

### Post by paradigm2 on 2009-05-19
Sshfs [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

seems to work very well for me with native linux machines and it is much more secure (ssh encryption) than samba.  I believe there is also a port for windows, though  am unsure of how well it works.

I mount the remote filesystem in /ets/fstab and then use it just like a local directory, including for music and playing videos.

---

### Post by anjilslaire on 2009-05-19
Samba works just fine for streaming video across a LAN, I do it daily. MY linux box is my media server, feeding laptops and xboxes running xbmc movies and music throughout the house.

---

### Post by c0nfusedami on 2009-05-19
maybe my internet is just clogged up with other programs i have wireless n i'll try closing out of some of my bittorrent applications and my second computer is a mac so i don't know if sshfs will work on that

---

