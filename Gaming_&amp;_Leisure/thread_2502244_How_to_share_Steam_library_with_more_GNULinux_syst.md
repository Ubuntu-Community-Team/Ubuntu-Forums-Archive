---
title: "How to share Steam library with more GNU/Linux systems?"
date: 2024-11-06
forum: Gaming &amp; Leisure
---

### Post by Shishimaru on 2024-11-06
Hi all.

I have Ubuntu and another GNU/Linux OS on my laptop.

My Steam library is on a separate Btrfs partition, but seems that every time I switch system I always must symlink the local compatdata to the partition. Is there any simpler way?

edit: resolved by copying /home's compatdata into the steam's partition.

---

### Post by 1fallen on 2024-11-06
I did this a few years back, I wish I had that on hand now but I don't.

Try This  Edit /etc/fstab and change the ext4 in /home to btrfs. This lets SteamOS know to mount it as BTRFS the next time you boot.

I always back-up any changes like this first:
```
sudo cp /etc/fstab /etc/fstab.bk
```
and I'll look to see that happened:
```
ls /etc/fstab*
/etc/fstab  /etc/fstab.bk

```

But I have no idea on how your other /home partitions are formatted.

---

### Post by Shishimaru on 2024-11-06
Hi, thank you!

Unfortunately this will not solve as I don't have a mount issue. I should try to explain better my situation, probably I wasn't clear enough. I do not have SteamOS or any Steam Deck.

I have this situation:
- partition 1 with Ubuntu
- partition 2 with Bazzite
- partition 3, only Steam library, easily mounted at startup at /media/games since it's in the fstab.

Now, to play Steam games on system 1, I have to symlink the local compatdata (I think it's under /home/myuser/steam/steamapps or something like that) to partition 3, again under /media/games/path-to-steam-library-i-dont-remember.
With the symlink, the Steam client can see the games and download/upload save files from/to the cloud.

If I move to system 2, I must delete the symlink and create a new one.

It's a bit "uncomfortable" and I was wondering if there was any easier way to share the library.

---

### Post by 1fallen on 2024-11-06
Ah that helps, much clearer now.

Have you read this yet?: [https://www.zxiiro.ca/post/steam-share-library-with-linux/](https://www.zxiiro.ca/post/steam-share-library-with-linux/)

---

### Post by Shishimaru on 2024-11-06
Yep!

That helps with multiple accounts on the same system, while I have two different systems.

---

