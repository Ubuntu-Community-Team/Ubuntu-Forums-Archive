---
title: "Shortcut for Terminal"
date: 2010-01-27
forum: Desktop Environments
---

### Post by navderm on 2010-01-27
Hi,

I have used gnome-terminal --desktop (no.)*(no.)+(no.)+(no.) to get the terminal of my desired size and position. 

Now i want to use keyboard shortcut for the same.

Though there is a standard keyboard shortcut declaring routine in ubuntu, when i use the shortcut to that this above command doesn't get executed probably because this is the upper layer application initializer. and at the lower level only terminal is used .

So i tried to make a new shortcut for it and to it i gave
name : Launch Terminal
Command : gnome-terminal --desktop (no.)*(no.)+(no.)+(no.)

but this doesn't work.!!!

can anyone help 

Thnx a lot.

---

### Post by navderm on 2010-01-27
Hi,

I was able to run the terminal. 

I am using the window button as the shortcut and
gnome-terminal --desktop --geometry 60*15+780+460 

BUT...
when this terminal opens its initial directory is the base directory and not
/home/navderm/ 
which it usually has to be...
also.
when i open the terminal from Applications/Accessories/, the initial directory is /home/navderm/ .

What is the problem?
how can i make the initially directory in the first case to be /home/navderm/

Sincerely,
navderm

---

### Post by John Bean on 2010-01-27
Just add your home folder path - /home/navderm/ in your case - to the command line.

---

### Post by navderm on 2010-01-27
Hi.

I tried it. 

It doesn't work !!! 

I don't understand why.

Can anyone please help !

---

### Post by t.rei on 2010-01-27
```
gnome-terminal --help-all
```tells you to do the following:

```
gnome-terminal --working-directory=/home/...yournamehere...
```

---

### Post by pastalavista on 2010-01-27
There are lots of terminal emulators available that are easy to configure. I like 'tilda'. It's in the repositories.

---

### Post by navderm on 2010-01-27
:)

thanks a lot guys. 

it works now

---

