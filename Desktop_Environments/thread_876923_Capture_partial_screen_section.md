---
title: "Capture partial screen section"
date: 2008-08-01
forum: Desktop Environments
---

### Post by josir on 2008-08-01
Hi folks, 

could you suggest a good screen capture utility that capture a rectangle area instead of the entire screen ?

I know that I can grab the screen, open Gimp and take the part that I want. But I need to automate this because I have hundreds of screens to capture.

Thanks in advance,
Josir Gomes

---

### Post by opscure on 2008-08-01
You can use xwd with the -rect option.
Read the manual here:
[http://www.xfree86.org/current/xwd.1.html](http://www.xfree86.org/current/xwd.1.html)
It should be installed aready but if not 
```
sudo apt-get install xwd
```
in terminal

---

