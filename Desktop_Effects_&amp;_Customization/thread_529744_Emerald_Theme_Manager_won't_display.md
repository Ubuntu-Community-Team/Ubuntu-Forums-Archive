---
title: "Emerald Theme Manager won't display"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by Latooni on 2007-08-19
'lo. I'm having a problem where the Emerald Theme Manager won't show any themes unless I open a Terminal and type in ```
emerald --replace
```. Then, if I close the Terminal used to run said command, it reverts back to not having a theme at all.

Some screens of the problem:
[http://fc02.deviantart.com/fs20/f/2007/231/0/e/screenshot01_by_Latooni.png](http://fc02.deviantart.com/fs20/f/2007/231/0/e/screenshot01_by_Latooni.png)
This is before I give the command.
[http://fc01.deviantart.com/fs20/f/2007/231/4/3/screenshot03_by_Latooni.png](http://fc01.deviantart.com/fs20/f/2007/231/4/3/screenshot03_by_Latooni.png)
After I give the command, it applies the theme manager.
[http://fc02.deviantart.com/fs20/f/2007/231/9/0/screenshot04_by_Latooni.png](http://fc02.deviantart.com/fs20/f/2007/231/9/0/screenshot04_by_Latooni.png)
And when I close the Terminal used to give the command, it reverts back.

I'm used to having to run emerald --replace at startup, and then closing the Terminal, but this seems to be different.

I'm using Ubuntu 7.04, also, if that matters.

Any help would be greatly appreciated.

---

### Post by waldorsockbat on 2007-08-19
Did you install compiz fusion and emerald separately? is so then you will have to add emerald to your sessions so that it will load at startup. add the code you type into the terminal(emerald --replace) into system >    preferences> sessions >new  and name it emerald.

---

### Post by Latooni on 2007-08-19
I'm using Beryl, but I haven't added it to the startup programs; I'll try that now.

EDIT: Fixed. Thank you for the help.

---

### Post by waldorsockbat on 2007-08-19
No problem glad that worked for you.

---

