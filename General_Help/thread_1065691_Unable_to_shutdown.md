---
title: "Unable to shutdown"
date: 2009-02-10
forum: General Help
---

### Post by kcode on 2009-02-10
On issuing command:
```

sudo halt

```
I got this error:
```

 timestamp too far in the future: Feb 10 21:04:29 2009

```

What does it mean?

Thanks

---

### Post by thestig_992 on 2009-02-10
you could use "sudo shutdown -h now" as an alternative. For halt, try googleing the error to find some more details

---

### Post by SeanTater on 2009-02-10
Remember, halt won't actually *turn off* your computer. You'll still need to press the power button when it's done. In case this isn't what you had in mind, try ```
sudo poweroff
```

The problem you're having isn't halt though. It's sudo. Do ```
sudo -k
``` and it should work.

---

