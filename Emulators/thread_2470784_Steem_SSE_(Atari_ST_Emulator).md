---
title: "Steem SSE (Atari ST Emulator)"
date: 2022-01-11
forum: Emulators
---

### Post by demonenero84 on 2022-01-11
Greetings :)
I am trying to install Steem [HTML]https://sourceforge.net/projects/steemsse/[/HTML] but I get this error:
"[FONT=monospace][COLOR=#000000]error while loading shared libraries: libcapsimage.so.5: cannot open shared object file: No such file[/COLOR]
 or directory"
Do you have any suggestions? 
Thanks in advance 
[/FONT]

---

### Post by Dennis N on 2022-01-11
I think you need to install the **libcapsimage** packatge, but it's not in the Ubuntu repository. With Google, I found this for you to check out:
[http://www.softpres.org/?id=download](http://www.softpres.org/?id=download)
Good luck.

I should add that there is a Fedora package for this in their repository.

---

### Post by demonenero84 on 2022-01-11
Thanks a lot for the quick reply :)
So I installed 2.3 and 4.2 ( I did "sudo cp libcapsimage.so.4.2 /usr/lib/ ; sudo ldconfig" and "sudo cp libcapsimage.so.2.3 /usr/lib/ ; sudo ldconfig" )
but I still get the same error :(

---

### Post by Dennis N on 2022-01-11
You need version 5. If you google libcapsimage.so.5, you will get some hits on this, like:
[https://github.com/keirf/Disk-Utilities/blob/master/README.md](https://github.com/keirf/Disk-Utilities/blob/master/README.md)
which led me to:
[https://www.kryoflux.com/?page=download](https://www.kryoflux.com/?page=download)
which is an archive that contains ver. 5 **&#8595;**  (see attached screenshot of archive contents).
Beyond this, I must leave it to you on how to proceed.
I hope you get it to work. Good luck.

---

### Post by demonenero84 on 2022-01-11
Thanks a lot for your help :)
Steem runs fine now

---

