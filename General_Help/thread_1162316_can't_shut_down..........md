---
title: "can't shut down........."
date: 2009-05-17
forum: General Help
---

### Post by muctadir on 2009-05-17
i can't shut down my pc. if i press shut down or restart the log in page is shown...!!!

what is the problem???
need help......

---

### Post by xpinsx on 2009-05-17
laptop or desktop?

---

### Post by muctadir on 2009-05-17
desktop.......

---

### Post by irv on 2009-05-17
At the login screen there should be a option to shutdown. I think it at the bottom of the screen somewhere?

---

### Post by muctadir on 2009-05-17
there is no button on the login screen.
there are only two option
select language and select session......!!!

---

### Post by alberto ferreira on 2009-05-17
Try Ctrl+Alt+Backspace or Ctrl+Alt+Delete several times to shut down

or

Ctrl+Alt+F1, login and type:
```
sudo init 0
```

---

### Post by irv on 2009-05-17
I had to see for myself what you were talking about so I logged off and went to the login screen. I have the a new logo that has three buttons on it and one is to shut down thee computer. I sorry I can help because my setup is altogether different than most users.
If you don't have the shutdown option in your panel just right click anywhere in a blank area and chose add to panel and select the shutdown option to place it on your panel.

---

### Post by irv on 2009-05-17
In case you want to see what my login screen looks like here is a couple of screen shots.
[ATTACH]114140[/ATTACH]

[ATTACH]114141[/ATTACH]

---

### Post by muctadir on 2009-05-17
the command worked.
but next time when i turn on my pc the same thing happens. and in the login screen there is no option for shut down...
on desktop the shut down and restart button is not working as i said before...

need help......

---

### Post by irv on 2009-05-17
> **muctadir said:**
> the command worked.
but next time when i turn on my pc the same thing happens. and in the login screen there is no option for shut down...
on desktop the shut down and restart button is not working as i said before...

need help......

Try to remove the shut down button and then add it back in.

---

### Post by muctadir on 2009-05-17
there was a shut down button on the login screen before, but now there isn't. i don't know why.....!!!

---

### Post by cariboo on 2009-05-17
If you click the seesion button, there is an option to shut down in the menu.

Or if worse comes to worse, open a terminal and type:

```
sudo shutdown -h now
```

or

```
sudo halt
```

as usual there are always several ways to do what you want when you are running Linux.

---

### Post by muctadir on 2009-05-17
> **irv said:**
> Try to remove the shut down button and then add it back in.
that helped.......
thanks.....
but still there is no shut down option on the login screen...

---

### Post by irv on 2009-05-17
Try this, Go to System> Administration> Login Window and try a different login window.
[ATTACH]114145[/ATTACH]

[ATTACH]114146[/ATTACH]

---

