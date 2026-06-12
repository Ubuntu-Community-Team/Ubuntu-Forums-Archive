---
title: "/usr/bin/cube: 29: Syntax error: Bad substitution"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by dude2425 on 2005-10-15
I've been getting this particular error for a couple days as far as I've noticed, and have no idea how to fix it. The only two games I've noticed it on  so far is Cube and Nexuiz. I've already tryed to reinstall the games but to no avail, and now I'm completely out of ideas.

Any help would be nice, as I'm trying to prove to my little bro (*cough*nonbeliever*cough*) that there are games worth playing on Linux.

---

### Post by FerGeCo on 2006-10-06
Hey,

It's a little late .. but perhaps this will help someone in the future:

I had the same problem .. it's because we use the dash shell..

You can alter the script:

First do a : ls -l /usr/local/bin/cube and copy the symlink text .. the part after -> and do the following:

Change 
```

if [ -L "$path" ]; then
   ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
   echo "${ll/* -> }" 
```

to: 

```
if [ -L "$path" ]; then
   echo "/your/game/path/here/cube"
```

the readlink() routine is used to determine where the "real" cube script / directory is.

---

### Post by billyfoxtrot on 2006-10-13
FerGeCo,

Thanks for this fix!  I just used it to fix ioquake3.  It works exactly the same.

---

### Post by matthewschwimmer on 2008-02-01
I did what you said, but now i get > 88: ./linux_client: not foundI checked the folder, and i clearly see the linux_client. Any suggestions?

---

