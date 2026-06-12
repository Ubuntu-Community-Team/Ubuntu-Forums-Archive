---
title: "matacity problems"
date: 2009-12-13
forum: Desktop Environments
---

### Post by billyboy1995 on 2009-12-13
when i log in i am missing the bar with the close, maximise,and the minimise. I have to "enable" the desktop effects but i can't really have desktop effects on my computer. I think it may have to do with refreshing the screen because it only appears after the refresh. If you need to see any files just let me know as i have no clue what is wrong because every thing was fine in 9.04 and until i updated my fresh install of 9.10.

Thanks bill

---

### Post by staf0048 on 2009-12-13
Just out of curiosity do you have Emerald installed/active as your window decorator?

---

### Post by billyboy1995 on 2009-12-14
no i do not. just wondering... do i need it?

---

### Post by pixel :-) on 2009-12-15
You mean you are missing the border and can't move around the windows?

first do a full upgrade of the system, maybe it will go away.

in a terminal try

metacity

or

metacity --replace

or

compiz --replace

(these commands are from memory, they could have mistakes)

send back the out puts.

---

### Post by staf0048 on 2009-12-15
> **billyboy1995 said:**
> no i do not. just wondering... do i need it?

No you don't need it.  Sometimes on my computer my title bar, minimize, maximize, and close buttons would disappear if I had Compiz on w/ Emerald as my window decorator and there was some issue with Compiz.  The best solution I've found for my issue (so far) is to install fusion-icon and place it in my start-up programs.  Then, if I ever have trouble I simply right click the icon on the panel and select Reload Window Manager - which usually does the trick, or I will try toggling between Compiz and Metacity for my window manager.  I noticed though, that this only occurred when I had Emerald set as my Window decorator.  So I no longer use Emerald and have had no problems.  

Your issue sounds a little different, even though the symptoms seem similar.

---

