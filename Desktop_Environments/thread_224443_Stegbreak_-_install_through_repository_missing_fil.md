---
title: "Stegbreak - install through repository missing files"
date: 2006-07-28
forum: Desktop Environments
---

### Post by M4LFUNCT10N on 2006-07-28
I installed stegdetect through synaptic, and bundled with it is stegbreak.  Running stegbreak gave an error that /usr/share/stegbreak/rules.ini did not exist.  I found the file while searching around through previous versions.  I added the files, but now the error I receive is "Segmentation fault".

What do I need to do to get this fixed?

---

### Post by blacksun on 2006-11-08
i have exactly the same problem; after I copy rules.ini to /usr/share/stegbreak/rules.ini
I get Segmentation fault

---

### Post by undadecor on 2008-06-13
I had the same problem.  Here is a workaround.


First, make sure wine is installed.

Head to [http://www.outguess.org/download.php]("http://www.outguess.org/download.php") and download the "Stegdetect 0.4 - Windows Binary."  Unzip it, then cd to the directory:
```
cd stegdetect
```

Then, we need to put the files in the correct locations:
```
sudo mkdir /usr/local/share/stegbreak
sudo cp rules.ini /usr/local/share/stegbreak/
cp * ~/.wine/drive_c/windows/system32/

```

Then, run this to use the program:
```
wine stegbreak.exe ARGUMENTS
```

---

### Post by undadecor on 2008-07-02
Filed a bug report on launchpad, bug #245063

[https://bugs.launchpad.net/ubuntu/+source/stegdetect/+bug/245063]("https://bugs.launchpad.net/ubuntu/+source/stegdetect/+bug/245063")

---

