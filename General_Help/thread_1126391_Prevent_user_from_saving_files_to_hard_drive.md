---
title: "Prevent user from saving files to hard drive"
date: 2009-04-15
forum: General Help
---

### Post by slacker9876 on 2009-04-15
Hello Community, 
I have created a kiosk style machine without menus and allowing access only to links on the desktop. How do I prevent users from saving to the computer, while preserving the rights to save to a flash drive?

This computer will be in a public library.

---

### Post by James_Lochhead on 2009-04-15
I would try and take write permission off the entire home directory. This may cause problems with applications though as they save their settings to the home directory. You can take them off (suggest from another account with root privileges) like this (in the terminal):

```

sudo chmod -R -w /path/to/home

```

All other solutions that I can think of would result in hidden files that could be written to.

Depending on the applications you are using you might be able to fiddle the settings so they don't actually save any settings.

---

### Post by 3Miro on 2009-04-15
> **James_Lochhead said:**
> I would try and take write permission off the entire home directory. This may cause problems with applications though as they save their settings to the home directory. You can take them off (suggest from another account with root privileges) like this (in the terminal):

```

sudo chmod -R -w /path/to/home

```

All other solutions that I can think of would result in hidden files that could be written to.

Depending on the applications you are using you might be able to fiddle the settings so they don't actually save any settings.

Yes hidden files are a problem. If you use Firefox, then you will not be able to save history and cookies. This in theory is fine, however, there are many legitimate pages (mail sites in particular) that require cookies to log in.

On an old Windows (I think 98), there was a fortress program that blocked writing to disk. However, we could still save files in Program Files\Internet Explorer.

On Mac, I have seen setting so that people are allowed to save files, however, all saved files (including browser history) gets cleaned after logging out. I guess you can make a script that purges the /home/guest_user folder and replaces is with a "clean" one.

---

