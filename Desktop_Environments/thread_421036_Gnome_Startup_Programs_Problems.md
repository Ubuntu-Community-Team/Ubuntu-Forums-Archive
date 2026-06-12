---
title: "Gnome Startup Programs Problems"
date: 2007-04-24
forum: Desktop Environments
---

### Post by balleyne on 2007-04-24
I've been having a strange problem with configuring my startup programs in Gnome (Ubuntu 6.06) that I can't seem to figure out. I go to System->Preferences->Sessions and then click on the Startup Programs tab, but it's as if I no longer have write privileges or something. It worked initially for the first few weeks of using Ubuntu, but when I tried a few weeks ago, and ever since, (1) I can't delete any entries, the button is always greyed out; (2) ANY changes that I make (Adding a program or editing a current program in the list) are forgotten the instant that I close the window, nevermind by before the next time I startup.

It's getting frustrating because there are a few programs that I have to manually start up every time I turn on my machine, and something as basic as configuring startup programs would make life a little easier.

I'm looking for help in one of two ways. First of all, any idea what may be wrong and how I might be able to fix it? And alternatively, if it can't be fixed, are there any workarounds so that I can manually edit the startup programs list (are the startup programs saved in a text file somewhere)?


Any help would be greatly appreciated!

---

### Post by jacobhpaul on 2007-04-24
I have the same problem :-/

---

### Post by jacobhpaul on 2007-04-24
I figured it out.  You have to change the permissions on your autostart folder to allow yourself to write in it.

Try This:

```
 sudo chmod +rw ~/.config/autostart
```

---

### Post by ComplexNumber on 2007-04-24
> **jacobhpaul said:**
> I figured it out.  You have to change the permissions on your autostart folder to allow yourself to write in it.

Try This:

```
 sudo chmod +rw ~/.config/autostart
```
that shouldn't be necessary. the entries that the user adds himself are stored in there and they shouldn't be owned by root. i don't know why yours were.

---

### Post by balleyne on 2007-05-06
Yeah, that was my problem too actually. Somehow that autostart folder became property of root. I used a slightly different command to fix it though, probably better in the long run as I believe it restores the permissions to what it should be by default:

```
sudo chown -R ~/.config/autostart
```

I noticed that the one file in there was own by root as well, which is why I reclaimed all the files within the folder.

---

