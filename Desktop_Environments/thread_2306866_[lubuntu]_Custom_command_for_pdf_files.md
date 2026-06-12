---
title: "[lubuntu] Custom command for pdf files"
date: 2015-12-19
forum: Desktop Environments
---

### Post by edward8 on 2015-12-19
I would like to add the option to convert any pdf to png by right clicking on it in PCManFM and selecting an item from the menu.

I know the very simple command line I need:
```
convert document.pdf document.png
```

but I don't know how to formulate this for any file in a shortcut.

I tried
```
convert %f %f.png
```

and even
```
convert "%f" "${%f::-4}.png"
```

but neither had any effect, as I don't really understand how %f can be used.

Is the only way to do this to write a script? (if so, I've done it already, so no problem ;))

Thanks for any help you can give me.

---

### Post by vasa1 on 2015-12-19
I'm guessing you may need to set up a "custom action". I haven't done so myself in a while but the file manager version may be important.

Here is a related link:
[http://ubuntuforums.org/showthread.php?t=2231186](http://ubuntuforums.org/showthread.php?t=2231186)

---

### Post by edward8 on 2015-12-20
Thanks - I've managed to set up a custom action - it now works with my own script, but I wondered if the script was necessary at all. I'd like to know how flexible using the %f variable is - can you take the input filename of "x.pdf" and make the output "x.png" within the custom command line option, or do you need to use a script?

---

### Post by vasa1 on 2015-12-20
Take a look at [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html). Maybe it has some pointers.

---

