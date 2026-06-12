---
title: "fixing colors in lxterminal"
date: 2012-03-03
forum: Desktop Environments
---

### Post by marinara on 2012-03-03
getting horrid colors in lxterminal.  like this
[IMG]http://i.imgur.com/YZlNu.png[/IMG]

luckily there is a fix.  just add ```

# Turn on 256 color support...
if [ "x$TERM" = "xxterm" ]
then
    export TERM="xterm-256color"
fi
```to your .bashrc


then do this:
[http://blog.credativ.com/en/2010/02/tipp-activating-256-colors-support-in-vim.html](http://blog.credativ.com/en/2010/02/tipp-activating-256-colors-support-in-vim.html)


ths code is from [http://henzenmann.blogspot.com/2011/03/proper-color-support-in-lxterminal.html](http://henzenmann.blogspot.com/2011/03/proper-color-support-in-lxterminal.html)

---

