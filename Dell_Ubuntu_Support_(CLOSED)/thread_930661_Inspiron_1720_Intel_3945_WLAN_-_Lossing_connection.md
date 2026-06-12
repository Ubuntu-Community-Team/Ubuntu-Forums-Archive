---
title: "Inspiron 1720 Intel 3945 WLAN - Lossing connection"
date: 2008-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JesterDev on 2008-09-26
When I leave my laptop on for and leave for awhile I loose my connection. I have to restart (yes restart, no ctrl-alt-backspace works with this) in order to connect again. Normally I am downloading when I do this, and just let it run while I sleep. But every time I come back, my connection is lost. 

Intel 3945 WLAN
Ubuntu 8.04 Hardy Heron

As long as I am surfing the web, or working something it stays active. However if I let it sit alone, I loose the connection. 

Any ideas, suggestions?

---

### Post by Crafty Kisses on 2008-09-26
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```

I also want to see the results of this command:
```
lshw -C network
```
I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

---

### Post by kmerley on 2009-02-12
When I was using Ubuntu 6.06 on my D620 laptop, the wireless worked fine and stayed on.  When I installed 6.06, it connected easily to my encrypted wireless router.  When I installed 8.04 later on, I had to do more manual settings to get it working.  It is an Intel 3945.  I noticed it is now wlan0 instead of an ethx.  That was a little disappointing that the wireless experience got worse from an upgrade.  I looked in the forums and found information about how to get the wireless light working, and performed those steps, and that works well.  However I still had the problem talked about here, that the wireless connection would die after some hours if I left the laptop on.  

Then I tried: 

ifdown wlan0

followed by: 

ifup wlan0

And that always brought it back up.  Then I saw a web article about this and the person only used:

ifconfig wlan0 up

So I put that in a text file and made it executable, then placed it in /etc/cron.hourly

And maybe this is too early to talk about it, but this time I left the computer on all day (more than 9 hours) and when I got home it was still connected.  

The lease length is usually reported to be in the realm of 32000 seconds, which is about 9 hours, and that does seem to sometimes be about the length of time before it loses a connection, but I didn't test that.  

I don't know if the cron job will ever kill a download either, because I haven't had it in this condition long enough to see what happens on that.  But I don't download that much on the wireless connection, so it may be a long time before I find out anything about that.

Has someone else found a more elegant solution?

---

### Post by kmerley on 2009-02-21
Well, over time, even with the cron.daily file, I lost the wireless connection on 8.04.  Now I am trying:

ifdown wlan0
ifup wlan0
ifdown wlan0
ifup wlan0

As the file.  In doing this manually I found that sometimes the ifup did not succeed, but so far it has always succeeded the second time.  So far so good, who knows?  I used to work on 6.06 and now it works strangely.  It does seem like 8.10 did better on this, and it asked something about allowing some keyring to operate, and that computer also with the 3945 seems to stay connected, doing well after the little pop-up message about keyring came up and I said OK.  How about a backport fix for this or an explanation?

For now I am trying the cron.hourly file above.  If it faile (2 days OK so far) I will report that.

---

### Post by kmerley on 2009-02-27
It has been many days now leaving the laptop (with a laptop cooler) on continuously, and it has not lost a connection yet.  However, this is quite a hack.  I think it is OK for most situations, but it might cause downloads to fail to send an ifdown command in the middle of the download.  I don't download CDs on this machine, I use wired connection computers to download large files.  So for me, it is OK.  In using 8.10 on another laptop, it asked me about keyring as it was connecting via the 3945 wireless it has, and I responded to that question in the affirmative, and now it doesn't lose its connection, so apparently this problem is fixed in that version.  I would like it if they would make that information easy to find to be used in their long term 8.04.

---

### Post by kmerley on 2009-03-03
Well, I finally rebooted, and then it was losing the connection about every 10 minutes.  I don't know why.  So that was a major problem, and doing this in an hourly cron job just doesn't fix that.  Something is wrong with the 3945 support in the LTS 8.04, but it is fixed in 8.10 apparently, at least for me and my D620.  Well, the LTS 8.04 would only have support for 6 months past what 8.10 will have, so it isn't that much better.  I guess if I really want long term support I need to go to CentOS something like that.  

Anyway, going to 8.10, installed over the net (has all the latest updates included) solved that problem.  Kind of a big shotgun method to fix it.

---

