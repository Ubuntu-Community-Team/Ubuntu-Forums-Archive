---
title: "Can you Customise the Failsafe Terminal?"
date: 2008-03-10
forum: Desktop Environments
---

### Post by ibuclaw on 2008-03-10
Hi, I was wondering if you could customize the failsafe terminal to load a "better" looking interface? (As opposed to the horrible orange and the smallest white terminal in the world ever).
I mean, I can't even read what I'm typing in!

Here is an example of what I would like to get it looking like (This is backtrack by the way).
[IMG]http://www.newbie.cl/nb/wp-content/uploads/2007/10/backtrack2.jpg[/IMG]

Only I would like it with my own user background and the gnome-terminal the way I have it setup. (grey on black and transparent)


Any suggestions or pointings in the right direction would be gratefully thanked.

Iain

---

### Post by ibuclaw on 2008-03-11
Okay, I've found the config file.

>  /etc/gdm/Xsession 

here is the failsafe script

```
 if [ x"$command" = xfailsafe ] ; then
  if [ -n "$zenity" ] ; then
    "$zenity" --info --text "`gettextfunc "This is the failsafe xterm session. $
  else
    echo "$0: Starting the failsafe xterm session."
  fi
  exec xterm -geometry 80x24+0+0
fi 
```

So apart from removing `exec xterm -geometry 80x24+0+0` and replacing it with gnome-terminal. How do I get my background up?

Iain

---

### Post by warp99 on 2008-03-11
Look at the man pages for gnome-terminal. Here are the command options that you may find interesting:
```

--pixmap FILENAME
    Specifies the image filename to be used as the background for this terminal.
-bgscroll
    Specifies that the background image should scroll together with the text as the screen scrools. 
--bgnoscroll
    Specifies that the background image should not scroll when the text scrolls in the terminal.
```

---

