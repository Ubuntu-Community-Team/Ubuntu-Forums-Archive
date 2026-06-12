---
title: "How to run X headless?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by puke on 2006-09-11
Hi,

I want to run X headless on Ubuntu.  I don't want it using any physical display, but just be able to connect to it remotely.  How do I achieve this?

---

### Post by Jussi Kukkonen on 2006-09-11
The nice thing about X is that in your case you don't have to 'run X'... 
* enable X-forwarding on the server (in sshd_config, I think)
* make the ssh connection with X-forwarding enabled (e.g. start with -X)
* start the app you want
That's it, the X-server on your client machine will take care of the rest. Don't expect fast screen updates though... Try FreeNX if this is what you need.

---

### Post by ruedu on 2006-09-11
I think what you're looking for is actually XDCMP.  This will allow you to remotely login to your system using another Linux system that has X installed.  I would not however do this remotely, or off of your own personal network as X is surprisingly BW heavy and doesn't like latency too much.  FreeNX would be a better solution if you're looking to access your box remotely.  

OR you could learn the cli :)

---

