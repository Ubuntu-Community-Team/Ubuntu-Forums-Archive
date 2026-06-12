---
title: "Xubuntu 12.04 Dual Monitor"
date: 2012-11-14
forum: Desktop Environments
---

### Post by gaseabra on 2012-11-14
Hi guys,

I've managed to setup my dual monitor on Xubuntu 12.04 (laptop integrated and external monitor) and it's working fine. The issue is: the config won't save. I've tried following methods:

1- Ran xrandr --output LVDS1 --left-of VGA1 on the terminal and it works, but on the next reboot both monitors get mirrored again and have resolutions reset.
2- I wrote a scritp with xrandr --output LVDS1 --left-of VGA1 and put it on init. This gets ignored.
3- I made a launcher in Sessions Applications but it won't execute.

Everytime I need to execute xrandr --output LVDS1 --left-of VGA1 and I even made a launcher with the command and placed it on my taskbar but that's not what I want. I want to boot my computer, log in and get my dual monitor set working.

Any idea anyone?

---

### Post by dannyboy79 on 2012-11-14
make a file called dualsetup.sh and put the following in the file
#!/bin/sh
xrandr --output LVDS1 --left-of VGA1

save the file. Make it executable using the command "chmod +x /folder/dualsetup.sh" (replace folder with the location you saved the file)

Now go to Xfce settings -> Session and startup

and create a new entry pointing to that file. It will make it start every time you log on. Hopefully it will work for you...

---

### Post by gaseabra on 2012-11-14
I'm not sure it's going to work cause I have that command running on Session Apps, but I'll give it a try on friday and post the result here.

Thanks in advance.

---

### Post by cortman on 2012-11-14
Best procedure is to create a folder called "bin" in your home folder, then save the file in there (no need for a .sh extension). Run

```
chmod u+x ~/bin/script_name
```

Then add it to startup programs (instructions [here]("http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/"))

---

### Post by gaseabra on 2012-11-17
Sorry to tell you that none of the solutions worked. :S

---

### Post by LewisTM on 2012-11-17
Just a thought but maybe you need a short delay before running xrandr on startup.
Adding [FONT="Courier New"]sleep 5 [/FONT]in your script, above the xrandr command, might help.

Cheers!

---

### Post by gaseabra on 2012-11-17
> **LewisTM said:**
> Just a thought but maybe you need a short delay before running xrandr on startup.
Adding [FONT="Courier New"]sleep 5 [/FONT]in your script, above the xrandr command, might help.

Cheers!

Woa! Works like a charm!


Just a feedbak: I used dannyboy79's solution mixed with yours! Thanks a lot!

---

