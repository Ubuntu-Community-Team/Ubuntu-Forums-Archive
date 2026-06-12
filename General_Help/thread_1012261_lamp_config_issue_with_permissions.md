---
title: "lamp config issue with permissions"
date: 2008-12-15
forum: General Help
---

### Post by cjoki on 2008-12-15
Hello,


I am a windows migrant and need a little help finalizing my lamp stack. 

I have installed lamp on my ubuntu 8.10 desktop. I also setup rapache to handle apache issues and the full netbeans system (c++, php, java, ruby, etc...). 

Now I need to move my web development files to the var/www/....etc...folders. Since the www is owned by root I guess I have to use the command 
```
sudo cp <source location> <destination location>
```

I am guessing this command will move all files and sub directories?

also since I am using Netbeans as my editor for php do I need to configure netbeans in some way to grant it access to the files in the var/www files? or is this some other sudo command I need to execute?


Thanks.

---

### Post by louieb on 2008-12-15
You have a few options. You can use the **chow** command and change the ownership of /var/www to be you. Or you can use the** chmod **command to give all read /write permissions to /var/www .

What I did was change my apache configuration to use a folder in my home directory as the document root. 
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by cjoki on 2008-12-15
louieb thank you. I used the following command to change the owner and the group of the www folder and all of its subdirectories...I can now work free!
```
chown -hR username:username /var/www
```

---

