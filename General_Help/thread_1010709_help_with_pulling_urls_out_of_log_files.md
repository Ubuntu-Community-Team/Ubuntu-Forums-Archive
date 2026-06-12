---
title: "help with pulling urls out of log files"
date: 2008-12-14
forum: General Help
---

### Post by a person on 2008-12-14
I would like to get a list of urls out of my xchat logs.  So far I have:

```
cat *.log | grep http:// > url.txt

```

I have been suggested to use http:\:\/\/.* but that doesn't return any results.

I would like to grab urls that also start with www also (being able to pull urls that don't contain either http:// or www would be nice).  This also returns the whole line, I would rather it output just urls.

Any help would be appreciated and I hope I was being clear enough.

---

### Post by eBoxNet on 2008-12-14
you can try this (i am not sure it will work)
```

#!/bin/sh

if [ -z $1 ]; then
        echo "Needs filename as argument."
        exit 1
elif [ -f "$1" ]; then
        fname="$1"
fi

while read a;
do

  echo "$a" | sed -e "s+http://++"

done < "$fname"
```

* Save this as a shell script of a name you like, e.g. url-extract.sh

* Make it executable with chmod +x url-extract.sh

* Give your filename as the first argument:
url-extract.sh filename_that_is_to_big_to_edit_by_hand.txt


original post : [http://www.linuxquestions.org/questions/linux-desktop-74/bash-script-to-edit-text-file-518072/](http://www.linuxquestions.org/questions/linux-desktop-74/bash-script-to-edit-text-file-518072/)

---

### Post by a person on 2008-12-14
That will only search one file and would remove what I'd like to keep, wouldn't it?

---

### Post by eBoxNet on 2008-12-14
it will search your file and then it will display the results

---

### Post by a person on 2008-12-14
Regardless, I would like to search the whole directory, not just a single file.  Thank you though for your replies.

---

### Post by eBoxNet on 2008-12-14
Search inside .txt
```
grep "something" *.txt
```

Search inside folder (directory)
```
grep -R "something" /dir
```

---

