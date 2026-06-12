---
title: "Why does ubuntu loose it's default swap behavior?"
date: 2009-05-14
forum: General Help
---

### Post by baking666 on 2009-05-14
When I first install ubuntu it has swap space enabled by default but after a few reboots it looses it's default swap enabled and I have no swap space...I've had to manually set it everytime I reboot :-(

---

### Post by Elfy on 2009-05-14
Can you run this and note the UUID for your swap partition

```
blkid
```

Then check the UUID fstab has for swap 

```
cat /etc/fstab
```

They need to match - if you aren't sure how to edit fstab then post back

---

### Post by baking666 on 2009-05-14
> **forestpixie said:**
> Can you run this and note the UUID for your swap partition

```
blkid
```

Then check the UUID fstab has for swap 

```
cat /etc/fstab
```

They need to match - if you aren't sure how to edit fstab then post back


Ok worked a treat thanks :-)

I had played around with adding a script to session startup along the lines of swapon /dev/sda5 but wondered why ubuntu lost it's default...any ideas why? as it's been consistent from one ubuntu release to the next for me and currently I'm on linux mint derived from ubuntu :-)

---

### Post by dcstar on 2009-05-15
> **baking666 said:**
> Ok worked a treat thanks :-)

I had played around with adding a script to session startup along the lines of swapon /dev/sda5 but wondered why ubuntu lost it's default...any ideas why? as it's been consistent from one ubuntu release to the next for me and currently I'm on linux mint derived from ubuntu :-)

And you have **never** played with the partitions after install, haven't you?

---

