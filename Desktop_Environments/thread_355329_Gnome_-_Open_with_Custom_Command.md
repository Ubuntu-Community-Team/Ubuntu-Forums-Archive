---
title: "Gnome - Open with Custom Command"
date: 2007-02-07
forum: Desktop Environments
---

### Post by musther on 2007-02-07
In Gnome it's possible to change the applications and commands associated with files by going to their properties and then open with.  Click on add and one of the things you can do is type a custom command.  If you type something like:

```
my-new-script-for-doing-clever-things -h -e
```

Or whatever, then that's what shows up in the context menu later:

```
Open With "my-new-script-for-doing-clever-things"
```

Now some things, usually things which are installed don't display the command there, they display a nice message instead.  For example the gimp doesn't say Open With "gimp", it says Open With "The GIMP", and the same with "Movie Player" etc.

What I want to know is how to specify what I want to appear when entering the custom command.

Thanks.

---

### Post by kevinlyfellow on 2007-02-08
Right click
Properties
Open With
Add
Drop-down box "custom command"
Enter in the path of your script

Edit:
Sorry, I misunderstood your question.
I'm not sure, but at least I bumped you up :-)

---

### Post by musther on 2007-02-08
No worries, I'll add one too:

Bump!

I'm betting there's somewhere which needs an entry, like the desktop files which give menu entries.  Ah well

---

### Post by madeddie on 2007-10-15
I hope someone still reads this, I'm answering pretty late :)

Anyway, Gnome also uses the MimeType line from the $appname.desktop file in /usr/share/applications

So make your app a $appname.desktop file or if it already has one, edit it. Not sure what happens with program updates though.

---

