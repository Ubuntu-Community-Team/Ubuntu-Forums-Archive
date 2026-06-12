---
title: "i need help. swap file is way too big"
date: 2009-02-17
forum: General Help
---

### Post by panda_HAVOK on 2009-02-17
ok so i think i made a bigger problem for myself than i really need at the moment. i dispise vista yet on my hp laptop my primary computer i had ubuntu installed on it a while ago and i installed it while i was on vista so someone crashed ubuntu because they were an idiot and well im not even sure what they did so i used vista because i had the option to switch opperating systems at start up. well i found my live cd of ubuntu and put it in and restarted the computer. i should have put the cd in and oppened it while still in vista to install it because i knew how to install it from there. but ubuntu starts up and i install while running ubuntu and everything went well except one tiny little thing that really became really big. when i chose which area of the hard drive to install it and which to have the swap area i put the install in the recovery section of my orriginal partition and the swap took over the existing hard drive. im running it fine right now but i only have 9gigs free space. and all my music personal info and all that is still on the other part but i cant access it. is it all dead or can i revive this part of my drive cuz otherwize im ******. i dont have the right vista install disk and just a live cd of ubuntu. keep in mind im fairly new. give or take 5 months of tinkering with linux.. please help

AIM: disposed0teen
MSN: [email]panda_havok@hotmail.com[/email] 

help help help

---

### Post by taurus on 2009-02-17
You need to stop using that machine as soon as possible because the more you write to the harddrive, the harder it would be to recover your data from it.

Maybe TestDisk can do something about it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by cariboo on 2009-02-17
Could you open an Applications-->Accessories-->Termianl and type:

```
sudo fdisk -l
```

and paste the output in your next post.

Jim

---

### Post by panda_HAVOK on 2009-02-17
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37223   298993716   82  Linux swap / Solaris
/dev/sda2           37224       38913    13574925   83  Linux

---

### Post by dcstar on 2009-02-17
> **panda_HAVOK said:**
> ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37223   298993716   82  Linux swap / Solaris
/dev/sda2           37224       38913    13574925   83  Linux
```

There is no Windows partition, there is only a (very) big Swap partition and one Linux partition.

The only data you have is on that Linux partition, all else is long gone.

You can boot off a Live CD and resize both partitions, detailed instructions can be searched out of the forums.

---

### Post by cariboo on 2009-02-18
I would suggest trying [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to see if you can recover any of your data. I would suggest using the [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") instead of installing any more software, or trying to resize the partition, you may probably need another hard drive for the recovered files.

Jim

---

### Post by Rohen on 2009-02-22
Paragraphs are your friend. :p

---

