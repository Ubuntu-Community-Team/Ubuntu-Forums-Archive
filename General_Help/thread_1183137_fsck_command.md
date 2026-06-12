---
title: "fsck command"
date: 2009-06-09
forum: General Help
---

### Post by tmorosco on 2009-06-09
Hi all,

As a part of ongoing diagnosis of a periodicly unstable system, I am running fsck with:

 [FONT="Courier New"]fsck -f -y -v /dev/sda7[/FONT]

sda7 is a 700GB ext3 partition on one of my drives (unmounted, of course).

I've read that it can take a long time on large partitions, but its been running for over 24 hours now.  

Periodically the screen scrolls with new information (I'm afraid I can't make heads or tails of the verbose messages, last line reads:

[FONT="Courier New"][139882.792501] [<c0103f7b>] sysenter_do_call+0x12/0x2f[/FONT]

My questions are:
1) Is 24+ hours a reasonable amount of time for fsck to run on such a drive size?

2) Anyone have any suggestions where I can learn to decipher verbose fsck messages I am getting?

3) Can I safely kill fsck mid-process without likely damage to the partition?

Thanks for any leads, I'm trying to learn, not just get the answers.

---

### Post by dcstar on 2009-06-09
> **tmorosco said:**
> Hi all,

As a part of ongoing diagnosis of a periodicly unstable system, I am running fsck with:

 [FONT="Courier New"]fsck -f -y -v /dev/sda7[/FONT]

sda7 is a 700GB ext3 partition on one of my drives (unmounted, of course).

I've read that it can take a long time on large partitions, but its been running for over 24 hours now.  

Periodically the screen scrolls with new information (I'm afraid I can't make heads or tails of the verbose messages, last line reads:

[FONT="Courier New"][139882.792501] [<c0103f7b>] sysenter_do_call+0x12/0x2f[/FONT]

My questions are:
1) Is 24+ hours a reasonable amount of time for fsck to run on such a drive size?

2) Anyone have any suggestions where I can learn to decipher verbose fsck messages I am getting?

3) Can I safely kill fsck mid-process without likely damage to the partition?

Thanks for any leads, I'm trying to learn, not just get the answers.

fsck should only take minutes, not hours unless you have a highly corrupted filesystem.

Turning on verbose messages is no value whatsoever to anyone who does not understand what those messages are.

If fsck is not specifically saying it is writing/changing something, then you may well be able to **end** the process (not **kill**) without any consequences.

---

### Post by oldos2er on 2009-06-09
I had a 1TB partition formatted ext3, and I never could get a successful conclusion when running fsck on it. I think one time I let it run more than 48 hours, but it still didn't complete. I changed it to ext4, and no longer have this problem. I'm offering this as my experience, not advice that you should do the same.

 As I recall, I shut down my system rather than simply killing fsck outright. I was terrified of losing data, but this never happened. Again, I can't recommend this procedure to anyone else (I did of course have backups). Just FYI.

---

### Post by bodhi.zazen on 2009-06-09
The messages from fsck are cryptic to say the least.

If you are having these problems is could indicate either a hard drive that is about to fail or a major corruption in your file system.

either way , complete failure may be imminent (I am not sure about the error message, it is just a bad sign when fsck fails).

I advise you back up your data, re-format the partition, and restore your data. If you continue to have problems I would venture a failing hard drive.

---

### Post by tmorosco on 2009-06-12
Short udpate:  Since several info sources cite very long runtimes for fsck on large partitions (over a week for 4TB!) I've decided to be patient for a little while.  the 'counter' part of the verbose messages is up to 382160, which doesn't correlate to uptime or running seconds.  I may try and stip it when it reaches 400k.  Who knew a simple fsck would be so intensive?  It wouldn't hurt to have a warning message come up for large disks to warn noobies.

---

### Post by LKjell on 2009-06-12
Are you using Ubuntu while doing the check?

---

### Post by tmorosco on 2009-06-12
Yes, booted to Ubuntu 8.10, kernel 2.6.27-9 (recovery mode).
Dropped to root shell, made sure the partition was unmounted before running fsck.

---

### Post by LKjell on 2009-06-12
I never ran a fsck on verbose mode before but the msg looks like a function call for each inode. Eventually do you hear any noise-like crack on your hdd? If you do it might have some badsector which also decrease reading and writing speed of fsck. Believe me if fsck on this mode takes a long time then checking for badblocks takes ages.

If I was you I would just cancel fsck and run fsck -pf. To cancel you press ctr+c. If that also takes a very long time then just cancel it and run fsck -pcf. And start back up your files after that.

---

### Post by tmorosco on 2009-06-17
Thanks LKjell,

There are very infrequent HDD grinding, like its accessing a sector of the disk, but I'd say not more than a couple times a day.  

So I was very patient up until today, 9+ days into the fsck.

First I tried a Ctrl-Z to stop the process .... nothing.
After a minute or two, I tried a Ctrl-C to kill it. .... nothing.
Finally I tried a Ctrl-Alt-Del, and it paused for a minute.  I was writing down the message it displayed:

[FONT="Courier New"]Hangup
root@Trixis: /dev # init: rS-sulogin main process (7191) kill ..."
[/FONT]

And then it started scrolling verbose output again, but this time faster output (maybe 45 seconds between scrolling), and slightly different output messages. Mixed in is a:

[FONT="Courier New"][nnnnn.nnnnn] Pid:7370, comm: kstop0 Tainted: P     D (2.6.27-9-generic #1)[/FONT]

So I think I somehow managed to kill off a child process of the main fsck. 

Anyway,  additional Ctrl-Alt-Del and other key combos are not producing any effects.  And the machine is in single user mode, and I can't figure out another way to kill it.

I'm really not happy about hitting the power or soft-restart buttons, but can you see any alternatives??

*sigh*  I knew I didn't want to go into diagnosing the video instabilities on this machine.  What a time sink!

---

