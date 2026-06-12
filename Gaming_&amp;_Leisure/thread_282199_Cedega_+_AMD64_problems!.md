---
title: "Cedega + AMD64 problems!"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by horgh on 2006-10-22
I use Edgy, 64-bit version. I installed Cedega from .deb file with no problems at all. I can run Cedega fine, no error messages. But when I try to install any game I get this: 

/home/horgh/.cedega/.winex_ver/winex-5.2.6/bin/winex3: 162: /home/horgh/.cedega/.winex_ver/winex-5.2.6/winex/bin/pthreads_stack_test: not found
[: 162: 0: unexpected operator
/lib/ld-linux.so.2: could not open

But the file is there for sure, but for some reason I'm not able to execute it. I even tried to copy the file "pthreads_stack_test" to other directory, still when I try to execute it, bash: 

./pthreads_stack_test: No such file or directory

This has nothing to do with permissions, they are fine. So, I'm really out of ideas, what could be wrong? Is it the file or what? 

Please help me :confused:

---

### Post by chrisharris0 on 2006-10-31
I have the exact same problem,  using Edgy, amd64, and an nivida 6200


let me know if you had any success! 

thanks

---

### Post by chrisharris0 on 2006-10-31
Its not a problem with pthreads, running it with --use-pthreads no 

still gives the "/lib/ld-linux.so.2: could not open" error

---

### Post by horgh on 2006-10-31
Installing these: 

ia32-lib-sdl
ia32-libs
lib32asound2
libc6-i386 
lib32gcc1
libc6-dev-i386

solved that problem for me, anyway I still can't use Cedega, now I it complains about not founding x11drv... Have to figure something out for that too.

---

