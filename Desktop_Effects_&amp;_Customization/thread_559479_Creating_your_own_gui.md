---
title: "Creating your own gui"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by weedeatr on 2007-09-25
hi
I would just like to know if there is a program or something i can use to create my own gui for xubuntu feisty..
i am currently downloading it and thinking of creating my own gui!!:)

tx

-weedeatr-

---

### Post by jimcooncat on 2007-09-25
A gui -- graphical user interface -- can be all kinds of forms.

At it's simplest would be a bash script with zenity. Zenity will show a simple text box, selection with prompt, calendar, or other widget. Your user picks a choice and your bash script processes their answer. Very simple to start with, not a lot of customization available, can be powerful with a good script.

The middle ground is what most people think of gui -- an application that uses a widget set and custom forms. There are many toolkits and methods and available for that. My personal drive to create gui applications will be to use Python, WxWidgets, and SqLite. 

A window manager or desktop environment, like Xfce that Xubuntu uses, can also be thought of as a gui, although they are so much more. These are the result of many people's work, and it's too big a project for one person to handle. However, you can customize them to no end, and if you can figure how to package your customizations and share them, you can distribute unique computing experiences to others. Check out the many themes available, panel widgets, desktop toys, and Devils Pie to place your windows.

---

### Post by weedeatr on 2007-09-25
Thank you i will have a look into it as soon as my download finishes :D

weedeatr

---

### Post by hyperair on 2007-09-25
For more complex GUIs (forms and widgets) you can try out Glade as well. If I'm not mistaken, it works with all languages, as long as you wish to use Gtk+

---

### Post by weedeatr on 2007-09-26
is there maybe a way i can do it in python??

---

### Post by hyperair on 2007-09-26
You can, using PyGTK. I still suggest that you use Glade to design your user interfaces, then import it using your script.

---

