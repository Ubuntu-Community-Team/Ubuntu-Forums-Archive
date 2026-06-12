---
title: "[SOLVED] help with devilspie"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by rob1984 on 2008-02-22
can anybody help me with devilspie?

i'm trying to embed a terminal on my desktop. i've followed the tutorial and all i get is a regular terminal window. 

my config file looks like this:

(if
(matches (window_name) &#8220;DesktopConsole&#8221;)
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype &#8220;utility&#8221;)
(geometry &#8220;+50+50&#8243;)
(geometry &#8220;924×668&#8243;)
)
)

---

### Post by DaymItzJack on 2008-02-22
Do you use compiz fusion? Because there is a better and easier way of doing this.

---

### Post by mD3m4r415 on 2008-02-22
The best way is to use Compiz Fusion... there is a good tutorial at ([http://lifehacker.com/software/linux-tip/embed-a-terminal-in-the-desktop-with-compiz-fusion-294005.php]("http://lifehacker.com/software/linux-tip/embed-a-terminal-in-the-desktop-with-compiz-fusion-294005.php"))

---

### Post by rob1984 on 2008-02-23
thanks guys but ive got it working now.

turns out i had to type the config file muanually.  not just copy and paste from the tutorial due to the UFT8 characters.

thanks anyway

---

