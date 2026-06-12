---
title: "Ubuntu - can not execute binary file"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2008-04-07
it compiled ok?

show the output of "ls -alt"
show the value of $PATH with the command "echo $PATH"
show the command you're using to execute the object file and the error output

---

### Post by Shredder on 2008-04-08
I am having the same problem on a fresh 7.10 install with updates applied.

here is the output of ls -alt:

gw-user@gw-linux:~/srcds$ ls -alt
total 3444
drwxr-xr-x 27 gw-user gw-user    4096 2008-04-08 10:51 ..
-rwxrwxrwx  1 gw-user gw-user 3513408 2008-04-08 10:33 hldsupdatetool.bin
drwxr-xr-x  2 gw-user gw-user    4096 2008-04-08 10:33 .

here is the output of echo $PATH:

gw-user@gw-linux:~/srcds$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/gw-user/srcds

here is the error message I am getting when I try to execute the binary:

gw-user@gw-linux:~/srcds$ hldsupdatetool.bin 
bash: /home/gw-user/srcds/hldsupdatetool.bin: No such file or directory

The error is the same if I try to execute the binary including the explicit path:

gw-user@gw-linux:~/srcds$ /home/gw-user/srcds/hldsupdatetool.bin 
bash: /home/gw-user/srcds/hldsupdatetool.bin: No such file or directory

This one is boggling my mind, any help would be appreciated.

---

### Post by superyounan1 on 2008-04-08
prove that the file is located at that path

cd into where that file is and do
```

pwd
// pwd output here
ls
// ls output here

```

your path doesn't include the current directory, inorder to be able to execute binaries in your current working directory withouth putting in a relative or full path, you should append to your path. backup your parth first if you want.

```
export PATH=$PATH:.
```

this will update the PATH variable to be the current value of PATH plus '.', as in your current directory. So if I have a binary in:

```
/home/myname/projects/test/hello.o
```
now with the updated path i can do:
```
cd /home/myname/projects/test/
hello.o
// hello output
```
otherwise you would need to either use the complete path, like you said you did (but i'm not convinced the path is right because of that error), or you can cd into the right place and do the following instead
```
./hello.o
```
this is the relative path to execute hello.o assuming you're already in hello.o's direcotyr. this would work without appending the current working directory '.' to the path variable. 

so do what i suggested at the beginning to demonstrate the file is exactly where you think it is. Then try the relative path or update $PATH

---

