---
title: "mv command permission denied"
date: 2009-01-27
forum: General Help
---

### Post by anthony3stacks on 2009-01-27
I been a linux user for a couple of months now and I never had a problem with the mv command in my terminal now I get a permission denied error trying to move any file 

anthony@anthony-laptop:~/Videos$ mv video01.mpg /Documents
mv: cannot move `video01.mpg' to `/Documents': Permission denied

I used the sudo command but when I go to the folder where I sent my file its not there  

thx

---

### Post by ibutho on 2009-01-27
Hi and welcome to the forum

The problem seems to be as a result of entering the wrong path

Try 
```
cd ~/Videos
mv video01.mpg ~/Documents/

```

In the command you entered above, you missed the ~ in front of /Documents which means that you are trying to copy the file to a directory thats just off / and thats only writable by root.

---

### Post by adamlau on 2009-01-27
Followed by: 

```
sudo rm -rf /Documents
```

If you so desire :) .

---

### Post by geirha on 2009-01-27
And if you ran that command « mv video01.mpg /Documents » as root, then video01.mpg has now been renamed to Documents and moved to / .

---

