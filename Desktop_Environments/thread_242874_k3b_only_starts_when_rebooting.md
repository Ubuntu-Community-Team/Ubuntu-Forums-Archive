---
title: "k3b only starts when rebooting"
date: 2006-08-24
forum: Desktop Environments
---

### Post by bernardo on 2006-08-24
Hello. 
My problem is simple: whenever i type ```
k3b
``` in the command line, nothing happens. Neither if i type ```
sudo k3b
```
If i try to check if k3b is loaded:
```
ps aux|grep k3b
``` it gives me:
```
user      17433  0.1  2.7  34604 14104 pts/0    D    14:57   0:00 k3b
```
According to the manual of ps, D means "Uninterruptible sleep (usually IO)"

But ! when i reboot, K3b will start with the desktop. ](*,) 

I couldn't find any single answer on the forum or the wiki or on the net (although many questions). 

So what is the workaround for this bug and when will it be fixed ?

I'd really like k3b to work, as i prefer it over the other burning apps.

Thank you.

---

### Post by bernardo on 2006-08-24
Bump !
:neutral:

---

### Post by bernardo on 2006-08-26
still no one ?:confused:

---

### Post by bullgr on 2006-08-26
i have a similar problem with k9copy...

i figure out, that were is a mount problem. k9copy starts and after a litle while there is not any hdd drive, it's not mounted and whatever i do, i can't mount it again until i reboot.

try to insert any cd-dvd (movie, mp3 whatever) and see i your burner is still mounted.

if the burner is not mounted, then you have the same problem with me, i believe it's a bug in ubuntu...

---

### Post by bullgr on 2006-08-26
ups, sorry, i forgot something...

if you use gnome, i use too...
it is not strange that k3b and k9copy are applications for kde?

maybe kde applications that use the burner have the mount bug?

why is gnomebaker working perfect?

---

### Post by bernardo on 2006-08-28
Thank you for your reply. Yes this must be a bug i remember having experienced that with breezy too so it's surprising i didn't find any information on the web about it. It should have been fixed or at least an explanation why it can't be fixed (if it can't).
Maybe it's a kde bug since you said it doesn't work with k9copy either...i don't know.

---

