---
title: "M101 spiral galaxy"
date: 2006-04-24
forum: Desktop Environments
---

### Post by morequarky on 2006-04-24
You probably already know about the hubble telescope in association with other telescopes created this really nice image of M101.

the question I have is this:

what image program, if any, in ubuntu is able to open and view the ~60mb jpg or ~450mb tiff?

would my computer be able to view it? (512ram, 1gb swap, 64bit intel)

note: my wife bought this computer and i am not sure it is a really 64bit.  I suspect it could be a 2.2ghz 32bit processor.  do you know how i can find out for sure?

quarky

---

### Post by nanotube on 2006-04-24
hm, the default image viewer program, as well as the gimp image editor, both should be able to view those files...

as to your cpu, i don't know how where to look to find out if its a 32bit or a 64bit... maybe if it came with some documentation from where you bought it? :)

---

### Post by art on 2006-04-24
There is a program called lshw (list hardware). run it as 
sudo lshw
and it will give a list of all your hardware. Then look for the part for cpu, and if it's a 64 bit, you'll have a line saying:
width 64 bit 
and 32 otherwise...

---

### Post by morequarky on 2006-04-24
Thanks a lot for your answers.  great help.

i ran the default image viewer,as far as i know, on the 60mb jpg and after a bit it crashed but i don't know why.   it happened a few days ago so i don't remember any error.  if it happens again i'll note it.

I do have a 64bit processor :)  yeah, thanks so much
i also have 64bit 512mb ram.  i wonder though, is it possible i have a 32bit bus?
wouldn't that slow me down.  oh well, can't change the motherboard for a while.

quarky.

---

