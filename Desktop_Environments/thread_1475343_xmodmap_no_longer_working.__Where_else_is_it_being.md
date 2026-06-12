---
title: "xmodmap no longer working.  Where else is it being run from?"
date: 2010-05-06
forum: Desktop Environments
---

### Post by icarus128 on 2010-05-06
Hi everyone, I am looking for more information regarding an my key mapping suddenly not working anymore.  I upgraded to lucid lynx yesterday and today I put in my normal xmodmap file that swaps capslock and the left ctrl.  The next time I logged in ubuntu asked me if I wanted to put the xmodmap file in the load list, I put it on the load list and it stopped working.

I went through /etc/gdm/Xsession and ended up removing every line having to do with xmodmap or xkbdmap except the one saying

```

if [[ -f $HOME/.Xmodmap ]]
then
   xmodmap $HOME/.Xmodmap
fi

```

And it still didn't work.  Reasoning that running the same xmodmap file a second time removes the changes since it swaps the keys that were swapped originally I removed this line and it has started working.  So apparently when I tell ubuntu to put the file on the load list it merrily runs it from somewhere else in spite of the fact that gdm will run it automatically?
To satisfy my curiosity I'm just wondering where this "somewhere else" is in case I run into something like this in the future.  Does anyone know?  I could grep every file on my hd looking for xmodmap but that seems like more trouble than it's worth.
Thanks in advance!

---

