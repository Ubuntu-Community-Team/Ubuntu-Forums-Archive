---
title: "Installing Flash Plug-in for Opera"
date: 2006-07-06
forum: Desktop Environments
---

### Post by vaibhavkapoor on 2006-07-06
Hi,

I am using Opera on the Drapper, I need to flash in the flash plug-in in the plugins directory of opera but I cannot paste the plug-in files in the directory.

I tried running the flash player, installer also but it was not able to find the directory where Opera was installed. After going through the readme.txt of the insallation folder I found that I could just copy and paste the plug-in files.

The location of the Opera plug-ins folder is /usr/lib/opera/plugins

How do I paste files to this folder?

I am looged in as root

---

### Post by rudiz on 2006-07-06
mv file targetfile

---

### Post by vaibhavkapoor on 2006-07-11
> mv file targetfile

I would really appreciate if you could explain a bit more. I don't really understand what is the command and how to execute it.

I am a newbee to linux

Regards,
Vaibhav Kapoor

---

### Post by lordlollo on 2006-07-11
You can try 
```
man mv
```
Anyway, the syntax is very simple 
```
mv path_to_the_file_you_want_to_move/file_name /path_to_the_location_you_want_to_move_the_file
```

---

