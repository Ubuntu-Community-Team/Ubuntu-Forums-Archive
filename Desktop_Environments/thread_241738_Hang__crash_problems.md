---
title: "Hang / crash problems"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Flavian on 2006-08-22
Hi folks!
I got some hang / crash problems on my ubuntu.
I have nm-applet (Network Manager) which handles my wireless connection very well, running on my laptop. Since my neighbour has a wireless network too, it always wants to connect to it, because his is called 8_something...
and mine: wireless_net... the thing is that for some reason sometimes it just hangs my whole computer if I switch from his network to mine. I encountered that it might be when the computer has not fully loaded yet, but I am not quiet sure.
The only thing I can do is move my mouse, etc... keyboard and klicking does not work anymore! I can not start a terminal to manually kill the network manager because I use XGL/Compiz and keyboard shortcuts won't work. btw: in that state the keyboard wouldn't work anyways!
It's a little annoying since every once in a while I have to kill my laptop and reboot. Sometimes 2 or 3 times in a row... :(


Another thing is that I can not turn OFF the computer over "System" - "Quit" in XGL/Compiz, I do NOT KNOW WHY. There is simply now "shutdown" nor a "restart" button :/
This results in ca. 1/3 hangs after logging off. Since I can not DIRECTLY shut down the PC, it just wouldn't load the splash screen and the laptop will freeze.
Again I would have to kill my laptop to shut it down...


I would be very glad for ANY solution on this!
Flo

---

### Post by Flavian on 2006-08-24
Noone got any help for me?

---

### Post by Ramses de Norre on 2006-08-24
> **Flavian said:**
> Another thing is that I can not turn OFF the computer over "System" - "Quit" in XGL/Compiz, I do NOT KNOW WHY. There is simply now "shutdown" nor a "restart" button :/
This results in ca. 1/3 hangs after logging off. Since I can not DIRECTLY shut down the PC, it just wouldn't load the splash screen and the laptop will freeze.
Again I would have to kill my laptop to shut it down...
It's normal that those buttons aren't there, I've accustomed myself to shutting down my machine from terminal, I find it way easier and I always have a terminal or three open..
So if you don't mind: to reboot pick one of these: ```
sudo init 6
sudo shutdown -r now
sudo reboot
```

To shutdown one of these: ```
sudo init 0
sudo shutdown -h now
sudo halt
```
You can change the "now" with shutdown in any value to define the minutes to wait before shutting down.

You can create a script and make a launcher for this commands if you like that better but as far as know you can't get the buttons..

I don't know about your other problem, maybe check /var/log/messages for any error messages.

---

### Post by martinz on 2006-08-24
Hi,

It seems I may have the same problem:
1. At startup, my keyboard is not responding on the logon screen
2. At shutdown, computer hangs straight away on a black screen with a cursor on top left...

Using xgl+compiz (I think) and nm-network applet
](*,)  <-- very useful on this forum...

Martin

---

