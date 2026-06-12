---
title: "Switching between Compiz and Metacity - How?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by richardq on 2006-09-26
I'm running Compiz/AIGLX. It's running fine. However there are a couple of apps that seem to be a bit unstable under Compiz (Inkscape and Kino). So I'd like to easily switch to Metacity to run these. I don't see any way via CSM to switch back and forth. Can anyone point me to any packages (if there are any) that give me that taskbar icon functionality to switch back and forth easily?

---

### Post by beerorkid on 2006-09-26
```
sudo apt-get install compiz-manager
``` is a great way to switch between both

start it and it will put an icon in the notifications area.  click it and it has many options

---

### Post by richardq on 2006-09-26
> **beerorkid said:**
> ```
sudo apt-get install compiz-manager
``` is a great way to switch between both

start it and it will put an icon in the notifications area.  click it and it has many options

compiz-manager is not listed in synaptic and running that command from the terminal yields "E: Couldn't find package compiz-manager"

The only other close thing is "gnome-compiz-manager", which is already installed on my system. But still no icon in notification area.

Any clues? Maybe I'm missing a repository?

---

### Post by beerorkid on 2006-09-26
```
deb http://www.beerorkid.com/compiz dapper main
```
would be needed.

[http://beerorkid.com/compiz/](http://beerorkid.com/compiz/)

since they are switching to the new beryl many of the repos have removed a bunch of the packages.  I think the above repo has been repopulated with all the packages and is the main mirror the others get their copies from.  i will get in there and check.  but when I run the above code it works (well says it is already installed, but you get it)

Edit:
it has to be from that/my repo cuz it is the only one I have listed in my sources.list

Basically it was the last version of quinnstorms compiz.  it reset everything and I could not get it to run with the usual startup command.  looked at the forums and saw people mentioning to get compiz-manager.  it is pretty cool actually.

I do not log in with a XGL session, just the default session and have put compiz-manager in the startup session thingy.

---

### Post by dentaku65 on 2006-09-26
For metacity:
```
sudo metacity --replace gconf
```

For compiz:
```
sudo compiz-start --replace gconf
```

Or install compiz-manager

8)

---

