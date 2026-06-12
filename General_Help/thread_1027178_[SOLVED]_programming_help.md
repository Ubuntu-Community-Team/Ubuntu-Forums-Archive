---
title: "[SOLVED] programming help"
date: 2009-01-01
forum: General Help
---

### Post by reldon on 2009-01-01
after writing and compiling a program using gcc why do I need to put in a "./" before the program name in order to get it to run?...

Also, how do I get this new program to run using the launcher or set it up so anyone can run it??

---

### Post by wmdiem on 2009-01-01
I think it needs to be in one of the default path directories, like /usr/bin otherwise you need to specify for it to execute (either relative like ./ or absolute /home/me/myprog)

---

### Post by Ahadiel on 2009-01-01
> **reldon said:**
> after writing and compiling a program using gcc why do I need to put in a "./" before the program name in order to get it to run?...

Also, how do I get this new program to run using the launcher or set it up so anyone can run it??

Type the following to see what directories you could put your program in to avoid using ./ or having to specify the full path.
```
echo $PATH
```

The ./ simply tells the shell to execute the file from the current directory. /full/path/to/executable would work just as well.

---

### Post by reldon on 2009-01-01
thanks for all your responses.  :-)

I checked the path variable and put the files into the usr/games directory.

I have the following files:

garden              : the executable
Garden.glade        : the glade file for the window the program uses
Off.jpg             : the Off image file used by the window/program
On.jpg              : the On image file used by the window/program

I verified each file has the following permissions:  -rwxr-xr-x

I created a launcher by dragging the executable to the panel.  This included the full path.

When I click on the launcher the display (launcher icon) shows some kind of animation (like it expands then disappears) but the program does not run.  If I go to the directory where it is (ie usr/games) and double click on the garden executable then it runs fine.

It will also run from the usr/games directory if I am using my regular login or as sudo in nautilus.

I am totally stumped and confused. 

Are there any other suggestions?

---

### Post by jespdj on 2009-01-01
There's a [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum here, where your question belongs.

---

### Post by reldon on 2009-01-01
thanks jespdj.

I have moved it there and will tag this as solved.:)

---

