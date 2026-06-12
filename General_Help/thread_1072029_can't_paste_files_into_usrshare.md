---
title: "can't paste files into usr/share"
date: 2009-02-17
forum: General Help
---

### Post by daniel_w93 on 2009-02-17
Hi people
I really hope somebody can help me...

I'm working in blender right now and tried to run the script "3gen" which is a tree generator. 

In order to do that I have to copy the downloaded files into the directory: usr/share/blender/scripts/blender

when I tried to paste it into the folder the following error message appeared:  
There was an error moving the file into /usr/share/blender/scripts/blender.
Error moving file: Permission denied

When I tried to change the permissions for the folder it said:
You are not the owner, so you can't change these permissions.

The owner name that was displayed was "root"

please somebody help me cause I'm stuck and I need to finish this animation for tomorow so please anybody got an idea?

---

### Post by konqueror7 on 2009-02-17
```
sudo cp * /home/Downloads usr/share/blender/scripts/blender
```

that shoudl do it, just change the first directory with your download directory...

or just better move all the files...
```
sudo mv /home/Download/MyFolder usr/share/blender/scripts/blender
```

---

