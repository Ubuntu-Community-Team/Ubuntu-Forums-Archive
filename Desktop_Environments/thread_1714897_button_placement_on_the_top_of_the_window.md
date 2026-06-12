---
title: "button placement on the top of the window"
date: 2011-03-26
forum: Desktop Environments
---

### Post by wog on 2011-03-26
I want the three buttons on the top of the window to be on the right side, but every time I go to another theme they get switched over to the left again.

What do I do to fix this tendency?

---

### Post by tgm4883 on 2011-03-26
> **wog said:**
> I want the three buttons on the top of the window to be on the right side, but every time I go to another theme they get switched over to the left again.

What do I do to fix this tendency?

The button placement is theme dependent. You either need to choose a theme with the buttons on the right or move the buttons yourself using these instructions [http://blog.daviey.com/blogroll/anything-but-the-buttons.html](http://blog.daviey.com/blogroll/anything-but-the-buttons.html)

---

### Post by wog on 2011-03-26
How does one create or alter a theme, then? Is there a graphical application for it, or am I going to have to wade through code in a text editor to do this?

---

### Post by tgm4883 on 2011-03-26
> **wog said:**
> How does one create or alter a theme, then? Is there a graphical application for it, or am I going to have to wade through code in a text editor to do this?

Sorry, IDK if there is a text editor for themes.

---

### Post by stinkeye on 2011-03-26
Open gconf-editor
```
gconf-editor /apps/metacity/general/button_layout
```

Skip this part if the buttons are already how you like them and go to the set as mandatory part.
Double click on the **button_layout** entry and change the value to
```
menu:minimize,maximize,close
```
Click OK


Now, right click on the **button_layout** entry in the right panel and select
set as mandatory.
This will make the key unwritable so that 
no matter what the theme dictates the buttons will remain on the right. 
You may have to log out/in for mandatory to take affect.


If you ever need to set it back 
```
gksudo gconf-editor
```
go to 
File > New Mandatory Window

This window only lists keys you have made mandatory, so it is
easy to find the relevant entries,
and Right click and select Unset Key.
You may have to log out/in to be able to write to the key again in **gconf-editor /apps/metacity/general/button_layout**.

---

### Post by wog on 2011-05-27
Wow! Thank you! I didn't even know it was possible to set mandatory! :)

I'm marking this thread solved.

---

