---
title: "There is no GNOME Login Sound item in Startup Applications"
date: 2010-08-05
forum: Desktop Environments
---

### Post by feisty john on 2010-08-05
In Lucid Lynx, I am trying to change my GNOME login sound, and I find you can't do it under System -> Preferences -> Sounds anymore. So I followed the recommendation of every search result relating to "gnome login sound" and tried to modify it under System -> Preferences -> Startup Applications. However, there is nothing relating to the GNOME Login Sound or any other login sound in my startup applications list.

How do I add GNOME Login Sound to make it an option in the Startup Applications list? How could it not be there to begin with?

---

### Post by _h_ on 2010-08-05
System -> Preferences -> Startup Applications

Click Add and use this information:

```
Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in
```

That should work.

---

### Post by feisty john on 2010-08-05
> **_h_ said:**
> System -> Preferences -> Startup Applications

Click Add and use this information:

```
Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in
```

That should work.

Ah, I had seen that bit of code in other suggestions of how to *change* the login sound, and I didn't know if there was another way to add the "GNOME Login Sound" item to the Startup list. Thanks, I'm sure this will work.

---

### Post by stupidscript on 2010-08-21
This is a good place to change the sound, too.

[I still haven't found the simple, "preferences-style" graphical way to modify the login sound or other system sounds in 10.4, just command line stuff.]

According to (running in terminal):

/usr/bin/canberra-gtk-play --help

 In System -> Preferences -> Startup Applications -> GNOME Login:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

becomes

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --file=/path/to/file.wav

or whatever audio file type you wish to use. Unfortunately, this is not working for me at the moment, but whaddya gonna do? I'll try an .ogg file type and see what happens.

Now ... about that simple, "preferences-style" graphical way to do this ... anyone?

---

### Post by wijit on 2011-02-03
If you can:
> **stupidscript said:**
> 
 In System -> Preferences -> Startup Applications -> GNOME Login:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

becomes

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --file=/path/to/file.wav


then why don't you try making it:

/usr/bin/canberra-gtk-play --file=/path/to/file.wav

---

