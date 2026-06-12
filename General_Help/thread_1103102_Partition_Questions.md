---
title: "Partition Questions"
date: 2009-03-22
forum: General Help
---

### Post by Lucrothe on 2009-03-22
Hello,

I have a 320GB hard drive that I plan on using as my main HD.  I setup something along the following lines.

30GB (30720) for Ubuntu 8.10 install - ext3
10GB (10240) for /home - ext3
5GB (5120) for swap
200GB (204800) for Vista - NTFS
Left over for an extra Vista My Documents drive - NTFS

Is 30GB too much for the main install section of Ubuntu?

I've noticed that a lot of the application are really using the /home partition.  I was under the impression that this would be used more like a My Documents section for pictures, docs, and videos.  I think I should increase this drastically.

What do most people set for their install partition?
What do most people set for their /home partition?

I also have an internal 1TB drive that I use as a media sharing drive.

Can I set folder share permissions in Vista and ALSO set folder permissons on the same folder in Ubuntu? I dual boot into a different OS depending on the task at hand, and I want to make sure depending on the OS that I am in other computers on my network can still access the shared folders. 

Any help and tips would be greatly appreciated!

---

### Post by sekinto on 2009-03-22
Yes, I think you should give your home partition a little more space. Ubuntu doesn't take up that much space, and even if you install a ton of additional software it shouldn't get that big.

The /home directory will end up getting fairly large, it is like the Documents and Settings directory in pre-7 Windows (and the User directory in Windows 7). The /home/[yourlogin] directory will not only store all you personal files like images, audio, videos and documents (media ends up using the most space on most people's computers), but it will also store all your personal settings for different Ubuntu applications.

And you definitely do not need 5GB of swap, I wouldn't go over 1-2GB (if you really need 5GB of swap space you either run way too many programs at a time or you need more RAM).

---

### Post by Rocket2DMn on 2009-03-22
30 GB is a lot for your root partition, I think you should swap sizes on root and /home.  Most people keep their documents and personal files in their home directory, which is what really takes up space.  A base install of Ubuntu is only a few GB (3.2 GB or so).  My root partition is at 4.33 GB right now, while my /home is at 53.57 - and I don't even store my music, pics and videos in /home (they are stored on my Vista partition which is currently using 179.32 GB).

---

