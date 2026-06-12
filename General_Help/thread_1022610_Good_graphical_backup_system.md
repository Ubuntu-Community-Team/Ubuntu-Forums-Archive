---
title: "Good graphical backup system"
date: 2008-12-27
forum: General Help
---

### Post by obsrv on 2008-12-27
Is ther good graphical backup system for making backups of /etc  and whole /home direcotry? I need graphical one for my wife to use on her Ubuntu machine.

---

### Post by skillllllz on 2008-12-27
Try Flyback. It's simple and relatively straight forward. [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by obsrv on 2008-12-27
User interface is OK, and overall program has very good usability, but one problem... It hangs :( downloaded the lastes version. All the output I get:

```
obsrv@PIRATE:~/Tools/flyback$ python flyback.py
flyback.py:330: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.xml = gtk.glade.XML(RUN_FROM_DIR + 'viewer.glade')
flyback.py:373: GtkWarning: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
  file_list_widget.append_column(column)
count not parse gconf /apps/flyback/crontab - using defaults
Killed
obsrv@PIRATE:~/Tools/flyback$ 

```

Note: I killed the program, because it hanged.

---

### Post by sdennie on 2008-12-27
I use Simple Backup:

```

sudo apt-get install sbackup

```

It's very easy to both backup and restore files with that.  It also saves things as a standard tar file so you don't even really need the program to restore files.

---

### Post by Hydrid on 2008-12-27
System Imager

---

### Post by hyper_ch on 2008-12-27
why not just writing an own script and put it in cron... so it will make a backup regurarly...

---

