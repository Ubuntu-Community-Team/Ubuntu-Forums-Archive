---
title: "open windows .url files in ubuntu!"
date: 2010-01-30
forum: Desktop Environments
---

### Post by alex_o on 2010-01-30
Old version, no multiple links in command line
```
#!/bin/bash
# script:  winlink
# author:  Alex Osborn(alex_osborn0@hotmail.com)
# date:    10 Jan 2010
# tested:  Ubuntu 9.10 (amd64)
# description:    Opens windows .url files in firefox, feel free to edit and use as needed just dont steal the credits!
#
if [ -f "$1" ];then
	if grep URL "$1" > /dev/null;then
		firefox -new-tab `grep URL "$1"|grep -iv eurl|tail -c +5`
	else
		echo invalid linkfile
	fi
else
	echo empty file
fi
exit
```
new version, multiple links in command line and in browser
```
#!/bin/bash
# script:  winlink
# version: 0.2
# author:  Alex Osborn(alex_osborn0@hotmail.com)
# date:    10 Jan 2010
# tested:  Ubuntu 9.10 (amd64)
# description:    Opens windows .url files in firefox, feel free to edit and use as needed just dont steal the credits!
#
TMP="/tmp/${0##*/}$$"
cat "$@"|grep -s URL|grep -ivs eurl > $TMP
LINE=1
MAX=`cat $TMP|wc -l`
while [ "$LINE" -le "$MAX" ];do
	LINK=`head -q "$TMP" -n $LINE|tail -qn 1|tail -qc +5`
	if [ -n "$LINK" ];then
		firefox -new-tab "$LINK"
		echo "$LINK"
	fi
	LINE=$((LINE+1))
done
rm $TMP
exit
```

1. Save the newest code to /home/USERNAME/bin/winlink.sh

2.
```
chmod a+x /home/USERNAME/bin/winlink.sh
```

3. In the file browser navigate to a .url file or make a blank one

4. Right click, properties -> open with

5. Click Add, and navigate to /home/USERNAME/bin/winlink.sh

6. Press Open

7. Press Add and then make the default application to launch .url files be winlink

8. Close and test!

---

### Post by falconindy on 2010-01-30
Neat idea, but I can't help but think this can be done in a far simpler manner. I've squeezed your script down to this:
```
#!/bin/bash
cat "$@" | sed -n 's/^URL=\(.*\)$/\1/p' | while read link; do
    firefox -new-tab "$link"
done
```

---

### Post by alex_o on 2010-01-31
> **falconindy said:**
> Neat idea, but I can't help but think this can be done in a far simpler manner. I've squeezed your script down to this:
```
#!/bin/bash
cat "$@" | sed -n 's/^URL=\(.*\)$/\1/p' | while read link; do
    firefox -new-tab "$link"
done
```

```
#!/bin/bash
cat "$@"|sed -n 's/^URL=\(.*\)$/\1/p'|while read link;do
firefox -new-tab "$link";done
```

tested and it allows multiple links with a terminal but the file browser only opens one of the links :(

thanks for helping though!

---

### Post by alex_o on 2010-02-12
by the way this goes great with the firefox addon savelink:

[https://addons.mozilla.org/en-US/firefox/addon/14019](https://addons.mozilla.org/en-US/firefox/addon/14019)

---

### Post by GrahamM on 2011-01-19
I have tried several approaches to this problem and I find this works just great.

One thing that puzzles me, is that I can change the names of the url files by deleting the url suffix. But the links still open???

One other thing - How would I get an Internet icon rather then the text icon for these links? I did try the other route using fx-url that is on these forums. Assogiate allows an icon to be chosen, but it does not appear on the desktop - Maybe something to do with how Assogiate and Gnome interact?

---

### Post by GrahamM on 2011-01-24
> **GrahamM said:**
> I have tried several approaches to this problem and I find this works just great.

One thing that puzzles me, is that I can change the names of the url files by deleting the url suffix. But the links still open???

One other thing - How would I get an Internet icon rather then the text icon for these links? I did try the other route using fx-url that is on these forums. Assogiate allows an icon to be chosen, but it does not appear on the desktop - Maybe something to do with how Assogiate and Gnome interact?

I was able to use winlink.sh and have all links work and have a nice Internet icon associated with the links.(I created a symbolic link and called it WINLINK). I used Assogiate to associate *.url files with WINLINK. I more or less followed the method in [ THIS LINK]("http://ubuntuforums.org/showthread.php?t=495131&highlight=fx-url+assogiate&page=2") post 14 items 4-8, but chose Multipurpose file for Category, Application/winlink.sh for Name, Description WINLINK and for icon, I copied one of Ooomingmaks in [THIS POST]("http://ubuntuforums.org/showpost.php?p=3276790&postcount=15") and moved it into /usr/share/icons/Humanity/mime/48/. Everything else in Assogiate is same as in Oomingmak's post.

Only other problem I had, was to strip the Default and Baseurl lines fron some of the links. Did this as outlined in [THIS POST]("http://ubuntuforums.org/showpost.php?p=10377428&postcount=8")

---

