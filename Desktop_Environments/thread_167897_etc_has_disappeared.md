---
title: "/etc has disappeared"
date: 2006-04-29
forum: Desktop Environments
---

### Post by morrin on 2006-04-29
Hi

I rebooted my machine  and I couldn't log in. I was able to use a live DSL cd to access the disk and noticed that my /etc directory had disappeared and in it's place was an executable called etc. If I run this executable I get back

 ./etc
usage: ./etc [-hv] [-x dir] file
 -h         print this help
 -x dir     extract into dir
 -v         be more verbose
 file       file to test

Did anybody ever come across this before. I haven't got a clue where to start to fix this, or what may even have caused this.

Thanks

---

### Post by BoyOfDestiny on 2006-04-29
[QUOTE=morrin]Hi

I rebooted my machine  and I couldn't log in. I was able to use a live DSL cd to access the disk and noticed that my /etc directory had disappeared and in it's place was an executable called etc. If I run this executable I get back

 ./etc
usage: ./etc [-hv] [-x dir] file
 -h         print this help
 -x dir     extract into dir
 -v         be more verbose
 file       file to test

Did anybody ever come across this before. I haven't got a clue where to start to fix this, or what may even have caused this.

Thanks[/QUOTE]

Hmm, I've run into something similar. If you take the executible option away from a folder (like in nautilus) it makes the contents look like a files (even if there are folders in there). can you try a 

sudo chmod 777 /etc

Does that help you at all?

---

### Post by Quirky on 2006-05-01
First I'd check to see if the /etc directory got busted with a mistyped command:

```
zgrep sudo /var/log/auth.log* | grep etc
```

Although you'd have to do a sudorm-rf/etc and a sudo mv X /etc to get the symptoms described.

---

### Post by Ramses de Norre on 2006-05-01
No you don't have to do those commands to get that, as BoyOfDestiny said: if you remove the permission to execute a folder you can't browse the folder nomore and it will look like a file.

---

### Post by morrin on 2006-05-02
I tried the two suggestions above. Still none the wiser though. 
I chmod etc to 777 but it didn't make any difference. If I "file" it I get back 

./ file etc
etc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped

I cant remember running any particular unusual commands that might have caused a problem.

---

### Post by morrin on 2006-05-05
Is there any way that I can re-install without deleting all my home directories etc? Or would I be best just to back up files I don't want to delete and do a completely fresh install. I haven't been able to find a simple solution to the problem.

---

### Post by mcduck on 2006-05-05
[QUOTE=morrin]Is there any way that I can re-install without deleting all my home directories etc? Or would I be best just to back up files I don't want to delete and do a completely fresh install. I haven't been able to find a simple solution to the problem.[/QUOTE]
Well, considering that when you try to run './etc' it tells you to use switch -x to extract, I think you have somehow compressed your /etc to a file.. You could try to run 'sudo ./etc -x /etc' (or should it be './etc -x /', I'm not sure how that works..)

---

### Post by morrin on 2006-05-05
[QUOTE=mcduck]Well, considering that when you try to run './etc' it tells you to use switch -x to extract, I think you have somehow compressed your /etc to a file.. You could try to run 'sudo ./etc -x /etc' (or should it be './etc -x /', I'm not sure how that works..)[/QUOTE]

Thanks for the idea. I hadn't thought of that. Unfortunately it didn't get me anywhere . I made a directory caleed etc2 and tried 
% ./etc -x etc2
and got back ...

usage: ./etc [-hv] [-x dir] file
 -h         print this help
 -x dir     extract into dir
 -v         be more verbose
 file       file to test

I thren tried 
%./etc -x etc2 etc
and got back
etc: invalid cramfs--wrong magic

---

### Post by mcduck on 2006-05-08
[QUOTE=morrin]Thanks for the idea. I hadn't thought of that. Unfortunately it didn't get me anywhere . I made a directory caleed etc2 and tried 
% ./etc -x etc2
and got back ...

usage: ./etc [-hv] [-x dir] file
 -h         print this help
 -x dir     extract into dir
 -v         be more verbose
 file       file to test

I thren tried 
%./etc -x etc2 etc
and got back
etc: invalid cramfs--wrong magic[/QUOTE]
You forgot the slash in front of the directory, it should be 'sudo ./etc -x /etc2'

---

### Post by morrin on 2006-05-09
[QUOTE=mcduck]You forgot the slash in front of the directory, it should be 'sudo ./etc -x /etc2'[/QUOTE]

I had tried that too, but to no avail. Still got the exact same output

---

