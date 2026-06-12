---
title: "remote X on windows"
date: 2011-02-27
forum: Desktop Environments
---

### Post by waratah on 2011-02-27
I upgraded to Ubuntu 10.10  Maverick and gdm no longer supports xdcmp.  I thought others may have an issue with:

Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyError: cannot open display: localhost:10.0 ubuntu 

When connecting to Ubuntu from a remote windows machine using Cygwin X.  

firstly install the startx command.  I used X-start-menu-icons and it installed what I needed.

Now run startx  which gives you an X session to work with.

Use command "xhost +"  this disables security on your X server running on windows.  Because it is not the main screen it is not much of a risk.

ssh -X user@server

this will establish a command line connection.   Mostly I want to use mail so I type "evolution"  and it starts on my windows screen remotely.  I also wanted to firefox to connect locally to a secured port for jetty.

You will probably have to install a window manager on cygwin to manipulate the screens.

---

