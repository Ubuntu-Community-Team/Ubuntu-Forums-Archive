---
title: "gdm problem: username, password dialog box missing"
date: 2010-07-11
forum: Desktop Environments
---

### Post by gcadenaz on 2010-07-11
hello!
this is my first ever post so please be patient if i've created a thread in the incorrect place or something like that.

i have a problem :-D

upon starting my laptop (no dual boot - only ubuntu 10.04 installed) it does its thing (you know, boot up text flying all over the place) and then gets to the login screen....except!....

there's no login dialog box appearing!

it shows the default background (the purply image), it does the startup sound (du du) and the mouse cursor is there but there's no username, password dialog box.

here's what i've tried.

ctrl-alt-f1 to get to a terminal

entered username and password

sudo service gdm stop

sudo apt-get install --reinstall ubuntu-desktop

sudo apt-get install --reinstall gdm

sudo dpkg-reconfigure xserver-xorg

sudo service gdm start

...

still no dialog box!

i've tried a whole bunch of other things which i can't remember now (which doesn't really help here.

note: there's no /gdm directory in my /etc/X11 directory.

---

### Post by gcadenaz on 2010-07-12
ok a couple of updates...

I tried going to,
/etc/dbus-1/system.d

and looking in gdm.conf
but it just looked like scribbly to me (i was trying to find some user permissions)

then i tried something simple like,

gdm --version

and it said,

** (gdm-binary:3329): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.100" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:3329): WARNING **: could not acquire name; bailing out

so then i tried,

sudo gdm --version

and it loaded the login screen again (the default purple screen) and again it had no dialog (username, password) box.

so I did ctrl-alt-f1 and it the terminal showed,

gdm-binary[3336]: WARNING **: Unable to load file '/etc/gdm/custom.conf' : No such file or directoy
gdm-binary[3336]: WARNING: Unable to find users: no seat-id found.


ok....so....

I'm missing custom.conf

anyone know what custom.conf should have in it?

thanks in advance :)

---

### Post by tom17 on 2010-07-14
I'm having the same problem on two machines.

Laptop: I think it was a fresh install at 9.10 and then upgraded to 10.04. When I boot up, I get a login screen, but when I try to switch user, I get the problem you described above. I get the main gdm login screen and the central dialog to choose users or login, except there is no list of users and nowhere to type in a user name.

Desktop/server. I had left this on 9.04 I think as I did not want to risk breaking stuff with the upgrade (no time, new toddler :) ). Today I must have accidentally accepted a dialog asking to do a dist-upgrade rather than a normal update. By the time I noticed this it was too late to go back so it's now 9.04 upgraded to 9.10. On this one, I get the same problem even after a reboot.

I need to rebuild both of these machines from scratch, I realise this, but in the meantime, my wife is nagging me to put windows on them. Ugh.

Any ideas?

---

### Post by gcadenaz on 2010-07-15
hey tom

yeah it's a nasty problem. I spent some serious hours (what am i talking about?....i spent about 4 working days!) trying to fix it with no luck.

despite every linux geek saying that what i ended up doing shouldn't be necessary, for all intents and purposes it WAS necessary....

I just ended up getting a 10.04 live cd and re-formatting the entire system. i know it's a sledgehammer approach but damn it works!

i'd like to give you some advice but i'm a total noob.
your wife is a smart woman, i was seriously close to throwing in the towel and going back to windows.

---

### Post by c-f on 2011-01-27
Have you been able to resolve the issue????

If so how...

I really not wish reinstall the whole thing!

Claude

---

### Post by c-f on 2011-01-27
[SOLVED]
In the shell (CTRL+ALT+F1) I did:
sudo apt-get update
sudo apt-get upgrade

Done!

Maybe something was broken from previous update?

Claude

---

### Post by elvisd on 2011-01-31
I had the same problem.
After trying and googling I have found that was caused (at least in my case) from an unterminated apt-get that messed up my system.

After a simple 
```
sudo dpkg --configure -a 
```
everything is back to normality.
Hope this helps someone else

---

