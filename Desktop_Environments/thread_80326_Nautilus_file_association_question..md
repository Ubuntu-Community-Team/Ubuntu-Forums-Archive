---
title: "Nautilus file association question."
date: 2005-10-21
forum: Desktop Environments
---

### Post by Kevlar on 2005-10-21
Ok, I have some video files that I wish to view using mplayer.  If I right click on one of the files and select "Open with other applicaton..." from the menu and then select use a custom command I run into a problem.  If I just type in mplayer in the custom command box it works perfectly, but if I put in any command line options it fails.  As an example using a file named test.asf I can do the following:

From a command prompt:
mplayer -ontop -geometry 97%:85% test.asf
and it will play perfectly.

From Nautilus if I select to open with other application and use a custom command of mplayer it will also work (though not with the options I want.  If I try to use the custom command and type mplayer -ontop -geometry 97%:85% it will just fail.  

Does anyone have any idea how to make Nautilus properly pass the command line options as a default action?  Any help is much appreciated.  I know I am just doing something wrong here.  Google searches have not helped me.

---

### Post by chanders on 2005-10-22
I think it would be hard to pass those command as a default with an "Open with..." I might be wrong but my advice would be to write a script and use "Open with...." and put the name of your script....

Here's howto....
Create a script called MplayerCustom.sh with this code in it

```
mplayer -ontop -geometry 97%:85% $1
```

and save it in ~/bin that is /home/YourLoginNameHere/bin

Right click on it and in the permissions, make sure read, write and execute is checked....

Right click on the asf file and choose open with, custom command and browse to the script in the bin directory. And thats it!!

---

### Post by Kevlar on 2005-10-22
Thanks, that worked perfectly.  I was evidently making this much harder than it needed to be.

---

