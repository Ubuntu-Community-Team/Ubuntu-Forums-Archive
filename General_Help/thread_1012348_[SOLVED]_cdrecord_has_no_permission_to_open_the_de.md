---
title: "[SOLVED] cdrecord has no permission to open the device"
date: 2008-12-15
forum: General Help
---

### Post by DarkDancer on 2008-12-15
I had this problem in Hardy (never resolved) and lived with it for 6 months, now I have it in intrepid. When I try to Burn an audio CD, I get the Above error. Tell me what you need/want to know. I'm going to reboot now so I can get the disk out of the drive (another symptom). Oh, I'm trying to burn with K3b...

---

### Post by DarkDancer on 2008-12-15
Well, um, never mind, it appears that it has sorted itself...

---

### Post by jpkotta on 2008-12-15
Are you in the cdrom group?  You can check with ```
groups
```
If not, add yourself with 
```
sudo adduser $USER cdrom
```
You will have to log out and log back in for the changes to take effect.

---

### Post by SonicSteve on 2009-01-02
For those who come across this thread I had the same issue. 
I found that I needed to 
sudo chmod 777 /media/cdrom
I then did the same to /media/cdrom0 and /media/cdrom1 
these are the filesystem mount points that the cd/dvd drives use. 
I did everything I could think of to /dev/scd0 and /dev/scd1 but the device listings seemed to be fine. It seemed to be a permissions problem with the automount of CD/DVD

---

### Post by AlexanderDGreat on 2010-08-26
@sonicsteve

Hi sonic, I always use the sudo chmod 777 /dev/sr0 - it solved my problems and k3b worked fine. But when I insert a new disc it reverts back to its original permission, that is, I can't use the device it's 660 again.

How do you permanently change the device permission? Thanks.

---

### Post by 1branchonthevine on 2010-08-27
This is the only thing that worked for me... have to reboot computer after changes BTW! 
Post #34
[http://ubuntuforums.org/showpost.php?p=7185976&postcount=34](http://ubuntuforums.org/showpost.php?p=7185976&postcount=34)

---

### Post by AlexanderDGreat on 2010-08-27
A funny thing after several attempts again, the DVD broke!

Can anyone confirm that just by changing different file permissions -- break your DVD?

So I just installed a new dvd and I didn't need to change permissions and k3b went smooth running again.

---

