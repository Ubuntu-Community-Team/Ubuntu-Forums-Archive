---
title: "Nautilus slows as it goes"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Clive McCarthy on 2012-02-17
I was transferring 1,000 x 4.8MB images from a USB 2.0 connected CF memory card and found that the transfer rate slowed dramatically as the files were moved.

Initially Nautilus reported 15MB/sec but this slowed to just 5MB/sec as the task went on. The CF card is rated at 15MB/sec.

In fact it took three tries to move all the images because Nautilus exited without any message, twice. :confused:

What is going on? It is a very simple task but it is a little scary when I'm unloading my camera's images to have Nautilus crash.

---

### Post by gordintoronto on 2012-02-17
Just opening a new file in a folder that contains 1,000 files, takes an astonishing length of time. If your drive contains bad sectors which have been remapped, that can make it worse.

---

### Post by Clive McCarthy on 2012-02-17
Opening the CF card doesn't seem to be the problem. It is the file operations that have a problem. I was able to watch the transfer rate progressively collapse over a few tens of seconds. It is almost as if there was some kind of cache being filled which was being emptied at a much slower rate, though that doesn't quite make sense. I also suspect that the first attempts to move the files caused nautilus to crash because perhaps the transfer rate had become effectively zero!

---

### Post by gordintoronto on 2012-02-17
When there are 900 pictures in the receiving folder, and number 901 comes along, everything grinds to a halt for a significant amount of time. During this period, the flash drive doesn't send anything, so the effective transfer rate falls off a cliff.

---

### Post by Clive McCarthy on 2012-02-17
So what's the disease and what is the cure? Is the file system repeatedly traversing a growing linked-list of directory entries?

The destination drive has no bad sectors, so no remapping. It's formatted with ext4. There is lots of free disk space.

---

