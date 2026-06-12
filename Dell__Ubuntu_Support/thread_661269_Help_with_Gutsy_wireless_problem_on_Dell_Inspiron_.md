---
title: "Help with Gutsy wireless problem on Dell Inspiron 1420"
date: 2008-01-07
forum: Dell  Ubuntu Support
---

### Post by wjhildreth on 2008-01-07
Hello all,

My wife and I bought a Dell Inspiron 1420 with Feisty pre-installed. We wanted Gutsy so installed that. The system seems to work great with a couple of exceptions.

1) We cannot enable anything but the regular graphics on the desktop, none of the desktop visual effects. Does this machine's graphics card support them? If not it is not the end of the world.

2) This is the real problem, the wireless network runs fine for a while, then just hangs. You can try to select the wireless network from the network manager but nothing happens. You have to re-boot the machine to get it back up. Also, while shutting down it hangs with the message Deactivating Device eth0.

Can someone please help me resolve this? My wife starts back to school in a week and I really need to get it working.

Warm Regards,
Joe Hildreth
Waverly, TN

---

### Post by natehall on 2008-01-07
You say you installed Gutsy. Did you do it with the Dell DVD?

---

### Post by wjhildreth on 2008-01-07
Nope, i installed with Gutsy CD's I received from SHIP-IT or what ever it is called.

Regards,

Joe

---

### Post by natehall on 2008-01-07
I have a 1420N and a fresh Install with Gutsy is what I'm using right  now to post this. You can get it here [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by wjhildreth on 2008-01-07
Are you able to use the desktop visual effects as well?

Regards,
Joe

---

### Post by natehall on 2008-01-07
> **wjhildreth said:**
> Are you able to use the desktop visual effects as well?

Regards,
Joe
 Never tried to. From what I've been reading about it some tweaking is necessary.

---

### Post by wjhildreth on 2008-01-07
Thanks for the information. I tried another fix before doing a new re-install by blacklisting the network driver and using a different. If that works, she will be fine. If it doesn't do the job, I have the DVD iso on its way down now.

Thanks again for your help.

Regards,

Joe

---

### Post by fragos on 2008-01-07
My 1420n upgrade with the Dell DVD went well and everything works as before.  Compiz blacklisted the Intel card in the 1420n.  You can override that blacklist check but there will be an isue on video out.  I haven't bothered to try and will wait for Dell to deal with this.

---

### Post by wjhildreth on 2008-01-07
When you say it will affect video out, do you mean when it is hooked to an external monitor or the video display of the laptop itself?

Regards,

Joe

---

### Post by fragos on 2008-01-07
It's not clear to me weather it means the DA15 external video port or certain video applications that use XV.  An example would be tvtime which displays a video stream from a TV tuner.  Another might be a webcam.  The following link is Dell's explanation.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

---

### Post by wjhildreth on 2008-01-08
Fragos,

Thanks for the update and link. She will be using it for school so the fact that the graphic card has been blacklisted will be of no real consequence. Thanks for your help.

Regards,

Joe

:)

---

### Post by grenet on 2008-01-08
Hello to u all,
I had the same problem with my 1420N that was upped to 7.10.  This weekend I did a fresh install off the Dell ISO and everything is working much better.

I found that many of the older programs were used during the upgrade, like Network Manager, in older version.

The fresh install cleaned it all up, and things are working much better.

---

### Post by wjhildreth on 2008-01-08
Grenet,

If things still seem out of order after blacklisting the wireless driver I will do a complete re-install from the DVD image I downloaded.

Thanks for the update and information.

Joe

---

### Post by bakketti on 2008-01-08
> **wjhildreth said:**
> Thanks for the information. I tried another fix before doing a new re-install by blacklisting the network driver and using a different. If that works, she will be fine. If it doesn't do the job, I have the DVD iso on its way down now.


Joe-

I am having the exact same problem. Very very annoying.

What driver are you using instead?

---

### Post by wjhildreth on 2008-01-08
Here is what I done. So far it seems to be working fine. See link:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues")

Regards,

Joe

---

### Post by fragos on 2008-01-08
I use my system on two wireless networks depending on location.  At home I have a strong signal, TrendNET access point and never have any problems.  The other network has less power to where I am.  It's a Linksys and I get some disconnects on an inconsistent basis.  If I click the network manager icon I can see the available signals.  Sometimes it disappears and others the signal goes to 0.  Sometimes I can reconnect manualy even though the network doesn't show as available.  Have those of you with troubles used the network manager icon to examine the situation?  Have you tried other wireless networks or only one?

---

### Post by wjhildreth on 2008-01-08
Currently, the machine is only used on one wireless network. At home with a linksys wireless router. The signal strength is always good. Now once she starts back at school it will be different networks.

The problem I was experiencing was that the connection would drop and if you go to network manager, you would see it with plenty of strength but would be unable to connect to it. The solution my wife would use was to reboot the system, where it would hang with the above eth0 message. I suppose she could have restarted the network manager and accomplished the same thing, but let's face it, I am glad she is making the change from windows. I am sure as time passes she may be willing to learn more, but for now, I need to make it as trouble free as I can.

Since I have blacklisted the IPW3945 module and replaced it with the IWL3945 I have not had any issues. But it may be too early to tell. I suspect I will know more in a day or two. Or maybe as early as this evening when I get home from work.

Regards,

Joe

---

### Post by bakketti on 2008-01-08
Thanks, Joe. I will try this tonight and let everyone know if the problem persists.

I have used my Gutsy system on 3 wireless routers (Microsoft, Linksys, and Belkin). I first started getting problems at my parents home using the Microsoft router (go figure). Over the holiday, my system crashed about 5-6 times. I have had one crash on my Linksys and no problems at all with the Belkin. I havent had any problems like what fragos is describing.

---

### Post by wjhildreth on 2008-01-08
Let us know for sure how things work out for you.

Joe

---

### Post by notwen on 2008-02-13
I have recently upgraded my Inspiron 1420n using Dell's Gutsy DVD and I also am having issues connecting to certain APs I use.  AT home my LinkSYS works w/o any issue, but the other APs are inconsistent and I will need to reboot in order to reconnect after random amounts of time.  Also on a cosmetic note, I have also noticed that my wifi LED no longer lights up regardless of whether it's currently connected or roaming.  Does blacklisting the ipw module and adding the iwl module also disable my wifi LED?

For the time being I have re-installed Dell's Feisty CD image, as over all it has more of what I need w/o any additional steps.

---

### Post by fragos on 2008-02-13
I changed to the IWL driver on my 1420n with Dell Gutsy.  The access point I had problems with I still do.  Subjectively perhaps less often. IWL wasn't a silver bullet. I've also noticed that the WiFi LED doesn't come on any more.

---

### Post by notwen on 2008-02-14
I never could understand why a fully functional piece of hardware may go from stable to unstable in a newer release.  Hopefully with Hardy they will resolve the ipw module issue, but as the case w/ most things that get blacklisted, they tend to stay there.  Here's to hoping. =]

---

### Post by jumkey on 2008-02-14
I have the same problem with my 1420n and have been around the block as well.

My original symptoms were:

* wireless would not connect automatically on boot (I had to go to the Networking GUI and deselect/select the wireless adapter)
* netstat showed errors and dropped packets (about 5% retransmissions)
* large downloads sometimes would fail, YouTube videos would fail about half the time at 15 seconds. If it had to buffer data it would lock up completely and I would have to kill the page.

I reinstalled from the  Dell OS Reinstallation 7.10 DVD ISO. After blacklisting ipw3945 I get:

* wireless now works on boot
* no dropped packets or errors
* wi-fi light no longer works
* the wireless interface via the GUI is now listed as a "wired" wlan0_rename interface, and I can't add a WEP key except via the nm-applet - but this works.

All of this runs perfectly well on my office wireless network using a Cisco router. If YouTube stalls it says "buffering", waits and then continues to play. At home, however (with a DLINK router) my symptoms are unchanged and downloads continue to fail.

I opened a ticket with Dell prior to blacklisting and am forwarding on to them the results to see what they say now. I'll post whatever their response is when I receive it.

---

### Post by fragos on 2008-02-14
> **jumkey said:**
> I have the same problem with my 1420n and have been around the block as well.

My original symptoms were:

* wireless would not connect automatically on boot (I had to go to the Networking GUI and deselect/select the wireless adapter)
* netstat showed errors and dropped packets (about 5% retransmissions)
* large downloads sometimes would fail, YouTube videos would fail about half the time at 15 seconds. If it had to buffer data it would lock up completely and I would have to kill the page.

I reinstalled from the  Dell OS Reinstallation 7.10 DVD ISO. After blacklisting ipw3945 I get:

* wireless now works on boot
* no dropped packets or errors
* wi-fi light no longer works
* the wireless interface via the GUI is now listed as a "wired" wlan0_rename interface, and I can't add a WEP key except via the nm-applet - but this works.

All of this runs perfectly well on my office wireless network using a Cisco router. If YouTube stalls it says "buffering", waits and then continues to play. At home, however (with a DLINK router) my symptoms are unchanged and downloads continue to fail.

I opened a ticket with Dell prior to blacklisting and am forwarding on to them the results to see what they say now. I'll post whatever their response is when I receive it.

Very detailed and quantified analysis.  My initial problems were more of an annoyance and not with my home network.  I still see some of the issues with one network I use but things have at least improved some -- not scientific measurement.  I have two questions which may not have easy answers.

1. How does signal strength factor in.
2. How much does the bandwidth or number of users impact the access point (based on DCHP IP assignment I've been the 6th concurrent user on the AP I have issues with)

---

### Post by valke on 2008-02-14
i did the blacklisting, however, i can't seem to access any wireless connections at all. i use my laptop at home, and have a netgear router that gives off perfect signal, but now i can't connect to the wireless.

---

### Post by jumkey on 2008-02-14
I'm not a RF guy but as I understand it signal strength is related to signal/noise ratio, so to handle this the wireless card negotiates a slower or faster speed depending upon the strength of the signal. Also apparently the cards themselves can retry dropped packets without the network stack even being aware of it, which would result in higher packet latency (and slower network speeds) but no errors that would be reported. This same logic applies to question 2, so I think the number of users would make no difference to this issue.

My greatest concerns is seeing errors and retransmissions on the interface. In wired connections ANY errors are indicative of a hardware or driver problem. I looked at a Unix box in my office that has been up for more than a year with 70M+ packets (I assume this has rolled over) and zero errors or packet loss.

Clearly there is  a driver problem - so the only question is how and when is Dell going to fix it.

---

### Post by jumkey on 2008-02-14
valke:

What do you see if you do an ifconfig -a? Is your interface getting an IP address from the router?

---

### Post by fragos on 2008-02-14
> **valke said:**
> i did the blacklisting, however, i can't seem to access any wireless connections at all. i use my laptop at home, and have a netgear router that gives off perfect signal, but now i can't connect to the wireless.

Just double checking but here are the instructions from Dell that I followed to blacklist the ipw driver and to use the iwl driver.  My 1420n works properly with those directions.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

PS: Love your avatar

---

### Post by valke on 2008-02-14
haha thanks, fragos. yes those are the the instructions that i used. i undid it but i am going to do it again, and take notes as to what's wrong.

***edit
hmmm, i just tried it and it seems to be working again. let me try dl'ing something heavy...

thanks again fragos :)

---

