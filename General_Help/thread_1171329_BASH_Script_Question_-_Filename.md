---
title: "BASH Script Question - Filename"
date: 2009-05-27
forum: General Help
---

### Post by Aysah on 2009-05-27
Currently I'm debugging a script that we have that works on our RedHat servers but not on ubuntu.  All our other scripts work fine except this one that is suppose to check the filename and if it says "TEMP_", we skip that file.  I've commented out the rest of the code and threw an echo in there to test if the check is working and isn't unfortunately:

```
if [ ! ${filename05} = TEMP_ ]; then
echo $filename{05}

```

I put a file in the directory with the prefix, "TEMP_" and it still echoes the filename which is wrong.  This is very frustrating to me being that it works in our Redhat machine that is using an older version of BASH but not on this fresh box.

Any help would be appreciated.

---

### Post by HereInOz on 2009-05-27
Somewhere in the back of my mind there is a thought that /bin/sh on Ubuntu is a symlink to /bin/dash, not /bin/bash.

Does that help in any way?

---

### Post by nebileix on 2009-05-27
Try removing the curly bracket. By the way, the echo $filename{05} is different from the if expression ${filename05}. Is that what u wan?

---

### Post by Aysah on 2009-05-27
I friggin love you man.  Parts of my code got copied and pasted incorrectly so the syntax in my post is incorrect.  But either way all I needed to do was change the interpreter at the beginning of my script from "#! /bin/sh" to "#! /bin/bash".

Thanks again everyone

---

