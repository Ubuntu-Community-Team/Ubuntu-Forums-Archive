---
title: "Simple sudo mv bash script"
date: 2009-03-22
forum: General Help
---

### Post by alanwalterthomas on 2009-03-22
I want to help out a technophobe put 2 files in a root access folder & thought a bash script might be the best thing possible if it's just a double click & enter password. I've hardly graduated from noob level myself & have never written a script.

I want this to happen on the person's computer after they download two files to their desktop:

sudo mv /home/alan/Desktop/th_pt_BR.* /usr/share/myspell/dicts/

Thanks to anyone who can show me what a little script like that would look like.

---

### Post by Yashiro on 2009-03-23
```
#!/bin/sh
echo Starting.
sudo mv /home/alan/Desktop/th_pt_BR.* /usr/share/myspell/dicts/
echo Finished.
exit
```

---

