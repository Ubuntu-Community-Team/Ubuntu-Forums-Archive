---
title: "Can't change file associations in KDE"
date: 2015-07-18
forum: Desktop Environments
---

### Post by Fibonacci on 2015-07-18
Since I reinstalled Kubuntu I've been unable to change the default program to open any files in KDE.

For instance, JPEG files are opened with Firefox by default instead of the more appropriate Gwenview. I've tried the following:
[LIST]
[*]Opening KDE System Settings and moving Gwenview to the top for image/jpeg type. They still open with Firefox by default.
[*]Editing $HOME/.local/share/applications/mimeapps.list to put gwenview.desktop before the others. It was already in first place, and still JPEG files open with Firefox.
[*]Installing another app which opens JPEG files (e.g.: Comix). JPEG files now open with Comix instead of Firefox.
[*]Uninstalling Comix. JPEG files open with Firefox again.
[*]Editing /usr/share/applications/defaults.list by hand. JPEG files were set to open with EOG (which is unusual considering Gnome is not installed in this machine). Still opening with Firefox.
[*]Editing /usr/share/applications/firefox.desktop to remove the "image/jpeg" string from the MimeType line. Still opening with Firefox.
[/LIST]

What else should I do?

Thanks in advance.

---

### Post by speartip on 2015-07-20
You should just need to, Right click any file in dolphin, go to properties, then file type options. under application preference order, move the app you want to open that file to the top of the list, then click Apply.
All files of that type should now open with the app. you chose.

---

### Post by Fibonacci on 2015-07-24
Does that mean the Application lists on the KDE System Settings serve absolutely no purpose?

---

### Post by Erik1984 on 2015-07-26
Just to make sure, what is the content of the line starting with ```
image/jpeg=
```?
Here it is ```
image/jpeg=kde4-gwenview.desktop;
```
So kde-4- before gwenview.desktop and firefox is not on that line at all.

---

### Post by Fibonacci on 2015-07-28
"image/jpeg=kde4-gwenview.desktop" doesn't work, and "image/jpeg=gwenview.desktop" doesn't work either.

---

### Post by Simon_Tomoko on 2015-07-30
I hope these visual aids will help you out;

1. Right click on the image and go to the option Open With --> Other...
[[IMG]http://s30.postimg.org/l8snt8o7x/snapshot1.jpg[/IMG]]("http://postimg.org/image/l8snt8o7x/")

2. Expand the Graphics menu and select Gwenview. Check, Remember association...
[[IMG]http://s2.postimg.org/732d62f3p/snapshot2.jpg[/IMG]]("http://postimg.org/image/732d62f3p/")

3. Open System Settings and choose File Associations.
[[IMG]http://s29.postimg.org/5m1rucjn7/snapshot3.jpg[/IMG]]("http://postimg.org/image/5m1rucjn7/")

4. Type the file extension at the top and expand then select the type.
[[IMG]http://s11.postimg.org/w101zje27/snapshot4.jpg[/IMG]]("http://postimg.org/image/w101zje27/")

5. Here you can select Gwenview and move it to the top of the stack, even remove the association to FireFox, if you desire.
[[IMG]http://s17.postimg.org/6iffh3863/snapshot5.jpg[/IMG]]("http://postimg.org/image/6iffh3863/")

There you go,  let me know if you bump into any problems.

---

### Post by Fibonacci on 2015-08-09
Does that mean the Application lists on the KDE System Settings serve absolutely no purpose?

---

