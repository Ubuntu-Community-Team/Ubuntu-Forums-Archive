---
title: "uninstalling TCE and ET"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by 71CH on 2007-05-12
Can somebody please tell me how I can completely uninstall TCE and ET?  Thanks.

---

### Post by noerrorsfound on 2007-05-12
```
sudo rm -r /usr/local/games/enemy-territory && rm -r ~/.etwolf
```

---

### Post by 71CH on 2007-05-12
thanks for your response but I get this when I type that in

[PHP]rm: descend into write-protected directory `/home/keedai/.etwolf'? y
rm: descend into write-protected directory `/home/keedai/.etwolf/pb'? y
rm: remove write-protected regular file `/home/keedai/.etwolf/pb/pbsv.so'? y
rm: cannot remove `/home/keedai/.etwolf/pb/pbsv.so': Permission denied
rm: remove write-protected regular file `/home/keedai/.etwolf/pb/pbcl.so'? y
rm: cannot remove `/home/keedai/.etwolf/pb/pbcl.so': Permission denied
rm: remove write-protected regular file `/home/keedai/.etwolf/pb/pbag.so'? y
rm: cannot remove `/home/keedai/.etwolf/pb/pbag.so': Permission denied
rm: descend into write-protected directory `/home/keedai/.etwolf/etmain'? y
rm: remove write-protected regular file `/home/keedai/.etwolf/etmain/etconfig.cfg'? y
rm: cannot remove `/home/keedai/.etwolf/etmain/etconfig.cfg': Permission denied
rm: remove write-protected regular file `/home/keedai/.etwolf/etmain/servercache.dat'? y
rm: cannot remove `/home/keedai/.etwolf/etmain/servercache.dat': Permission denied
[/PHP]

---

### Post by noerrorsfound on 2007-05-12
I believe I know the problem. I purposely left out "sudo" in the command to remove your .etwolf directory, because it was in your home folder so I assumed it wouldn't require admin privileges. What I forgot is that the ET installer requires you to run as root, and since you run it as root (with sudo) then some files that it extracts are owned by root.

Here is the correct command (notice the second sudo):
```
sudo rm -r /usr/local/games/enemy-territory && sudo rm -r ~/.etwolf
```

---

### Post by 71CH on 2007-05-12
i think it worked
thanks :)

---

