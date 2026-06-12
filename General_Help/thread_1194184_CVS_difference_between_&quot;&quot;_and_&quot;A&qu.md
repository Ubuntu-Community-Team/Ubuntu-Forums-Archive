---
title: "CVS difference between &quot;?&quot; and &quot;A&quot;"
date: 2009-06-22
forum: General Help
---

### Post by hwttdz on 2009-06-22
What is the difference between "A" and "?" when one runs a cvs update command? 

Descriptions of both are given here:
[http://www.network-theory.co.uk/docs/cvsmanual/updateoutput.html](http://www.network-theory.co.uk/docs/cvsmanual/updateoutput.html)

Thanks.

---

### Post by ManiacDan on 2009-06-22
A means "The file has been added to your private copy of the sources, and will be added to the source repository when you run commit on the file."

? means "File is in your working directory, but does not correspond to anything in the source repository, and is not in the list of files for CVS to ignore"

So...that's it.  If it's marked as A, you've "added" the filename to the CVS system, but not checked anything in.  If it's ?, it's not version controlled at all, and not ignored.  You should only see A after you've done cvs add <file>, before you've run your next commit.

-Dan

---

