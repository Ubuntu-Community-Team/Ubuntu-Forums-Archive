---
title: "Internet connection with awesome on Lucid"
date: 2010-07-20
forum: Desktop Environments
---

### Post by tim042849 on 2010-07-20
I'm using lucid with gnome, but am experimenting with awesome.
When awesome loads, there is no internet connection. I created
an .awesomerc file with the folowing: ```

os.execute("nm-applet &")

```
but no luck, no connection. Can anyone enlighten me on the correct
procedure?
I believe that awesome has a small user base. If anyone is viewing
this and feels that there may be another forum or list to ask questions
about awesome, I'd like to know.
Thanks
tim

---

### Post by tim042849 on 2010-07-20
Just tried  creating
~/.config/awesome/rc.lua
and putting the code there. Now, when I attempt to log into
awesome, the applet window pops up and indicates that I have
connected, but awesome **hangs** and the window manager 
does not load. :(

---

### Post by rafal_p on 2010-08-09
I haved same problem.
The solution i found here >>>
[http://www.robsearles.com/2010/05/15/awesome-wm-nm-applet-secret-service-operation-failed/](http://www.robsearles.com/2010/05/15/awesome-wm-nm-applet-secret-service-operation-failed/)

is:

edit (as root/sudo) the  
/usr/share/dbus-1/services/org.gnome.keyring.service 
file, comment out where it says 
```
#Name=org.gnome.keyring
```
and add the line
```
Name=org.freedesktop.secrets
```

this helped me - try it  :D

rafal_p

---

