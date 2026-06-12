---
title: "xclip"
date: 2005-11-15
forum: Deferred/Invalid Requests
---

### Post by mariuss on 2005-11-15
Not sure if this the right forum for this...

The latest xclip is in the repository but it is not "Ubuntufied", after you install it the binary is not on the PATH, you have to know where it is installed:
/usr/X11R6/bin/xclip

xclip's home page: [http://people.debian.org/~kims/xclip/](http://people.debian.org/~kims/xclip/)

Are there any other similar command line tools doing the same thing?

---

### Post by Darling on 2005-11-25
I've just installed xclip  as well (I really don't understand why this isn't a default utility). and it installs in /usr/X11/bin. I simply copied it tu /usr/local/bin and now I can use it as a normal user. 
I've also set it up with alias xclip="xclip -selection clipboard". It would even be better if it also set up a /dev/clipboard like in cygwin.

Another nice option is you can setup a script in nautilus-scripts that does a 
cat $file | xclip -selection clipboard

---

### Post by mariuss on 2005-11-26
I wrote a simple Nautilus extension script that will copy the names of the selected files to the clipboard:
[http://marius.scurtescu.com/?p=113](http://marius.scurtescu.com/?p=113)

---

### Post by Darling on 2005-11-29
copy the names is usefull too, but in most cases I want to copy the contents of the selected file (cat).
Another nice command is 
xclip -o -sel clip | mysql -h pizza.storedesk.com databaseName | xclip -i -sel clip

put a select statement in the clipboard, execute the command and you have the result in xml in the clipboard ;-)

---

### Post by jdong on 2005-11-29
looks somewhat promising as a Universe candidate... try to do it that way.

---

### Post by mariuss on 2005-11-29
[QUOTE=jdong]looks somewhat promising as a Universe candidate... try to do it that way.[/QUOTE]

Not sure what should I try? Could you give me a hint?

Thanks

---

### Post by jdong on 2005-11-29
[https://wiki.ubuntu.com/UniverseCandidates](https://wiki.ubuntu.com/UniverseCandidates)

Make sure it meets the requirements, and simply add it to the table.

---

### Post by mariuss on 2005-11-29
Thanks, now I see.

It seems that the original creator should add packages, I'll see.

---

### Post by Whizzy on 2005-12-09
join my forums today

[www.springshield.spreebb.com:D](www.springshield.spreebb.com:D)

---

