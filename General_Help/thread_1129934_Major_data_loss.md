---
title: "Major data loss"
date: 2009-04-19
forum: General Help
---

### Post by clarkey on 2009-04-19
Hi I just installed the Jaunty RC and used manual partitioning to reinstall my intrepid installation but when I rebooted I found my home partition had been wiped clean! I have a seperate home and root partition the root which I format with every install but keeping the home partition the home partition was obviously EXT3 (as it was in intrepid) but I set it to be used as EXT4 i thought this was possible? I am 95% sure I didnt set to format the partition though any help would be a unbelieveable help I had family photos from the last 8 years most of which I don't have duplicates of, I know I should have a backup system I certainly will create one now!

Thanks again in anticipation

---

### Post by 3Miro on 2009-04-19
Stop using the computer NOW. Run it from the live CD only.

There are ways that may recover at least some of the lost data from a formated partition, but someone else would have to help you with that one. I have never done it myself.

---

### Post by lovinglinux on 2009-04-19
> **clarkey said:**
> I have a seperate home and root partition the root which I format with every install but keeping the home partition the home partition was obviously EXT3 (as it was in intrepid) but I set it to be used as EXT4 i thought this was possible? I am 95% sure I didnt set to format the partition though ...

The problem is that you changed the file system, so instead of just mounting the /home partition, you formatted it with the new file system (ext4).

I'm afraid you have lost everything. As already said, you could try recovering something using specialized software, but I can't help you with that either. Stop using the computer and boot from Live CD, otherwise you will keep writing to the disc and lowering your chances of recovering something.

---

