---
title: "Missing buttons-null.css"
date: 2021-10-05
forum: Desktop Environments
---

### Post by zozio32 on 2021-10-05
HI,

I recently got a issue with Firefox and gThumb (maybe some other app, I am not sure). I am missing the buttons-null.css file. this completely messes up the 2 apps, they are useless.
Here is the error I am getting when starting firefox from the terminal:

```
zozio32@zozio32-p6-2487ea:~$ firefox

(firefox:6743): Gtk-WARNING **: 23:24:09.196: Theme parsing error: gtk.css:1:101: Failed to import: Error opening file /home/zozio32/.local/share/gnome-shell/extensions/unite@hardpixel.eu/buttons-null.css: No such file or directory
^CExiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.
Exiting due to channel error.

```

same with gThumb:

```
zozio32@zozio32-p6-2487ea:~$ gthumb

(gthumb:8894): Gtk-WARNING **: 23:32:20.065: Theme parsing error: gtk.css:1:101: Failed to import: Error opening file /home/zozio32/.local/share/gnome-shell/extensions/unite@hardpixel.eu/buttons-null.css: No such file or directory
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::at: __n (which is 19) >= this->size() (which is 19)
Aborted (core dumped)
zozio32@zozio32-p6-2487ea:~$ 
```


anyone could just pass me the missing file so I can add it where it should be?

thanks in advance

---

### Post by ActionParsnip on 2021-10-06
Sounds like a theming issue. If you contact the maintainer of the theme you are using it may help. Seems to have some issues with the Unite Shell extension that you are using

---

### Post by zozio32 on 2021-10-06
I really use a bog standards Ubuntu theme...   I really haven't changed a thing. Can i just isntall a new theme altogether?  I'll try that.

---

### Post by zozio32 on 2021-10-06
well, I have changed the theme, and it is still the same issue. buttons-null.css is missing

---

### Post by Holger_Gehrke on 2021-10-06
That file does not exist. What does exist are directories named 'buttons-left' and 'buttons-right' with files 'always.css', 'both.css', 'maximized.css', and 'tiles.css'.

If the shell extension 'unite' is correctly configured it will generate a file name from these eight depending on the state of the window in question and your choice of whether to put the buttons on the left or on the right of the title bar. Obviously something is not right. If you have not configured where you want the buttons to go ('left' or 'right'), JavaScript will have a value of null for that choice, which somehow gets translated into the string 'null'; why it doesn't look for one of  'buttons-null/{always,both,maximized,tiles}.css' I don't quite understand, might be that it's missing some other configuration settings, too.

Try configuring the extension and explicitly telling it where you want the buttons to go. And no, I can't tell you where this option is, I'm not using Gnome, I just looked at the source code of the extension.

If that doesn't help try removing the extension. 

Holger

---

### Post by zozio32 on 2021-10-07
Hi,

thank for the answer. I have specified button left or right just now as you suggested, but it did not change the problem unfortunately. May be after a reboot.

---

