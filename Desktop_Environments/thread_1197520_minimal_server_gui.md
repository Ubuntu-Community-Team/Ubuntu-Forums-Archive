---
title: "minimal server gui"
date: 2009-06-26
forum: Desktop Environments
---

### Post by frio on 2009-06-26
Anyone have any suggestions on a minimal GUI for server edition 9.04 that I can use for those times when the CLI is just killing me? Really just a text editor and a file browser would suffice.

Also, what need I do to get this minimal GUI up and running. Preferable not at boot time, only when I decide to run it from the CLI.

Thanks in advance!

---

### Post by madverb on 2009-06-26
Why is CLI killing you? You have a text editor. It's called vim.
[http://www.swaroopch.com/files/byteofvim/byte_of_vim_v051.pdf](http://www.swaroopch.com/files/byteofvim/byte_of_vim_v051.pdf)

Give it a chance. I bet you end up loving it.

Then you can use Midnight Commanader for a file browser.
[http://www.midnight-commander.org/](http://www.midnight-commander.org/)

Peace!

---

### Post by penguin-power on 2009-06-26
> **frio said:**
> Anyone have any suggestions on a minimal GUI for server edition 9.04 that I can use for those times when the CLI is just killing me? Really just a text editor and a file browser would suffice.

Also, what need I do to get this minimal GUI up and running. Preferable not at boot time, only when I decide to run it from the CLI.

Thanks in advance!
xfce is the answer.

to install, open terminal and copy/paste the line below.

sudo apt-get install xubuntu-desktop

here is the [howto]("http://www.debianadmin.com/install-xfce-desktop-in-ubuntu.html") for more info...

and here is a few [screenshots]("http://www.debianadmin.com/ubuntu-xfce-desktop-screenshots-tour.html") (look near bottom for links)

..................

the above will do if you are not bothered about the gui always running.

consider that you could "switch off" or "stop" the gui by using runlevels.

in short, if you change to runlevel 3, you have console only. if you the change to runlevel 5, thats "gui mode".  
-so, always operate in runlevel 3, and when you need a gui, activate runlevel 5 and the gui will start.
( this is the best of both worlds ;) )

here is more info on [runlevels(wiki)]("http://en.wikipedia.org/wiki/Runlevel"), and how to do [runlevels in ubuntu]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")

ps: bookmark this [site for your admin]("http://www.debianadmin.com/"), and [this one for your rss feed.]("http://www.ubuntugeek.com/")


good luck :)

will

---

### Post by snowpine on 2009-06-26
Xubuntu-desktop is overkill for your needs!

Try icewm, openbox, fluxbox, etc. with lightweight apps like leafpad and pcmanfm.

'sudo apt-get install xorg xterm icewm leafpad pcmanfm' for example.

All you need to do is type 'startx' to launch the GUI.

---

### Post by frio on 2009-06-27
Just want to thank you guys for the replies. I ended up finding 'screen' and it got me feeling a little better. At least enough to get the server, wireless and webmin going. Now I need to head over to the the networking forum to find out why my wireless connection is soooo damn slow.

thanks again!
Frio

---

