---
title: "Mounting with SMB doesnt show certain folders"
date: 2005-07-11
forum: Desktop Environments
---

### Post by flak9 on 2005-07-11
Long time browser, first time poster!  I have been using HH for several months and love it!  Except for this little problem.  I have tried many different things in fstab and none have been working.  Here is the situation:

I have Windows Server 2003 running several windows shares on the network.  When I use the code below to mount directories that have fewer than approx. 500 small directories inside the share they all work fine with read/write.  I have one directory that is shared and has about 1800 directories that is giving me all kinds of fits.  For instance, when I begin playing an mp3 from one of the dir's inside the share, it plays fine.  Now when I try to go back and access the share again it shows no directories OR something like 767.  It shows the correct free space but half or all of the folders disappear!  I know the drive is working great and all other windows pc's have no problem working with it.  The permissions seem fine because it allows me to read and write but as soon as I stop playing that first file and go back and list, it causes that problem.  

When I use the connect to network server option from the menu it lists all the folders (1767) correctly, but in order to open or play files, I have to copy them to my local ubuntu machine.

When I mount using the code below everything seems to mount fine on the small shares.  When I begin browsing the big share using the same in my fstab, the problems occur.  Can anyone point me in another direction if this isnt the way to go for that big of share.  I am starting to run out of things to try.  All I care about is being able to read.  Writing to that share is not a top of the list priority!

```
 //192.168.0.252/winshare        /home/ryan/Desktop/NShares/winshare  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

Thanks  :)

---

### Post by mp3guy on 2005-07-12
have you tried checking show hidden files in nautilus?

---

### Post by flak9 on 2005-07-12
Yep.  I even made one file hidden and that files shows fine.  I am thinking about trying NFS.  Does anyone know of any good Windows Server 2003 to Ubuntu NFS how to guides?  I have seen some linux to linux guides, but none for win2k3.  Ive got Services for UNIX installed already but never worked with NFS.

Last night I went a ahead and copied about 1000 folders from that non working share to another drive and am going to try and create another share and fool with more permissions.

---

### Post by flak9 on 2005-07-12
Ok, I went ahead and installed mandrake 10.1 on one of my older machines.  It works fine.  It seems to be a problem with ubuntu, because it does it on both my Hoary laptop and desktop  :?

---

### Post by flak9 on 2005-07-12
I decided to dump smb with that share.  I setup NFS and everything is working fine.  NFS is running a tad slow for my tastes.  I would still like to know why smb won't work with directories that big.  I googled until my eyes couldnt take the lcd anymore.  I will still play with it and post if I find why.

---

### Post by Trops on 2005-08-10
sort of related I suppose but what are you using to play MP3s from your network drive under samba? I can access the shares but can't play the mp3 files

---

### Post by GreySim on 2005-08-11
I'm having problems with disappearing folders in shares with less than 20 folders, so I don't think the problem is necessarily just that your share is so large.  I have absolutely no idea how to troubleshoot this though, so I've just left it alone for now, and am only sharing so that you might benefit somehow in your own troubleshooting.  :)

---

### Post by tombeharrell on 2005-08-11
I've got a problem with Windows 2003 shares from Ubuntu too. When I mount them from Places -> Connect to Server, they mount fine and I see all the files and directories. However trying to access a subdirectory it hangs. I have to click the X, which gives me a Force Quit option after a few seconds.

Any thoughts?

Tom.

---

