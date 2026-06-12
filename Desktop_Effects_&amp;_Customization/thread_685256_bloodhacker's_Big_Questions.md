---
title: "???????bloodhacker's Big Questions???????"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by bloodhacker2 on 2008-02-02
1. How to install Compiz (with the plugins like the cube) for this computer specs. (i think i have install compiz but i don't get any effects at all, and i could int find the emerald theme manager)
[http://www.walmart.com/catalog/product.do?product_id=5663691](http://www.walmart.com/catalog/product.do?product_id=5663691)

2. How to start the cube.

3. How to install conky and how to make it comm on on start up.

4. How to add different themes to conky (if you can).

5. How do i know if i am Feisty,  Edgy ,  Dapper,

6. How to get compiz to start on startup

Ps.. i am working with 2 computers that is why i am asking all these questions because both are different and i am lost like a dog.

---

### Post by koldphlame on 2008-02-02
ARE YOU RUNNING UBUNTU 7.10?:confused:


IS THE FIRST QUESTION?:)

---

### Post by ntowakbh on 2008-02-02
> **bloodhacker2 said:**
> 1. How to install Compiz (with the plugins like the cube) for this computer specs. (i think i have install compiz but i don't get any effects at all, and i could int find the emerald theme manager)
[http://www.walmart.com/catalog/product.do?product_id=5663691](http://www.walmart.com/catalog/product.do?product_id=5663691)

2. How to start the cube.

3. How to install conky and how to make it comm on on start up.

4. How to add different themes to conky (if you can).

5. How do i know if i am Feisty,  Edgy ,  Dapper,

6. How to get compiz to start on startup

Ps.. i am working with 2 computers that is why i am asking all these questions because both are different and i am lost like a dog.

1.
Applications-->Accessories-->Terminal
```
sudo apt-get install compizconfig-settings-manager
```
System-->Prefrences-->Appearence
Visual effects tab, select custom, then click preferences.

EDIT: For emerald run in Terminal
```
sudo apt-get install emerald
```

2.
You've clicked preferences, in the window, click "General Options", go to desktop size tab, and change horizontal virtual size to 4(if it isn't already). Click the back button in the lower lefthand corner of the window.
Check "Desktop Cube" in the menu(it may ask you about disabling "Desktop Wall" allow it to disable it.  Make sure "Rotate Cube" is checked.
<CTRL><ALT><DownArrow> unfolds the cube.
<CTRL><ALT><Left/RightArrows> rotate cube left/right.
<CTRL><ALT>Click, hold, and move mouse to rotate also.

3.
I would help, but I do not use conky, sorry.

4. 
See number 3.

5.
If you have the latest version, you are running Gusty. To check for sure what you have:
Open terminal
```
cat /etc/issue
```
7.10 = Gusty
7.04 = Feisty
6.10 = Edgy
6.06 = Dapper

6.
For me it did by default, after I enabled effects.

Hope I was able to help.

---

### Post by bloodhacker2 on 2008-02-02
> **koldphlame said:**
> ARE YOU RUNNING UBUNTU 7.10?:confused:


IS THE FIRST QUESTION?:)

lol hell ya i am running 7.10

---

### Post by bloodhacker2 on 2008-02-02
> **ntowakbh said:**
> 1.



2.
You've clicked preferences, in the window, click "General Options", go to desktop size tab, and change horizontal virtual size to 4(if it isn't already). Click the back button in the lower lefthand corner of the window.
Check "Desktop Cube" in the menu(it may ask you about disabling "Desktop Wall" allow it to disable it.  Make sure "Rotate Cube" is checked.
<CTRL><ALT><DownArrow> unfolds the cube.
<CTRL><ALT><Left/RightArrows> rotate cube left/right.
<CTRL><ALT>Click, hold, and move mouse to rotate also.

3.
I would help, but I do not use conky, sorry.

4. 
See number 3.





Well what do you use. and i cant seem to find General Options in my preferences, is their another way to get to this? i am just luring all this Linux stuff and i am trying to lune as much as i can...

---

### Post by bloodhacker2 on 2008-02-02
> **ntowakbh said:**
> 1.
Applications-->Accessories-->Terminal
```
sudo apt-get install compizconfig-settings-manager
```
System-->Prefrences-->Appearence
Visual effects tab, select custom, then click preferences.

EDIT: For emerald run in Terminal
```
sudo apt-get install emerald
```

2.
You've clicked preferences, in the window, click "General Options", go to desktop size tab, and change horizontal virtual size to 4(if it isn't already). Click the back button in the lower lefthand corner of the window.
Check "Desktop Cube" in the menu(it may ask you about disabling "Desktop Wall" allow it to disable it.  Make sure "Rotate Cube" is checked.
<CTRL><ALT><DownArrow> unfolds the cube.
<CTRL><ALT><Left/RightArrows> rotate cube left/right.
<CTRL><ALT>Click, hold, and move mouse to rotate also.

3.
I would help, but I do not use conky, sorry.

4. 
See number 3.

5.
If you have the latest version, you are running Gusty. To check for sure what you have:
Open terminal
```
cat /etc/issue
```
7.10 = Gusty
7.04 = Feisty
6.10 = Edgy
6.06 = Dapper

6.
For me it did by default, after I enabled effects.

Hope I was able to help.


this is what i get when i enter the first two codes you gave me..
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
bloodhacker@bloodhacker-laptop:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emerald
```

---

### Post by ntowakbh on 2008-02-02
try running 
```
sudo apt-get update
```

And then try installing them again. 

As for the first question, those packages need to be installed to get to what I was talking about.

---

### Post by bloodhacker2 on 2008-02-02
nope that dint work, i still get the same error message...

lol man this suck, i hope i can fix it....

---

### Post by bloodhacker2 on 2008-02-02
i don't think it is downloading the updates, because i install this just about the same time i installed it on my other computer and my other computer has been installing allot of updates but this one is the only one that i have say that there is no updates for it.


what is the deal???

---

### Post by bloodhacker2 on 2008-02-02
common someone hast to know how to fix this.......

---

### Post by Monster_user on 2008-02-03
Try running these commands in a terminal.

```
glxinfo | grep render
```


Then try this.

```
compiz --replace
```

Did you install Compiz? Beryl?, or Compiz-Fusion? Compiz-Fusion is the one with all of the effects for 7.10+.

You may need to add the Compiz-Fusion repository, in order to get the effects. Since CCSM, and Emerald are not installing, that is what I expect.

---

### Post by bloodhacker2 on 2008-02-06
ok for the firs command this is what i got....

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
```


And on the secont command this is what i got....

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

IS THIS WAS I WAS LOOKING FOR TO GET?????

---

### Post by bloodhacker2 on 2008-02-06
but see what i am looking for the most is getting emerald them on my computer.

like on my other computer when i installs compiz the emerald them manager was in my preferences and on this one i cant find it at all... what is the deal?

---

### Post by ferrettmerr on 2008-02-06
hey make sure you have the right repositories
system > admin > software sources, make sure you uncheck the cd and check the others on the first page, and the two on the second page, then try the commands again.

---

### Post by bloodhacker2 on 2008-02-07
nope i still get the same thing. i have compiz on my computer i just don't have the emrald theme mangier and that is all i am interested in.

---

