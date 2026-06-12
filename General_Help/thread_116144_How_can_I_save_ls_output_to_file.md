---
title: "How can I save ls output to file?"
date: 2006-01-12
forum: General Help
---

### Post by kennyhow on 2006-01-12
I want to list the contents of a directory and save it to a file.

This is possible in DOS but I haven't found it possible with th "ls" command.

DOS is something similar to this : DIR > myfile.txt

and I tried this : ls -R home mylist.txt

and I get nothing.

Any ideas on how this can be done?

Thanks,
Ken

EDIT:  Nevermind.  I answered my own question.  I left out the >.  Now it worked.
So, for those that are wondering...the final line is:
ls -R home > mylist.txt

---

### Post by darth_vector on 2006-01-12
```
ls -R /home > myfile.txt
```

EDIT: oops, missed the last bit. sorry - long day! #-o

---

