---
title: "How do i setup Conky RSS?"
date: 2009-05-16
forum: Desktop Environments
---

### Post by BazookaAce on 2009-05-16
Hi, 

How do i setup RSS in conky? Can somebody tell me what the configfile should be named, and in with folder it should go?

Thanks in advance.

---

### Post by m_duck on 2009-05-16
Check out the [conky documentation]("http://conky.sourceforge.net/variables.html") for how to use the rss function.

As long as you already have conky up and running, you just need to add a few lines to your ~/.conkyrc. For example, to display a feed title, followed by the newest 3 items in the feed:
```
${rss http://website.com/feeds 10 feed_title}
${rss http://website.com/feeds 10 item_title 1}
${rss http://website.com/feeds 10 item_title 2}
${rss http://website.com/feeds 10 item_title 3}
```Where obviously you need to change the URL to the one you want and the 60 means update every 60 mins. There are a couple of other options to use as well which are outlined on the site mentioned above.

HTH

---

### Post by BazookaAce on 2009-05-18
Thanks! 

But one question. I followed the conky-guide in this forum, and my Conkysetup is in the "conkymain"-file. How can i use several conkys? I've tried to setup a "Now Playing"-conky in the .conkyrc-file, but nothing happens.

---

### Post by sherl0k on 2009-05-18
If you want to use multiple conky configurations, specify the **-c** parameter at runtime.

According to the manpage:

-c | --config=FILE
    Config file to load instead of $HOME/.conkyrc 

So in theory you can have multiple versions of conky running with multiple config files.

---

### Post by m_duck on 2009-05-18
Yeah, what sherl0k said :D

If you were to start conky normally, it will load the ~/.conkyrc preferably, or /etc/conky/conky.conf if that doesn't exist. To load different configs, say ~/.conkyconfig1 and ~/.conkyconfig2 you would need to execute```
conky -c ~/.conkyconfig1
```and```
conky -c conkyconfig2
```To make them automatically launch on startup you will need to add a script that is a bit like the following to your autostarted apps:```
#!/bin/bash
sleep 5 && conky -c ~/.conkyconfig1 &
sleep 5 && conky -c ~/.conkyconfig2 &
```You then need to open a terminal and type```
chmod +x /path/to/script
```in order to make it executable. The **sleep 5** is in case you are using compiz or something to stop borders being drawn behind them, thought you will probably need to increase this number to delay conkys start until after compiz is loaded. There is another way to stop the shadows from within compiz but I don't know how to do it as I don't use it.

---

### Post by BazookaAce on 2009-05-18
Thanks! I'll try this out! If i'm not back in 10 minutes, i did it :)

---

