---
title: "How can I convince my mom to let me convert to a parition?"
date: 2009-06-20
forum: General Help
---

### Post by alienkid10 on 2009-06-20
I use WUBI because mom wouldn't let me install before, because she feared for Windows. But after talking to her a bit she was giving at letting me partition and install that way, but then she talked to a friend we have who uses Linux on almost all his PCs. The friend said "WUBI just partitions in a different way..." I KNOW that's not [completly] true! It installs in a file not partitions in a different way. How can I convice her? Also we don't have CD recovery media but we do have a recovery partition so I was wondering how to convert that to a bootable CD as a just in case.

---

### Post by hyperdude111 on 2009-06-20
You can install onto a usb device and use that as your partition. However read guides before you do this, I "broke" my dads computer last summer doing this before i was experienced with linux.

---

### Post by merlinus on 2009-06-20
You are absolutely correct about wubi.  It still is running on windows, not on linux.

What version of windows?  And what are your system specs?

---

### Post by lisati on 2009-06-20
Some computers that come with a recovery partition come with an option to create bootable recovery CDs or recovery DVDs. Have a good look through the programs installed in Windows and, all going well, you might find something suitable for making a backup of your recovery partition.

---

### Post by alienkid10 on 2009-06-20
XP SP3 home sys spcs: [ATTACH]118379[/ATTACH] gathered from Ubuntu.

I have looked from progs installed to do that but can't find anything.

---

### Post by mike555 on 2009-06-20
Before you delete Ubuntu from your Windows , be sure to read up about changing the "boot.ini" file in Windows ... or you might not be able to boot Windows again ..........
  and of course if you are going to install Ubuntu to a separate partition and keep Windows be sure to read up about picking "manual partition" during the install or you will erase Windows and it will be gone.........

---

### Post by alienkid10 on 2009-06-20
why does boot.ini need to be edited?(edit: oh to remove wubi?) I have installed manual partitioning in VMs and have read a lot about. So I sort of will know what I am doing. I just need to convince her to let me partition...

---

### Post by merlinus on 2009-06-20
Promise to clean your room and take out the garbage daily for a year....:lolflag:

---

### Post by alienkid10 on 2009-06-20
that might work but... no. My room stays clean most of the time.

---

### Post by merlinus on 2009-06-20
OK.  Perhaps you can create a cd or usb boot disk for windows, and demonstrate it to your mom as proof of your skill.

---

### Post by alienkid10 on 2009-06-20
Not that good, and she knows my skill level.

---

### Post by raymondh on 2009-06-20
you can tell her that if windows crashes, so does the WUBI-installed Ubuntu hence you both won't have any OS to work on until you get windows fixed.

---

### Post by howefield on 2009-06-20
Of course, you mom might just be more aware of your capabilities than you are ;-)

Do you have a track record for good ideas badly executed ?

You're correct to be careful about how you get back to where you are now in case of disaster. Bear in mind that the recovery partition may only get you back to factory default, ie all your data files, including passwords, email, programs ect are at risk. You want a fool proof backup contingency plan a bit stronger than "we do have a recovery partition"

---

### Post by alienkid10 on 2009-06-20
a track record for good ideas badly executed not really. I understand a recovery partition will go bye bye I/it messes up my partition table, that's why I want CD version of it. I'll back up before the install anyhow so personal things won't be a problem.

any other tips?

EDIT: [raymondhenson]("http://ubuntuforums.org/member.php?u=769495") just saw you're post and you have a point, but she'll just say "so we won't be able to use it until it's fixed."

---

