---
title: "alittle help with accessing stuff from terminal"
date: 2008-12-09
forum: General Help
---

### Post by ShaolinF on 2008-12-09
Hi Guys

I have a mysql server setup on my ubuntu 8.10. The problem is everytime I want to access my server I need to go to the directory of the file and then run it. Is there anyway I can type it anywhere in terminal (regardless of directory) and it'll load up the required files ? I want to beable to type mysql -u root -p anywhere and it should log me into my sql area.

---

### Post by LoneWolfJack on 2008-12-09
it should work exactly like that. if you open a new shell window and type mysql, what does it say?

---

### Post by ShaolinF on 2008-12-09
It says I havent installed it and should use apt-get etc - I have build it from source btw.

---

### Post by tacutu on 2008-12-09
if the executable is not in the PATH, you might try:

```
/path/to/mysql/binary/mysql -u root -p
```

alternatively, put /path/to/mysql/binary in your PATH environment (in .bashrc)

---

### Post by ShaolinF on 2008-12-09
Is it located in /etc/skel/.bashrc ?

---

### Post by tacutu on 2008-12-09
no, the one in your /home/USERNAME directory. If you want it for all users, I think you should add a file in /etc/profile.d but I'm not 100% sure. Try reading /etc/profile and /etc/bash.bashrc, see if you find something there.

---

### Post by ShaolinF on 2008-12-09
Ok. Now how do I add the path and where abouts in the file?

Is this correct:

#Set up PATH for MySQL
PATH=$PATH:/usr/local/mysql/source/bin/mysql
export PATH

?

---

### Post by tacutu on 2008-12-09
that looks correct. don't forget to 'source' the file after saving the changes. That is, if you added the path in, say, .bashrc, do:
```
source ~/.bashrc
```

---

### Post by ShaolinF on 2008-12-09
what does that do ? refresh or something ?

---

### Post by tacutu on 2008-12-09
yes, it makes bash read the file so that it knows of the new variable. Or, you could logout and re-login. 
As to the matter of where in the file, I don't thing it matters. I usually just append it to the end.
BTW, looking at your path, it seems that you compiled mysql but did not 'make install'. I am not familiar with mysql, but a make install should install it in /usr/local, with the binary in /usr/local/bin, which means you don't have to mess with the paths. read the INSTALL file that came with the sources.

---

