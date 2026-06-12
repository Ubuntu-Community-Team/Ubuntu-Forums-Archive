---
title: "Need help with root"
date: 2009-05-29
forum: General Help
---

### Post by JimmieAnderson on 2009-05-29
Hi I'm new to Ubuntu how do I use the root program someone told me about it but I'm not sure where to find it he said something about "sudo" but I cant find it in the menus can you help me?

---

### Post by madverb on 2009-05-29
Troll?

What are you trying to do?

---

### Post by ActiveFrost on 2009-05-29
_root_ is not a /program/ - it's a user ( like _Administrator_ on Windows XP ).
_sudo_ is a way to tell your pc that you want to do something as root ( and again, it's just a command ).

---

### Post by JimmieAnderson on 2009-05-29
Ah ok thanks so how do I use it and why

---

### Post by madverb on 2009-05-29
You use it if you need full access to your Linux install.

---

### Post by ActiveFrost on 2009-05-29
Read this guide : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and you'll hopefully do not need our help anymore ( regarding this question ) ;)

---

### Post by ad_267 on 2009-05-29
You don't need to know about it. If you try to do anything that requires you to be the root user Ubuntu will ask you for your password and let you know you're doing something that requires administrator privileges. 

Of course if you're trying to do everything from the command line then yes you need to know about sudo/root, but I doubt that's the case.

---

### Post by pmlxuser on 2009-05-29
well to just add on what other have already said.

when you wnat to perfoma activities or commands that require Administrative powers in this case in other linux version called root, in ubuntu /debian based systems you use sudo.

sudo sort of gives u super powers to do administrative work on your computer.

to use sudo - you just type the usual command (assuming that you are  familiar with wht a command is) in the following manner

```

$sudo cp /somefolder1/somefile   /bin/somefolder2/

```

the command above will copy somefile1 into the folder /bin/somefolder2/   under normal circumstances you can not just copy files into the bin folder because its a system folder and only the administrator or someone with administrative powers can do that.

---

### Post by tuxmanic on 2009-05-29
You can activate the **root**  from **Administration  > Users and Groups**....:).

Use ***su*** command from termnil to log on as root...

---

