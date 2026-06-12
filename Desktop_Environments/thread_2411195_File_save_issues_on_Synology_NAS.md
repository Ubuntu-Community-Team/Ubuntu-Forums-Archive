---
title: "File save issues on Synology NAS"
date: 2019-01-26
forum: Desktop Environments
---

### Post by sawozny on 2019-01-26
I have an SMB share on a Synology DiskStation NAS DS216J with a mirrored pair of 4TB drives that I’ve been using with no problems with my Ubuntu 16.04 workstation for almost 2 years.  I recently needed to move to 18.04 for a new version of GNUCash but since then I’ve been experiencing intermittent weirdness writing to my share.  Sometimes a write would end up with an incomplete file, but I wasn’t able to get it to do it consistently until now.  

When I use the current version of FreeCAD 0.17 and I write to the OS’s local disk (my desktop or my home folder) files write fine, but when I try to write to the SMB share (either by saving a file in FreeCAD’s native format or doing an export of a different format for slicing software to use, etc...), the file appears where it’s supposed to, but is zero bytes.  I can repeat it any time I want to, but FreeCAD is the only software I can make do it consistently.  I’ve checked with the FreeCAD forums, but nobody seems to be having this problem (perhaps no one has this NAS) and logging within the application doesn’t seem to log disk writes so there are no clues there.

Does anyone have any suggestions for how to get more detail on disk write operations? Particularly in GVFS SMB mounted shares?  

Alternatively, can anyone with 18.04 and access to an SMB share and / or Synology NAS see if this is a general GVFS/SMB problem in 18.04 or just related to this NAS?  The steps to duplicate are fairly simple.

    1. From a terminal:
        a. sudo add-apt-repository ppa:freecad-maintainers/freecad-stable
        b. sudo apt-get update
        c. sudo apt-get install freecad
        d. freecad
    2. Within FreeCAD:
        a. File -> New
        b. In the dropdown that defaults to Start choose Part
        c. Click on the gold cube icon (hoverover is “Create a Cube Solid”) and a cube should appear in the workspace.
        d. File -> Save to Desktop or ~Home.  A file should appear about 3K in size.
        e. File -> Save As to SMB share.  A file of the same size should appear, but ends up being 0 bytes, which is my problem, particularly considering there is no screen feedback indicating something went wrong; that’s why I’m trying to find the right log file.

If this can’t be replicated on any SMB share, I’ll take it to Synology and see what they can tell me, but this operation worked fine under Ubuntu 16.04 with this software.  The only thing that’s changed is I’ve moved to 18.04 but that’s a significant move involving a lot of pieces so I’m not sure where to start looking.  

Any suggestions would be appreciated.

Thanks,

Scott

---

### Post by him610 on 2019-01-26
Now, I had never heard of freecad until I read your post. I just installed freecad from the repository because I was curious about your issue. I have a file server on my network with both smb/cifs and nfs servers running on it. 
Your *step e* is where I can not continue. There is no *Save to SMB share*, only the local directories/folders show up on my freecad console (could be a configuration issue.)
However, my installed freecad has a python console that shows all of the commands issued. 
You may have a permission issue with your NAS.
Have you considered saving the file locally then copying (backup) the saved file to your NAS device?

There is a freecad directory in your home directory, ~/.FreeCAD that contains at least a couple of configuration files, and possibly your log files.
This is what mine looks like.
```
hugh@G4560:~$ ll .FreeCAD/
total 24
drwxrwxr-x  2 hugh hugh 4096 Jan 26 22:20 ./
drwxr-xr-x 48 hugh hugh 4096 Jan 26 22:44 ../
-rw-rw-r--  1 hugh hugh  924 Jan 26 22:59 system.cfg
-rw-rw-r--  1 hugh hugh 8213 Jan 26 23:05 user.cfg
 
```

From the main freecad console, if you navigate to Edit>Preferences, there is a tab *Output window* where you can select whether you want to record log messages, warnings, and errors (with color codes). In the tab *Macro,* it appears you can select to Log all commands ... to a file, and you get to select where the file is written - maybe .FreeCAD/scripts (which might be adjacent to .FreeCAD/logs - just guessing)

You may know all of this already, but I am just trying to help out. Good luck.

---

### Post by sawozny on 2019-01-27
> **him610 said:**
> Now, I had never heard of freecad until I read your post. I just installed freecad from the repository because I was curious about your issue. I have a file server on my network with both smb/cifs and nfs servers running on it. 
Your *step e* is where I can not continue. There is no *Save to SMB share*, only the local directories/folders show up on my freecad console (could be a configuration issue.)

I'm sorry, I should have put quotes around the actual command.  Step e was To execute a "File -> Save As" and then save to your SMB share.  One would expect that the SMB share would show up in the left hand nav in the dialog, but it doesn't seem to in this case.  I've learned you can get to it by navigating the local file system from the root to /run/user/1000/gvfs and then into the folder smb-share: and whatever you call your share.  This will put you at the root of that share and when I save a FreeCAD file there, the file appears, but is 0 bytes.  I'm curious if someone else with access to an SMB share gets the same results.  If they do, I'll focus on GVFS, Samba and the OS.  If they don't, I'll turn my focus to the NAS's SMB server implementation.

> **him610 said:**
> 
You may have a permission issue with your NAS.
Have you considered saving the file locally then copying (backup) the saved file to your NAS device?


I briefly considered there might be a permission issue, but a couple things suggest it's not the case.  First, I can drag and drop a file in Nautilus to the same location on the share I'm trying to save to from FreeCAD while running it as my regular user ID and second until my 18.04 upgrade, there were no problems saving to anywhere on this share.  My user ID is an administrator on that share.  And yes, the copying of files to the NAS after I save them locally works and is my present workaround, but I don't want to leave it this way permanently because I just know some day I'm going to forget, save a file I've put a lot of work into on the NAS, and then lose all that work.

> **him610 said:**
> 
There is a freecad directory in your home directory, ~/.FreeCAD that   contains at least a couple of configuration files, and possibly your log   files.
This is what mine looks like.
```
hugh@G4560:~$ ll .FreeCAD/
total 24
drwxrwxr-x  2 hugh hugh 4096 Jan 26 22:20 ./
drwxr-xr-x 48 hugh hugh 4096 Jan 26 22:44 ../
-rw-rw-r--  1 hugh hugh  924 Jan 26 22:59 system.cfg
-rw-rw-r--  1 hugh hugh 8213 Jan 26 23:05 user.cfg
 
```

From the main freecad console, if you navigate to Edit>Preferences, there is a tab *Output window* where you can select whether you want to record log messages, warnings, and errors (with color codes). In the tab *Macro,*   it appears you can select to Log all commands ... to a file, and you   get to select where the file is written - maybe .FreeCAD/scripts (which   might be adjacent to .FreeCAD/logs - just guessing)

You may know all of this already, but I am just trying to help out. Good luck.

I did try ramping up logging at the places you mentioned as well as running FreeCAD with a -l switch but nothing indicating anything is amiss during disk operations was logged.  But I appreciate the second set of eyes.  

If I could further appeal upon your good nature, can I get you to try a save to your SMB share just to narrow my search field a little?

Thanks,

Scott

---

### Post by sawozny on 2019-01-27
Oh, one more thing. There is apparently some ambiguity regarding where to find GVFS mounted shares.  If you don't find your SMB share where I said, run a "sudo ps -aux | grep gvfsd-fuse" and the folder in the result after the gvfsd-fuse path should be where your GVFS shares are mounted.  I would think if we're running the same version of Ubuntu they should use the same mount point, but just in case.  :)

---

### Post by sawozny on 2019-01-29
FYI, I found a new way to replicate this problem.  Any save to my SMB share from Notepadqq results in this error: 

Error trying to write to "/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/new 1.txt"

In the show details box, all that's there is "Invalid Argument".  I'm going to see if Notepadqq is any less active when "idle" than FreeCAD is and give the comparative strace approach a try.

---

### Post by him610 on 2019-01-29
> I just know some day I'm going to forget, save a file I've put a lot of work into on the NAS, and then lose all that work.
Just a thought - You could probably schedule a cron job to periodically (daily, hourly, etc) rsync your local files to your NAS. 
There are some folks who provide help and advice in these forums that are real experts using cron and rsync

---

### Post by sawozny on 2019-01-30
> **him610 said:**
> Just a thought - You could probably schedule a cron job to periodically (daily, hourly, etc) rsync your local files to your NAS. 
There are some folks who provide help and advice in these forums that are real experts using cron and rsync

Moving my regular workspace and doing some sort of scheduled sync is on the list of fallback possibilities, but I'm hoping I can locate the actual problem so it doesn't come to that.  :)

BTW, knowing where the SMB share is now in the root filesystem, were you able to try saving a file from FreeCAD to see if the file saves for you or ends up at 0 bytes?

Thanks,

Scott

---

### Post by sawozny on 2019-02-03
Trying to isolate the problem, I built an SMB share on a Windows 7 Pro machine to see if I still had this problem and I did.  So it's definitely not a NAS problem.  Then I took the SMB versions on the NAS and the Win7 machine to SMB1 and the save process started to work again when each was reduced to SMB1 and then broke when I went to SMB2.  I don't want to leave this share at SMB1, so I'm going to do my comparative tests with SMB1 vs SMB2 rather than local vs SMB.  More as it develops (hopefully).

---

### Post by 1clue on 2019-02-04
Have you tried exposing your SMB share as NFS on the synology, mount in the native UNIX file sharing mode and trying again?

Synology can expose your native file sharing protocol, using multiples for the same directories. SMB/CIFS, Mac and UNIX.

---

### Post by sawozny on 2019-02-04
That's a good point.  This way I don't have to mess with my Windows clients.  I've been considering this, but I'm presently in "dog with a bone" mode and want to see what I can do to fix (or even just properly identify) THIS problem, rather than working around it in case someone else gets bit by it.  What I hope will happen is that I'll put enough data together at the system call level to log a solid bug, but OS development is far beyond my present skill set so I'll gather what data I can and hopefully someone with the skills to do something about it will be able to fix it while I access my NAS over NFS so I can get on with my life.  :)

---

### Post by sawozny on 2019-02-04
For anyone following along, my earlier statement about this working fine under Ubuntu 16 and not under Ubuntu 18 turned out to be only because Ubuntu 16.04 only speaks SMB1 out of the box and my share was set to allow SMB1 connections if SMB2 didn't work out. So the issue is really SMB1 vs SMB2 and not Ubuntu version related because when I made the Ubuntu 16 system connect to the share over SMB2 the 0 byte problem happened. So while I was hoping to do comparative straces between working Ubuntu 16.04 talking to an SMB2 share and non-working Ubuntu 18.04 talking to an SMB2 share, SMB2 connections from both have this 0 byte file problem.

So, I proceeded to compare the straces between SMB1 and SMB2 saves on the same Ubuntu 18.04 system. What I found was in an SMB1 save, at the moment of truth, this system call happens:

```
openat(AT_FDCWD, "/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube.042708c2-dad1-487c-ab5f-3187f9fa4e4c", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 34
```
The 34 is the file handle and the system proceeds to write to that file handle, like:


```
write(34, "PK\3\4\24\0\0\0\10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\f\0\0\0Do"..., 1004) = 1004
```

and so on until the whole file is written, then it does the rename and checks it's work by making sure there is no file with that destination name, doing the actual rename and then making sure there is a file with the name expected in that location:

```
access("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube", F_OK) = -1 ENOENT (No such file or directory)
rename("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube.042708c2-dad1-487c-ab5f-3187f9fa4e4c", "/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube") = 0
access("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube", R_OK) = 0
```

And all is well in the world. I have a working file on my SMB1 share.

In the SMB2 scenario, the original file creation has some sort of problem:

```
openat(AT_FDCWD, "/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube SMB2.435bf00e-f823-40d2-b216-c98834210f3f", O_WRONLY|O_CREAT|O_TRUNC, 0666) = -1 EINVAL (Invalid argument)
```

This return is despite the fact that there IS, indeed, a file of that name in that location, which we will see below. So, in the absence of a file handle, no writes occur but the code proceeds to the rename stage as if it had written the file (which is probably why no screen feedback occurs that there was an error). The rename happens via the standard process of checking to see if the destination name is in use, doing the rename and then checking for the file of the new name, but since there was no data written to the file (how could there be with no file handle returned in the first place?) the file is 0 bytes:

```
access("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube SMB2", F_OK) = -1 ENOENT (No such file or directory)
rename("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube SMB2.435bf00e-f823-40d2-b216-c98834210f3f", "/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube SMB2") = 0
access("/run/user/1000/gvfs/smb-share:server=diskstation,share=fileshare/Test Cube SMB2", R_OK) = 0
```

My next step is to see if there's a way for me to dig further into the openat call and see what went wrong on the SMB2 connection vs the SMB1 connection getting a file handle returned.

If anyone has any suggestions on how to proceed, particularly on how to find out why the openat on the SMB2 share returned a -1 rather than a file handle, I'd love to hear your thoughts.

Thanks,

Scott

---

### Post by Morbius1 on 2019-02-05
I'm getting confused by your posts most likely because I do not have your NAS.

The Linux client through the File Manger will negotiate with the server ( NAS ) the correct smb dialect to use between values set by the "client min protocol" and the "client max protocol". Now in Ubuntu 16.04 it didn't get very far since the max is set to NT1 ( samba speak for smb1 ). But in Ubuntu 18.04 the max is set to smb3 so it should be able to negotiate the dialect to use between smb1 to smb3 automatically.

So the thing that's confusing me here is what is the NAS set at. I found a synology demo here: [https://demo.synology.com/en-uk/dsm](https://demo.synology.com/en-uk/dsm) and you are allowed to set the min and max _server_ protocol between smb1, smb2, something called "smb2 with large MTU" ( I have no idea what that is but I'm guessing that is a reference to smb2.1 ), and smb3.

Your description almost sounds like an oplock ( opportunistic locking ) issue not an smb dialect issue but you would have had the same issue with Ubuntu 16.04 since the smb dialect used should not make any difference.

---

### Post by sawozny on 2019-02-05
> **Morbius1 said:**
> I'm getting confused by your posts most likely because I do not have your NAS.

Actually, it's much more likely because I've done a poor job keeping it straight for anyone but me.  I may need to start a new thread as it's drifted pretty far from the original.  I initially thought it might be my NAS because if it wasn't more people would be affected.  Then as I proceeded with troubleshooting, I realized it's not the NAS because I can duplicate this problem on any share I make an SMB2 connection with and it's not a new problem introduced in Ubuntu 18.04 vs 16.04 because I have the same problem if I add client min and max protocol lines in smb.conf forcing a connection over SMB2, rather than the SMB1 connection I was getting using Ubuntu 16.04 because my NAS was allowing either SMB1 or SMB2 (it's default setting).  Now in 18.04 that allows SMB2 connections out of the box, it tries an SMB2 connection with my NAS and succeeds, but that connection is buggy (I have LOTS of other problems with the SMB2 share, but this FreeCAD issue is the only way I can presently demonstrate it consistently) and I have this 0 byte file problem I'm trying to isolate because I think there's a bug somewhere in the OS / GVFS / the SMB subsystem.  So, I definitely get why it's confusing.  Perhaps I should have started a new thread.

> **Morbius1 said:**
> The Linux client through the File Manger will negotiate with the server (  NAS ) the correct smb dialect to use between values set by the "client  min protocol" and the "client max protocol". Now in Ubuntu 16.04 it  didn't get very far since the max is set to NT1 ( samba speak for smb1  ). But in Ubuntu 18.04 the max is set to smb3 so it should be able to  negotiate the dialect to use between smb1 to smb3 automatically.

Exactly my experience, except with a modification to smb.conf on Ubuntu 16.04 as you described, it can be made to make an SMB2 connection which also gives me the 0 byte file problem.

> **Morbius1 said:**
> So the thing that's confusing me here is what is the NAS set at. I found a synology demo here: [https://demo.synology.com/en-uk/dsm](https://demo.synology.com/en-uk/dsm) and you are allowed to set the min and max _server_  protocol between smb1, smb2, something called "smb2 with large MTU" ( I  have no idea what that is but I'm guessing that is a reference to  smb2.1 ), and smb3.

The NAS is presently set to SMB2 min and max so I can test this issue.  It was originally set to SMB1 or SMB2 which is why everything worked fine on Ubuntu 16.04 before my upgrade to 18.04 (because it was only making SMB1 connections).  

> **Morbius1 said:**
> Your description almost sounds like an oplock ( opportunistic locking )  issue not an smb dialect issue but you would have had the same issue  with Ubuntu 16.04 since the smb dialect used should not make any  difference.

I totally agree that the SMB dialect SHOULD not make any difference, but I can repeatedly demonstrate it switching back and forth on the server side, not only on my NAS, but also on a share on a Win 7 Pro workstation where I can also switch the SMB server's SMB version from 1 to 2.

I've been looking into strace options and I think what I'll do next is look into the execution stack returned with the failed openat system call and see if, based upon what FreeCAD is calling, I can write a short program to demonstrate this easily and submit it as a bug. I think now that SMB1 is falling farther and farther out of favour, this will eventually become a problem for someone else and hopefully this can get fixed before it becomes widespread.

Thanks,

Scott

---

### Post by Morbius1 on 2019-02-05
Like I said above I do not have your NAS and I really try to have or create a user's environment when I post a response but ..... I would shift the client side mount from the file manager to cifs. The file manager uses gvfs + smbclient and has its own set of issues. A cifs mount is Linux kernel based and is more ... predicatable. Then you can easily explore different alternatives to find the secret sauce to make this work or to add on to your bug report.

** Create a mount point at ... say ... /media/NAS

** Then do a temporary mount of the nas:
```
sudo mount -t cifs //diskstation/share /media/NAS -o username=xxx,password=yyy,uid=1000
```

Different variations:

[1] Much like the way smbclinet uses smb.conf to find the min / max levels cifs references the kernel to find those values and here it's also set to negotiate which dialect to use from smb2.1 to smb3. If the NAS is set at smb2 you may need to specify that in the mount with a vers=2.0:
```
sudo mount -t cifs //diskstation/share /media/NAS -o username=xxx,password=yyy,uid=1000,vers=2.0
```

[2] oplock - and I admit this is just a hunch - Disable it on the client:
```
sudo mount -t cifs //diskstation/share /media/NAS -o username=xxx,password=yyy,uid=1000,nobrl
```

nobrl doesn't really disable it all it does is stop the client from sending a request for one.

---

### Post by sawozny on 2019-02-05
The NAS itself was never the issue as I've replicated the issue on a SMB share on a Windows 7 machine and the results were the same.  I also found that a simple:

```
echo "This is a test" > /run/user/1000/gvfs/smb-share\:server\=diskstation\,share\=fileshare/TestFile.txt
```

Would result in a 0 byte file when speaking SMB2 vs the data getting in the file when speaking SMB1.  I did a Wireshark trace to see what was going on and could definitely see the difference, but not the reason why.

Either way, doing a proper mount like you suggested made all this go away, so I think the problem is somewhere in GVFS and it's SMB client.  I'll log a bug, but the long term fix for me will be a CIFS mount like you suggested.

Thanks,

Scott

---

