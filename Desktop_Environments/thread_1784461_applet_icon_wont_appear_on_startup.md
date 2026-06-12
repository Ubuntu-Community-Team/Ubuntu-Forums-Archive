---
title: "applet icon wont appear on startup"
date: 2011-06-17
forum: Desktop Environments
---

### Post by hyfanious on 2011-06-17
hi 
I use "Startup Application" to call a file (freedom.jar)
this application has an applet icon
it was appearing before correctly
but now the main program appear but applet icon wont appear anymore
and if I run program manually (after starting up) it will work correctly.
what am I supposed to do?
tnx.

---

### Post by hyfanious on 2011-06-24
bump

---

### Post by Bucky Ball on 2011-06-24
Double posting is against forum rules. I have asked mods to merge the two. ;)

---

### Post by Joris Donders on 2011-06-24
This is a bit strange; but ok let's try at least something. 

Press Crtl+Alt+t this opens a terminal; 

type:" unity --reset " and press enter

Now hopefully this will solve your problem, but I MUST ADD that it is not shure it'll fix it.

---

### Post by hyfanious on 2011-07-10
> **Joris Donders said:**
> This is a bit strange; but ok let's try at least something. 

Press Crtl+Alt+t this opens a terminal; 

type:" unity --reset " and press enter

Now hopefully this will solve your problem, but I MUST ADD that it is not shure it'll fix it.
I use Lucid
and as I know It doesn't use Unity! am I wrong?
beside that I set up Lucid and this program in several other pcs
all of them encounter with this problem after a while
sounds fishy
why it happens after a while??!!

---

### Post by koleoptero on 2011-07-10
You can try adding a delay before it starts. Create a programname.sh file somewhere and in it enter:
```
sleep 3 && program
```
where you replace program with whatever you added to the startup files. Then change the file's permissions to make it executable (right-click on it and set it from there) and add that file to the startup applications.

It may be possible to add "sleep 3 && program" to the startup directly but I'm not sure about it.

Also if it doesn't work try some more delay than 3 seconds before giving up. :)

---

### Post by hyfanious on 2011-07-10
> **koleoptero said:**
> You can try adding a delay before it starts. Create a programname.sh file somewhere and in it enter:
```
sleep 3 && program
```where you replace program with whatever you added to the startup files. Then change the file's permissions to make it executable (right-click on it and set it from there) and add that file to the startup applications.

It may be possible to add "sleep 3 && program" to the startup directly but I'm not sure about it.

Also if it doesn't work try some more delay than 3 seconds before giving up. :)

I tried that before, Nothing changed.
but thanks for ur well consideration

---

### Post by koleoptero on 2011-07-10
> **hyfanious said:**
> I tried that before, Nothing changed.
but thanks for ur well consideration

perhaps if you open it with xdg-open? It's the last possibly helpful thing I can come up with lol.

---

### Post by hyfanious on 2011-07-11
> **koleoptero said:**
> perhaps if you open it with xdg-open? It's the last possibly helpful thing I can come up with lol.
I know nothing about this "xdg-open"
What should I do with this?

---

### Post by koleoptero on 2011-07-11
> **hyfanious said:**
> I know nothing about this "xdg-open"
What should I do with this?

You point it to the file you want opened. ie:

```
xdg-open /path/to/file/you/want/opened
```

and it opens the file with the deafult application for that filetype.

---

