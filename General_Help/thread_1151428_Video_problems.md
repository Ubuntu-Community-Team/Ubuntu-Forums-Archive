---
title: "Video problems"
date: 2009-05-06
forum: General Help
---

### Post by radioactiveman69 on 2009-05-06
Hey all,

I am running 9.04. I am having problems watching youtube videos. all videos that i watch on the net are really choppy and not in sync. Any ideas on how to fix this problem?

Thanks,

Ryan

---

### Post by mb_webguy on 2009-05-06
Are you running the 32-bit version or the 64-bit version?

---

### Post by radioactiveman69 on 2009-05-06
Im not too sure.. where can I get that information.. im pretty sure its the 32

---

### Post by colau on 2009-05-06
> **radioactiveman69 said:**
> Im not too sure.. where can I get that information.. im pretty sure its the 32
From terminal type
```

uname -a

```

---

### Post by radioactiveman69 on 2009-05-06
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by orbish on 2009-05-06
Sounds like the intel driver issue.  Is your video card integrated/are you on a laptop?  If so, check the known issues sticky for the workaround.  I haven't been lucky with the fix though.

---

### Post by colau on 2009-05-06
> **radioactiveman69 said:**
> Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
It is 32 bit.
From terminal can you 
[html]
lspci
[/html]

---

### Post by radioactiveman69 on 2009-05-06
no its a desktop with a radion card.. its a wierd thing going on.. do you think it might have something to do with a bad install on the flash player?

---

