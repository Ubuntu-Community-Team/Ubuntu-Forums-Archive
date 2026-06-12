---
title: "Openbox menu &amp; Return to Castle Wolfenstien"
date: 2012-11-25
forum: Gaming &amp; Leisure
---

### Post by DukeOfMixture on 2012-11-25
Hello

I've searched for a solution already, so please forgive if this specific question has been answered.

I am using Openbox

If i start Return to Castle Wolfenstein from the Terminal within its directory using Wine, it works

```
&#9556;&#9552;&#9571; user @ computer
&#9553;
&#9562;&#9552;&#9552;&#9552;&#9571;  ~/.wine/drive_c/Program Files/Return to Castle Wolfenstein  &#9553; #!  wine WolfSp.exe
```But when I use the following line in the Openbox menu:

```
wine ~/.wine/drive_c/Program\ Files/Return\ to\ Castle\ Wolfenstein/WolfSP.exe
```I get the error "Couldn't load default.cfg"

Thanks in Advance

---

### Post by DukeOfMixture on 2012-11-25
Here is what I have accomplished so far.

In order to expedite the launching of the game, I added the following line to my .bash_aliases file:

```
alias rtcw='cd ~/.wine/drive_c/Program\ Files/Return\ to\ Castle\ Wolfenstein/ && wine WolfSP.exe && exit'
```Now, I can launch it from the terminal w/out having to change any directories.

**But I still haven't gotten it to function with an Openbox menu item.**

---

### Post by mastablasta on 2012-11-27
why are you using wine to run RTCW? RTCW has a native linux client. use that instead.

---

### Post by DukeOfMixture on 2012-11-27
I've heard about that. I don't know why but I've been wary of using installers. I like the official repositories.

However, is this site reliable?:

[http://zerowing.idsoftware.com](http://zerowing.idsoftware.com)

If so, then I may try it.

---

### Post by mastablasta on 2012-11-28
well it's from the company that made the game so i would guess so.
 
you can have a look at playdeb add their PPA and install from there if you do not want to use installer.

---

### Post by mateo14 on 2012-11-28
> **DukeOfMixture said:**
> I've heard about that. I don't know why but I've been wary of using installers. I like the official repositories.

However, is this site reliable?:

[http://zerowing.idsoftware.com](http://zerowing.idsoftware.com)

If so, then I may try it.

This is new version of RTCW for Linux:

[http://code.google.com/p/bzzwolfsp/](http://code.google.com/p/bzzwolfsp/)

[http://code.google.com/p/bzzwolfsp/downloads/list](http://code.google.com/p/bzzwolfsp/downloads/list)

---

### Post by mastablasta on 2012-11-28
holy smokes... need to try that!!!

---

### Post by DukeOfMixture on 2012-11-28
> **mateo14 said:**
> This is new version of RTCW for Linux:

[http://code.google.com/p/bzzwolfsp/](http://code.google.com/p/bzzwolfsp/)

[http://code.google.com/p/bzzwolfsp/downloads/list](http://code.google.com/p/bzzwolfsp/downloads/list)


Thank you for that.

---

