---
title: "Disable mouse right-click"
date: 2009-06-02
forum: General Help
---

### Post by mhall119 on 2009-06-02
Several old threads asked for this and it was never answered.  I have found a way to do this, it may not be the best, but it works.

```
xmodmap -e "pointer = 1 2 99"
```

This will cause a right-click to produce a "Button 99" instead of a "Button 3" click event.  There may be better ways, but this is all I've found.

You can also probably put the part in quotes into ~/.Xmodmaprc to have it run automatically, but I haven't verified that yet.

---

### Post by GaryMac on 2011-12-16
Hi I have an Internet Cafe and trying to impose a few restrictions on the public user account ..  including disable the right click.

xmodmap -e "pointer = 1 2 99"
This only works for one session = on restart - back to normal ..  

Is there a permanent fix for this ... on the one public account ?

---

### Post by GaryMac on 2011-12-17
Update >   I have tried running  ...      xmodmap -e "pointer = 1 2 99"  
Then   ...    xmodmap -pke > .Xmodmap  
(it creates a files called .Xmodmap in your home directory)

Then you have to create a file called **.xinitrc** in your home directory where you put this commandline xmodmap .Xmodmap

I found these instructions here > [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)


On re-start I got a box asking if I wanted to run xmodmap  =   check ok

But the right click was still available.

---

### Post by GaryMac on 2011-12-17
Just to add I have also tried the suggestion above ...

You can also probably put the part in quotes into ~/.Xmodmaprc to have it run automatically, but I haven't verified that yet.

Which did not work either.

---

### Post by moumimi on 2011-12-22
I have just try this and test it :
create a text file modmapD.sh  (any file name, I use D for disable) that has
xmodmap -e "pointer = 1 2 99"
 
and save it under <username>/.kde/Autostart/      your path can be found at system setting-Account details-Path
then associate the modmapD.sh with sh, here is how, right click the file and choose open with-other, at the top input sh and check at the botton for remember application association. I would create another modmapE.sh (not in the autostart folder. ) with 
xmodmap -e "pointer = 1 2 3"
 
to test. Now .sh file will be a simillar as msdos .bat .

Just upgraded to 11.10 , the associate file does not allow to associate wit sh

opps, I was using kubuntu, re install kubuntu to 11.10 and still work

---

### Post by GaryMac on 2011-12-23
Just to clarify this thread was solved ...
 
Here ..
 
[http://ubuntuforums.org/showthread.php?t=1896685](http://ubuntuforums.org/showthread.php?t=1896685)

---

