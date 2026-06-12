---
title: "Exit Fluxbox and Immediately Login Back In(auto login)"
date: 2009-07-20
forum: Desktop Environments
---

### Post by 4dplane on 2009-07-20
Hi,

when I restart my computer the auto login takes me straight into Fluxbox. When I use the Exit command from the fluxbox menu I exit Fluxbox and I'm asked for a username/password. Is there a way to log me straight back in? The reason why is it would work as a refresh button because when I use restart from the Fluxbox menu it restarts but it kills my nm-applet icon and I would like to sometimes reload a different .asoundrc file.

So is there a way never to be asked for a User/Pass and always login as a specific user?

Thanks,
4D

---

### Post by kerry_s on 2009-07-21
there's a setting in the login manager, but the lowest you can set it is 10 seconds.

> 
the reason why is it would work as a refresh button because when I use restart from the Fluxbox menu it restarts but it kills my nm-applet icon and I would like to sometimes reload a different .asoundrc file.


doesn't fluxbox have a restart option?
[http://fluxbox-wiki.org/index.php?title=Howto_edit_menu](http://fluxbox-wiki.org/index.php?title=Howto_edit_menu)
> [restart] (label) {command}
   This tells Fluxbox to restart. If command is supplied, it shuts down and 
   runs the command (which is commonly the name of another windowmanager). 
   If the command is omitted, Fluxbox restarts itself.


---

### Post by 4dplane on 2009-07-21
> **kerry_s said:**
> 
doesn't fluxbox have a restart option?


Yes, but when I use it, the nm-applet icon does not reappear in the gnome-panel, only logging out and back in does. Also, I need to reset the .asound file and it too will need a log out / in.

Thanks,
4D

---

### Post by 4dplane on 2009-07-21
Ok,

how about

```
/etc/init.d/gdm restart
```

it works but how can I let a none admin(sudo) run this command?

I would rather not give this account admin rights. I tried changing the chmod and chown but nothing worked.

4D

---

### Post by kerry_s on 2009-07-21
> **4dplane said:**
> Yes, but when I use it, the nm-applet icon does not reappear in the gnome-panel, only logging out and back in does. Also, I need to reset the .asound file and it too will need a log out / in.

Thanks,
4D

i don't mean a straight restart that only does fluxbox, but you can put your own commands.

example:
**[restart] (restart-all) {nm-applet;next-command;etc...}**

i don't know the command your using to reset your asound file, but i would just put what ever startup command you got in your ~/.fluxbox/startup that should restart it just as if you just logged in.

> it works but how can I let a none admin(sudo) run this command?

you can use a sudoers nopasswd option:
[B]sudo visudo
%users ALL=NOPASSWD: /etc/init.d/gdm[/B]

then just use-> **sudo /etc/init.d/gdm restart**

---

### Post by 4dplane on 2009-07-21
When I run this command:
```

[restart] (restart-all) {nm-applet}
```

a restart happens but the nm-applet icon does not reappear.


Thanks for the visudo info.

it works, but... there's always a but...](*,)

The restart never happens. It shuts down but never restarts; I think because the user is logged out and not able to exe the start up command. If I run the command "/etc/init.d/gdm restart" from the same user in an ssh connection from a different machine, the gdm restart works perfectly.

4D

---

### Post by kerry_s on 2009-07-21
i don't know the only thing i can think of is your fluxbox setup is not right.
let me see your ~/.fluxbox/startup

---

### Post by 4dplane on 2009-07-21
Here you go

```
#!/bin/sh
# Used by startfluxbox
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/home/main/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.

# Sets a black background
/usr/local/bin/fbsetroot -sold "#000000"

#toolbar
gnome-panel &

# so gnome programs look good
gnome-settings-daemon &

# Calls wireless card
  nm-applet --sm-disable &
  #nm-applet

# exec fluxbox
# or if you want to keep a log:
  exec fluxbox -log "/home/main/.fluxbox/log"

```

---

### Post by kerry_s on 2009-07-21
that looks fine, sorry i'm out of ideas, i haven't used fluxbox in a while.

---

### Post by 4dplane on 2009-07-21
thanks for your help...

so to you the nm-applet should just reload when I use the fluxbox resart command?

Another thought, is there any way to set the auto login timer to 1 sec instead of 10sec?

4D

---

### Post by kerry_s on 2009-07-21
> **4dplane said:**
> thanks for your help...

so to you the nm-applet should just reload when I use the fluxbox resart command?

Another thought, is there any way to set the auto login timer to 1 sec instead of 10sec?

4D

yeah, the nm-applet should always be there when restarted, at least that's how i remember it. you might want to try wicd (wicd-client &)instead, see if it does the same thing.

i think there is, but i can't remember, let me test & get back to you.

---

### Post by 4dplane on 2009-07-21
I found out how to set the auto login timer to > 10 sec.

[http://www.dotslashblog.com/2009/06/ubuntu-timed-login-in-less-than-ten-seconds/](http://www.dotslashblog.com/2009/06/ubuntu-timed-login-in-less-than-ten-seconds/)

or
edit
```
sudo gedit /etc/gdm/gdm.conf-custom
```

```
AutomaticLoginEnable=false
 
TimedLoginEnable=true
TimedLogin=<insert your username here>
TimedLoginDelay=5
```

I set it to 1 and then 0, both work but with 0 you still see the login screen for just a flash. No Problem!

Ok, Well thanks again. At a later point I will try and resolve the Fluxbox restart issue w/ nm-applet but for now this will work. Off to another problem. talk to you again I'm sure...

4D

---

