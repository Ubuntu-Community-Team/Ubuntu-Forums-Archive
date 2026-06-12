---
title: "How to add &quot;Turn Off&quot; icon on desktop - Ubuntu 7.10"
date: 2007-12-05
forum: Desktop Environments
---

### Post by leoh on 2007-12-05
Hi everyone.
I've searched for this, but found no clear solution or instructions on how to do it.
I'm building an Ubuntu 7.10 PC for my grandma.
Since she can't see very well and her motricity is not the best (she even uses the mouse with 2 hands), I want to put a big "Turn Off the system" icon on the desktop.
How can I do that?
The little icon on the upper right corner is not big enough.

I also apreciate any other suggestion for anything else, taking into account that my grandma is 85.

Thanks!

---

### Post by staticvoid on 2007-12-05
hmm... this is tricky, because the command for shutting down you have to have permission
you could create a launcher with the command
```
gksu shutdown now
```
but then she would have to enter her password... which would defeat the purpose...

oh and once you make the icon, right click it and choose "stretch icon" to make it nice a big :D

sorry I can't be of much help. 
on other thing: go to Adminitration>System>Login Window and choose I think the third tab over. You can set her to log inautomatically when the computer turns on.

ok, byebye,


sv

---

### Post by leoh on 2007-12-05
> **staticvoid said:**
> but then she would have to enter her password... which would defeat the purpose...
Yes, I know, I am looking for something cleaner so that she clicks, gets a confirmation window, and then shuts down. I'd like to have the same window that I get when I click on the upper right little icon on the menu bar.

> **staticvoid said:**
> oh and once you make the icon, right click it and choose "stretch icon" to make it nice a big :D
Thanks, I've already done that with the rest of the icons she will use (Firefox, OpenOffice Writer, etc).

> **staticvoid said:**
> You can set her to log inautomatically when the computer turns on.
Already done that. Thanks!

---

### Post by bingoUV on 2007-12-05
Read [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7) for a way to run privileged commands without giving a password. Through it, run "shutdown -h now". Or, better still, if hibernate works on that computer, try running "pm-hibernate".

---

### Post by staticvoid on 2007-12-05
[QUOTE=leoh;3895823
Since she can't see very well and her motricity is not the best (she even uses the mouse with 2 hands), 

I also apreciate any other suggestion for anything else
[/QUOTE]

could you post a screenshot? perhaps put her Icons in a panel and make the panel very wide. But this is only because I do not know how to make a command for shutting down on the desktop :P
then the turn off button would be big :D
something like this:

---

### Post by leoh on 2007-12-05
How did you put that launchbar?
Where can I find it?
It may be good enough for what I want.
Any other options or suggestions for my grandma's Ubuntu?

---

### Post by metalheart on 2007-12-05
All icons in Ubuntu themes can have maximum size of 48 pixels. If you change the top panel to 48 pixels, all icons are also changed.
If you want, you can make your own even larger shutdown icon or create your own theme.

---

