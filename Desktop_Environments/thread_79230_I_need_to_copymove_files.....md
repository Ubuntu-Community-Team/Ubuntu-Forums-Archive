---
title: "I need to copy/move files...."
date: 2005-10-19
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-19
hi..
I have files that i need to move to /usr/local/games/base....

however it wont let me drag or copy to the folder...
How can i get it to caop..
I assume its a root permissions porblem..
A terminal solution is fine....

thanx

---

### Post by adwait on 2005-10-19
If the terminal is fine then here goes:
For MOVING:
```
sudo mv <file> /usr/local/base/..
```
for COPYING
```
sudo cp <file> /usr/local/base/..
```

In place of <file> you can put the filename, or a directory or even anything using a wildcard
eg: *.mp3 to move all the mp3 files in a particular folder

---

