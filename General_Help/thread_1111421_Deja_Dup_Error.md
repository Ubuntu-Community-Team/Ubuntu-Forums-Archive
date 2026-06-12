---
title: "Deja Dup Error"
date: 2009-03-30
forum: General Help
---

### Post by domi84 on 2009-03-30
I have installed Deja Dup on Hardy by thir repository:
[https://launchpad.net/~deja-dup-team/+archive/ppa](https://launchpad.net/~deja-dup-team/+archive/ppa)

When I try to backup this is the error:
```
mimmo@mimmo-laptop:~$ deja-dup

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

(deja-dup-preferences:16878): GLib-GObject-WARNING **: IA__g_object_set_property: object class `GtkCellRendererPixbuf' has no property named `gicon'

** (deja-dup:16874): WARNING **: Operation.vala:290: The name org.gnome.SessionManager was not provided by any .service files

** (deja-dup:16874): DEBUG: DuplicityInstance.vala:115: Running the following duplicity (16886) command: ionice -c3 duplicity collection-status --exclude=/media/disk/Dati/Mimmo/Backup/DejaDup --exclude=/home/mimmo/.cache --exclude=/home/mimmo/.thumbnails --exclude=/home/mimmo/.gvfs --exclude=/tmp --exclude=/proc --exclude=/sys --exclude=/home/mimmo/.local/share/Trash --exclude=/home/mimmo/.thumbnails --exclude=/home/mimmo/.beagle --exclude=/home/mimmo/Musica --include=/home --exclude=** --no-encryption file:///media/disk/Dati/Mimmo/Backup/DejaDup --verbosity=9 --volsize=5 --log-fd=16

** (deja-dup:16874): DEBUG: DuplicityInstance.vala:426: duplicity (16886) exited with value 1

mimmo@mimmo-laptop:~$ 
```
Help me Please...

---

### Post by mikix on 2009-04-02
This is a known bug with the Hardy version.  It doesn't seem to affect Deja Dup for Intrepid or Jaunty.

[https://bugs.launchpad.net/deja-dup/+bug/352492](https://bugs.launchpad.net/deja-dup/+bug/352492)

I'm the developer of Deja Dup, and I'm looking at it, but I'm not sure why it fails yet.  I have to get my hands on a Hardy system first.

---

