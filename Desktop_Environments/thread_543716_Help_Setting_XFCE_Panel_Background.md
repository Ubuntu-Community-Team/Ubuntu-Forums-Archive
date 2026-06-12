---
title: "Help Setting XFCE Panel Background"
date: 2007-09-05
forum: Desktop Environments
---

### Post by cujo on 2007-09-05
I want to change the xfce panel color to something other than the theme default.  Can someone help me with this?  I'm afraid I'm not sure where to start.  There don't seem to be any obvious '.' files to look into for this.

Thanks

---

### Post by mojoman on 2007-09-06
I think you have to edit the file for the gtk-2.0 theme that you're using. It can be done BUT I've never done it myself so I'm no expert on this.  However, check where the theme you're using is located (use the command locate and grep to find, post back if you need help on this) and then look at the relevant files in it, most likely it called [theme-name]rc or maybe even panelrc. Then, find the lines on the panel and start your trial and error :)

I found these pages in other forums, they might help.

[http://www.linuxquestions.org/questions/showthread.php?t=470494](http://www.linuxquestions.org/questions/showthread.php?t=470494)

[http://xfce-look.org/comments/discussion.php?id=1&forumpage=0&PHPSESSID=0b0fb6c7f2a27022a33ff44e250b24aa](http://xfce-look.org/comments/discussion.php?id=1&forumpage=0&PHPSESSID=0b0fb6c7f2a27022a33ff44e250b24aa)

Post back if I can help any more, and to let me know if it worked.

best regards
mojoman

---

### Post by cujo on 2007-09-06
Well that is a start.

It turns out that the panel color inherits the default background color of your windows as well.   I think there may be a way to specify the color of particular elements, but I have to do some more investigating.

Theming is a real pain.

---

### Post by cujo on 2007-09-06
Ok, so I overlooked the section in one of the links you sent that explains how to do it.

Basically, I needed to add this chunk to my theme...

```

style "panel"
{
    #stuff I wanted here
}

class "*Panel*" style "panel"

```

Now to make it pretty...

There is also a link here for anyone wanting some info on some xfce customizations...
[http://jozmak.blogspot.com/2007/04/optimizing-xubuntus-user-interface.html]("http://jozmak.blogspot.com/2007/04/optimizing-xubuntus-user-interface.html")

---

### Post by mojoman on 2007-09-06
Ok, good to see that you're on your way of solving it, and thank's for the info. Interesting blog, I bookmarked it myself. :)

---

### Post by cari on 2007-09-16
hello!

is there a way to enable alpha-transparency, so I could use "fade to transparent" image as a background?:confused:

thanks!

---

