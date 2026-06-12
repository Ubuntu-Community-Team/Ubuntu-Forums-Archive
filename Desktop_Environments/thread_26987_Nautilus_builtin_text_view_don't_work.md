---
title: "Nautilus builtin text view don't work"
date: 2005-04-14
forum: Desktop Environments
---

### Post by garlito on 2005-04-14
When I try to view a plain text file, for example with "nautilus /etc/fstab" command I obtain this error:

Couldn't display "/etc/fstab".
The location is not a folder.

Is this feature removed from gnome-2.10 ?

Thanks,
Garlito.

---

### Post by p!=f on 2005-04-14
[QUOTE=garlito]When I try to view a plain text file, for example with "nautilus /etc/fstab" command I obtain this error:

Couldn't display "/etc/fstab".
The location is not a folder.

Is this feature removed from gnome-2.10 ?

Thanks,
Garlito.[/QUOTE]
Nautilus is not a text editor. If you want to edit files use gedit intead. If you'd run
```

nautilus /etc

```
you'd get the /etc/ directory.
```

sudo gedit /etc/fstab

```
to edit it under root privileges.

---

### Post by garlito on 2005-04-14
[QUOTE=garlito]When I try to view a plain text file, for example with "nautilus /etc/fstab" command I obtain this error:

Couldn't display "/etc/fstab".
The location is not a folder.

Is this feature removed from gnome-2.10 ?

Thanks,
Garlito.[/QUOTE]
 Yes, but in warty I can use nautilus to view text files. That seems broken now. I copy from the hoary nautilus manual:

Viewing Files in a File Browser Window

The file manager contains viewer components that enable you to display particular types of file in a file browser window. For example, you can display the following types of files in a file browser window:

    * Plain text files
    * PNG files
    * Joint Photographic Experts Group (JPEG) files 

To reload the contents of a file browser window, choose View &#8594; Reload. To stop loading an item, choose View &#8594; Stop.

When you display a file in a file browser window, the viewer component might add menu items to the file manager menus. The menu items relate to the file type that is displayed. For example, when you display a PNG file, the Edit menu contains flip and rotate menu items.

Also, when you display some types of file in a file browser window, you can use the file manager zoom buttons to change the size of the item.

Thanks.

---

