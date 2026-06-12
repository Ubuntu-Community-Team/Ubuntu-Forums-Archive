---
title: "Best way to partition a 1TB drive for speed"
date: 2009-05-17
forum: General Help
---

### Post by mac9416 on 2009-05-17
Hello, all!

    I recently bought a 1TB Western Digital Caviar Black 7200 RPM 32MB cache hard drive. A one terabyte drive, to put it in a few words.
    A friend told me that a drive as huge as that can't reach its full potential if everything is in one partition. He says it should be split into about 6 partitions. What's the best way to go about that? I could split it into /, /boot, and /home partitions, but I understand /boot only takes 250MB, and / takes 15GB. That leaves a huge ~950GB partition. So, should I split my home directory into separate partitions? Perhaps a 10GB ~/music partition, a 10GB ~/Pictures partition, and a 50GB ~/BlenderFiles partition? That still leaves a huge partition for the rest of the home directory.
IN SHORT what is a good partitioning strategy for a 1TB drive if I'm worried about speed?

Thanks
-mac

---

### Post by mb_webguy on 2009-05-17
I hate to say that your friend doesn't know what he's talking about, but... well...

The apparent speed of a drive is determined by the actual read/write speed and the distance the head has to travel between locations on the disc.  You can't do anything about the former except buy a faster hard drive.  You can improve the latter some -- though likely not to a perceptible degree -- by partitioning the drive so that the more frequently read or written directories are located near each other on the drive.  

Linux is actually a very small operating system, and its software tends to be much less bloated compared to Windows equivalents.  If you create an 8-12GB partition for root and use the rest of the drive for /home, you'll assure that the most often accessed areas of your filesystem (e.g. the system and application files and directories) are located near each other on the drive.  The less-often accessed information (i.e. your data) can use the rest of the drive.  

Again, though, given the access speeds of modern drives, fancy partitioning isn't likely to provide a noticeable difference in hard drive access times.  There are several reasons to keep various directories on separate partitions depending on your specific system and usage, but increasing hard drive access speed isn't really one of them.  (Note:  You friend would have been correct about 15 years ago, during the age of slow platter drives where movement of the head from one point to another on the drive took a non-insignificant amount of time.  But we've come a long way since then.)

---

