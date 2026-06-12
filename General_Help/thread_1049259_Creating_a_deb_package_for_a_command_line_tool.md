---
title: "Creating a deb package for a command line tool"
date: 2009-01-24
forum: General Help
---

### Post by ezekiel000 on 2009-01-24
I tried to package a python command line tool to so that I could install it and be able to run it from any terminal with a single command rather than "python ./app.py [options] [filename.ext]"
but the way I have done this it doesn't pass along the options to the application, can anyone help me fix this.

Attached is the deb I've created.
The script "tagtheora" just contains:
#!/bin/sh
exec python /usr/lib/tagtheora/tagtheora.py

---

### Post by jgoguen on 2009-01-24
That script doesn't pass the options along to the python script.  Try this script instead:
```
#!/bin/sh

exec python /usr/lib/tagtheora/tagtheora.py $@
```
Note the $@ at the end of the exec line.  

Alternatively, possibly a better option, put this line as the very first line in tagtheora.py:
```
#!/usr/bin/env python
```
Then, make the python script executable (if it isn't already):
```
sudo chmod +x /usr/lib/tagtheora/tagtheora.py
```
And finally, instead of /usr/bin/tagtheora being a script, make it a link.  Back up tagtheora in case you want to keep it, this will remove it:
```
rm -f /usr/bin/tagtheora; ln -s /usr/lib/tagtheora/tagtheora.py /usr/bin/tagtheora
```
After that's all done, you should be able to run **tagtheora <options> <filename>**.  I'm more confidant about my second solution working, I'm not 100% certain about how exactly $@ handles parameters that were quoted and similar things.

---

### Post by ezekiel000 on 2009-01-24
Thanks I used your first solution and it worked great.

Edit: I would thank your post and mark the thread as solved like it says in your signature but both options seem to be missing.

---

### Post by jgoguen on 2009-01-24
Yea, those were removed because they were too hard on the database.  The admins are looking for an alternative that are kinder to our database though, they recognize that Thanks and Solved are very popular features.

---

