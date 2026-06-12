---
title: "mv command not working"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by xfearxnxloathing on 2008-01-16
i am trying to replace the menu icon "start-here.png" with a custom one and i am following directions from: [http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/](http://www.pendrivelinux.com/2007/10/19/changing-the-ubuntu-start-menu-panel-icon/)

i'm typing this in the terminal
> atreyu@aXion:~$ sudo mv /home/atreyu/Applications/ubuntu skins/menu icons/5 ubuntu/start-here.png /usr/share/icons/Human/22×22/places/
mv: target `/usr/share/icons/Human/22×22/places/' is not a directory: No such file or directory


now i promise that the directory i am trying to move the file to exists because i am staring at it as we speak.  please help!

**update**

so i moved the file to the desktopand typed in terminal
> atreyu@aXion:~$ cd ~/Desktop
atreyu@aXion:~/Desktop$ mv ~/Desktop/start-here.png /usr/share/icons/Human/22x22/places/
mv: overwrite `/usr/share/icons/Human/22x22/places/start-here.png', overriding mode 0644? y
mv: cannot move `/home/atreyu/Desktop/start-here.png' to `/usr/share/icons/Human/22x22/places/start-here.png': Permission denied
  wtf?!

---

### Post by ayampanggang on 2008-01-16
you sure those other directory exist? check them out.
if they do try to use mv to move one file at a time.

---

### Post by xfearxnxloathing on 2008-01-16
> **ayampanggang said:**
> you sure those other directory exist? check them out.
if they do try to use mv to move one file at a time.


i updated the original post, check it out.  i am only trying to move one png file.  both directories exist.  it comes up with that "blahblahblahoverwrite?" i'[m supposed to say yes or something to get it to accept but i honestly have no clue cause "y" or "yes" did not work.  =[

---

### Post by sisco311 on 2008-01-16
> mv ~/Desktop/start-here.png /usr/share/icons/Human/22x22/places/```
sudo mv ~/Desktop/start-here.png /usr/share/icons/Human/22x22/places/
```or you can run your file browser as root:
```
gksu nautilus
```

---

### Post by xfearxnxloathing on 2008-01-16
> **sisco311 said:**
> ```
sudo mv ~/Desktop/start-here.png /usr/share/icons/Human/22x22/places/
```or you can run your file browser as root:
```
gksu nautilus
```


go look and see if that directory exists for you cause i'm beginning to go crazy.  i've tried sudo...

> atreyu@aXion:~/Desktop$ sudo mv ~/Desktop/start-here.png /usr/share/icons/Human/22x22/places/
[sudo] password for atreyu:
mv: cannot stat `/home/atreyu/Desktop/start-here.png': No such file or directory


let me try to run the file browser as root.

**update**

wierd, somewhere along the lines of saying no such file or directory it added it anyway, lol.  must have been a bug or something.  i logged out and back in for another reason before doing the "gksu nautilus" code.  after typing in that command and the window popped up i noticed the png was missing off my desktop so i went to see if it had moved and it did.  thnx everyone!  

how do i log out of root for the browser so that i can get my regular theme back?

---

