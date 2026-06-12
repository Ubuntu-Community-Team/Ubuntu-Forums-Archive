---
title: "installation help."
date: 2009-02-23
forum: General Help
---

### Post by bostock73 on 2009-02-23
Hey guys. I have an amd 1250x graphics card, and the linux drivers are supplied on their website. If i download it to my desktop, and CD to there, what terminal action must i use to install it? it is a .run file.

Thanks.

---

### Post by etdsbastar on 2009-02-23
send me the screen shot. or explain clearly.

---

### Post by konqueror7 on 2009-02-23
if i understand it correctly,
```
cd Desktop/
```
then,
```
sudo somefile.run
```

---

### Post by bostock73 on 2009-02-23
I'm running kubuntu with kde 4. Ive cd to the desktop and hit sudo blablah.run

I just get command not found. Any ideas guys?

---

### Post by konqueror7 on 2009-02-23
try opening the terminal and just type "sudo ", then just drag the file into the terminal and hit enter...

---

### Post by mb_webguy on 2009-02-23
You need to make sure the file is executable.  Either right-click and change the permissions in Properties, or go to the terminal and use "chmod a+x /path/to/file".  Then you should be able to run the file with "sudo /path/to/file".

---

