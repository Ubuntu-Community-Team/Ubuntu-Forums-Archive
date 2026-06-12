---
title: "Connection manager for ftp"
date: 2012-06-19
forum: Desktop Environments
---

### Post by scarfaceDeb on 2012-06-19
Good night.

Is there any connection manager for ftp? (something similar to ftp manager in total commander).
It should be able to save access info about any connection, so that i won't need to feel it all again.

I don't need filezilla, gFtp or any other stand-alone ftp client.
I'm looking for a more integrated into gnome way.

Gnome shell extension would be the best option. (like dropdown menu with a list of all saved accesses to the different ftps).

Thanks in advance.

---

### Post by sudodus on 2012-06-19
I guess you run the file browser Nautilus.

Choose the menu item
File -- Connect to server
and in the GUI you can select various connection modes including FTP.

Once a connection is established it can be saved as a bookmark (and it appears on the left panel for future use). Is this what you want?

---

### Post by scarfaceDeb on 2012-06-20
thank you for an answer.

I know about this option, but It's not convenient for me.
First of all, I have a lot of ftp accounts (30-40) and I don't want to have all of them in front of me all the time when I use Nautilus.
Second of all, It would be better to have a separated from a local bookmarks place for my ftp accounts.

Now I'm thinking about making some bash scripts or writing a gnome shell extension for my purpose.

---

### Post by LewisTM on 2012-06-20
Gigolo is the tool for you.
It can bookmark remote locations including FTP and connect/disconnect on-the-fly. It integrates with the GIO/GVFS framework.
For maximum efficiency I suggest you set the Preferences/Interface to show the side panel and the detailed list mode.

Cheers!

---

### Post by scarfaceDeb on 2012-06-23
this's almost exactly what I was looking for.
Thank you very much!

---

