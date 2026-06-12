---
title: "Shotwell not working in 14.10"
date: 2014-10-24
forum: Desktop Environments
---

### Post by mrkeef on 2014-10-24
Since upgrading to 14.10 yesterday, shotwell does not work. It starts, but when I click the mouse on any menu or icon or photo nothing functions.

Any ideas?

Thanks

Keith

---

### Post by spacesamurai2 on 2014-10-24
No issues with my upgrade. Just curious, but what version are you running?

$ shotwell --version
Shotwell 0.20.1

---

### Post by mrkeef on 2014-10-25
$ shotwell --version
Shotwell 0.20.1

---

### Post by mrkeef on 2014-10-25
I ran shotwell from a terminal and got the following:

mrkeef@Amelia:~$ shotwell
L 11391 2014-10-26 07:05:36 [CRT] PhotoMonitor.vala:1069: Unable to reimport [14757] /mnt/server-photos/2014/10/img_7308.jpg due to master file changing: Unexpected early end-of-stream
L 11391 2014-10-26 07:05:36 [CRT] PhotoMonitor.vala:1069: Unable to reimport [14759] /mnt/server-photos/2014/10/img_7310.jpg due to master file changing: Unexpected early end-of-stream
Killed

I removed the offending photos from the folder, but shotwell still fails to work correctly. There is no output on the terminal.

---

### Post by spacesamurai2 on 2014-10-26
Hmm, not seeing any other postings or sites showing a similar issue. Not sure, but maybe the mount is not recognized by the updated software. You could try with a brand new Shotwell library, and try importing the pictures again.

---

### Post by mrkeef on 2014-10-27
It seems to be finding the photos but trips when it tries to update.

I tried deleting the database file in ~/.local/share/shtewell/data but still no luck

---

### Post by mrkeef on 2014-10-27
Finally fixed it by removing it and then re-installing it. My biggest dear was that it wouldn't keep tags, but I had set it up to write tags to the files so it's all good.

root@Amelia:/home/mrkeef# apt-get remove --purge shotwell*
apt-get install shotwell

It then proceeded to rebuild the database and now seems to work as expected.

---

