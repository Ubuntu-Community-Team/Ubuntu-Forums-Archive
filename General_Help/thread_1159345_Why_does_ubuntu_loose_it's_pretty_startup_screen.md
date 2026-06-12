---
title: "Why does ubuntu loose it's pretty startup screen?"
date: 2009-05-14
forum: General Help
---

### Post by baking666 on 2009-05-14
When I first install ubuntu it has a pretty start screen with progress bar as it loads...but after a few reboots it hangs around for a few seconds and then drops out to text mode and shows all the systems messages (all show ok) as it boots up..I like the pretty progress bar ;-)

---

### Post by dcstar on 2009-05-15
> **baking666 said:**
> When I first install ubuntu it has a pretty start screen with progress bar as it loads...but after a few reboots it hangs around for a few seconds and then drops out to text mode and shows all the systems messages (all show ok) as it boots up..I like the pretty progress bar ;-)

```
sudo update-initramfs -u all
```

---

