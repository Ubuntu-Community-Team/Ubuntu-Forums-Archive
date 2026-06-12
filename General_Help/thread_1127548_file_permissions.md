---
title: "file permissions"
date: 2009-04-16
forum: General Help
---

### Post by handal on 2009-04-16
i got a little problem, on mt ubuntu 8.04 install (my web server) every time i uploade a new file or install a module(component i joomla the files becomes un wrightable. so every time i have to open my ftp client and chmod all files to 777 is there a woraround for this, so the file becomes auto 777

---

### Post by adamitj on 2009-04-16
You upload your files from your a web page, right? It the answer is yes, all files are created on disk with default 644 permissions (-rw-r--r--) for the current process user (please someone correct me if I am wrong). This means that your files are been written to disk in a way that only the current user for your HTTP server process can read and write it.

I presume you are using Apache (you could specify it), and I don't know exactly if there is a way to set file permissions automatically. 

What I can propose to you is a little "ugly" workaroud: 

1) Create a root script file in /root (like "file_permission") what do a chmod in all files of your desired folder;

Example for "/tmp" folder:

```
#!/bin/sh
chmod 777 /tmp/*
```

If you want to 777 all subfolders and files from a folder, change it to

```
#!/bin/sh
chmod -R 777 /tmp/*
```

2) set this file as an executable with command:
```
sudo chmod +x /root/file_permission
```

3) Put this file to run regularly into your /etc/crontab. I would suggest at every 60 seconds. To do it, open your /etc/crontab file with root permissions and add the line to the end of file:

open:
```
sudo gedit /etc/crontab
```

add new line:
```
00-59/1 * * * * /root/file_permission
```

---

### Post by Alekz_ on 2009-04-16
Well.. Maybe you should set umask 022 on your ftp server...


I mean, 022 IF you want ALL files with chmod 777! :)

[]'s

Alekz_

---

### Post by Iowan on 2009-04-16
> **Alekz_ said:**
> Well.. Maybe you should set umask 022 on your ftp server...
I mean, 022 IF you want ALL files with chmod 777! Wouldn't **umask 022** result in default permissions 644 for files, 755 for directories? [http://www.tech-faq.com/umask.shtml]("http://www.tech-faq.com/umask.shtml")

---

