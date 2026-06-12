---
title: "Need Help With NTFS access"
date: 2009-04-29
forum: General Help
---

### Post by gs2088a on 2009-04-29
[FONT=Arial][SIZE=4]I'm new to Linux, in fact, I'm in the middle of installing it on my desktop (I have a removable hard drive tray).  I hope that by the end of the year, I will have all our computers (we have 3 here at home) will be converted to Linux.  However, I need a little help here.

For the time being, our notebooks are Windows XP Pro, and I have countless amount of files that I have archived on my desktop (it acts as a pseudo server, or file repository).  As a result, I have to be able to access these files from our notebooks, thru the desktop, which will be linux.  What I need is to know how to access the NTFS/FAT32 drives from my notebook, thru lunix, to the NTFS/FAT32 drives:

notebook----->linux (c drive on desktop)----->NTFS/FAT32 drives on desktop.

I need the NTFS/FAT32 drives to be immediately accessible on bootup.

Can anyone tell me where I can get step, by step instructions?????

One of the big reasons I need this, is because when I backup the notebook, I zip the files, and the script I created automatically copies them to the desktop where they are stored.

Thanks in advance.


[/SIZE][/FONT]

---

### Post by max_power on 2009-04-29
what version of ubuntu are you using? The NTFS drives should auto mount after you log in.

i just noticed that you marked this thread in the "general" category. If your not using a disto that comes with auto mounting of NTFS (like ubuntu 8.10 and up) then you are in for a bit more work. 

check out this link it has a step by step [http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/]("http://www.arsgeek.com/2006/09/25/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable/")

---

