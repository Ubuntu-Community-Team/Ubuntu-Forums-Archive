---
title: "a script to start openwengo 2.0 ?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by damu on 2006-07-17
I use openwengo 2.0 to make my phonecalls and chat.
Every time I start my computer, I have to open a terminal and copy and paste:
cd wengo
LD_LIBRARY_PATH=. ./qtwengophone


:-k 
Is there a way , so that I could either :

1)create a launcher

2) have openwengo starting when Ubuntu starts


Thanks

---

### Post by saracen on 2006-07-19
make a script with those commands.  The way you do that is by opening up a text editor (gedit) and then inputting those commands into the body of the file.  Then you need to make the file executable.  So:

```
gedit wengo.sh&
(put commands in file and save)
chmod +x wengo.sh
```

The part where I said put commands in file - you should put the following in the file:

```
#!/bin/bash
cd wengo
LD_LIBRARY_PATH=. ./qtwengophone
```

Better than saying 'cd wengo' is to say 'cd <full_path_to_wengo_directory>' - so if you have wengo in your home directory and your username is 'user' then instead of 'cd wengo' put 'cd /home/user/wengo'.  

After that you can make a launcher that points to that file and stick it on your desktop or wherever...

oh ya, and to have it start when you login, go to System->Preferences->Sessions and then add the command /home/user/wengo.sh to the list of startup programs.

---

### Post by damu on 2006-07-20
oh man, u're amazing...I am not a programmer, so, following the steps u gave to me and having now a launcher that works for openwengo ...it's magic! :p 

Thanks bunch! ;)

---

