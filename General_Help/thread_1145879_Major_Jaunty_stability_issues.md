---
title: "Major Jaunty stability issues"
date: 2009-05-02
forum: General Help
---

### Post by seanlano on 2009-05-02
I've recently upgraded to Jaunty from Intrepid, and on my desktop PC (an Acer Aspire, fairly new) it works just fine, at least as good as Intrepid, if not better. However, on my laptop (a Thinkpad R61i, even newer than the desktop) Jaunty seems to crash all the time. The system completely locks up, nothing I can do will work. The crashes don't seem to follow a pattern, sometimes I can work for quite a while without issues, sometimes it locks up during boot, sometimes just after log-on, sometimes it takes a few minutes (it crashed during my first attempt to post this), sometimes it doesn't happen. The system seems to slow down, then stop. Generally, first the keyboard stops responding, then the mouse slows to a crawl, and then everything stops (about 2-3 seconds from OK->Broken). There is no "Crash Notification" from apport after I reboot. Both the latest Generic and Realtime kernels have the same problem. I certainly didn't have anything like this happen in Intrepid. I have done about 6 re-installs (ranging from Alpha-6 to the Stable releases), and all have been problematic, although the later versions have been slightly improved. 

Are there system logs I can check which might contain info?
What new things in Jaunty might be causing me problems?
What do I do??

---

### Post by linuxkrn on 2009-05-02
I have this same problem, but with a Dell XPS M1730.

I *think* it's the wireless...  I've tried all the kernel options (noapic/noacpi/etc), tried changing everything and still get lockups.

I had ext4, so went to ext3 thinking it was the delete bugs.  Nope.  Turned off home-dir encryption, again nothing.  Disabled compiz, created temp users, and almost everything else.  The only thing that seemed to work was disabled wireless. (kill switch before booting)  But it's impossible to test with network traffic that way.

FYI, there is a bug open about locks caused by 'strace gedit', I get that too but think it may be un-related to this problem.


My hardware:

Dell XPS M1730
Intel X9000 @ 3.4GHz
4GB RAM (64bit install)
Dual nVidia 8800M GTX SLI @2560x1600
Dual SSD in RAID-0
Wireless Intel 4965 AGN Nic

FYI: [http://forums.opensuse.org/network-internet/wireless/404058-freeze-up-problem-may-related-4965-card-3.html](http://forums.opensuse.org/network-internet/wireless/404058-freeze-up-problem-may-related-4965-card-3.html)

Update: It was suggested that an 8.10 bug with 4965 drivers had a regression issue.  So per the release notes for 8.10, I installed the backport modules.  That seems to have solved my problems.  I've now run for over an hour without a lockup.  Even ran wine playing Guild Wars on a NTFS-3G partition while playing mp3s.  :)
```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by seanlano on 2009-05-02
Come to think of it, the only times I have had problems is at home... where I use my wireless network. Thinking back, when I used it at school with no network connection it worked fine. I'll try the backports thing now. Thankfully I normally use the laptop at home via a wired connection, so disabling wireless is no big problem at the moment. I'll try it. Thanks.

---

### Post by seanlano on 2009-05-02
I've installed the backports module, and restarted, and am testing the wireless now (ethernet unplugged), and for 30 mins now it has been fine. I think it is solved. Interesting though that you read the 8.10 release notes for this problem, because wireless was fine for me in 8.10, but i suppose I could have had the backports module without knowing it. Thanks.

---

### Post by seanlano on 2009-05-02
It happened again! I was running with the wireless and the ethernet unplugged, and it froze again! I noticed that the wireless network indicator LED was flashing. ???

Any ideas now?

---

### Post by Nycticorax on 2009-05-06
I'm having similar problems on a Thinkpad t40 with a ATI Radeon graphics card. Disabling wireless and Compiz doesn't solve it. I'm getting the impression it's less frequent with the 2.6.27 kernel but that may not be true. Does anyone have any advice? Is there an open bug report for the jaunty graphics card problems? Is there any way we can collect helpful data? I haven't been able to find any relevant messages in /var/log/* or .xsession-errors. It seems that some people are having some success messing about with which driver they are using for their graphics card. 

There's a similar thread at

[http://ubuntuforums.org/showthread.php?t=1137378]("http://ubuntuforums.org/showthread.php?t=1137378")

---

### Post by bclintbe on 2009-05-07
I might be having the same problem as the rest of you. Can't have anything to do with wireless for me, since I'm on a wired connection on a desktop. Most of the time everything is running fine, but out of the blue the computer will just totally lock up... no response at all and I'm forced to switch off my powerbar and hard boot. This has only been happening since I did a fresh install of 9.04. In all previous versions of Ubuntu on this computer it never happened. Any more info I can give? Anyone have any suggestions?

---

### Post by schickb on 2009-05-07
> **bclintbe said:**
> I might be having the same problem as the rest of you. Can't have anything to do with wireless for me, since I'm on a wired connection on a desktop ... Anyone have any suggestions?

If you are using one, try disabling the "restricted" video driver under: System -> Administration -> Hardware Drivers.

For me, this totally solved the lockup problem. Unfortunately, you lose the ability to run compiz effects.

---

### Post by bclintbe on 2009-05-07
Based on the other posts I've seen I disabled the nvidia driver I was using, shut off all the desktop effects also. I still had a lock up happen today. I just realised though that I had not restarted since disabling the restricted driver. We'll see if restarting helps now.

---

### Post by seanlano on 2009-05-08
I've installed the 2.6.30rc4 kernel from the ubuntu kernel website, and so far I haven't had the lockup happen, but hibernate doesn't work and there is no bootsplash (at least for usplash, not sure about splashy). Also, the ubuntu kernel site only has the generic kernel, not the RT kernel, which is sometimes annoying. I could move back to Intrepid, but I really can't be bothered, and my the problems seem to be decreasing. 

Try the 2.6.30 or 2.6.29 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

---

### Post by bthornton84 on 2009-05-30
I just wanted to chime-in on this because I've also been experiencing almost the exact same thing on my Lenovo Thinkpad T61. I did a fresh install of Jaunty, having run Intrepid previously; this machine had never crashed to my knowledge running Intrepid or even Windows 7. I don't notice any slowdowns before the crash, but the past few times it has crashed, it crashes hard: everything on the screen locks and the Caps-Lock LED blinks on and off. And just like the original poster: sometimes it happens within a few minutes of booting, and sometimes it doesn't happen for an hour or even more. There is nothing in the syslog/messages to indicate why the crash happened. I am always connected to a Wifi network so I can't comment on the behavior when Wifi is not on.

I do run Compiz with nVidia drivers (as installed by the "Hardware Drivers" program) and my gut tells me it might be related to that somehow. If anybody has new information, please follow up! Thanks.

(BTW -- I am not 100% sure but this *seems* to only happen when I'm running on battery...)

---

### Post by statmonkey on 2009-06-07
For what it is worth.  I have 4 machines running Jaunty, only on my server for some odd reason - actually maybe not now that I think about it - I have this problem.  I disabled the NVidea drivers and shut of compiz and all seems fine now.  I had exactly this issue with only this box.  It would lock up, giving no error messages (meaning to my mind a pretty serious kernel panic if it could not even write a message).  The only hint might be that since this was a server and I did not want to start all over I initial did an upgrade, the only machine I did that on.  

After the upgrade I had a drive show up bad and the lock ups started to happen.  I had turned on Nvidia driver immediately.  I then tried for a clean install but it would not let me go advanced and kept stopping me by saying the CD drive was mounted.  There is no cd drive on this box.  I was forced to accept the standard install but no big deal.  After the clean install the lockups continued to happen.  I have since shut off Nvidea and compiz and after about 9 hours of uptime have had no reoccurance.

---

### Post by seanlano on 2009-06-07
The Thinkpad R61 I am having problems with only has Intel graphics, so I don't even have the nVidia drivers installed, and I still had the problems. However, everything seems to be ok now with the 2.6.30rc4 kernel. Although I cannot hibernate, and usplash doesn't work, but I can live with that. Jaunty is better than Intrepid by enough of a margin for me to put up with it.

---

### Post by wbrown on 2009-06-07
Greetings: 

I am also having this issue with a fresh install of Jaunty 9.04.  I do have nvadia graphics installed.  

The main thing I notice is that the system freezes like clockwork every time I download something with apt-get for large files.  Even if I boot into the recovery console and enable the root console with networking, the system still hangs during an install of something like flashplugin-nonfree or any fire really.  This makes me think it is not video driver related since I'm in the root recovery console.  

I'm on a amd64 bit system.   I'm using this kernel: 
Linux ubuntu 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:12 UTC 2009 x86_64 GNU/Linux

I'm am going to try the earlier suggestions of upgrading the kernel to 2.6.30 to see if that helps.  

Lets hope it doesn't take another 20 download attempts to get the kernel to my workstation.  

Please help. 
Bill.

---

### Post by statmonkey on 2009-06-08
There are just enough differences between both seanlano and wbrown's situations from mine that they would seem to me different issues.  I am pretty sure in my case it is something specifically related to this box and maybe it has to do with the upgrade/install process I went through.  I can confirm that shutting down compiz and Nvidia seems to have worked for me in this case though.  I really beat on my other three installations and none of them shows any issues.  They all run flawlessly.  So again that leads me to believe it is something about this particular install and maybe a hardware/kernel combination or the install as stated earlier.  

I will be setting up another laptop later this week so that should be interesting.  But I am just flailing around like both of you.  I keep hoping that if there is enough activity on this thread someone with more knowledge will come along and give us an idea or two.  I have read some other threads where similar issues occur and all with no conclusive answer.  I even read of some similar issues on Suse installs so maybe it is kernel related.  Really wish I could be of more help and would like to know why this is happening.

---

### Post by seanlano on 2009-06-08
I've installed the 2.6.30rc8 kernel, and now I can hibernate and use usplash. As far as I am concerned, my problems are fixed with this new kernel. Give it a go. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/"). Post any issues you have, although I probably won't be able to help, it will be interesting to see the success of others.

---

### Post by wbrown on 2009-06-16
Hello again: 

For followup, I am now running the ppa kernel

bill@ubuntu:~$ uname -a
Linux ubuntu 2.6.30-020630rc8-generic #020630rc8 SMP Wed Jun 3 09:04:33 UTC 2009 x86_64 GNU/Linux

which no longer crashes the system but does not allow me to run my audio setup in realtime :(  

Bill.

---

### Post by seanlano on 2009-06-17
I have the 2.6.30rc8 kernel as well, and I am able to run in RT. I was doing it just now with JACK and my FP10 (at 5.8msec latency! Unreal!). Check your */etc/security/limits.conf* again, I think it might get reset after a kernel install. It should be something like: 
```
gksudo gedit /etc/security/limits.conf


[I]...other things, removed for simplicity...
[/I]
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19
```
You will also need to make sure you are a member of the "Audio" group. *System -> Administration -> Users and Groups*.

---

