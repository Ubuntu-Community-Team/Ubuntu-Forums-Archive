---
title: "Directx"
date: 2005-12-12
forum: Desktop Environments
---

### Post by Akya on 2005-12-12
would some one help me install directx?

---

### Post by RAOF on 2005-12-12
Um, you can't?  And if you mean "how can I play windows games", I would suggest that the easiest solution **by far** is to actually use windows, if you happen to have a license.

If you **don't** have a windows license, still want to play windows games, and want help installing the free, unsupported Cedega then:

1) Download the WineCVS.sh script.  From your other posts, I believe you already have.  Find out what directory you downloaded it to.
2) Open a terminal
3) Type the following commands into the console:
```
sudo apt-get install build-essential cvs
sudo apt-get build-dep wine
cd <the directory that you downloaded WineCVS.sh to>
chmod +x WineCVS.sh
./WineCVS.sh

```
And follow the prompts for the WineCVS script.

---

### Post by Chua-Chua on 2005-12-12
where can I download the script?
Is the downloading of the script the only step I need to do?

---

### Post by RAOF on 2005-12-12
I'd suggest looking at the WineCVS howto [here]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45").  It's not Ubuntu specific, but that should work.

---

