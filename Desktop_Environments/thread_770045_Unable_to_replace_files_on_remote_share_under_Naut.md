---
title: "Unable to replace files on remote share under Nautilus"
date: 2008-04-27
forum: Desktop Environments
---

### Post by mcmunt on 2008-04-27
Strange one, this one.

On a remote Win share, copy one file from a folder and paste into another to replace a file of the same name. Prompts as expected asking whether I want to replace or skip this file. Choose replace and an error message window appears saying "error while copying 'filename'". The error details say "Error renaming temporary file: Text file busy".

Doesn't matter what files I try to copy/replace, some are text based, some are images (png, jpg, etc), the error is always worded the same.

If I copy the same files on the cmdline, it works just fine. If I do the same copy/replace process on my local drive, it works. If I do a normal copy without the replace, it's fine.

Before the upgrade to Hardy I never saw this problem. Anyone got any ideas?

I've re-mounted the drives and reset all files to 0755 and made sure I'm the owner.

---

### Post by mcmunt on 2008-04-27
Bump, bump. Anyone?

---

### Post by nquinnathome1 on 2008-04-27
I don't seem to have that problem; I placed a file on a Windows share, made a copy of it on another folder on the same share, then copied that file and pasted it back to where the original file was and it replaced it no problem at all.

What copy of Windows is running the share? How are you mounting it? As a permanent (fstab entry) or on an as-needed basis?

---

### Post by mcmunt on 2008-04-28
The share is on a Windows Server 2003 box and it's being mounted from fstab with the following lines,

//192.168.0.10/www    /media/www      smbfs    auto,credentials=/root/.credentials,uid=1000,umask=000,user	0 0
//192.168.0.10/movies    /media/movies      smbfs    auto,credentials=/root/.credentials,uid=1000,umask=000,user	0 0

I double-checked the .credentials file is still there and has the right username and password. I think it's mounted OK as using cp and Midnight Commander to do the file copy gives no problems. But using Nautilus to copy files creates a hidden tmp file in the destination and GEdit will not save any changes to the files. Another editor, Geany will save the files and MC can also edit and save the same files OK??!!

I have noticed that the trash folder on this share is now called .Trash-1000 rather than .Trash-myusername. Listing file permissions also shows -rwxrwSrwx for all of the files. Excuse the noob question but what's the S for?

---

### Post by nquinnathome1 on 2008-05-09
Interesting; I've never seen or used it myself, but an S in that area means 'change group ID on execution' - meaning when the file(s) are executed, the process will 'inherit' the rights of the group of the owner of that file, rather than the rights of the person executing the file as normally happens.

With regards to your fstab entries, try changing them slightly; your www folder is currently:

```
//192.168.0.10/www /media/www smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user 0 0
```

Try changing it to:

```
//192.168.0.10/www /media/www smbfs credentials=/root/.credentials,uid=1000,file_mode=0770,dir_mode=0770 0 0
```

---

### Post by rje_nc on 2008-10-24
I am having the same problem when I try to copy a file to my mounted Windows Server share from my Ubuntu system using Nautilus.  I get the msg: Error renaming temporary file: Text file busy

I can delete the file from the server using Nautilus and then drag the file over to the Windows share without any problems.  This is very frustrating!

I am running v8.04.1 and my fstab lines look like this:
//cgserver/shared	/mnt/servershared	cifs	credentials=/.winpasswd,uid=bob,gid=cge,_netdev 0 0
//cgserver/bob_docs	/mnt/serverbob	cifs	credentials=/.winpasswd,uid=bob,gid=cge,_netdev 0 0
//cgserver/cge		/mnt/servercge	cifs	credentials=/.winpasswd,uid=bob,gid=cge,_netdev 0 0

I added the file_mode=0770,dir_mode=0770 entries to fstab and rebooted but this had no effect on the problem.

I don't think it is a permission issue because I can copy new files and create directories without problems.  I can also open a document from the mounted share and save it back to the server using Openoffice or Moneydance without any problems.  It appears to be a Nautilus issue.

Any suggestions would be appreciated...

P.S.:  I noticed that if I mount the folder from Nautilus (Places/Connect To Server), I can copy over the file.  It is only when I try to copy over to a folder mounted from fstab.

---

### Post by rje_nc on 2008-10-25
I may have found a solution to my problem copying files over an older version on a Windows share.  I added the noperm option to the mount parameters in fstab and now I can drag a new version over the older one without any errors.

Bob

---

### Post by pharbar on 2009-05-08
Same problem here.  However, the problem seems to be in Nautilus itself, as Thunar works fine, to the point of correctly receiving newer versions of a files copied within, or dragged over from Nautilus. Saving newly edited files on the share FAILS for text files (using Gedit, even if opened from a Thunar window), but SUCCEEDS for Open Office documents (even if opened from a Nautilus window). Is this because Gedit is tightly bound in with Nautilus?

The mount command I use (either in a terminal or in a nautilus script) is:
sudo mount -t cifs -o -ssh //192.168.0.2/studydocs /media/studydocs

To summarise: the problem lies in Nautilus (and Gedit) being unable to rename existing files on a mounted remote share. Since Thunar can do this reliably with the same permissions, surely it's simply a Nautilus (or related) bug?

PS: I'm still on 8.10, since 9.04 was giving me graphics driver problems.

---

