---
title: "High CPU usage with BitTorrent"
date: 2006-07-30
forum: Desktop Environments
---

### Post by andrewski on 2006-07-30
I've had a lot of trouble with BitTorrent on Linux.  Any of the clients I've used--the official, BitTornado, Freeloader, or gnome-btdownload--seem to run up the CPU automatically, even if the download isn't consuming bandwidth in either direction.  I've not had the problem on Windows.  To test, I downloaded the Ubuntu Dapper CD via BT (OK, it wasn't *just* a test ;)) and I've since seeded it on both Windows and Ubuntu with the same results: Windows is fine, Ubuntu is not.

I've configured port forwarding on my router according to instructions I've found in various places on the internet to good effect; my speeds have been better, but the CPU usage was not affected.

I had some friendly if speculative help from profox on IRC in #ubuntu.   He wondered, because my hard drive on my laptop is SATA, if it may be because I don't have DMA on the drive.  Sure enough, I don't and can't enable it via hdparm.  I assume this could just be a general problem, and I honestly can't gauge its effect; hardware ain't my thing.

In any case, can anyone speak on either of these issues and what I can do about either or both?  Many thanks in advance!

---

### Post by taurus on 2006-07-30
Maybe you should check out azureus to see if your CPU is going crazy.  I also use azureus for my bittorent stuff...

---

### Post by adamkane on 2006-07-30
High CPU usage means you're still using the safe 386 kernel that ships with Ubuntu. Update to a 686 or k7 kernel:

Intel Pentium (Other than Pro or 486):

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

``` 
AMD K Series (Duron, Athlon, Sempron):
 
 ```

sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

``` 

Reboot.

---

### Post by andrewski on 2006-07-30
No, not in my case:
```
andrew:~ uname -r
2.6.15-26-686
```
Any more ideas?

---

### Post by adamkane on 2006-07-30
Does your bittorrent use Java? Which version of Java are you using?

---

### Post by andrewski on 2006-07-30
> **adamkane said:**
> Does your bittorrent use Java? Which version of Java are you using?
No, actually the only client to use Java mentioned here is Azureus.  All the others, AFAIK, use Python.

---

### Post by adamkane on 2006-07-30
Have you tried connectly directly without a router in order to eliminate this as a problem?

---

### Post by jISh on 2006-07-30
Most clients actually do have a high CPU usage. There are a few exceptions, notably being rTorrent (command-line based), kTorrent (KDE based), and a good option is to run uTorrent through WINE, like I do. There's a great guide to setting up uTorrent floating around on these forums. I have three torrents downloading at average speeds and my CPU meter spikes only between 0%-11%!

---

### Post by adamkane on 2006-07-31
You want to use Azureus, if you have multiple files downloading at once. It's a superior download manager.

---

### Post by adamkane on 2006-07-31
ipv6 also seems to be an issue:
[http://www.ubuntuforums.org/showthread.php?t=218733](http://www.ubuntuforums.org/showthread.php?t=218733)

---

### Post by andrewski on 2006-07-31
> **taurus said:**
> Maybe you should check out azureus to see if your CPU is going crazy.  I also use azureus for my bittorent stuff...
OK, report from the field: Azureus does seem to work better.  (Who knew?)  So maybe it's a Python problem?  Anyone else have any ideas before I hit up Launchpad?


Adam, no, I haven't tried connecting without a router and I don't have that luxury unfortunately. :(

---

### Post by endfx on 2006-08-01
I figured I would mention this even though it probably won't help you out.

I had this problem using azureus under windows. It would just consume a lot of CPU resources. Solution: I upgraded java (azureus runs on java).

After the upgrade it worked properly.

You seem to be having the same problem with python. Try upgrading python.

---

### Post by andrewski on 2006-08-01
Programming in Python, I don't think that same situation applies; at least not as much.  Azureus does seem to use "a lot" of CPU: roughly 70%.  So it's *better*, but only slightly, by my reckoning.  Can anyone else confirm what Azureus and the other clients do on your system?

---

