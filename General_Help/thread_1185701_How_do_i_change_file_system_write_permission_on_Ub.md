---
title: "How do i change file system write permission on Ubuntu 8.04"
date: 2009-06-12
forum: General Help
---

### Post by izuchi on 2009-06-12
i can not copy and paste any thing into my file system it tells me access denied and i am new to Ubuntu i try using some chown command but its not working please somebody help me and tell what to do please thanks

---

### Post by merlinus on 2009-06-12
Can you be more precise as to exactly where you are trying to write?  If it is to files and directories in the / partition, then you can only do this with sudo.

Changing ownership of anything within / is unwise.

---

### Post by LKjell on 2009-06-12
Hi could you tell us what you are trying to copy and past and to where? And what is the mount path for you filesystem? And to answer the question. You change your file permission by using the chmod command. chmod 777 <file> will let everyone read write and execute the file.

---

### Post by gradinaruvasile on 2009-06-12
In ubuntu you are a restricted user.You can copy files normally in your home directory (Places->Home Folder). Other than that you have to use higher level permissions (via sudo). That happens also when u are asked for your password (the system has to write files and configurations when installing software etc.). 
Also u can write to other partitions than the root one. It is not wise to write in places not owned by your user if u dont know exactly what are u doing. Linux permits much higher control over the OS but u may break it fast if dont have proper knowledge.
The best practice would be creating folders in your home directory and keeping stuff there.

---

