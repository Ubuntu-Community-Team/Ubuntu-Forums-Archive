---
title: "How do I restore a folder using a Live USB?"
date: 2009-02-25
forum: General Help
---

### Post by andonato on 2009-02-25
Let's say I want to restore a system directory - we'll call it "FolderA" - that I accidentally deleted. Let's assume that there are items in FolderA that you need root privileges to manipulate. 

I have my LiveUSB session up and running. A simple 

```
sudo cp /usb/location/FolderA /local/location/
``` 

gives the following:

```
cp: omitting directory `/usb/location/FolderA'
```

What do I try next?

---

### Post by kestrel1 on 2009-02-25
Try this ```
sudo cp -r /usb/location/FolderA /local/location/
```

---

### Post by andonato on 2009-02-25
That worked! Many thanks!!

---

### Post by kestrel1 on 2009-02-25
No problem.

---

