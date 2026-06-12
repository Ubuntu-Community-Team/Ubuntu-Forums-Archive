---
title: "gnome file transfers fail without notification"
date: 2009-04-05
forum: Desktop Environments
---

### Post by CAsurfer on 2009-04-05
I just tried to transfer about 100 GB across a network using nautilus on Intrepid. I had one nautilus window open with the local directory, one with the remote (ssh) directory, and I dragged and dropped the files from the remote directory to the local directory.

When I came back 9 hours later, the transfer was done. But NOT ALL of the files had been copied, and there was NO ERROR MESSAGE indicating I might be missing files.

So the gnome file transfer failed silently. If I hadn't thought to compare the directories, I could have lost considerable data (I'm wiping the remote directory).

Has anyone else noticed this?

---

### Post by WatchingThePain on 2009-04-05
Hi, that's a lot of data.
I have not personally experienced it but it's a pretty bad thing to happen.
Here's a guess..it's to do with how Icmp has been set up (on their side)?, because that's what would send you a message.
What's your ping rate like?.
I imagine there should be a log of the transfer somewhere which might help.

---

### Post by CAsurfer on 2009-04-06
The server is on my local network, administered by me, running vanilla Hardy Heron. I didn't touch the OpenSSH configuration on the server beyond installing it via apt-get. 

In other words, everything is at default. Yet I still get silent failure. This strikes me as a serious bug.

WatchingThePain, to answer your second question, the ping is understandably quick, since it's all local.

---

