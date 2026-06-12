---
title: "Mapping an FTP folder for normal use"
date: 2006-06-09
forum: Desktop Environments
---

### Post by kitsched on 2006-06-09
I'm trying to map an FTP folder and then edit the files contained in it directly with gedit but I'm having no luck. Whenever I open a file for editing it says that it's read only. And so I can't save it or anything, the only solution being to copy the files to a working directory on my local drive and then after editing copy them back to the mapped drive. Which isn't exactly elegant...

I searched through the forums and the closest match I found, actually the exact same problem that I'm having is [this thread]( http://ubuntuforums.org/showthread.php?t=128482). However, nobody answered the poster's problem there.

I hope somebody will answer here.

---

### Post by kitsched on 2006-06-10
Bumpybump...

---

### Post by scxtt on 2006-06-10
if someone has the exact same problem, why create a new thread? -- not a biggie (isn't my server :p), but ...

anyway ... i think it'd be better using an SSH connection instead of an FTP connection ... SSH also uses sFTP connections, so it'll work the same ...

i am able to connect to my old college account via connect to server and edit files directly from the folder and just click save (i.e. no "read only" problems) ...

honestly, i tried this yesterday - and i was having the problem w/ "read only" - but it worked today ... the only difference was that there was a discrepancy w/ who owned the file (it was using my local user/group setting instead of the one for my college account) ...

---

