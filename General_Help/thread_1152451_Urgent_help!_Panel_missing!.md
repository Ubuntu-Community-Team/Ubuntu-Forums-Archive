---
title: "Urgent help! Panel missing!"
date: 2009-05-07
forum: General Help
---

### Post by Acapulco on 2009-05-07
Hello. For some unknown reason today an error started popping up regarding evolution-alarm-notify, about not being able to connect to some server or something. I have never used Evolution and since it was very annoying I thought, "let's remove it".

I used Synaptic to remove Evolution (complete remove) but  the error was still there....then, on a *brilliant* (ahem..) move I did 

```

sudo apt-get update
sudo apt-get remove evolution*
```

and then

```
sudo apt-get autoremove
```

After that, I restarted my session (ctrl-alt-backspace) my panel was gone! No top or bottom panel to launch programs, no clock, no shutdown button, etc.

So, I switched to TTY1 and did a 

```
sudo apt-get install evolution*
```

After a couple of hours it installed a *lot* of stuff, including mysql and Apache for some reason (which I don't really care right now)...but my panel is still gone!

Please help me get it back. I have no idea what to do. The internet connection is still working fortunately, as well as every icon I have on my desktop...but that's it...

Any ideas on how to recover from this mess?

Also...I learned the lesson of doing stuff with "*" in it... :(

Thanks

---

### Post by _Purple_ on 2009-05-07
Try pressing ALT+F2 and type gnome-panel.

---

### Post by UbuntuNerd on 2009-05-07
if you can still get to the terminal type this command, it should restore your panels to default:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by Acapulco on 2009-05-07
Thanks a lot for the quick response. I couldn't get Alt-F2 to execute since gnome-panel wasn't even installed for some reason. So I had to apt-get install gnome-panel (after removing mysql because it was causing some errors with the b2evolution package, whatever that is..) and the ctrl-alt-backspace did the rest.

Thanks again. You saved my machine! :)

---

