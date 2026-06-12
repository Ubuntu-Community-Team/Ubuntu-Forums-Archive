---
title: "rsync Help with sh script"
date: 2009-02-08
forum: General Help
---

### Post by pasha07 on 2009-02-08
so i haven't found a good synch program for linux that looks at a folder in my usb and a folder in my hard and decides what files are the newest and updates the usb and local folder bi-driectionally according to which file is the newest. 

so i am using the following commands:

```
rsync -avuz /media/KINGSTON/Documents/My\ Documents/ /media/disk/My\ Documents/

rsync -avuz /media/disk/My\ Documents/ /media/KINGSTON/Documents/My\ Documents/
```

which work perfectly in keeping all files updated on both folders. 

now i am trying to write an sh script but nothing happens. i have 

```
chmod u+x sync.sh 
```

and here is the sh file:

```
#!/bin/sh
#
rsync -avuz /media/KINGSTON/Documents/My\ Documents/ /media/disk/My\ Documents/
rsync -avuz /media/disk/My\ Documents/ /media/KINGSTON/Documents/My\ Documents/
```

is there something i am missing or is there any better way to write this? any help would be very much appreciate it. 

thanks

---

