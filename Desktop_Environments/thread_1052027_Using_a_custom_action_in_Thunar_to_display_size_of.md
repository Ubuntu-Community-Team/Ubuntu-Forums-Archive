---
title: "Using a custom action in Thunar to display size of multiple folders and files"
date: 2009-01-27
forum: Desktop Environments
---

### Post by omkrasu on 2009-01-27
**Hello!** I had this problem since i use Thunar.

Now it got solved. (And please forgive me if this message isn't well formated, because this is my first post.)

All you got to do is to open a Thunar window, then go to Edit, and then to Configure custom actions...

Add a new action by clicking on the plus sign.

For a name give for example: **Counter**
For description give like: **Disk usage counter**

And this is the key, in the command field put this code:

**du -h -c %N | grep total | zenity --text-info**

Now, advanced users may leave out "grep total", if they want detailed information about all the selected folders and files.

And to finish the job, you have to set everything on in **Appearance conditions** (next to the Basic tab).

Please, if you have a better solution for checking the disk usage of multiple folders, to check the size, post a reply.

Bye!

---

### Post by omkrasu on 2009-01-27
Sorry... i forgot to finish it.

Close the Thunar window, open a new one, and select as many files and folders as you want to,

right-click on them and under the Create archive option you'll see Counter. Click, and voilá it shows the info in a text window.

Bye!

---

### Post by adamlau on 2009-01-27
Useful UCA, omkrasu :) . I made a couple of quick changes to suit my needs:

Estimate Space Usage
```
du -chs --apparent-size %N | zenity --text-info
```

---

