---
title: "How  to run a command automaticaly  at startup ?"
date: 2008-12-04
forum: General Help
---

### Post by rams123 on 2008-12-04
I have to insert a command in terminal in order to connect to internet. So every time I start Ubuntu I have to open terminal and enter a command     to connect to internet . This  is very hard for me to do every time. 

Is there any way to run that  command automatically at startup  ?

---

### Post by binbash on 2008-12-04
System > Preferences > Sessions add it here to start it at gnome start up OR

add the command before exit at /etc/rc.local

(Try Sessions one first)

---

### Post by felldin on 2008-12-04
Go to system->preferences->sessions. Under the startup program tab click add and then you should be able to add a command there.

---

### Post by rams123 on 2008-12-05
After starting Ubuntu I will do like this to connect to internet - 

1. Open terminal

2. Type "cd /home/ram/Desktop/crclient" and press enter

3. Then again type - "./crclient -u rams123 " and press enter.
[B]
Can you please tell me how to do the above steps automatically at startup ?[/B]

---

### Post by puppywhacker on 2008-12-05
You probably don't need to cd to the directory unless the script is not very clever. So go to the menu's the other 2 answered.

```

System - Preferences - Session - Add
/home/ram/Desktop/crclient/crclient -u rams123

```

If your script is not very clever you can run the commands sequentially when you seperate them with a semi-colon ( ; )

```

cd /home/ram/Desktop/crclient/;./crclient -u rams123

```

---

### Post by rams123 on 2008-12-07
Thanks. 

Can you please tell me what do you mean by CLEVER here ?

---

### Post by zika on 2008-12-07
> **rams123 said:**
> Thanks. 

Can you please tell me what do you mean by CLEVER here ?

For example, if while executing it, it is supposed that You are in aforementioned directory. Then these two approaches would make a difference. Bad choice of words ... ;)

---

