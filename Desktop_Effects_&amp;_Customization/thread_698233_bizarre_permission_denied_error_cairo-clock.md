---
title: "bizarre permission denied error: cairo-clock"
date: 2008-02-16
forum: Desktop Effects &amp; Customization
---

### Post by Drone4four on 2008-02-16
I was just using cairo-clock, impressed by the fresh artwork I downloaded off gnome-look.org.  I added some more themes and now cairo clock won't run.  Here is the error message: ```
drone4four@ubuntu:~$ cairo-clock
bash: /usr/bin/cairo-clock: Permission denied
drone4four@ubuntu:~$ sudo cairo-clock
sudo: cairo-clock: command not found
drone4four@ubuntu:~$ 
```  Why can't I run cairo-clock now, but I could moments ago?  I can't explain it.  When I do a sudo apt-get install cairo-clock, it says it's already installed, which means that cairo-clock exists in my hard drive.

---

### Post by JO3Y on 2008-02-17
I had this problem and this worked for me
open a terminal and type

```
sudo chmod +x /usr/bin/cairo-clock
```

then try 

```
sudo cairo-clock
```

or

```
sudo /usr/bin/cairo-clock
```

---

