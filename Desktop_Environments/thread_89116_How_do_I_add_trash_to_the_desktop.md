---
title: "How do I add trash to the desktop?"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Noah0504 on 2005-11-11
I want to know how to add a link to the trash on my desktop, similar to the Recycle Bin on Windows.

---

### Post by adwait on 2005-11-11
Right click on your desktop and choose to create a custom launcher. In the command type
```
nautilus ~/.Trash
```

---

### Post by quietglow on 2005-11-11
Or you can go Applications>System Tools>Configuration Editor. Then under Apps, find Nautilus the Desktop. You can control lots of stuff from there--I like having icons etc.

---

### Post by Noah0504 on 2005-11-11
I right clicked and selected to create a launcher.  I put in what you said, but when I click on it I get this error:

"Couldn't find "/home/noah/~/.Trash"."

---

### Post by Noah0504 on 2005-11-11
[QUOTE=quietglow]Or you can go Applications>System Tools>Configuration Editor. Then under Apps, find Nautilus the Desktop. You can control lots of stuff from there--I like having icons etc.[/QUOTE]
Thanks!  That was easier than I though, haha.

---

### Post by adwait on 2005-11-11
Lol, when I say ~ I mean /home/<user> directory.
So ~/.Trash = /home/noah/.Trash

but oh well......you problems solved.

---

### Post by Noah0504 on 2005-11-11
[QUOTE=adwait]Lol, when I say ~ I mean /home/<user> directory.
So ~/.Trash = /home/noah/.Trash

but oh well......you problems solved.[/QUOTE]
Oh, haha.  Well, I'm still new to the Linux world, so I wasn't aware of that.  Thanks for the help anyway!  :)

---

### Post by quietglow on 2005-11-11
FWIW, if you go under Metacity, you can control lots of the windowing features. I like my window buttons over on the left cause I frequently switch back and forth between a Mac (at work) and my laptop.

Now if the metacity folks would do some more work on "application centered" window switching :-)

---

### Post by Noah0504 on 2005-11-11
[QUOTE=quietglow]FWIW, if you go under Metacity, you can control lots of the windowing features. I like my window buttons over on the left cause I frequently switch back and forth between a Mac (at work) and my laptop.

Now if the metacity folks would do some more work on "application centered" window switching :-)[/QUOTE]
There wouldn't happen to be any options to have Gnome remember the position of my windows, would there?

---

### Post by quietglow on 2005-11-11
You mean like K does (annoyingly I find) by default when you log out? There is a way to do that, but its in a different area...System>Preferences>Sessions and then you can name a session and set it up etc. I haven't messed with it that much--I don't really want to see what my desktops looked like last night when I boot up the next morning :-)

If you mean having apps open in the same spot, I have no idea.

---

### Post by Noah0504 on 2005-11-11
[QUOTE=quietglow]You mean like K does (annoyingly I find) by default when you log out? There is a way to do that, but its in a different area...System>Preferences>Sessions and then you can name a session and set it up etc. I haven't messed with it that much--I don't really want to see what my desktops looked like last night when I boot up the next morning :-)

If you mean having apps open in the same spot, I have no idea.[/QUOTE]
Yeah, I meant the latter.  Hmm, it seems no one really knows.  Well, actually, I think there is some application or script or something that does it, but I don't remember, and I would prefer not to have to mess with anything like that.

Oh well.  Anyway, thanks for the help earlier.  See you around.

---

