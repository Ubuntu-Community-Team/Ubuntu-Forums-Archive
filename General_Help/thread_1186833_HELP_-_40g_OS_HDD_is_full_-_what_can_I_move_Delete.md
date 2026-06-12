---
title: "HELP - 40g OS HDD is full - what can I move? Delete kernals?"
date: 2009-06-13
forum: General Help
---

### Post by PsychedelicWonders on 2009-06-13
I have a 40g HDD for my OS both Xp PRo & ubuntu.

problem is, there is 0% left and my computer isnt running right.

So what can I move off of that HDD to another one to free up some space?

I think I have like 4 or 5 kernals on my grub menu, would deleting a few of these free up space?

If so, how do I go about doing that?

---

### Post by synapsys on 2009-06-13
Delete contents of /var/log/

Run

```
sudo apt-get clean
```

Move large files music / videos to a different hard drive.

Buy a bigger one if you can afford it (40GB is really tiny nowadays)

---

### Post by 73ckn797 on 2009-06-13
You may find kernels listed in Synaptic. You could remove the unnecessary ones from there.

More space is certainly needed. A 160GiB drive can be found for under $50 US dollars at Micro Center, if you are in the US.

---

### Post by PsychedelicWonders on 2009-06-13
> **synapsys said:**
> Delete contents of /var/log/

Run

```
sudo apt-get clean
```

Move large files music / videos to a different hard drive.

Buy a bigger one if you can afford it (40GB is really tiny nowadays)

The 40g HDD is strictly to run OS.

I have a 500g for media storage.

I believe all of the extra kernals I have are eating up the rest of my HDD space.

So will that get clean clear up all of the extra kernals?  there is like 5.

---

### Post by drs305 on 2009-06-13
Here is a guide to recovering lost disk space:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Check your trash system for unremoved trash - which still takes up space. Check root trash also and use SHIFT-DEL to remove the root Trash folder. Use caution since SHIFT-DELETE can't be reversed.
```
gksudo nautilus /root/.local/share
```

In this guide I wrote about StartUp-Manager, there is a section on how to manually remove older kernels (near the bottom of the guide). You can also use synaptic and the guide covers this as well.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by PsychedelicWonders on 2009-06-21
Ok, I'm going to remove all of the old kernals today

I literally think there are 5, so I should just keep the latest 2 right?

Do you really think the other 3 are taking up that much space where this is going to make a big difference?

I will do that and then also empty the trash of the root

I'm going to be upgrading to 64 Win 7 from XP Pro

I may not have enough room on my windows partition.

So what should I do?

I believe I partitioned my 40g OS HDD 45% for windows and 45% for Ubuntu and then there the rest is for a swap partition.

So how can I save my entire Ubuntu parition with all of my upgrades and modifications with out losing a single bit of code I've written?

I would like to use the 40g HDD if I can, but I dont think its going to be enough to run both OS, so I will upgrade to at least an 80g before I do this upgrade.

I have a backup external 500G WD passport and an internal 500G media HDD.

Suggestions?

---

### Post by renkinjutsu on 2009-06-21
my experience is that you can't get root privelages using sudo/gksu when your drive is full, delete some other files before uninstallying things with synaptic

---

### Post by paperplate9 on 2009-06-21
Remove user files before you start deleting system stuff! Unless you have some program that is just hogging the disk, start with deleting music, videos, big documents, etc...

do:

to find dirs in your home taking up double-digit megs or more:
cd ~; du --max-depth=1 -h|egrep "^[0-9]{2,}[0-9]*M"|sort -nr

to find dirs in your home taking up gigs:
cd ~; du --max-depth=1 -h|egrep "^[0-9]+\.?[0-9]*G"|sort -nr

lol, I just used my own advice and cleaned up about a gig (mainly object files that were lying around)!

---

### Post by PsychedelicWonders on 2009-06-21
I keep all of my media on the 500g.  I dont know how the 40 is tapped already.

So you want me to run those two codes and delete everything that shows up?

---

### Post by PsychedelicWonders on 2009-06-21
Where exactly do I delete the other kernals?

I went to system>admin>synaptic package manager

But I get totally lost and dont know what to delete?

Is there a way for you guys to see everything on my 40g so you can help tell me what I can delete?

---

### Post by drs305 on 2009-06-23
> **PsychedelicWonders said:**
> Where exactly do I delete the other kernals?

I went to system>admin>synaptic package manager

But I get totally lost and dont know what to delete?

Is there a way for you guys to see everything on my 40g so you can help tell me what I can delete?

In synaptic, the kernels are listed as "linux-image-2.6.XX=XX-generic" or "linux-image-2.6.XX-XX" with XX-XX being 26,27,28, etc and the latest update (11,14,18,22, etc.) So you would see which kernels are referenced in your menu.list and you could delete some of the older ones. You can also delete the same number's "linux-headers..."

The current kernel you are running can be seen by running "uname -r" in a terminal - obviously you don't want to delete that one.

These images are not huge, so don't expect a lot of extra free space once you have removed them.

---

