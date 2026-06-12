---
title: "Update crashes Gnome"
date: 2006-07-06
forum: Desktop Environments
---

### Post by Toet on 2006-07-06
Hi,

This morning my update manager told me I have 3 updates to install. Clicking the little icon for it crashes my Gnome and gives me the logon window.

Anyone a solution for this?

---

### Post by Fritti on 2006-07-06
I've seen this on 2 PCs now. With the first I suspected hardware, but now that I'm at work and it crashed in exactly the same way, I suspect it's a bug.

Do you have an nvidia card and driver? I suspect it's related to that.

---

### Post by Fritti on 2006-07-06
Sorry, forgot to post the work-around:

- open a terminal (Applications, Accessories, Terminal)
- type:

   sudo apt-get update

[lots of output that you should be able to ignore]

   sudo apt-get upgrade

[more output]

  Answer 'Y'

Now it should download and install the updates, and the icon in your panel should go away.

---

### Post by Toet on 2006-07-06
Yes I do have a nvidia card. Thanks for the work arround, it works!

---

### Post by Bolorino on 2006-07-06
Same problem here.
I also have a nvidia card, but is the first time I see the X-server crashing after listing the updates.

What have changed since the last update with no crash?

---

### Post by Fritti on 2006-07-06
I don't think anything has changed, but something in the update texts causes the X server to crash. My /var/log/Xorg.0.log.old ends with:

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

Which is not exactly useful to anyone :(

---

### Post by mdbarton on 2006-07-06
Same problem here - and I also have an nvidia card.  Thanks for the workaround, will try it tonight.

---

### Post by Fritti on 2006-07-06
Reported as [https://launchpad.net/distros/ubuntu/+bug/52056](https://launchpad.net/distros/ubuntu/+bug/52056)

I don't think there's much Ubuntu can do if it's a bug in the nvidia driver though :(

---

### Post by freim on 2006-07-06
I also got the same problem using the nvidia driver (1.0.8762+2.6.15.11-2).

It's been a bit flacky before also crashing X from time to time, but now it crashes every time. It even hanged my box hard the first time I tried to update today :mad: 

Guess I'll use apt-get for the time being, but this is a rather serious bug in either the nvidia driver or the update-manager.

---

### Post by CharlesBasengaKiyanda on 2006-07-06
Same problem here with nvidia-glx driver 1.0.8762+2.6.15.11

I did it twice. Changed the driver line in xorg.conf back from nvidia to nv and it worked without problem.

---

### Post by CharlesBasengaKiyanda on 2006-07-06
Note that I just tried opening the update manager while using the nvidia-glx driver and everything works fine. No software freeze and no x crash. Could the problem be related to the actual update being performed?

---

### Post by Fritti on 2006-07-06
Certainly; I've updated both my systems before using the same driver, the problem only manifested today with the 3 updates of login, passwd and ppp.

---

### Post by FerGeCo on 2006-07-06
Hi!

I just wanted to say that i also have this problem. The problem was repeatable with the last 3 updates (login, passwd and ppp) before that it also crashed but only once and the second time you could just update.

---

### Post by VirtuAlex on 2006-07-06
It seems to be crashing while it downloads update descriptions, which it supposed to show at the bottom part of the window.

---

### Post by Beamerboy on 2006-07-06
[QUOTE=Fritti]Certainly; I've updated both my systems before using the same driver, the problem only manifested today with the 3 updates of login, passwd and ppp.[/QUOTE]

Same here, I have never had a problem with it crashing before and I have had nvidia-glx driver installed since I installed the system.  So I don't see why people are so quick to blame the nvidia drivers.

Furthermore, when xorg crashed, I logged back in and was able to do the update fine.

We need some more info on this.

---

### Post by VirtuAlex on 2006-07-06
[QUOTE=Beamerboy]I don't see why people are so quick to blame the nvidia drivers.[/QUOTE]
It is just based on evidence. Everybody use update, but only people with nvidia have troubles. Probably there is some flaw in the update program, but it is nvidia driver which allows it to crash xorg.

---

### Post by Beamerboy on 2006-07-06
[QUOTE=VirtuAlex]It is just based on evidence. Everybody use update, but only people with nvidia have troubles. Probably there is some flaw in the update program, but it is nvidia driver which allows it to crash xorg.[/QUOTE]

As I said in the 64bit forum, that logic is unsubstantiated.  Nvidia is the most widely used graphics cards for linux.  I have never had a crash in xorg before these updates today, so it certainly isn't something that is happening with any sort of pattern.  It could just be that people using other drivers have either not experienced the crash yet or have not reported it.

Dismissing the problem as a driver issue is completely premature at this point in time.

---

### Post by VirtuAlex on 2006-07-06
[QUOTE=Beamerboy]I have never had a crash in xorg before these updates today[/QUOTE]

Well, I did have a crash in xorg. First it happened about a month ago with exactly the same symptoms. Second time it was (if I remember it right) with gtkpod. I accidently dragged something in the window and then dropped it on itself with desastrous result - xorg rebooted. I am not saying it IS nvidia problem, but it defenitely MAY BE nvidia problem. I just want somebody to investigate the issue, cause it is quite serious. I still did not do the update, so if somebody knows how to troublesoot this issue I am available. Anybody?

---

### Post by Beamerboy on 2006-07-06
[QUOTE=VirtuAlex]Well, I did have a crash in xorg. First it happened about a month ago with exactly the same symptoms. Second time it was (if I remember it right) with gtkpod. I accidently dragged something in the window and then dropped it on itself with desastrous result - xorg rebooted. I am not saying it IS nvidia problem, but it defenitely MAY BE nvidia problem. I just want somebody to investigate the issue, cause it is quite serious. I still did not do the update, so if somebody knows how to troublesoot this issue I am available. Anybody?[/QUOTE]

Oh I am happy to accept it may be an nvidia driver issue, but I guess having been a software tester in a corporate environment, I am not so quick to draw conclusions with so little info available.  I mean, there have only been what a dozen people reported it so far out of I expect 10s of thousands (if not more) users with nvidia devices?

Jumping to conclusions with so little info only delays the troubleshooting process, because people may go down completely the wrong path as a result, meaning the actual cause takes longer to discover and then fix.

---

### Post by JeffreyRatcliffe on 2006-07-06
I had the same problem with the same 3 updates.
I also have an nvidia card

---

### Post by orb9220 on 2006-07-06
Yep! mine last night did the same.

You can bybass that window by right click tray icon and install that way.

Didn't crash and after I ran the update manger it was empty of course it did not crash after that/

Have to wait and see if it does it on the next one.

FYI: The update before those was a mouse update. Then new 3 updates crash after I click on desktop after update manger opens. If I don't click it sat there fine. Just wondering if it is connected?  :confused:

---

### Post by VirtuAlex on 2006-07-06
[QUOTE=Fritti]Reported as [https://launchpad.net/distros/ubuntu/+bug/52056](https://launchpad.net/distros/ubuntu/+bug/52056)

I don't think there's much Ubuntu can do if it's a bug in the nvidia driver though :([/QUOTE]

I digged a little through launchpad.net and it seems that this issue has some history:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/50245]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/50245")
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/49980]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/49980")
[https://launchpad.net/distros/ubuntu/+source/nvidia-glx/+bug/49834]("https://launchpad.net/distros/ubuntu/+source/nvidia-glx/+bug/49834")
and even such interesting thing as
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/47122]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/47122")
seem to be same exactly beasts.
Nobody seems to be working on it though...

---

### Post by VirtuAlex on 2006-07-07
So I guess nobody interested in investigation of this issue. Then I'll go apt-get the updates. Anyway I now have this [buggy file]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/47122") on my hard drive which is able reproduce xorg crash in gedit or firefox.

---

### Post by Fritti on 2006-07-07
Beamerboy: I agree that it's not blatantly obvious that it's a bug in the nvidia-driver, but I reasoned that a) X itself is crashing (not a client) and b) it doesn't happen for lots of people because otherwise it would have been seen by more people, so it's not a bug in the X server generic code and c) binary drivers are evil and should die and so I'm quick to blame them :)

Anyway, some of those new bugs report that indeed switching back to 'nv' works around the crash so I really do think it's the binary driver that's at fault here.

VirtuAlex: great digging! I tried some search texts in launchpad before reporting but obviously not enough. Looks like this bug is here to stay for a while yet though.

---

### Post by Fritti on 2006-07-07
OK, I've notified nvidia of the problem:

[http://www.nvnews.net/vbulletin/showthread.php?p=931048](http://www.nvnews.net/vbulletin/showthread.php?p=931048)

Maybe it'll help.

---

### Post by stephg on 2006-07-07
Try to switch to LegacyUbuntu theme. It worked for me.

---

### Post by stephg on 2006-07-07
When I switched to the LegacyUbuntu theme, the crash didn't occured anymore for the update manager. 

But even with the LegacyUbuntu theme activated, your file is still very effective in order to crash my X server :) Just displaying the file in Firefox does the trick. Impressive !

---

### Post by JeffreyRatcliffe on 2006-07-24
Had the same problem again this evening - 3 packages (this time kdelibs-bin kdelibs-data kdelibs4c2a) to update and calling them up crashes Gnome.

This is getting boring... Is really nobody working on this?

---

### Post by stephen53 on 2006-07-24
I just updated my laptop and had the same problem. The updates were (kdelibs-bin kdelibs-data kdelibs4c2a) . This is the first time I have had this problem. I tried several times to update with X crashing. I used control alt backspace to restart X . On the update icon , I right clicked and from the menu selected install the updates. This worked. I also have an nvidia graphic card. The manager would start up then about 20 to 30 seconds later crash. What ever is causing this most likly is related to the nvida 3D graphic driver. I wonder if people using nvida without the accelerated driver also have this issue?

---

### Post by eems01 on 2006-07-24
Same problem here.  Nvidia drivers on a laptop.  Usually I apt-get but today I clicked on the icon while my wife was logged in.  I'll try out my desktop that has an ATI card.

---

### Post by bsmith1051 on 2006-07-24
Add one more nvidia user experiencing this problem. 

BTW I didn't report it before (about a month ago) because it eventually resolved itself.  I've since installed several updates.  It's only today that I'm back to the same X crashes again.

---

### Post by ChrisC on 2006-07-24
Another nvidia user ...

In my case (vanilla Dapper, first update), it wants to install 52 updates.  I can see the description for each one, until I get to "linux-image-2.6.15-26-386".  When I click on that one, and it downloads the description text (I can see the network activity happening), it promptly crashes X and I have to log in again.  The "linux-386" entry immediately preceding it on the list is fine.

My guess is that the kernal image update list is huge, or perhaps has some weird character in it.

I'm glad I searched this forum before posting :)

---

### Post by sterwill on 2006-07-25
Same problem here.  nvidia-glx driver, update manager kills X.  Here's the backtrace from the X server dying:

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a86]
1: [0xffffe420]
2: /usr/bin/X(Xfree+0x21) [0x819678a]
3: [0xb73b1c1a]
4: /usr/bin/X [0x8146f1d]
5: /usr/bin/X(CompositeGlyphs+0x94) [0x813a96f]
6: /usr/bin/X [0x813d209]
7: /usr/bin/X [0x813e76e]
8: /usr/bin/X(Dispatch+0x19e) [0x8085d26]
9: /usr/bin/X(main+0x47c) [0x806e0a8]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d57ea2]
11: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

```

Not much to debug with a proprietary driver.

---

### Post by Sef on 2006-07-25
> wonder if people using nvida without the accelerated driver also have this issue?

I don't have the accelerated driver on my desktop, and the update went fine.

---

### Post by VirtuAlex on 2006-07-25
nv works fine. It can be proven by opening the troubled file from [https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/47122]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg/+bug/47122")
It will crash nvidia but under nv it opens just fine.

---

### Post by computx on 2006-07-25
I had this exact same problem. My workaround was launching synaptic and doing the updates from there. No crashes with synaptic.

---

### Post by v4169sgr on 2006-07-25
Kubuntu user running update manager with Nvidia card. Add another data point for the kde-libs update crash. This happened consistently just at the moment update-manager was attempting to display the update description for the first selected update - 'Loading description ...'

---

### Post by genzo on 2006-07-27
i've had the problem a couple of days ago before kernel update (which fixed it) and now it happened again today.. the update manager is whack :/

why does it crash while synaptic doesnt?

---

### Post by VirtuAlex on 2006-07-27
> **genzo said:**
> why does it crash while synaptic doesnt?
It is some string displayed in the list of changes in certain packages causes problem with nvidia driver. Nvidia people say that [it shold be resolved in the next driver release]("http://www.nvnews.net/vbulletin/showthread.php?p=931048").

---

### Post by Paul Chang on 2006-07-29
Same problem here. I have a XFX GeForce 6800XT card, and using 
the driver NVIDIA-Linux-x86-1.0-8762-pkg1. Never had any crash problems before until this morning's update of xorg.

---

### Post by VirtuAlex on 2006-07-30
Hey, guys, if you do not mind to confirm that opening the link I mentioned before would crash x... I just want to know if this is positive corellation between crash from that file and crash from update.
Thanks

---

### Post by ChrisC on 2006-10-09
Consarn it!  This problem still exists!

I just had an X-session crash (log out to login prompt) when I looked at the descriptions of the security fixes proposed by the software update checker.

Exactly as I described here 2.5 months ago: [http://ubuntuforums.org/showpost.php?p=1296022&postcount=32](http://ubuntuforums.org/showpost.php?p=1296022&postcount=32)

When is this going to be fixed?

---

### Post by ChrisC on 2006-10-10
No, really, when is this going to be fixed?  I have diligently kept my Ubuntu install neat and updated and apt-installed only, and this kind of thing should not happen.  To me, an automatic X logout is just as bad as a spontaneous reboot because of all the app state information (e.g. browser windows opened, work in progress) that I suddenly lose.

And note bounty below.  I'll even pay for a pointer to the relevant entry in a bug tracking database somewhere!

---

### Post by ChrisC on 2006-10-10
bump ...

---

### Post by Fritti on 2006-10-31
This should be fixed in the 8776 driver update. Not sure what driver version Dapper has as I'm running Edgy now, but seeing that Edgy still has 8774 I doubt it. However I haven't yet tried to reproduce the crash on Edgy, maybe the packaged driver version includes this fix.

---

