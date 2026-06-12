---
title: "[Solved] Conky window doesn't fit the content"
date: 2013-08-15
forum: Desktop Environments
---

### Post by sashkello on 2013-08-15
Hi all!

I've got a problem with a rather simple Conky I've made. It's reading rss and printing some output. However, it cuts off the text at some point. That is, it's supposed to show 5 entries, but it shows only 3, the third one ending in the middle of it. 

The weird thing is that it did load first time I made it, but stopped working properly afterwards. Reloading didn't help. I'm using Cinnamon desktop, but I actually observed same thing with KDE when tried on another computer.

[B].conkyrc
[/B]```
# --- Window Layout & Options --- #
own_window yes 
own_window_transparent yes
own_window_type normal 
own_window_hints undecorated,below,skip_taskbar,skip_pager
double_buffer yes 
use_spacer right
use_xft yes
alignment top_left 
gap_x 20
gap_y 10


# --- Colours, Sizes, Fonts & Margins --- #
update_interval 2.0
stippled_borders 3
border_width 10
default_color white


# --- Text --- #
draw_outline no
draw_borders no
font Monospace:size=8:weight=bold
uppercase no
draw_shades yes


TEXT
${color Medium Spring Green}Latest Blog Posts${hr 1}${color}
${execp python rss.py}

```

[B]rss.py
[/B]```
import feedparserimport datetime as dt


try:
    feed = feedparser.parse("http://www.rssmix.com/u/3793062/rss.xml")
    for i in range(5):
        try:
            blog = feed["items"][i]["link"][7:]
            if blog[:3] == "www":
                blog = blog[4:]
            if blog.split(".")[0] == "feedproxy":
                blog = blog.split("/")[2]
            else:
                blog = blog.split(".")[0]
            date = dt.datetime.strftime(dt.datetime.strptime(feed["items"][i]["published"][:-6].rstrip(), "%a, %d %b %Y %H:%M:%S"), "%d %b")
            print "[" + date + "]","${color Sky Blue}", "("+ blog +")  "+feed["items"][i]["title"], "${color}"
        except:
            pass
except:
    pass
```

What I expect to see (and Python script itself prints it fine):
[HTML][date] (blog) text
[date] (blog) text
[date] (blog) text
[date] (blog) text
[date] (blog) text[/HTML]

What Conky looks like:
[HTML][date] (blog) text
[date] (blog) text
[date] (blog) te[/HTML]

I'd really appreciate your help with this, guys. Thanks.

---

### Post by Petro Dawg on 2013-08-15
You might be exceeding your text allotment, try adding these lines to your conkyrc file above "TEXT" 

text_buffer_size 2048  
max_user_text 65000

Let me know if it works or not, so I know if I need to dig deeper into your code.

Also a screenshot of the issue is worth a 1000 words.

---

### Post by sashkello on 2013-08-15
Thanks, Petro! That worked perfectly :)

---

### Post by Petro Dawg on 2013-08-15
You are welcome.

You might want to post any further issues you have with Conky [here]("http://ubuntuforums.org/showthread.php?t=281865") in the mega-thread to be sure someone skilled in Conky see's your question.

---

### Post by sashkello on 2013-08-15
Cool, thanks, I'll surely post the screen there when I'm done.

---

