---
title: "Strange mouse left button problem"
date: 2009-03-26
forum: General Help
---

### Post by keithclark on 2009-03-26
My son must have set something incorrectly but for the life of me I don't
know what or even how to describe what is happening clearly.

Within a window, say Firefox, if the left mouse button is depressed, the
cursor turns into the four arrow keys and the movement of the mouse just
moves the window.  Just like it would do it the title bar were selected and
dragged around.  It happens no matter where the cursor is within the
window.

Clicking the left mouse button on a menu, like System drop down menu still
works as normal.

I hope I've described the problem clearly enough for someone to offer a
fix.

Thanks,

Keith

---

### Post by ryanhaigh on 2009-03-27
Just guessing but it sounds as though left-click (aka button 1) has been assigned to move window. I'm on a windows machine at the moment but the only place I can think of that this can be done from is a compiz settings manager application. Try disabling compiz with the following command (press alt-f2 to bring up run dialog). If the mouse returns to normal then you can go into compiz settings manager and change the setting for moving the window.
```
metacity --replace
```
Then you can run the following to return to compiz.
```
compiz --replace
```

EDIT:
Actually another thing I thought of is that your alt key may be pressed or stuck. Alt+Button-1 moves the window whether using compiz or not.

---

