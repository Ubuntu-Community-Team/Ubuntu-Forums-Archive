---
title: "Noob question: How to open executables as root"
date: 2009-05-16
forum: General Help
---

### Post by D-meist on 2009-05-16
Trying to open a program.  So I double clicked on ops in the file browser:

[IMG]http://i130.photobucket.com/albums/p241/D-meist/Screenshot.png[/IMG]

Then I got this error message:

[IMG]http://i130.photobucket.com/albums/p241/D-meist/Screenshot-1.png[/IMG]

So I tried to sudo open it using Terminal:

[IMG]http://i130.photobucket.com/albums/p241/D-meist/Screenshot-2.png[/IMG]

Then as you can see in the picture, it says sudo: ops: command not found

I know I'm missing something simple here.  Please help.  Thank you. :)

-Daniel

---

### Post by taurus on 2009-05-16
Maybe because ~/Desktop/s/ops-for-linux is not in your path.  Therefore, you need to include the ./ in front of the file if you are already in that directory.

```
sudo ./ops
```

---

### Post by 3rdalbum on 2009-05-16
In the terminal, type sudo and then a space. Drag the file to the terminal and run the result.

---

