---
title: "Mumbles: Notification Eye Candy"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by dot_j on 2007-04-22
Hi everybody - I want to announce my new project [mumbles]("http://www.mumbles-project.org"). It's a different take on notifications - similar to libnotify in Ubuntu, but based more on Growl for OSX.

It started as an attempt to learn a bit about python, dbus and cairo and I'm pretty happy with the results. It's plugin based and so far I have plugins for Gaim and Rhythmbox, as well as a script that can send custom notifications.

It's composite enabled - in that it uses transparency, so (I think) it looks quite nice if you're running Compiz or Beryl - but it still works if not.

Please check it out at [mumbles-project.org]("http://www.mumbles-project.org")

It's still a new project and I have lots in mind to make it better. So if anyone would like to contribute a plugin, patch, or artwork, I would greatly appreciate it. One of the first things I would like to do is create a deb package, so if anyone has any experience with that please contact me through the normal channels.

Thanks - and I hope you dig it.

dot_j

[IMG]http://sourceforge.net/dbimage.php?id=120166[/IMG]

---

### Post by Ender Black on 2007-04-22
It works really nice.  Can we get more plugins?  Namely, Amarok.  I know that is a KDE application, but everyone I know uses Amarok for their music collection since nothing in Gnome works as well.  

But beiing able to see the last incoming chat from Gaim (Pidgin) without having to roll the cube over to my communication desktop is super nice.  Thanks

---

### Post by hackerssidekick on 2007-04-24
Have to say it, this looks really nice! And I haven't even installed it yet! Will be following this closely :D

---

### Post by beefcurry on 2007-04-24
I would say creating a lib that different programs can parse into would be a better approach then plugins, but never the less, great work!

---

### Post by loell on 2007-04-24
will this also work , without compositor? how will it look like?

---

### Post by Aetherius on 2007-04-24
Nice one, a composite enabled notifier is most welcome ;)

However, I'll stick with libnotify in the interim.

I agree with beefcurry, in that *as well* as developing individual app-specific plugins, it would be good to develop it into a lib, possibly even a binary/script that can be called with appropriate parameters, similar to notify-send.

I also think you shouldn't have a tray icon for it. Most of us have enough tray icons, and we especially don't need one for an application you would ideally want to appear seamless.... if that makes sense.

Despite that, great work! and keep it up!

---

### Post by TheSe7enthSin on 2007-04-28
Wow, great work on it.
I agree that a tray icon shouldn't be needed. Maybe just a config GUI from the app menu?

I have a suggestion that maybe can be implemented in future releases; when the notification is clicked, it opens up the chat window.

---

### Post by TheSe7enthSin on 2007-04-29
Is there a way I can get this to automatically start when I turn my pc on?

---

### Post by strungoutfan78 on 2007-12-28
run command
```
mumbles -d
```

this will run mumbles as a daemon in the background.  in other words no tray icon.

to add it to your startup simply:
System>Preferences>Sessions
and add it to your startup items.

hope this helps.

**EDIT**  on another note, anyone know how to prevent compiz-fusion from reducing the opacity of mumbles notification windows?  it seems to recognize them as "Normal" type windows, which means if i disable opacify on Normal windows, basically i've disabled the plugin alltogether.

---

### Post by celticbhoy on 2007-12-28
I have installed and set to run, but just does not notify of anything on my system.
I use AMSN instead of pidgin, and amarok for music. What other apps does this 'link' to??

---

### Post by strungoutfan78 on 2007-12-28
i seem to be experiencing a problem getting it to work for evolution myself.  the firefox plugin works flawlessly with flock but no notification for new mail.

i can send test messages all day long just fine too.:confused:

---

