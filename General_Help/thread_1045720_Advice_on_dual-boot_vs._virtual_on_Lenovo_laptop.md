---
title: "Advice on dual-boot vs. virtual on Lenovo laptop"
date: 2009-01-20
forum: General Help
---

### Post by david.karr on 2009-01-20
I'm a long-time Unix user, but I've never used Linux on my personal box. Next month I'm going to get a new personal laptop (probably a Lenovo T61). I had assumed I was going to dual-boot XP (maybe Vista) and Ubuntu. I'm hearing that using virtualization may be better than dual-booting, if only for the ability to run both at the same time.

Can I get some information about tradeoffs and costs of this approach?  I get the feeling that vm software is not free.

---

### Post by rockin_goliath on 2009-01-20
Virtualbox OSE, which is in Ubuntu's software repositories, is a great free and open source solution to virtualization. There is also a proprietary (but still free) version of Virtualbox which provides the ability to use USB devices in the virtual machine (also I've never had the need).

An advantage to using Windows virtually is that it is easy to backup. Since all the files needed for the virtual machine sit in the home folder, you don't have to worry about complicated schemes to backup two operating systems. All you have to do is backup Linux, and everything else comes with it!

Another advantage is the ability to share folders between the guest (Windows) and the host (Linux). You can edit the registry to map the My Documents folder to your Home folder in Linux (or another of your choosing)

One of the sacrifices of running Windows virtually is the lack of 3d support, so if you plan on playing any graphics intensive games, use a dual-boot.

A disadvantage of a dual-boot is that if you ever want to get rid of Windows entirely, you have to wipe your hard drive and start over, which is annoying. With Virtualbox, the amount of space needed to run Windows expands dynamically, so you are only using the space that you need.

I personally used to have a dual-boot to use Adobe Audition, but since I got some pro-audio programs working in Linux, I got rid of the dual-boot, and now just use Windows XP virtually for whenever I need MS Word or Excel. It has really made my backup routines much simpler (with Sbackup) and I can use all the Linux applications that I love side by side.

---

### Post by rockin_goliath on 2009-01-20
One more thing: Virtualbox allows you to make snapshots of the virtual machine, so if you really screw something up, you can very quickly go back to the previous snapshot.

---

### Post by AliTabuger7 on 2009-01-20
Yeah, the real difference that you must consider is hardware acceleration. You will not be able to play modern games in a virtual machine. Since games are one of the only things that have been slow to get working in Wine, most users only need to go back to win to play games. In which case, a virtual machine is not appropriate.

Other than that, virtual machines can be somewhat RAM intensive. About 2GB of RAM is about as little as I would want to have on a virtual machine host.

---

### Post by rockin_goliath on 2009-01-21
Naaa, I just give Windows XP 1 out of my 3 gb of ram and it runs great. Windows Vista might be a different story, however.

---

### Post by HNP45acp on 2009-07-22
[SIZE=3][FONT=Times New Roman]Great info here [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/SIZE]
[SIZE=3][FONT=Wingdings][FONT=Wingdings][/FONT][/FONT][/SIZE] 
[SIZE=3][FONT=Wingdings][FONT=Wingdings][/FONT][/FONT][/SIZE][FONT=Times New Roman][SIZE=3]I would like to highjack the thread for a moment with something that will interest most noobies.  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I currently have been dual booting – I have a lot of work that I did in Win that would take too long to transfer to linux.  There are also a few softwares that I still have (paid lot of $) that only run on Win and there’s no alternative in Linux. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]But it’s too much work to maintain a running copy of Win, especially when I only need it once in a while. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]1)[/SIZE]      [SIZE=3]Is there an easy way to install a lite version of Win in VirtualBox so that I don’t have to give it too much RAM?  I prefer to lite it up from linux, and don’t want to use nLite because of NET.  [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]2)[/SIZE]      [SIZE=3]Will I have to use Win anti-virus/spyware? (will Win compromise my Linux?)  [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]3)[/SIZE]      [SIZE=3]How do I maintain it (i.e. periodically reinstall, update, defrag, clean up, etx)[/SIZE][/FONT][FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Thank you. [/SIZE][/FONT]

---

