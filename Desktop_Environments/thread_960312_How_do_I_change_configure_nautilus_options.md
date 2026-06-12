---
title: "How do I change configure nautilus options"
date: 2008-10-27
forum: Desktop Environments
---

### Post by Nopposan on 2008-10-27
Hi, folks.

Please tell me how to configure Nautilus file management options.  'Can't find anything in the "preferences" or "system" menus that looks promising.

Thanks.

---

### Post by hictio on 2008-10-27
What do you have in mind? What do you need specifically?

---

### Post by Nopposan on 2008-10-28
I'd like to be able to have it display the window that a person can type the path into.  I'd also like to configure it to default to the "list view" setting.

Thanks.

---

### Post by hictio on 2008-10-28
Cool, then, I'm not really sure if there is a way of doing this within the GUI, so, type:

```

Alt + F2

```

And then type:
```

gconf-editor (ENTER)

```

Navigate, or open: apps/ Nautilus/ preferences
And set, check the option:

'always_use_location_entry'

And, then, set, change, or edit the value:
'default_folder_viewer' as 'list_view' ,(without quotes)

No need to reboot or anything.

You can also set those values directly from the Terminal prompt, but I don;t recall the exact syntax at the moment, and I'm kinda in a hurry to look it :)

---

### Post by oldos2er on 2008-10-28
> **Nopposan said:**
> I'd like to be able to have it display the window that a person can type the path into.  I'd also like to configure it to default to the "list view" setting.

Thanks.

 You want the 'Location bar.' It should have a toggle you can click to enter a directory name.

---

### Post by hictio on 2008-10-28
> **oldos2er said:**
> You want the 'Location bar.' It should have a toggle you can click to enter a directory name.

This is the toggle that oldoser means, click on the 'pencil and paper icon':

[url=http://xs.to/xs.php?h=xs432&d=08442&f=naut.01912.png]
[img]http://xs432.xs.to/xs432/08442/naut.01912.png.xs.jpg[/img]
[/url]

And it will expand onto the Location Bar:
[url=http://xs.to/xs.php?h=xs432&d=08442&f=naut.00665.png]
[img]http://xs432.xs.to/xs432/08442/naut.00665.png.xs.jpg[/img]
[/url]

---

### Post by Nopposan on 2008-10-30
Right, but I wanted the location bar to display all the time.

Thanks, Hictio.

---

