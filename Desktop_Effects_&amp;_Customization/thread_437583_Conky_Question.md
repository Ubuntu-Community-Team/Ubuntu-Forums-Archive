---
title: "Conky Question"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by ghandi69_ on 2007-05-08
Hey guys, I'm having some problems with Conky.

Mainly, I have it installed, and when I go to the terminal and type conky, everything works dandy.

I'm trying to add it to my startup programs in gnome, and I gone to preferences>sessions and done so.  When I restart, it shows up for a little bit, but once the desktop is completely done loading it disappears.  WHen I show my currently running processes, conky is there running, but I can't see it.

When I go to log out and log back in, as its logging out, it "show up" again for a breif second before going to the login splash screen.

Any ideas?

ps: sometimes it will just work.. sometimes it will not, without changing any settings.  I would say if I restarted my computer 10 times, conky would show up 2 out of the 10, and the other 8 it will remain hidden, without changing anything.

---

### Post by jfinkels on 2007-05-08
> **ghandi69_ said:**
> Hey guys, I'm having some problems with Conky.

Mainly, I have it installed, and when I go to the terminal and type conky, everything works dandy.

I'm trying to add it to my startup programs in gnome, and I gone to preferences>sessions and done so.  When I restart, it shows up for a little bit, but once the desktop is completely done loading it disappears.  WHen I show my currently running processes, conky is there running, but I can't see it.

When I go to log out and log back in, as its logging out, it "show up" again for a breif second before going to the login splash screen.

Any ideas?

ps: sometimes it will just work.. sometimes it will not, without changing any settings.  I would say if I restarted my computer 10 times, conky would show up 2 out of the 10, and the other 8 it will remain hidden, without changing anything.

Make a script "startconky.sh" that looks like this:
```

#!/bin/bash

sleep 15 && conky

```
make it executable:
```

chmod +x startconky.sh

```
and then add that script to your startup programs.

The sleep will allow your background to load before starting conky.

---

### Post by ghandi69_ on 2007-05-08
> **jfinkels said:**
> Make a script "startconky.sh" that looks like this:
```

#!/bin/bash

sleep 15 && conky

```
make it executable:
```

chmod +x startconky.sh

```
and then add that script to your startup programs.

The sleep will allow your background to load before starting conky.

Hey man, works like a charm, thanks for the quick reply.

I'm always trying to learn more about how linux runs and I'm teaching myself a little shell scripting at the current moment, any chance you care to explain why making conky "sleep" for a while makes it function correctly??

---

### Post by jfinkels on 2007-05-08
> **ghandi69_ said:**
> Hey man, works like a charm, thanks for the quick reply.

I'm always trying to learn more about how linux runs and I'm teaching myself a little shell scripting at the current moment, any chance you care to explain why making conky "sleep" for a while makes it function correctly??

We're not making conky sleep, sleep is a program in itself! Type the following in the terminal to read more about sleep:
```
man sleep
```
(in general typing *man* followed by the name of the program will give you lots of excellent info on how the program works and configuration options).

The "&&" tells the shell to execute the first program, and if it executes without exiting with an error, then execute the next command.

---

### Post by Psy-Krow on 2008-04-11
> **ghandi69_ said:**
> Hey man, works like a charm, thanks for the quick reply.

I'm always trying to learn more about how linux runs and I'm teaching myself a little shell scripting at the current moment, any chance you care to explain why making conky "sleep" for a while makes it function correctly??

also,  it has to load after compiz loads..  probably why it was not showing up all the time,  sometimes it would load before and not show.. sometimes it would load after compiz and then show.

sleeping for 15 makes sure it loads last and thus shows up =P

---

