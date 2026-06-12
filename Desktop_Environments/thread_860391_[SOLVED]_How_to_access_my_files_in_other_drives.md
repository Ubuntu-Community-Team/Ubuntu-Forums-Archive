---
title: "[SOLVED] How to access my files in other drives?"
date: 2008-07-15
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-15
I have converted to xubuntu. In ubuntu all my drives were visible but in xubuntu they are not visible. How to access them easily? How to make a link to them?

---

### Post by snowpine on 2008-07-15
> **mirchichamu said:**
> I have converted to xubuntu. In ubuntu all my drives were visible but in xubuntu they are not visible. How to access them easily? How to make a link to them?

Hi there, try opening your Thunar file browser and navigating to the /media directory... do you see them there?

---

### Post by mirchichamu on 2008-07-15
Hello snowpine! How are you sir? I can now only one partition there. Where are the other partitions? Thanks for your support.

---

### Post by snowpine on 2008-07-15
I am very well my friend. :) We are making progress--you have one of your partitions now! I am sorry I don't know more about Xubuntu; I only tried it for a brief while. I typically use Nautilus in Ubuntu, and like you said, it showed me all the partitions, no problem. Do you still have Nautilus installed? If so, why don't you give that a try and see if it works?

Otherwise I think you need to mount them on the command line, and I don't know how to do that. (yet) :(

---

### Post by snowpine on 2008-07-15
Oh I just had another idea, can you try running 'thunar-volman' (short for volume manager) from the terminal?

---

### Post by mirchichamu on 2008-07-15
> **snowpine said:**
> I am very well my friend. :) We are making progress--you have one of your partitions now! I am sorry I don't know more about Xubuntu; I only tried it for a brief while. I typically use Nautilus in Ubuntu, and like you said, it showed me all the partitions, no problem. Do you still have Nautilus installed? If so, why don't you give that a try and see if it works?

Otherwise I think you need to mount them on the command line, and I don't know how to do that. (yet) :(

You know I am very new to linux. Ubuntu was giving a lot of problems. Some member advised to switch over to xubuntu. I did it, and I am happy upto some extent. I cannot afford to have a look at Natilus? By the way what is Nautilus and why there are so many versions of linux???????? I am totally confused??????

---

### Post by snowpine on 2008-07-15
> **mirchichamu said:**
> You know I am very new to linux. Ubuntu was giving a lot of problems. Some member advised to switch over to xubuntu. I did it, and I am happy upto some extent. I cannot afford to have a look at Natilus? By the way what is Nautilus and why there are so many versions of linux???????? I am totally confused??????

Yes I remember you from the other thread, I am sorry if we are confusing you. :( I think you are learning well and making good progress. :)

Nautilus is the Ubuntu file browser. Thunar is the Xubuntu file browser. They are pretty much the same, but not exactly--one important difference is that they use different "volume managers" to detect drives and partitions. I remember that you used to have Ubuntu on this computer, right? Did you uninstall Ubuntu yet, or do you currently have both Ubuntu and Xubuntu installed? If you still have Ubuntu, then you still have Nautilus. It should show up in your applications menu, but if not,  you can type 'nautilus --no-desktop' in the terminal to launch it. If the drives show up in Nautilus, but not in Thunar, that is a clue that we can use to help you.

I am not an expert at partitions, unfortunately, so that is the only suggestion I can make at this time. There are some real experts on these forums though. :)

---

### Post by snowpine on 2008-07-15
Oh okay, I thought of a really simple way to check. Go to your System menu and launch the System Monitor. Now, click on the Processes tab. Do you see either of these items in the list: gnome-volume-manager or thunar-volman?

---

### Post by mirchichamu on 2008-07-15
> **snowpine said:**
> Oh okay, I thought of a really simple way to check. Go to your System menu and launch the System Monitor. Now, click on the Processes tab. Do you see either of these items in the list: gnome-volume-manager or thunar-volman?

Yes I can see Gnome-volume manager and only thunar not thunar volman.

---

### Post by sisco311 on 2008-07-15
> **mirchichamu said:**
> I have converted to xubuntu. In ubuntu all my drives were visible but in xubuntu they are not visible. How to access them easily? How to make a link to them?
open a terminal and post the output of:
```
mount
```
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by mirchichamu on 2008-07-15
Thanks cisco311 for ur support.
Here is the screenshot.

---

### Post by sisco311 on 2008-07-15
1.) create the mount points:
```
sudo mkdir /media/sda1
sudo mkdir /media/sda5
sudo mkdir /media/sda6
```2.)get the UUID of the partitions:
```
sudo vol_id -u /dev/sda1
sudo vol_id -u /dev/sda5
sudo vol_id -u /dev/sda6
```3.)edit the fstab:
```
gksu mousepad /etc/fstab
```and add this lines:
> 
UUID=xyz-xxx /media/sda1 ntfs defaults,umask=0002,gid=46 0 2
UUID=xyz-xxx /media/sda5 ntfs defaults,umask=0002,gid=46 0 2
UUID=xyz-xxx /media/sda6 ntfs defaults,umask=0002,gid=46 0 2replace xyz-xxx with the UUID you get from step 2.)

4..)mount the partitions:
```
sudo mount -a
```5.)open Thunar and check the /media folder.

---

### Post by mirchichamu on 2008-07-15
My dear you have taught me like I am a professional?? hahahaha
Please tell me step by step how to do?

---

### Post by snowpine on 2008-07-15
Thanks sisco, I have always wondered how this was done!

Just to clarify, Mirchichamu only has to do this once, right, and then it will be set up forever?

Mirchi, Sisco's instructions may look complicated, but just be patient and take it one step at a time. Everything in a Code box should be entered into the Terminal, one line at a time. (You can use Copy and Paste to avoid typos.) Make sure to write down the UUID's from Step 2, because you will need them in step 3. If you get stuck at any point, stop and ask for help.

---

### Post by sisco311 on 2008-07-15
Just copy and paste the commands (one line by one) in the terminal.

1..) You need a mount point (directory) from where you
can access the partitions.

2.) The UUID is an uniqe identifier of a partition(some numbers).
The command will print the UUID of your partitions.
(usually /dev/sda1 is c: in windows and so on)

3.) The ```
gksu mousepad /etc/fstab
```command will open a text editor.

Add the mentioned lines to the file, but replace xyz-xxx with 
the UUID(numbers) you get from the vol_id commands.

---

### Post by sisco311 on 2008-07-15
> **snowpine said:**
> Thanks sisco, I have always wondered how this was done!

Just to clarify, Mirchichamu only has to do this once, right, and then it will be set up forever?


yes

---

### Post by mirchichamu on 2008-07-15
I got something like that? I am ifraid something may go wrong. Please see and advise.

---

### Post by mirchichamu on 2008-07-15
It is late night now. Will see you tomorrow inshaallah.

---

### Post by mirchichamu on 2008-07-16
Thanks once again and good evening.

I found a soluton. I am having "wine" installed, when I click on that, all my other drives open. But I don't know how to bring it to panel.

---

### Post by sisco311 on 2008-07-16
open your the fstab with the text editor:
```
gksu mousepad /etc/fstab
```and copy this lines at the end of the file:
> UUID=28B83D4DB83D1B30 /media/sda1 ntfs defaults,umask=0002,gid=46 0 2
UUID=821895CE1895C219 /media/sda5 ntfs defaults,umask=0002,gid=46 0 2
UUID=16E409AFE40991E3 /media/sda6 ntfs defaults,umask=0002,gid=46 0 2
save the file and exit(Ctrl+S, Alt+F4)

mount the partitions:
```
sudo mount -a
```In the file browser(Thunar) navigate to the /media directory to access 
the partitions.

---

### Post by mirchichamu on 2008-07-16
Thank you very much.
I did it, but every thing is doubled.I think I might have made some mistake somewhere. See the screen shot.

---

### Post by sisco311 on 2008-07-16
reboot the computer

---

### Post by mirchichamu on 2008-07-16
> **sisco311 said:**
> reboot the computer

Thank you so much. Now I am having all the drives on the desktop. Interestingly my ubuntu wallpaper also returned.
My problem solved.

---

### Post by CodeLab on 2009-05-15
Hi...
I Followed These instructions Exactly, But Cannot Mount
In My Case File System Is FAT32 And Not NTFS

So I Add These Lines At The End Of etc/fstab
> UUID=3886-E161 /media/sda1 FAT32 defaults,umask=0002,gid=46 0 2
UUID=744B-BF79 /media/sda5 FAT32 defaults,umask=0002,gid=46 0 2
UUID=945C-5891 /media/sda6 FAT32 defaults,umask=0002,gid=46 0 2But When I Mount I Get 
Unknown File System type 'FAT32' 
Error

Here Is The Output From sudo fdisk -l command
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2358    18940603+   c  W95 FAT32 (LBA)
/dev/sda2            2359        7296    39664485    f  W95 Ext'd (LBA)
/dev/sda5            2359        4716    18940603+   b  W95 FAT32
/dev/sda6            4717        4910     1558273+   b  W95 FAT32
/dev/sda7            4911        7191    18322101   83  Linux
/dev/sda8            7192        7296      843381   82  Linux swap / Solaris
Is There Different Method To Mount FAT32 Drives

Thanks

---

### Post by CodeLab on 2009-05-15
OK In The Above Quote
UUID=3886-E161 /media/sda1 FAT32 defaults,umask=0002,gid=46 0 2

I Replaced FAT32 With vfat
And I Had It Working

Thanks @sisco311
Great Explanation

---

