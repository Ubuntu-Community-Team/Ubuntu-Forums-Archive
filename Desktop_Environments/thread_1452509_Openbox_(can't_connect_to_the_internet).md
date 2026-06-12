---
title: "Openbox (can't connect to the internet)"
date: 2010-04-12
forum: Desktop Environments
---

### Post by livrcrux on 2010-04-12
Hello, 
I just recently installed ubuntu 9.10. I'm not completely new to Linux or to the command line, but new enough to find myself confused. 

I got interested in openbox when I saw that it was an available GUI, so I decided to give it a shot. For some reason I can't get Firefox to work. I type firefox in the terminal and the window comes up with everything working fine except for the fact that it doesn't connect to the internet. When I type the same command in Gnome it works just fine. I've Googled and Binged it, and while a wide array of topics are discussed about the autostart.sh and the menu.xml among other things, there is nothing discussing connecting to the internet. 

So can anyone point me in the direction of a functioning Firefox in openbox? 

Thanks ahead of time. 
-me

---

### Post by nothingspecial on 2010-04-12
You have to make network manager start at login or use a different app to connect to the internet.

I`ll layout what I do on a minimal install with openbox

Get a wired connection.
```

sudo ifconfig eth0 up
sudo dhclient
```

The next command will remove the Gnome network manager and install an alternative one. An advantage of this one is that it starts at boot rather than login as network-manager does.

```
sudo apt-get install wicd ncurses-base
```

then type ```
wicd-curses
``` to configure your connection.

---

### Post by livrcrux on 2010-04-12
Thanks a lot. It worked. openbox is mine now. :)

---

### Post by nothingspecial on 2010-04-12
No problem :)

---

### Post by TheDexter1111 on 2011-03-30
hi there, im having trouble getting a wireless conection...

I ran the same commands (replacing eth0 with wlan0) but no good... any help??

---

### Post by Ahz The Cat on 2011-05-13
if wicd is properly set up you should be able to configure wireless through the wicd curses dialog or the gui.  Failing that (my wicd is acting funny so I have to do this) boot into a regular gnome session, get your wireless going with network mgr, then log out and log into openbox session.  Your connection should remain intact.  

Also, try running iwconfig to see what your wireless connectivity looks like.

---

