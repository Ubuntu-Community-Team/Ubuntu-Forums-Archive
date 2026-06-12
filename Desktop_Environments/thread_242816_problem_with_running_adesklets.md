---
title: "problem with running adesklets"
date: 2006-08-24
forum: Desktop Environments
---

### Post by foxy123 on 2006-08-24
I am trying to set up a news feed adesklet, but have the following error:

```
:~/.desklets/newsfeed-0.0.4$ ./newsfeed.py
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./newsfeed.py", line 419, in ?
    Events(dirname(__file__)).pause()
  File "./newsfeed.py", line 109, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.4/site-packages/adesklets/events_handler.py", line 158,  in __init__
    self._alarm()
  File "/usr/lib/python2.4/site-packages/adesklets/events_handler.py", line 296,  in _alarm
    timeout=self.alarm()
  File "./newsfeed.py", line 157, in alarm
    self._display()
  File "./newsfeed.py", line 180, in _display
    self.draw_info()
  File "./newsfeed.py", line 238, in draw_info
    ret=self.draw_news_content(item,0)
  File "./newsfeed.py", line 313, in draw_news_content
    feed_lines= self.string_to_paragraph(feed_content)
  File "./newsfeed.py", line 394, in string_to_paragraph
    char_per_line=(self.x-2*self.borderX)/adesklets.get_text_size('x')[0]
  File "/usr/lib/python2.4/site-packages/adesklets/commands.py", line 516, in ge t_text_size
    return comm.out()
  File "/usr/lib/python2.4/site-packages/adesklets/commands_handler.py", line 10 3, in out
    raise ADESKLETSError(4,message)
adesklets.error_handler.ADESKLETSError: adesklets command error - syntax error

```

any help will be appreciated.

---

### Post by acdc_au on 2008-04-11
Hi!

I had the same problem, and then I found this forum:
[http://adesklets.sourceforge.net/forum_archive/topics/79.html]("http://adesklets.sourceforge.net/forum_archive/topics/79.html")

There a user suggests to delete these lines from the newsfeed.py file:
(located at the 392. line)

```
string_size=adesklets.get_text_size(string)
lines=len(string)/char_per_line
limit=char_per_line
```

I did as he said, and it worked for me. 
Bye

---

