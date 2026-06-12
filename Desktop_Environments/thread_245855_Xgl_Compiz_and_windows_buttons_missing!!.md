---
title: "Xgl Compiz and windows buttons missing!!"
date: 2006-08-28
forum: Desktop Environments
---

### Post by misosofos on 2006-08-28
Hello all:

After following some tutorials, finally I got my xgl+compiz working with my nvidia card and ubuntu dapper...

But something went wrong and windows don't show buttons (open, clouse, maximize...) nor borders... :confused: 

Anyone can help me solve this problem?

Thanks!

---

### Post by jhaitas on 2006-08-28
I am getting the same problem...
when i run 'thefuture' script i get this error:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

---

### Post by jhaitas on 2006-08-28
Try this... it worked for me...

```
sudo apt-get install libgl1-mesa --reinstall
```

---

### Post by arsenic23 on 2006-08-28
If you followed an older tutorial it may have had you start gnome-window-decorator with the script you made to start Compiz.  The version of Compiz that most people are using now requires cgwd.  So the first thing I'd do is go back to that script, where ever the tutorial had you put it and make sure it looks similar to this:
> killall gnome-window-decorator 
wait 

cgwd & 
compiz --replace gconf &
or this:
> #!/bin/bash
if ps -A | grep -e "compiz.real$" > /dev/null; then
killall cgwd
metacity --replace &
else
cgwd &
compiz --replace gconf &
xmodmap -e "keycode 22 = BackSpace Delete"
fi


The important thing is to call cgwd instead of gnome-window-decorator.  Of course you'll have to have cgwd ( and maybe a few other things installed ).

---

### Post by asplode on 2006-08-28
I had a similar problem.

What I did was to go into gconf-editor and change the order my compiz plugins loaded, because some depend on others, and the order was very messed up.  Once done, it works like a charm.

follow the directions listed here:
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)

---

### Post by misosofos on 2006-08-28
> **arsenic23 said:**
> If you followed an older tutorial it may have had you start gnome-window-decorator with the script you made to start Compiz.  The version of Compiz that most people are using now requires cgwd.  So the first thing I'd do is go back to that script, where ever the tutorial had you put it and make sure it looks similar to this:

or this:



The important thing is to call cgwd instead of gnome-window-decorator.  Of course you'll have to have cgwd ( and maybe a few other things installed ).

I have not it intalled and it doesn't figure out into my repositories.
What repository am I supposed to add?

Thx

---

### Post by arsenic23 on 2006-08-28
```
deb http://xgl.compiz.info/ dapper main
```

is the repo I'm using.  Though I see most of the brand new tutorials have more/different repositories in them.  I see:

```
deb http://www.beerorkid.com/compiz/ dapper main
```

in alot of the newer tutorials ( but I'm not using it ).


After adding one or both of those, see if the following packages are installed:
```
compiz xserver-xgl libgl1-mesa libglitz-glx1 compiz-gnome cgwd cgwd-themes compizthemer gconf-editor
```

Then just change that script like I said before and I think you'll be fine.

---

### Post by misosofos on 2006-08-29
Thanks you a lot Arsenic23!
It worked wonders!

---

