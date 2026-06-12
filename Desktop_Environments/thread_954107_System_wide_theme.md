---
title: "System wide theme"
date: 2008-10-20
forum: Desktop Environments
---

### Post by fballem on 2008-10-20
On my machine, I use the Blubuntu theme, including both GTK and GDM (for logon) as well as having set the background colour.

What I would like to do, on another machine that has multiple users, is set up blubuntu as the system wide theme. In other words, when I add a user, the default theme should be blubuntu (they can change it if they wish).

I would also like to change the theme for the existing users.

Any idea how I do this?

Thanks,

---

### Post by fballem on 2008-10-21
bump, please

---

### Post by LaRoza on 2008-10-21
You would have to have the system use it as a default, easiest way would be to have a custom ISO. I do not know how to do it otherwise.

Try RemasterSys if you go this route: [http://ubuntuforums.org/showthread.php?t=852868](http://ubuntuforums.org/showthread.php?t=852868)

---

### Post by fballem on 2008-10-21
I was hoping that I could set up something like a 'default profile' that could be used as a model for any new users.

That would just be a whole lot easier than creating my own custom distro. I'm not quite there yet!

---

### Post by fballem on 2008-10-29
When I set up a new user, the user has a theme setup. Where does the system get the information from that is used to setup that theme? It seems to me that if I can locate that and replace it with blubuntu theme, then any user that I set up will have the blubuntu theme by default, which is what I want.

If someone can tell me how to do this, then this should solve my thread.

Many thanks,

---

### Post by Idefix82 on 2008-10-29
What I would try is this: in /usr/share/themes there is a folder called Default. Why don't you try putting your own theme in there and see what happens? Don't forget to backup the folder before doing that.

---

### Post by fballem on 2008-10-29
> **Idefix82 said:**
> What I would try is this: in /usr/share/themes there is a folder called Default. Why don't you try putting your own theme in there and see what happens? Don't forget to backup the folder before doing that.

Thanks for the suggestion, but unfortunately, it didn't work. I did find that there are files in the Default theme that seems to indicate that there are hard codings involved.

There is a gtkrc file, with the following content:

#
# Default keybinding set. Empty because it is implemented inline in the code.
#

So somewhere, there is something that identifies the Default theme that is applied to a new user. Hopefully, someone will be able to tell us where that is, and how to set it.

Thanks,

---

