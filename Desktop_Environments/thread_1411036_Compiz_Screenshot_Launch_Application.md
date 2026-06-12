---
title: "Compiz Screenshot Launch Application"
date: 2010-02-19
forum: Desktop Environments
---

### Post by retznto on 2010-02-19
I hope this isn't a stupid question, I searched around but couldn't find an answer.

I have a very simple script I would like to run after I take a screenshot using compiz.

```
echo $0" "$1
dropbox puburl $1 | xsel --clipboard
```
The screenshot plugin saves in my public dropbox folder, and then this script copies the public URL to the clipboard.

The script runs fine when I run it from terminal with the file name as an argument, the problem I'm having is getting the screenshot plugin to do this for me.

In my "Launch Application" box (in the screenshot plugin configuration), I have this:
```
gnome-terminal -e ./copylink.sh
``` (copylink.sh is the filename of the script above)

It runs the script fine, but there are no arguments passed to it.

How would I go about getting the plugin to pass the filename as an argument? Is it even possible?

Thanks.

---

### Post by nilarimogard on 2010-02-19
You can use either imagemagick or gscrot to take the screenshot and then it's a lot easier

Here is an example script to take a screenshot and upload it to imgur. You can use it as an example and customize it for dropbox:

```
#!/bin/bash
screenshot='screenshot';
nano=`date '+%d-%m-%y-%N'`;
extension='.png';
file="$HOME/Desktop/$screenshot-$nano$extension";
sleep 3; scrot -s -b -q 0 $file;
curl -# -F "image"=@"$file" -F "key"="5d317f0bee23b282473522e1aa68f621" http://imgur.com/api/upload.xml|\
      grep -Eo '<[a-z_]+>http[^<]+'|sed 's/^<.\|_./\U&/g;s/_/ /;s/<\(.*\)>/\x1B[0;34m\1:\x1B[0m /'
exit 0
```

---

### Post by retznto on 2010-02-19
That's awesome! You've saved me a lot of time.

Thanks for your help :)

---

### Post by nilarimogard on 2010-02-19
You're welcome ;)

---

