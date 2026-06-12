---
title: "Thunar can browse smb share but all files are 0 byte and 'folder'"
date: 2020-05-05
forum: Desktop Environments
---

### Post by Edocecrous on 2020-05-05
Hi,

I have a WD mybook NAS on my local network with some file shares on it. Can access it from a Windows machine no problem.
I had problems accessing it from Thunar, first i had to set protocol to' client min protocol = NT1' to even be able to connect to it.
Then i couldn't access the shares, so after installing gvfs-backends, finally i was able to browse the files on the shares.

Here comes the next problem: all files are shown as 0 byte, and 'folder'-s, and can't open anything.

I have Xubuntu 20.04, and it's beyond me why something that was just worked fine 5 years ago in an old distro doesn't work on the newest...

Any help appreciated, 

Edo

---

### Post by CelticWarrior on 2020-05-05
To be clear: I have no solution for you at the moment. I'm only posting to explain *why something that was just worked fine 5 years ago in an old distro doesn't work on the newest...* The reason is exactly that, it's too old and uses deprecated protocols that due to security concerns are no longer supported in Ubuntu or Windows.

---

### Post by Morbius1 on 2020-05-05
If your NAS is running only with SMB1 enabled it's a damn bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476)

You have a choice:

[1] You already did one part in setting client min to NT1 but you next need to add the PPA referenced in the bug report above.

[2] Remove yourself from depending on gvfs and start using CIFS which is based in the Linux kernel which has adult supervision over what goes into it.

A typical *[COLOR=#ff0000]**temporary**[/COLOR]* cifs mount ( after installing cifs-utils ) would look something like this:
```
sudo mount -t cifs //server/share /some-mount-point -o guest,uid=1000,vers=1.0,sec=ntlm
```
After verifying that it works you can set this up in fstab so it happens without you going to the terminal.

---

### Post by Edocecrous on 2020-05-05
So it is a bug :( Damn

Tried quickly the PPA, but didn't work out...

Mounting it with cifs works like a charm, THANKS !!!!

Red it somewhere that cifs is the past and smb is the way to go, but screw that now...

---

### Post by Morbius1 on 2020-05-05
>  Red it somewhere that cifs is the past and smb is the way to go, but screw that now...                 
It's a discombobulation of terms. 

CIFS was the name given to the original dialect of SMB. It was later updated then renamed to SMB1 but the kernel developers kept the name CIFS for their module. CIFS can access any system running with SMB1 all the way up to SMB3 which is what WIn10 and a Samba server uses.

---

### Post by Edocecrous on 2020-05-06
Yes, i am aware of those facts, while searching for a solution i came upon an article that had the summary of that line...

Thank you again, now i can access my NAS!

---

### Post by him610 on 2020-05-08
Not trying to hijack thread, just adding comment.

I have a related issue, when I try, using Thunar, to open my fileserver, error message appears, > Failed to open 'fileserver'. Failed to retrieve share list from server: Software caused connection abort.

It is a legacy atom-powered server running freenas version 0.68 that I built about ten years ago.  
Maybe it is time to upgrade server hardware and software.

---

### Post by Artim on 2020-05-09
Be sure to mark the thread SOLVED!  There will be others to follow, with the same issue.

---

### Post by him610 on 2020-05-09
Deleted by him610

---

