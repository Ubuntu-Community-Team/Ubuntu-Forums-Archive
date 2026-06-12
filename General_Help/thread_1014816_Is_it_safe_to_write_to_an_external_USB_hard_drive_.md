---
title: "Is it safe to write to an external USB hard drive while running from a liveCD?"
date: 2008-12-18
forum: General Help
---

### Post by Viveck on 2008-12-18
Hello,

My laptop is effectively dead and entirely unable to even boot up to the windows loading screen. I've been toying with Knoppix and Ubuntu; I've used knoppix in the past to FTP gigantic folder or projects I'd not periodically backed up. However this time I've basically got an entire drive that I haven't backed up that holds about 80gb so I need to make sure I get a clean and solid transfer of my data.

I've read some information about transferring/writing to an NTFS external hard drive but I can't find any conclusive or recent information about how save it is in ubuntu or how exactly to do it safely.

If someone could point me in the right direction I would be very grateful!

Thank you

---

### Post by damis648 on 2008-12-18
Nothing really unsafe could happen. Just boot up the LiveCD and run in terminal (Applications>Accessories)
```
sudo apt-get install ntfs-3g ntfsprogs
```
and enter. That should do it. :popcorn:

---

### Post by Izek on 2008-12-18
I've written to my 8 GB Sandisk Cruzer Micro plenty of times back when I used a liveCD a lot to transfer files I wanted to keep from my windows machine. Though, "safely" would mean you would copy the files over, and then unmount the USB so that the data gets written then put the USB back in to see if the data really was written.

Oh wait, you meant NTFS, I gotta read posts more -_-

---

### Post by Viveck on 2008-12-18
damis648,

Thank you for your response; I will get right on it :).

---

