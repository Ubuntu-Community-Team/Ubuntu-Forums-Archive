---
title: "gnome problems"
date: 2006-11-28
forum: Desktop Environments
---

### Post by tomski on 2006-11-28
Hi all,

i installed compiz after getting AIGLX to work & inserted compiz -start into my default session but this really slowed my system down & also removed my window borders so i thought it was my card(ati radeon 9200se)

I uninstalled compiz & inserted metacity back into my gnome session( this was awkward because i had to browsse for the binary as i could not type into the box)
now i have a desktop back & all the apps i have started by default show & i have window borders but by removing compiz or inserting mteacity back in to  my session i no longer have the default right click menu on the desktop??

i realize now that i should have backed up some configs (but i do not know which ones) 
it would appear that some configs have been changed by installing compiz &  dont know what is wrong or how to fix this

please help if you can

thanks

---

### Post by tomski on 2006-11-29
So it would appear that nobody nows how to fix this
or nobody has experienced this???

i am slowly build a collection of unanswerable threads that nobody replies to!!

oh well the strugle continues

thanks

---

### Post by jazzgossen on 2006-11-29
I think it's nautilus that handles the icons on the desktop and the right-click menu. If I'm right, you could try resetting your nautilus settings.

---

### Post by tomski on 2006-11-29
ok i'll give that a go Jazzgossen, sounds logical but im sure i tried that

thanks for the reply though

---

### Post by tomski on 2006-11-29
Bingo i fixed it & thanks to Jazzgossen for the pointer.

Here is how to resolve:

after you have removed compiz & put metacity back into the default session if you still have the same or similar problems i have encountered here then open a terminal (not a root one!)
and open 
gconf-editor

now go to:
Apps->Nautilus->Preferences

in here scroll down to 'show desktop' remove the tick & then replace it & all should come back.

hope this helps you as it has me

************INFO NUGET****************
The amount of control you have over a linux box can be bad thing as well as a good thing but at least you dont need to reboot after making drastic changes;
In fact you should only need to reboot when you install a new kernel if you have installed new modules & made changes to a scripit in /etc/init dont forget the 'Runlevels' you can issue this command:
telinit 1 
this will send a sytem wide term & kill signal but will not kill init 0 & it will drop to runlevel 1 & go throught all the init scripts just like after rebooting.

---

