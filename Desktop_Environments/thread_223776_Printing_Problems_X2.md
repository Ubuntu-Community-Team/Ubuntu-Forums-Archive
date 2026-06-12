---
title: "Printing Problems X2"
date: 2006-07-26
forum: Desktop Environments
---

### Post by tripwire45 on 2006-07-26
I posted this several minutes ago in the HOW TO forum but something must have eaten my new thread because I can't find it anywhere. I even searched for all of the posts under my name and there was nothing related to that thread at all.

Anyway, like many people, I'm having trouble printing from Ubuntu. I have Dapper Drake installed as a virtual machine in VMware 5.5. The host machine is a Windows XP Pro. The HP Officejet printer is attached to the Windows host using USB. I've tried both CUPS and SMB with no result. I get a message saying that the host is busy and it will retry in 30 seconds. 

I can ping the host fine from the VM and even open shared folders on the host. I checked /var/log/cups/error_log and found a long list of this:

```
E [26/Jul/2006:20:19:02 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:19:02 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:19:06 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:19:06 -0600] CUPS-Delete-Printer: Unauthorized
E [26/Jul/2006:20:20:17 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [26/Jul/2006:20:20:29 -0600] [Job 10] No %%BoundingBox: comment in header!
E [26/Jul/2006:20:22:49 -0600] [Job 11] No %%BoundingBox: comment in header!
E [26/Jul/2006:20:23:37 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:40 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:43 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:45 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:45 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:45 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:46 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:46 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:46 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:46 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:50 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:50 -0600] cupsdAuthorize: Local authentication certificate not found!
E [26/Jul/2006:20:23:50 -0600] cupsdAuthorize: Local authentication certificate not found!
tripwire45@ubuntu:/var/log/cups$
```

Any ideas (and please don't eat this thread)?

-Trip

---

### Post by tripwire45 on 2006-07-27
Anybody? I can't believe I'm the only one in this situation and that a solution isn't available...:confused:

---

### Post by tripwire45 on 2006-07-27
Now I've got egg on my face. I got it working...but printing didn't work because of my dumb mistake. When going through the Windows printing setup sequence, I typed in the Windows host IP at //192.168.0.2. The forward slashes are unnecessary. 

I found the clue I needed in the screenshots at this site:

[http://easylinux.wordpress.com/2006/04/17/printing-from-ubuntu/](http://easylinux.wordpress.com/2006/04/17/printing-from-ubuntu/)

I hope this helps others who are in similar circumstances. Ubuntu prints! :D

---

