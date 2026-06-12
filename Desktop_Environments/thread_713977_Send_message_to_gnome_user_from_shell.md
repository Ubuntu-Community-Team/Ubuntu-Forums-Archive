---
title: "Send message to gnome user from shell"
date: 2008-03-03
forum: Desktop Environments
---

### Post by dlublink on 2008-03-03
Hi,

I am connected via SSH to a ubuntu machine and need to notify the user of an empending change to the system.

Is there a command to do this? In windows I could do this :

net msg 127.0.0.1 "banana"

I found 'talk', but I think that is for consoles only.

Thanks,

David

---

### Post by drubin on 2008-03-03
If you run the   shutdown  cmd, it alerts all the users that  it is about to shut down!

So yes there MUST be a way. How? not 100% sure.  :(

---

### Post by adieb on 2008-03-13
hallo guys

no solution found yet? i am looking for it too...
maybe this helps somebody:

if your desktop is locked, gdm offers you to leave a message to the user. if you do that, the user will get a nice message box...

does this work over dbus?


greetings

---

### Post by adieb on 2008-03-13
ok hello

i found out that there is a programm called "notify-send" that exactly performs the action you wish. (on gnome)
maybe you need to install so
> sudo apt-get install libnotify-bin 
the only problem is, that it needs to connect to the dbus-server of the user you want to inform about something, but it cannot since you are connected through ssh.

ssh -x works, buit then the message pops up on your desktop


still you could do something:
open a terminal at the display the user uses e.g.:
> 
DISPLAY=:0 xterm&
sudo write USERNAME [hit enter]
[write your message]
[end with "strg D"]


it´s not the perfect way, but who cares ?!

---

