---
title: "Sound Events in XFCE"
date: 2007-12-11
forum: Desktop Environments
---

### Post by razumok on 2007-12-11
hi everyone :)

does anyone know hoy to enable sound events in xfce?... I have been searching around and still haven't found anything.

sound is working correctly (Exaile, alsaplayer, everything)... but, sounds like starting XFCE or closing it, closing windows, or any other user-triggered sound is not working.

when I open the xfce settings manager, there is no button like "Sound Events" (though I've seen it in some images trough the web)

btw, I'm using Ubuntu 7.10 and installed XFCE over it from the repositories

thanks in advance :D

---

### Post by mali2297 on 2007-12-12
> **razumok said:**
> 
does anyone know hoy to enable sound events in xfce?


In general, **Xfce does not support sound events**.

You can get a simple system *beep* if you unmute PC Speaker. (Run alsamixer in the terminal or install xfce4-mixer,)

It should be possible to add startup and logout melodies with custom scripts.

But I do not think it is possible to add sounds to window events etc.

---

### Post by santiagoward2000 on 2007-12-12
> **razumok said:**
> hi everyone :)

does anyone know hoy to enable sound events in xfce?... I have been searching around and still haven't found anything.

sound is working correctly (Exaile, alsaplayer, everything)... but, sounds like starting XFCE or closing it, closing windows, or any other user-triggered sound is not working.

when I open the xfce settings manager, there is no button like "Sound Events" (though I've seen it in some images trough the web)

btw, I'm using Ubuntu 7.10 and installed XFCE over it from the repositories

thanks in advance :D

Hi!
You can set the sounds for starting Xfce going to **Applications / Settings / Login Window**, under the **Accessibility** tab.

---

### Post by mali2297 on 2007-12-12
> **santiagoward2000 said:**
> Hi!
You can set the sounds for starting Xfce going to **Applications / Settings / Login Window**, under the **Accessibility** tab.

With gdm, you can also play a logout sound if you want.
[http://ubuntuforums.org/showthread.php?t=633563](http://ubuntuforums.org/showthread.php?t=633563)

---

### Post by santiagoward2000 on 2007-12-12
> **mali2297 said:**
> With gdm, you can also play a logout sound if you want.
[http://ubuntuforums.org/showthread.php?t=633563](http://ubuntuforums.org/showthread.php?t=633563)

I've opened gdm through a terminal, but it opened the same window as going to **Applications / Settings /Login Window**, and I can't find any option for logout sound...

---

### Post by razumok on 2007-12-12
thanks for the replies... guess I'll have to get used to the system beeps :(

Just added a startup sound and works great, thanks santiagoward2000 :D

---

### Post by santiagoward2000 on 2007-12-12
> **razumok said:**
> thanks for the replies... guess I'll have to get used to the system beeps :(

Just added a startup sound and works great, thanks santiagoward2000 :D

You're welcome! :popcorn:

---

### Post by mali2297 on 2007-12-13
> **santiagoward2000 said:**
> I've opened gdm through a terminal, but it opened the same window as going to **Applications / Settings /Login Window**, and I can't find any option for logout sound...

Read [post #4]("http://ubuntuforums.org/showpost.php?p=3907604&postcount=4").

---

