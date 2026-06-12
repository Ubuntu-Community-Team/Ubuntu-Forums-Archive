---
title: "Problem deleting StartUp Program"
date: 2006-07-18
forum: Desktop Environments
---

### Post by frostie on 2006-07-18
In Preferences>Sessions>StartUp Programs I have:

xmodmap -e keycode\ 22\ =\ BackSpace\ BackSpace\ Terminate_Server

which is really annoying as I am constantly accidentally logging myself out!

There is no delete option and if I edit it to something else it just comes back again on next login. If I disable it it comes back. 

I think it is something to do with the compiz installation I tried, as compiz --replace gconf is also listed also with no delete option and also seemingly uneditable.

Is there a way I can remove these and get my backspace key back?

regards,
-- 
robert

---

### Post by akniss on 2006-10-30
> **frostie said:**
> In Preferences>Sessions>StartUp Programs I have:

xmodmap -e keycode\ 22\ =\ BackSpace\ BackSpace\ Terminate_Server

which is really annoying as I am constantly accidentally logging myself out!

There is no delete option and if I edit it to something else it just comes back again on next login. If I disable it it comes back. 

I think it is something to do with the compiz installation I tried, as compiz --replace gconf is also listed also with no delete option and also seemingly uneditable.

Is there a way I can remove these and get my backspace key back?

regards,
-- 
robert

Did you ever figure this out?  I'm having the same problem, and its driving me absolutely nuts.  I have to manually type metacity --replace now every time so that my metacity keybindings will work.

---

### Post by akniss on 2006-10-30
I've solved my problem, don't know if it will help anyone else.  I used a script called <Ra211.tar.bz2> to try and install XGL/Compiz on Dapper a while ago, and things have not been right since.  I finally relocated the script I used, and tried to go backwards through it to undo all the stuff it did. I did the following:
```
cd /usr/local/bin
sudo rm Xgl.sh
cd /user/share/xsessions
sudo rm Xgl.desktop
cd ~/.config/autostart
rm compiz.desktop
rm gnome-window-decorator.desktop
rm gnome-panel.desktop
rm xmodmap.desktop
```
And now all is right with my Dapper installation!  Hooray!  No reinstall for me!

---

### Post by msandersen on 2006-11-01
Thanks, this solved a problem for me also. I managed to get myself locked out, a startup program didn't work right and left me with a blank screen.

---

