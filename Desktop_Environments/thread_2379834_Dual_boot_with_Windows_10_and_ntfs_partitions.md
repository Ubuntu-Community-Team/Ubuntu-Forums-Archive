---
title: "Dual boot with Windows 10 and ntfs partitions"
date: 2017-12-10
forum: Desktop Environments
---

### Post by peabrane on 2017-12-10
Hi there,
I have 3 computers which all have the same problem. These are an old ASUS 1001px, a Dell Venue (which will replace the ASUS) and an AMD64 mongrel desktop. All are configured to have an NTFS partition which is /home/Documents - this partition is shared with a Windows 10 alternate boot. If I use the Windows 10 system for any length of time, the ntfs partition mounts read only in ubuntu-mate. The only way I can recover the situation is to reboot into W10 and restart immediately.
I have disabled hibernate mode in W10 on all PCs. I have disabled any sleep functions or put the time out to something huge. I have tried ntfsfix in ubuntu without success. I have read as many threads as I can find on the subject. I have looked for a hiberfile.sys on the ntfs partition without success.
To recap, I am not attempting to mount the W10 system partition (so presumably hibernation is not a factor here?), this is purely and simply a documents partition. I have had this problem for many versions of Ubuntu (although a couple of years back, Ubuntu refused to start if it could not mount /home/documents - these days it mounts it read only and doesn't tell you there is a problem).
This is not a huge problem as I rarely use W10 but as it is on each machine, I do log in occasionally. I have been expecting to see a fix in one or other forum for ages and not seen anything which works.
Anyone know how to fix this please?

---

### Post by oldfred on 2017-12-10
It still could be hibernation/fast start up.
Windows includes all NTFS (and maybe FAT32) partitions in its hibernation. So even if no hiberfile in a second NTFS partition, its still in main or c: drive partition's hiberfile.
Windows on updates is known to turn fast start up back on. So even if you turned it off, it may be back on after Windows is run for a while as updates may be in background, unless you also change that setting.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by peabrane on 2017-12-10
Thanks for replying oldfred. I'll have a good look at those links. I think most of my problems are related to W10 update. I'm having mega-internet problems at present and I won't be able to look at this for a few days or unless my provider gets their finger out sooner.

---

### Post by peabrane on 2017-12-12
My internet has recovered. Thanks oldfred for the links. I have checked all those and I definitely have hibernate disabled. I have also changed the registry as in those links many moons ago. I have been through similar threads in the past.
I would say my problem was linked to updates. You hint at a setting related to updates. Is that a different setting or is it a fact of life that updates turn on fast start and you can't change it?

---

### Post by oldfred on 2017-12-12
Have not seen anything on being able to change Windows setting on turning fast start back on. It also may make Windows default boot.
I believe there are settings to control when Windows does updates, whether manually or automatically.

---

### Post by peabrane on 2017-12-13
Again, many thanks for taking the time to reply.
I don't think the thread in your last reply is what I want. My problem is that as I rarely use W10, when I go in there, it usually wants to do an update. Perhaps I could turn updates off but I want an up-to-date system. So when I go back to ubuntu, the ntfs partition is sometimes mounted read only. What I really want, if it is even possible, is to stop W10 applying a fast start during updates (and I always reboot back to W10 until the update is 100% complete). So what I seem to be suffering from is the wreckage left lying around by completed W10 updates. Is there any hope there?

---

### Post by oldfred on 2017-12-13
Not sure.

I do have one Windows 10 system, just to watch TV that I cannot stream with Linux.
And I have to go on-line and find how to do things, even simple things.
And then examples are often for Windows 8 or somehow different, like a different flavor of Ubuntu. But they never give command line commands that could be used regardless of how gui looks.
And when I finally get to some actual screen, I swear it looks just like my old XP screen, but perhaps memory evades me, related to "old" in oldfred.

---

