---
title: "How to add an application to be launched at system starup in KDE?"
date: 2007-06-14
forum: Desktop Environments
---

### Post by dolarsrg on 2007-06-14
Hi everyone!

is there a way to do this from the system config panel?

If not, How can I do it from de bash?

Thanks in advance ;)

---

### Post by dannyboy79 on 2007-06-14
you can just add it thru the session manager, System, Prefs, Session, then go to the tab that has appliocations that are started when your X session starts. OR if it's more complex you can add it to your /etc/rc.local file.

---

### Post by dolarsrg on 2007-06-14
Thanks!

But in the session manager I can't find where to add the program :(

Mi session manager looks like you can see in the attached file :(

---

### Post by dannyboy79 on 2007-06-14
> **dolarsrg said:**
> Thanks!

But in the session manager I can't find where to add the program :(

Mi session manager looks like you can see in the attached file :(
ah, KDE. don't use it but found this: /home/<username>/.kde/Autostart, you can add links to applications you want to start when KDE starts

give it a shoot.

---

### Post by dolarsrg on 2007-06-14
I've try this command:
```
ln -s checkgmail /home/santi/.kde/Autostart/
```

Did I did right?

I've restat but it doesn't run automaticly.

Thanks again!

---

### Post by Nythain on 2007-06-14
just do a search for the .desktop file of the program you want to start automatically, copy it, and put the copy in to the ~/.kde/autostart directory.

---

### Post by dannyboy79 on 2007-06-14
i don't know if this autostart thing in Kubuntu works with symlinks? Is checkgmail executable? have you checked out gmail-notify if you can't get this to work?

---

### Post by dannyboy79 on 2007-06-14
> **Nythain said:**
> just do a search for the .desktop file of the program you want to start automatically, copy it, and put the copy in to the ~/.kde/autostart directory.

when installing checkgmail, no .dekstop file is created, otherwise a decent tip.

---

### Post by Nythain on 2007-06-14
it doesnt have a kmenu entry or anything???

---

### Post by Nythain on 2007-06-14
ok, well if you really need checkgmail autostarted...
open up kate.
put in something like this
```

[Desktop Entry]
Encoding=UTF-8
Exec=checkgmail
Icon=kpm
Type=Application
Name=checkgmail
GenericName=Gmail Checking Utility

```
save the file as checkgmail.desktop
at location
/home/username/.kde/autostart

restart x and see if that works... not sure if there are any command line arguments you need to pass with it

---

### Post by dolarsrg on 2007-06-14
Thanks!!!!

It works great!!

I've learn a lot :D

---

### Post by dannyboy79 on 2007-06-14
that was completely unneccessary! checkgmail works by simply double-clicking it from nautlis within gnome and I don't see why it would be any different in kde. as long as the checkgmail was executable and stored (not as a symlink) within the autostart folder, than it would have worked.

What he had you do was create a desktop icon file which is not what you needed.

---

### Post by Nythain on 2007-06-14
but it worked... i prefer dealing with links instead of moving/copying files around the computer... this way if anything happens, god forbid, they still have the binary right where it should be

---

### Post by dannyboy79 on 2007-06-14
you're right. it did work. Let's be honest here; you told him to do it this way only because that's the only way you knew how. I mean, let's look at what that file does that you created.......... You even added an icon to it, so what did you do that for then???

I am not trying to pick on you it's just that so many people suggest how to do something despite it being the completely incorrect way of doing it. I guess it's not the fact that it's incorrect, it's more of the fact that's it completely ____rigged.

but again, you're right, it does work.

---

