---
title: "What happend to the hard disk?"
date: 2008-12-26
forum: General Help
---

### Post by josephmo on 2008-12-26
I am using Ubuntu 8.1 on a system with three hard disks. sda is the boot drive for Ubuntu. sdb is the data drive.sdc has another OS on it, and I boot from it, I select through the BIOS.

When I was the only user on the system, I moved my HOME directory to the data drive, and named that partition data. From the file browser, I can see all three drives, and I can see the data drive with the label data (media/data). I could also see the third driver as well.

Moving the HOME partition to something other than the boot drive was a very complicated procedure, and when I looged in, I always got some message about the .dmrc file and how I should make sure that I am the owner and the file settings should be 644. I did all that, but I was still getting this message.

I added another user. This time around, when the new user logs on, I don't see the message about the .dmrc file and everything works fine. However, I did notice a side effect.

I can no longer see the /media/data or the third drive in the file browser. I only see the Computer and Boot. If I click on the Computer Icon, I see the /boot and Filesystem icons. When I click on the filesystem, I can click on the home icon, and that takes me to the home directory (which I know is on the /media/data disk).

If I open up a terminal session, and I log on as administrator, I can do an ls -l /media/data and it shows me everything in it. But if I do:
sudo cp -R /media/data/xxxx  /media/data/yyyy I get some sort of error message.

What do I need to do do I can see all the drives in the appropriate places. I have mount manager installed, and I tried using it. It shows me all the drives, but if I click on apply, I still don't see the drives in the file browser.

Any ideas?

---

### Post by damis648 on 2008-12-26
What filesystem are you using on /home? It MUST be Ext2 or Ext3, or whatever / is.

---

### Post by josephmo on 2008-12-26
> **damis648 said:**
> What filesystem are you using on /home? It MUST be Ext2 or Ext3, or whatever / is.

I am using Ext3

---

### Post by drs305 on 2008-12-26
The first thing I would try is to clear up the . 
 
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")


Depending on how you mounted your other drives, the reason you might not be able to see them now is that the permissions are set for viewing with the original user and not user #2.

---

### Post by drs305 on 2008-12-26
The first thing I would try is to clear up the .dmrc message you are  getting when you log in as yourself. This link explains the error message and how to correct it. It would be best to just follow the steps precisely and then deal with the other issues. The problem 'went away' it seems because you are no longer trying to log in as that user.

[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")
 
Depending on how you mounted your other drives, the reason you might not be able to see them now is that the permissions are set for viewing with the original user and not user #2.

---

### Post by josephmo on 2008-12-26
> **drs305 said:**
> The first thing I would try is to clear up the .dmrc message you are  getting when you log in as yourself. This link explains the error message and how to correct it. It would be best to just follow the steps precisely and then deal with the other issues. The problem 'went away' it seems because you are no longer trying to log in as that user.

[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")
 
Depending on how you mounted your other drives, the reason you might not be able to see them now is that the permissions are set for viewing with the original user and not user #2.

Yeah, the problem went away when I logged on as another user. This is why I did it, to figure if it's an issue with all accounts, or just that account.

In any case, I re-did the steps, and the .dmrc message went away. This is odd, because I had already done these steps, and things were working fine, and one time after logging in, I started getting this message.

I still don't see the second drive. How do I remount it, without destroying its contents? It's my HOME partition, and things are stored fine there, but it does not show me the drive.

---

### Post by drs305 on 2008-12-26
I don't understand your situation and delayed responding in hopes someone did. Are you trying this as the original user or as user2? 

Let's start with a known. Log on as user1. 
Confirm that your $HOME is where you think it is. Compare these command results:
```
 
ls /media/data/wherever.you.think.home.is
ls $HOME 

```

Tell us what you cannot see that you want to be able to view.

Please post the contents of:
```

sudo blkid -l
cat /etc/fstab
mount | grep "/dev/"

```

---

