---
title: "[SOLVED] Force Mount Vista"
date: 2008-12-21
forum: General Help
---

### Post by -Outcast- on 2008-12-21
Hello, 

I have to reinstall after my 8.10 locked me out. 

It's dualing booting with vista. 

I can access vista files if vista is shut down. But because vista takes so long to boot, I keep it in hibernation. 

So now if I try to access it form places, enter password it gives me an error unable to mount. This is due to vista still being in use (not shut down)

I have a code for terminal that override this, but after the new installation can't find it. something to do with force mount? 

Does anyone have it?

---

### Post by SlidingHorn on 2008-12-21
```
sudo mount /dev/[device] /media/vista -o force
```

is this what you're looking for?

---

### Post by -Outcast- on 2008-12-21
Certainly was thank you!

---

