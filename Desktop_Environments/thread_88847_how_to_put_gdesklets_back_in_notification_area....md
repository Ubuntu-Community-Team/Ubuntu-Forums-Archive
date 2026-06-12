---
title: "how to put gdesklets back in notification area..."
date: 2005-11-11
forum: Desktop Environments
---

### Post by Makrie on 2005-11-11
Hi

Not so cunningly, I chose to both remove gdesklets from the notification area and enable translucency... this means that now all my gdesklets are on black backgrounds and I can't access the configuration menu to change this!

Is there either a way of putting gdesklets back in the notification area or another way of accessing the configuration menu?

Thanks

Makrie

---

### Post by dcstar on 2005-11-11
[QUOTE=Makrie]Hi

Not so cunningly, I chose to both remove gdesklets from the notification area and enable translucency... this means that now all my gdesklets are on black backgrounds and I can't access the configuration menu to change this!

Is there either a way of putting gdesklets back in the notification area or another way of accessing the configuration menu?

Thanks

Makrie[/QUOTE]
If you do Applications-Accessories-gDesklets, does the icon reappear?

---

### Post by Makrie on 2005-11-12
[QUOTE=dcstar]If you do Applications-Accessories-gDesklets, does the icon reappear?[/QUOTE]

Hey David

Unfortuneately not, that opens up the gdesklets shell but does not give me back my notification icon - and I can't find any 'configuration' options in the shell...

Cheers!

---

### Post by 23meg on 2005-11-12
Did you by any chance remove your notification area from the gnome panel? What exactly did you do to remove gdesklets from the notification area?

---

### Post by Makrie on 2005-11-12
[QUOTE=23meg]Did you by any chance remove your notification area from the gnome panel? What exactly did you do to remove gdesklets from the notification area?[/QUOTE]

I had to double check just then! Nope, notification area still there, works just fine for rythembox.

As I recall, when I right clicked (just clicked?) on the gdesklets icon in the notification area, one of the options was 'display in notification area' - which I then unticked... urgh!

Thanks

---

### Post by 23meg on 2005-11-12
In ~/.gdesklets/registry you should see a config file with a .db extension. Edit the end of it to look like this: ```
 sS'__default__ trayicon'
p8
I01
s.
```

and relaunch gdesklets.

---

### Post by Makrie on 2005-11-12
[QUOTE=23meg]In ~/.gdesklets/registry you should see a config file with a .db extension. Edit the end of it to look like this: ```
 sS'__default__ trayicon'
p8
I01
s.
```

and relaunch gdesklets.[/QUOTE]

Thanks for that! Because of your advice I made it in the end, though not quite as cleanly as the way you suggested...

I opened that file and found a 'trayicon' entry higher up which I amended to look like you said... restarted and still nothing.

Went back to my saved .db file and added that code to the end... no change again.

I'd tried uninstalling and reinstalling a couple of times and it hadn't brought the identification icon back... this time I uninstalled, deleted the registry folder you specified above, reinstalled andbingo, there's my notification icon!

It's a shame there's not an easier way of bringing back the notification, if only to avoid having to display the gdesklets icon!

Anyhow, thanks for your time and advice, there's sure no way I would have thought to do that without your posts.

---

### Post by 23meg on 2005-11-12
You're welcome. If you want to get rid of the tray icon in a safe way, you can launch gdesklets with the --no-tray-icon option.

---

### Post by Makrie on 2005-11-12
[QUOTE=23meg]You're welcome. If you want to get rid of the tray icon in a safe way, you can launch gdesklets with the --no-tray-icon option.[/QUOTE]

Oh. Would you mind telling me how to do that, please? In fact, I'm not too sure I know how to start or stop gdesklets, except through the notification area...

And if I do start it with the 'no tray' option, how would I then access the configuration menu?

Cheers!

---

### Post by 23meg on 2005-11-12
Hit alt+f2 or launch a terminal and type
```
gdesklets --no-tray-icon
```
Before doing this, configure everything, so you won't need the configuration menu any longer. If you want to change the configuration, stop gdesklets with ```
killall gdesklets
```, launch it without the option, make your changes, quit, and then launch with --no-tray-icon again. 

You can also create a launcher and enter this as the command it will launch.

---

### Post by Makrie on 2005-11-12
Thank you very much!

---

