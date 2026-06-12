---
title: "Cant use &amp;exit in a bash script"
date: 2009-04-03
forum: General Help
---

### Post by martinianom on 2009-04-03
Hi, I have a couple of scripts that i use frequently.

I have a drawer on my panel with a button for each one of them. 

the thing is that I want to use '&exit' at the end of the command so that i dont have to deal with the blank terminal screen.

this is one of the scripts


#!/bin/sh

rsync --delete -r /home/martiniano/.kde/share/apps/amarok/podcasts/ /media/SANSA\ FUZE/PODCASTS/ &exit

xmessage -buttons Ok "Ready"

exit


i want it to do its thing and then show a message when its done


can anyone help? Thanks!

---

### Post by kerry_s on 2009-04-03
that looks okay to me, but you can lose the exits, not needed.

```

#!/bin/sh
rsync --delete -r /home/martiniano/.kde/share/apps/amarok/podcasts/* /media/SANSA\ FUZE/PODCASTS/ 
xmessage " Ready " -center -timeout 10


```

---

### Post by martinianom on 2009-04-03
yes, it works if i run it on a terminal

but if i create a launcher on my panel, I have to wait for it to finish and then close the terminal window manually

another example is:

```
 vinagre 192.168.2.4:9999 &exit

```

if i run this in a terminal it works fine but if a create a launcher (application in terminal type) it doesnt work at all

if I dont include the '&exit' it opens 2 windows. the remote pc and the blank terminal. how can I make it just show the remote pc window?

---

### Post by kerry_s on 2009-04-03
don't set it to run in terminal on the launcher, if you want the terminal put it in the script where you have control.

example: gnome-terminal -x rsync ......
or if you use xterm: xterm -e rsync ......

---

