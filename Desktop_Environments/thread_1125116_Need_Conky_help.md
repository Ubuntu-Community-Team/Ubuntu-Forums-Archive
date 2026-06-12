---
title: "Need Conky help"
date: 2009-04-14
forum: Desktop Environments
---

### Post by e_torano on 2009-04-14
I've just installed Ubuntu 9.04 on my machine (all's running fine with it). But, this problem has no relation to that at all (I think). Basically, I have installed conky and made my config etc. It looks okay, but there are two problems. Take a look at the attached screenshot to see.

The first is that it's showing up with the window border (I don't want it like this :P) and the second is that the top is being cut off.

I've attached my .conkyrc file so if somebody could take a look, I'd be really grateful.

Thanks, 
Euan

---

### Post by kpkeerthi on 2009-04-14
Use this settings:
```

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

---

### Post by e_torano on 2009-04-14
> **kpkeerthi said:**
> Use this settings:
```

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

Ok, that's problem one sorted - thanks. Any ideas on the second?

---

### Post by kpkeerthi on 2009-04-14
Oh. I missed that.

Delete the line that reads
```

    ${voffset -90}

```

---

### Post by e_torano on 2009-04-14
> **kpkeerthi said:**
> Oh. I missed that.

Delete the line that reads
```

    ${voffset -90}

```

Thanks tons :D Hopefully it works.

---

