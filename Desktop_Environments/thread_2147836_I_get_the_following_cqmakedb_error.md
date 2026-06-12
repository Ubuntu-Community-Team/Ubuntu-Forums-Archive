---
title: "I get the following cqmakedb error"
date: 2013-05-23
forum: Desktop Environments
---

### Post by fat_boy on 2013-05-23
After the files have been added to cscope.files  this is the script thsat is run:

cscope -cbkR
ctags --fields=+i -n -R -L ./cscope.files
cqmakedb -s ./mykernel.db -c ./cscope.out -t ./tags -p

2407 Segmentation fault      (core dumped) cqmakedb -s ./mykernel.db -c ./cscope.out -t ./tags -p


It worked OK previously, I just added a path fopr two new file types to go into the cscope.files and if I comment out either of these it is OK.

Is isnt caused by the number of files, because I have also built a browse database for the user mode code, and thats about 10 times the size of the kernel and that db builds OK.

Oh, I note that on opening the db file in codequery that the Exact Match and the other check box have gone. Other than that the db seems to be OK.

--edit--

I just added two more entries, same path, two file types, and specified a more complete path for all the other 'find <path> -iname ...' in the script file and the error has gone.

How odd.

So, dont knwo about a fix, but speficying the path more precisely seems to solve the issue.

---

### Post by dino99 on 2013-05-23
[https://github.com/ruben2020/codequery/blob/master/doc/HOWTO-LINUX.md](https://github.com/ruben2020/codequery/blob/master/doc/HOWTO-LINUX.md)

---

### Post by fat_boy on 2013-05-23
Unsurprisingly I read that web page already, I have installed it after all, and used the script as he suggests.

---

