---
title: "how do i do this  ??? triple A"
date: 2011-11-25
forum: Gaming &amp; Leisure
---

### Post by jedibrijon on 2011-11-25
im at downloading games for Ubuntu im trying to download tripleA  for  my computer and put it in easy tearms :guitar:thanks

---

### Post by Perfect Storm on 2011-11-26
Extract the .zip file

Open the terminal

```
cd /into/tripleA/folder
./triplea_unix.sh
```

Make sure you have java installed first.

---

### Post by jedibrijon on 2011-11-26
when i enter the code it says no file  found   help please?

cd /into/tripleA/folder ./triplea_unix.sh

---

### Post by Perfect Storm on 2011-11-26
cd /into/tripleA/folder

means you have to fill in like something;

```
cd /home/USERNAME>/Downloads/TripleA folder>
```
then hit the <enter> key afterwards before entering the next command.

You can see the Triple A's path in your filebrowser and copy it, it may be easier.

---

### Post by jedibrijon on 2011-11-26
i dont understand? , my username is brian@brian-inspiron-6000:~$ at least that what it say in the box.
You can see the Triple A's path in your filebrowser and copy it, it may be easier. whats that mean?

---

### Post by Perfect Storm on 2011-11-26
Where did you unpack the zip file? and what's the name of the folder?

---

### Post by jedibrijon on 2011-11-26
destop ,  triplea_1_3_2_2

---

### Post by Perfect Storm on 2011-11-26
ok,

```
cd ~/Desktop/triplea_1_3_2_2
./triplea_unix.sh

```

---

### Post by jedibrijon on 2011-11-26
this time it says Permission denied

---

### Post by Perfect Storm on 2011-11-26
The first command or the second command?

Please copy the in/output of the terminal.

---

### Post by jedibrijon on 2011-11-26
brian@brian-Inspiron-6000:~$ cd ~/Desktop/triplea_1_3_2_2
brian@brian-Inspiron-6000:~/Desktop/triplea_1_3_2_2$ ./triplea_unix.sh
bash: ./triplea_unix.sh: Permission denied
brian@brian-Inspiron-6000:~/Desktop/triplea_1_3_2_2$

---

### Post by Perfect Storm on 2011-11-26
Right click on triplea_unix.sh and click properties.

Go to Permissions tab and enable 'Allow executing file as program'.
Then try again.

---

### Post by jedibrijon on 2011-11-26
it already was

---

### Post by Perfect Storm on 2011-11-26
okay, instead of the command **./triplea_unix.sh** use **sh triplea_unix.sh** instead.

---

### Post by jedibrijon on 2011-11-26
brian@brian-Inspiron-6000:~$ ./triplea_unix.sh use sh triplea_unix.sh
bash: ./triplea_unix.sh: No such file or directory
brian@brian-Inspiron-6000:~$

---

### Post by Perfect Storm on 2011-11-27
> **jedibrijon said:**
> brian@brian-Inspiron-6000:~$ ./triplea_unix.sh use sh triplea_unix.sh
bash: ./triplea_unix.sh: No such file or directory
brian@brian-Inspiron-6000:~$


only;

```

sh triplea_unix.sh

```

---

### Post by jedibrijon on 2011-11-27
IT SAYS 

brian@brian-Inspiron-6000:~$ sh triplea_unix.sh
sh: Can't open triplea_unix.sh
brian@brian-Inspiron-6000:~$

---

### Post by Perfect Storm on 2011-11-27
Are you sure, you're have downloaded the right package? This is one I used to test it: [http://sourceforge.net/projects/triplea/files/TripleA/1_3_2_2/triplea_1_3_2_2_all_platforms.zip](http://sourceforge.net/projects/triplea/files/TripleA/1_3_2_2/triplea_1_3_2_2_all_platforms.zip)
...and it worked for me.

---

### Post by jedibrijon on 2011-11-27
after i extracted it went to my brian folder

---

### Post by Perfect Storm on 2011-11-27
```
cd && cd triplea_1_3_2_2
sh triplea_unix.sh
```

---

### Post by jedibrijon on 2011-11-27
it worked thanks does this mean i have to enter that command every time i want to play?

---

### Post by Perfect Storm on 2011-11-27
> **jedibrijon said:**
> it worked thanks does this mean i have to enter that command every time i want to play?

aye, but you can make a launcher for it. Here's the command for the launcher. Note that you need to change it if you move the folder elsewhere;

```
sh -c "cd triplea_1_3_2_2 && sh triplea_unix.sh"
```

---

