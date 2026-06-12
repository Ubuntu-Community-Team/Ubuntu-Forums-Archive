---
title: "ubuntu 10.04 removing multiple files in Makefile"
date: 2010-07-04
forum: Desktop Environments
---

### Post by alirezagh76 on 2010-07-04
I would like to delete multiple files with the same name but different extensions in a Makefile. As following


rm $(MAINFILE).{ps,pdf,aux,dvi,log,bbl,blg}

and I get the following error 

rm: cannot remove `paper.{ps,pdf,aux,dvi,log,bbl,blg}': No such file or directory

I have done this in opensuse without any error. I tried to reinstall make and install some other packages which could be relevant. 

I would be thankful if anyone can help me.

---

### Post by alhirzel on 2012-06-18
Sorry for the thread necromancy but I hope this helps someone in the future! This works with at least gmake.

```
MYFILE = foo.tex

# ...

clean:
    rm -f $(foreach ext, aux log out, ${MYFILE:.tex=.${ext}})
    #                    ^^^^^^^^^^^  ^^^^^^^^^^^^^^^^^^^^^^
    #                    extensions   trick for replacing extensions

    # evalutes to:
    # rm -f foo.aux foo.log foo.out
```

---

