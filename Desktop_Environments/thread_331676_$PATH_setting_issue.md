---
title: "$PATH setting issue"
date: 2007-01-04
forum: Desktop Environments
---

### Post by phez on 2007-01-04
I am having some problems adding a directory to the PATH on boot. I am a newb to Ubuntu but not to linux. 

I created a directory in the root directory. I am trying to add it to the PATH on boot but I can not get it to work. I have tried adding it to all of the normal files with no luck. I tried looking it up but everything I found indicates what I am trying should work. Is there a trick to making it work in Ubuntu? I am sure I am missing something basic here. :confused: 

Any help would be great.

---

### Post by taurus on 2007-01-04
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Then, create these two lines if they are not already there...

```
PATH=$PATH:**new_path**
export PATH
```

---

### Post by phez on 2007-01-04
Thanks taurus, 
I am a bone head. I was using the correct files but I forgot to export the PATH after I set it. ](*,)

---

