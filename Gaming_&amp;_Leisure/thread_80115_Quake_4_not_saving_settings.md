---
title: "Quake 4 not saving settings?"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by horsefactory on 2005-10-21
The game runs really nicely but every time I restart, it's in 640x480 still and asks for the CD Key. 

I'm assuming this is some sort of permissions issue or something, or do I need to create a .cfg file somewhere for it to write my settings?

I ran the initial setup with sudo, if that's anything. Thanks in advance if anyone knows what the issue is here :)

---

### Post by dmn_clown on 2005-10-21
Check the permissions of your ~/.quake4 directory.```
ls -la 
```

Your user account needs to have read/write permissions or the config file will not be saved.  

If you have r/w permissions the output will look something like this

```
drwxr-xr-x   4 user-name group-name     4096 2005-10-20 19:02 .quake4
```

---

