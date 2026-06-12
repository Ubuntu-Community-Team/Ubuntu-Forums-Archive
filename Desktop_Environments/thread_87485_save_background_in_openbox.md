---
title: "save background in openbox"
date: 2005-11-08
forum: Desktop Environments
---

### Post by erez1012 on 2005-11-08
i success to put the image on the background according to the commend:
feh --bg-scale name of file

but its do not appear in the next time i log on the computer??

---

### Post by viniosity on 2005-11-08
If openbox is anything like fluxbox then there should be a config file somewhere.  Look for it in a .openbox directory.  You could add that line to that config.

---

### Post by erez1012 on 2005-11-08
i dont find it!!

---

### Post by chombee on 2005-12-16
Add the line:

eval `cat $HOME/.fehbg` &

to your .xsesssion file. See the OpenBox page on the Ubuntu wiki.

---

### Post by tchock on 2005-12-18
I'm searching the forums for an answer to this... I've tried putting the eval command suggested by feh in my .xsession/.xinitrc (eval 'cat $HOME/.fehbg' &), but it does not appear to be executing the command. It only cats it. I can run the command manually and it just cats it, I still get the gray moirey default background. If I stick the command stored in .fehbg into my .xsession I get a background... so that's an option but it'd be nicer if i didn't have to edit .xsession every time I want to switch my bg... any ideas?

---

