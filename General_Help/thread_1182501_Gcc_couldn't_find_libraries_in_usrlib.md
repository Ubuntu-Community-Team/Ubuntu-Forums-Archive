---
title: "Gcc couldn't find libraries in /usr/lib"
date: 2009-06-09
forum: General Help
---

### Post by Vaulter101 on 2009-06-09
Hi all,

First of all... I  Love Ubuntu! It's the best EVA!

Now, I'm trying to wrap ffmpeg into python extensions. I first started with libavcodec and libavformat examples. All went well, till I try to link the code.

'gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.6/avtest.o -llibavcodec -llibavformat -o build/lib.linux-i686-2.6/avtest.so
/usr/bin/ld: cannot find -llibavcodec'

and then it complaints: 
'/usr/bin/ld: cannot find -llibavcodec
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1'

Both the library files sit right in /usr/lib directory. And they're the proper ones because when I link the object files from Code::Block IDE it works fine.

And running 'ldconfig -v' shows these libraries can be accessed as well.

Could some one please tell me what I could be doing wrong here?

Much obliged!

---

