---
title: "Home Folder Symbolic Link"
date: 2006-07-29
forum: Desktop Environments
---

### Post by jonnymccullagh on 2006-07-29
I have 2 hard drives and I am using one as the Kubuntu Dapper drive and I would like to use the other as my home folder but since I have not done this before I would like some clarification.
I will partition/format hdb1 as ext3 and set up /media/home in my fstab.
I would then like to create a symbolic link e.g.:
```
ln -s /home/jonny /media/home
```
So my questions:
1. Is this OK?
2. Do I need to delete the stuff I have already in /home/jonny e.g. /home/jonny/Desktop and /home/jonny/EasyUbuntu? If not, what happens to it when I make the link?
3. Do I need to change permissions on any of these directories?
Thanks in advance,
jonny

---

### Post by win_zik on 2006-07-29
I don't think a symbolic link makes any sense. Simply mounting the hd as /home in fstab seems to be the better way.

Be sure to make a backup of your homedir before you try this.

---

### Post by aysiu on 2006-07-29
I agree with win_zik: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by win_zik on 2006-07-29
> **aysiu said:**
> I agree with win_zik: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)
Just wanted to say, nice guide. Now that I know it I'll certainly link to it if the question comes up again.

Now enough with the thread hijacking. :D

---

### Post by jonnymccullagh on 2006-07-30
Thanks Folks,
I read over that guide and I tried a few things but I am now stuck.
- I converted a partition (hdb1) to ext3 using Gparted
- I backed up my home sudo mv /home to /home_backup
- I created a new home for for the mount point:  sudo mkdir /home
- I edited the fstab and added a line:
/dev/hdb1 /home ext3 nodev,nosuid 0 2

When I reboot and try to login as jonny I get an error:
Could not start kstartupconfig. Check your installation

This is understandable as there is no directory named /home/jonny

So I went back to the live CD and mounted my dapper install and the ext3(hdb1) I want to use as my home. I figured I would be able to copy and paste the directory /home_backup/jonny from my dapper install to my new ext3 home (hdb1)
I cannot copy and paste and even when I try to do this in a terminal I get error: 
cp: omitting directory `/media/dapper/home_bak/jonny'

I created a folder for the user jonny on the hdb1 and was able to copy files there but not directories - getting the same error as above.
I think this is a permissions problem but I cannot work it out.
Any more help would be appreciated,
thanks,
jonny

---

### Post by jonnymccullagh on 2006-07-30
I sorted things out and got it working.
I used the standard Kubuntu Dapper home and mounted my new home as /media/newhome
I then copied all of /home/jonny to /media/newhome/jonny
I then set up /etc/fstab with the details above and rebooted.
It worked OK so I have now got my home directory on a seperate hard drive :D I'm still not sure why I was having those problems but I think it was a permissions issue inside the LiveCD.
Thanks for the pointers,
jonny

---

