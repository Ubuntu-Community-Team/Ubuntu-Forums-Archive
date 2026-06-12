---
title: "Newbie-How do i  turn on Graphical Login Manager as it was??"
date: 2009-03-24
forum: General Help
---

### Post by M0rPh_ on 2009-03-24
Having little linux experience. I was messing up with settings till i removed the tick from **Graphical Login Manager**  . Pressed "Ok" and i was instantlly moved to a fullscreen console...Restarting leads me back to the same console
After some time i figured out to write down "startx" command (thats how i actually open my browser right now)
I still cant do any change to Services Settings while using startx (unlock isnt clickable) I m getting "[COLOR="DarkSlateBlue"]GDM (GNOME DISPLAY MANAGER) is not running"[/COLOR]error when trying to do things like log out,turn on muted volume  using my virtual environment
What should i do to correct it???

---

### Post by PetterDK on 2009-03-24
Hmm to be frank i dont know a solution to your overall problem.. But to start your GDM you can use

sudo /etc/init.d/gdm start

---

### Post by mhgsys on 2009-03-24
what happens if you enter

```

sudo /etc/init.d/gdm start


```




also found some other info here:
[http://ubuntuforums.org/showthread.php?t=460114](http://ubuntuforums.org/showthread.php?t=460114)

---

### Post by M0rPh_ on 2009-03-24
> **PetterDK said:**
> sudo /etc/init.d/gdm start 

thanks a lot  = )

---

