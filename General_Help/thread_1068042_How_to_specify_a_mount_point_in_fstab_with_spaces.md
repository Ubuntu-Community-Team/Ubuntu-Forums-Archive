---
title: "How to specify a mount point in fstab with spaces?"
date: 2009-02-12
forum: General Help
---

### Post by jerome1232 on 2009-02-12
Okay so I thought this was basic but I can't figure it out.

In my fstab I'm trying to add a new partition and give it a mount point that has spaces in it.

I've tried these two methods but both give me a "bad line in fstab" error.

```
UUID=209db27f-0c77-4c14-bddf-a8a9e954a6ad "/media/torrents/World of Warcraft" ext3 defaults,relatime 0 2
```
```
UUID=209db27f-0c77-4c14-bddf-a8a9e954a6ad /media/torrents/World\ of\ Warcraft ext3 defaults,relatime 0 2

```

Is there some non-standard way to get spaces in your mount point using fstab?

---

### Post by cariboo on 2009-02-12
> World\ of\ Warcraft

Remove the spaces eg:

```
World\of\Warcraft
```

the slash is the space.

Jim

---

### Post by jerome1232 on 2009-02-12
Thanks for responding I actually should've looked at the fstab man page before I posted, it says to escape them with a \040, I tried it that way and it worked great, I'm copying a large amount of files to that partition as soon as it's done I'll try mounting it with just backslashes and see if that works as well.

Thanks

---

### Post by jerome1232 on 2009-02-12
Okay so fstab took that literally World\of\Warcraft was just that, World\of\Warcraft.

Seems you have to escape spaces with a \040 so it became

```
/media/torrents/World\040of\040Warcraft
```

---

