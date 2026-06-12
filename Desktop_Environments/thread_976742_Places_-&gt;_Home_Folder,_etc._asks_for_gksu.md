---
title: "Places -&gt; Home Folder, etc. asks for gksu"
date: 2008-11-09
forum: Desktop Environments
---

### Post by bolucpap on 2008-11-09
My Menu Bar has started acting weird. Whenever I click on an icon in the "places" menu, like "Home Folder", "Documents", etc. I get prompted for my password. I think this happened when issued a "sudo baobab" instead of "gksu baobab" from a terminal. This does not happen for any other icons in the "Applications" menu. Any ideas on how to stop that?

---

### Post by mali2297 on 2008-11-09
Try resetting yourself as owner of all files in your home directory. From the command line, type
```

sudo chown -chR yourusername:yourusername /home/yourusername

```
If that doesn't help, reset the ownership of hidden files as well:
```

sudo chown -chR yourusername:yourusername /home/yourusername/.??*

```
Be careful so that you don't change ownership of any files outside the home directory.

---

### Post by ciscosurfer on 2008-11-09
This [thread]("http://ubuntuforums.org/showthread.php?t=976610") may also be helpful.

---

### Post by bolucpap on 2008-11-09
Sorry, changing the owner of the files under home directory did not work. Any other suggestions? By the way, I created a new user from scratch and logged in under that name. Did not have the problem.

---

### Post by bolucpap on 2008-11-10
Since there has not been a new reply in the past 12 hours, let me pose it as a question: Where does gnome (or nautilus?) keep the information about which locations will appear on the Places menu on the menu bar? And how does it decide whether to prompt for the administrative password or not?

---

### Post by bolucpap on 2008-11-10
bump?

---

