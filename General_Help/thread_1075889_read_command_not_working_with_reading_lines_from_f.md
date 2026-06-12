---
title: "read command not working with reading lines from file"
date: 2009-02-20
forum: General Help
---

### Post by etechship on 2009-02-20
I have two problems with this file
1) I have two lines on the website, and it only outputs one (fill free to hit the site and try it)
2) it wont pause, it just outputs "Please enter ...*"

```
#!/bin/sh

pause() {
        echo "Please enter a DVD-R into the drive and press [ENTER]:"
        read yeah
}

##growisofs -Z /dev/cdrw -dvd-video $file/

wget --quiet "http://admin.ucstreaming.net/_operations/dvd.php?status=burn" -O /root/vidss.txt

while read line
do
      echo $line
      one="$(echo $line | cut -d@ -f1)"
      title="$(echo $line | cut -d@ -f2)"
      folder='/vids/DVDS/'$one'/'

      pause

      echo $title
      growisofs -Z /dev/cdrw -dvd-video $folder
done < "/root/vidss.txt"

rm /root/vidss.txt


```

---

### Post by dcstar on 2009-02-20
> **etechship said:**
> I have two problems with this file
1) I have two lines on the website, and it only outputs one (fill free to hit the site and try it)
2) it wont pause, it just outputs "Please enter ...*"
...........

Of course it won't "pause", that is a DOS command:

[http://ubuntuforums.org/showthread.php?t=269408](http://ubuntuforums.org/showthread.php?t=269408)

---

### Post by etechship on 2009-02-20
If you notice, it calls a function, or is supposed to ...

---

