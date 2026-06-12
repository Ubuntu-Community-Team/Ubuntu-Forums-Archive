---
title: "Dual Boot With WindowsXP"
date: 2004-10-18
forum: General Help
---

### Post by RevJack on 2004-10-18
Does Ubuntu autmatically set up a dual boot with WindowsXP? I am thinking of giving Ubuntu a try, but want to dual boot with XP.

---

### Post by triad169 on 2004-10-18
Theoritically It should....  But not fool Proof.  Depends alot on how you have Hard Drives and Partitions setup.  If you do run into a problem just post A question up here and we can work out.  GRUB is pretty flexible.

Triad

---

### Post by adbak on 2004-10-18
I had a problem resizing my WinXP partition so that I could dual boot.  I ended up having to reinstall WinXP, this time setting up the correct partitions.  However, I had backed up everything before hand.  Even if I hadn't, it would have been worth the inconvenience because Ubuntu is just that awesome.

---

### Post by stodge on 2004-10-18
No problems here at all. I didn't touch my WinXP partitions, but manually edited the ones for Linux that used to hold Fedora.

---

### Post by RevJack on 2004-10-18
Thanks! I already dual boot XP with another Linux distro, so if Ubuntu can just take over the Linux partition, that would be great!

---

### Post by drunken-wallaby on 2004-10-19
if the boot partition of windows is located at hda1 you should not realize any problems. if now, you may have to configure the grub.conf manually...

---

### Post by RevJack on 2004-10-19
WindowsXP is on hda1. Thanks!

---

### Post by Hutch on 2004-10-19
I am dual booting XP with Ubuntu. To do the repartioning I first installed SUSE 9.1. I also setup an extra FAT32 partition to easily share data.

My only complaint about the Ubuntu setup was that it installed GRUB into the MBR without my intending it. I had wanted to add it into the NTLDR of my XP partition and boot that way. Mostly due to lingering concerns about having some application (Norton?) freak out about the MBR, and also because this is a Thinkpad T42 with some built-in IBM restore &amp; recover functionality in an extra partition. Of course, I'm sure it was user error on installing to MBR, and so far there have been zero ill effects.

Ubuntu is the best distro I've used so far (RH, Caldera, Turbolinux, and SUSE up to now)

---

### Post by stodge on 2004-10-21
I installed Ubuntu onto another PC with XP already installed. The installation was ok, but the MBR wasn't set up properly. When I rebooted the PC after the first part of the installation of Ubuntu, I got an error about NTLDR not being found. I had to re-install XP as I couldn't fix the MBR or repair the installation. :(

---

### Post by dcs on 2004-10-21
I am trying to dual boot with Ubuntu and Win XP. I've got a 2 gig NFTS partition with windows on it, a 90 gig ext3 partition with Ubuntu on it, a 50 gig FAT32 partition with music going to go on it (empty at the moment) and a half gig swap partition. I installed windows fine and then went onto instal ubuntu which I thought had also gone fine. Unfortunately when I tried to boot into windows I realised that GRUB wasn't giving me an option for booting to XP, only ubuntu. Reinstalling XP allowed me to boot into windows but not ubuntu. I'm now in ubuntu again with no windows XP.

I've been told that altering GRUB's menu.lst file might help if I add windows to it but it's read only and I'm not sure how I can alter it. Apart from this I have no idea how to setup a dual boot. Any ideas would really be appriciated, thanks.

---

### Post by eggshin on 2004-10-21
I'm currently dual booted with win-server2003 and ubuntu--works like a charm.

---

### Post by Araphel on 2004-10-24
To access the menu.lst file you need to enable logging into root in gdm.  Then login as root/password.

I'm new to linux and I can't remember exactly where I found the Root in GDM option. But it shouldn't be hard to find. I'm surprised someone more knowledgable hasn't answered this yet.

---

### Post by Trance56k on 2005-02-25
Just dont do what I did. I had my windows xp on the slave drive and tried to install Ubuntu on the master. Man that is a headache waiting to happen. Im now reformating both xp and Ubuntu lol. XP on the master drive this time. It turns out Ubuntu just installed it self and did not even detect Windows. So I tried rewriting the mbr. That didnt work either! Trial and error.

---

### Post by doc_b4 on 2007-05-30
> **dcs said:**
> I am trying to dual boot with Ubuntu and Win XP. I've got a 2 gig NFTS partition with windows on it, a 90 gig ext3 partition with Ubuntu on it, a 50 gig FAT32 partition with music going to go on it (empty at the moment) and a half gig swap partition. I installed windows fine and then went onto instal ubuntu which I thought had also gone fine. Unfortunately when I tried to boot into windows I realised that GRUB wasn't giving me an option for booting to XP, only ubuntu. Reinstalling XP allowed me to boot into windows but not ubuntu. I'm now in ubuntu again with no windows XP.

I've been told that altering GRUB's menu.lst file might help if I add windows to it but it's read only and I'm not sure how I can alter it. Apart from this I have no idea how to setup a dual boot. Any ideas would really be appriciated, thanks.
all you have to do is , on an empty hard drive, i used a 20 gig, install ubuntu. then boot from live cd, then go to gnome paqrtition editor. you will find a non allocated partition. format this partition ntfs. restart computer and boot win xp setup. setup windows on drive c. then restart computer and boot from live cd. go to gnome partition editor. delete aqll partitions except the ntfs. now install ubuntu again, this time choose to setup in freespace. ubuntu will recognize xp and when you reboot you will have a choice to use xp or ubuntu.

---

### Post by ori1porat on 2008-02-20
Hi, well im running on windows xp media center and i want to try ubuntu out. so i want to dual boot i guess. so i would like to ask for some help. i dont know how to do this. do i HAVE to partition my hdd or can i install ubuntu on c as well? can someone give me a step by step guide or mail me or something. thanks!

---

### Post by Nameless_one on 2008-02-20
Grub's menu.list is read-only, but you can edit it as root. Just ```
$ sudo gedit /boot/grub/menu.lst
``` and you can edit the file. 

(You might have to replace sudo with gksudo, which is the equivalent for graphical applications)

Also, adding a windows partition is fairly simple (I think there is an example in the file, too). In my machine, I just added this to the end of the file:
```
title           Microsoft Windows XP Professional
root            (hd0,3)
makeactive
chainloader     +1

```

All you have to do is figure out what to write in "root". You need to point it to the partition where Windows lies. Check [this](http://ubuntuforums.org/showthread.php?p=1319395) out. 

Also, if you find that the Windows boot sector is broken, you don't have to reinstall Windows. You can restore the boot sector with a Windows CD, using recovery console, and the FIXMBR command. However, I suggest that you use this with EXTREME caution, ONLY if you definitely know what you're doing.

---

### Post by Nameless_one on 2008-02-20
@ori1porat
You have to partition your drive and install ubuntu on a different partition. [This](http://www.psychocats.net/ubuntu/index.php) page might help you start. 

Basically you want to make a partition for Ubuntu, and install it on that partition, and then install Grub (a multi-loader for different Operating Systems), and point it towards Windows as I described above.

---

