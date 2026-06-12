---
title: "What do you think the 'executable path' is?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by dpaint4 on 2006-08-02
I'm using gnormalize to transode some of my old FLAC files to Vorbis. I also have some Musepack files, and gnormalize supports MPC, so I have the binaries I need from Musepack.net and I'm trying to place them someplace where gnormalize would like them to be.

But gnormalize just gives the error that they're not in 'the executable path'.

I've tried moving them to /usr/bin, /bin, /lib, and /usr/lib. These are places where other codecs I use are installed and recognized.

What would be a good educated guess as to what gnormalize wants me to do with these binaries.

I have had this working before in Dapper, but I don't remember where I finally ended up putting them. But at least I know I have the right binaries.

Notes : starting gnormalize from the terminal gives no useful information, and neither does the website. Just to head off those particular suggestions.

---

### Post by dpaint4 on 2006-08-02
It was /usr/bin as I thought from the start, but I forgot to change the permissions of the binary before I moved it. I'm responding in case anyone ever searches this and has made the same error.

I had to give myself permission to execute before moving the binary to /usr/bin.

---

