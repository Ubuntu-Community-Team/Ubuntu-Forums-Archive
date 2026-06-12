---
title: "beryl --replace only works if I keep terminal open"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by amneziac on 2007-08-06
there is a problem that when i say beryl --replace or beryl --replace &, it fixes my computer back to how it was but it never finishes so if I close terminal, it screws up again, how come?

---

### Post by Lord Illidan on 2007-08-06
You can always launch it from ALT F2

---

### Post by amneziac on 2007-08-06
I have it set up on the startup programs
so even when it loads, the settings dont take place
the closest ive gone to fixing this is using terminal
but after i close it, the settings dont work anymore

---

### Post by Vozmozno on 2007-08-06
Well, like Illidan said, press ALT + F2, and a window should pop up. write:  
beryl --replace 

And click run, see if it works, and post back to let us know =)

---

### Post by amneziac on 2007-08-06
thanks it works

---

### Post by Lord Illidan on 2007-08-06
I did some research for you and ended up with this :

[http://www.linuxquestions.org/questions/showthread.php?t=368739](http://www.linuxquestions.org/questions/showthread.php?t=368739)

In sort, you can do either this :

```
nohup beryl --replace
```

This will allow you to close the terminal window normally, and still leave the application running. For more information about nohup, type ```
man nohup
```

Else, you can do this :

```
beryl --replace&
```

and then type ```
exit
``` in the terminal or press CTRL+D. This will close the terminal, but leave beryl running..

---

