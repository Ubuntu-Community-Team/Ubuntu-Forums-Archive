---
title: "boot and home directories mysteriously gone"
date: 2008-12-06
forum: General Help
---

### Post by ukyo_rulz on 2008-12-06
Hello, my sister has ubuntu 8.04 installed (through Wubi) on her Acer Aspire 6920. It's been working fine for many months now, until last night. She shut the computer down normally, went to sleep, and when she woke up the next morning the computer would not boot any of the kernels. I looked at the terminal output and it seems to boot directly into a debian shell. My ls revealed that all the folders seemed to be present except for the boot directory (and the home directory, but I am unsure if the home directory is supposed to be present at startup or if it is simply mounted during boot. All the folders that are normally mounted by fstab are inaccessible. Is there any way to repair this? Is there any way to mount, say, a windows partition so that I can copy my own boot directory there and maybe get the thing to boot?

---

### Post by albinootje on 2008-12-06
With Wubi all the Linux-files are in 1 file on the Windows-partition as
far as i remember (reading before).
Perhaps this is useful :
From [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
this section :
Can I move my virtual disk file to a dedicated partition?
And this has some more info too :
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))
GL!

---

### Post by magmon on 2008-12-06
Wubi has been known to be unstable, but the only reason other than a wubi hiccup would be [COLOR="Red"]sudo rm -rf[/COLOR], did she run this command at any time? If so, it mangles an ubuntu install.

---

### Post by ukyo_rulz on 2008-12-07
> **magmon said:**
> Wubi has been known to be unstable, but the only reason other than a wubi hiccup would be [COLOR="Red"]sudo rm -rf[/COLOR], did she run this command at any time? If so, it mangles an ubuntu install.

My sister doesn't even know how to open a terminal. There's no way she would have been able to sudo her way into that mess. In any case, the darn thing just fixed itself this afternoon and we have no idea why or how. We're just gonna go ahead and back everything up while we can.

---

### Post by Jammanuser on 2008-12-07
> **ukyo_rulz said:**
>  Is there any way to mount, say, a windows partition so that I can copy my own boot directory there and maybe get the thing to boot?

Yes, there is. To mount ur Windows partition (using the Ubuntu LiveCD, of course!), first boot with the CD, and then open up a terminal, and run the following commands:

```
sudo mkdir /win
sudo mount /dev/**sda3** /win
```

Note: You should replace "sda3" with the appropriate partition number (if not correct), i.e. "sda1" or "sda2" instead of "sda3".
Running the above commands mounts ur Windows partition. And then to mount the **virtual disk**, u can use:

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

```
Now simple open up a file browser (Places>Computer>File system>), and go the /win folder...there u will find all ur Windows stuff! ;)

Cheers! :)

-jammanuser

):P

---

