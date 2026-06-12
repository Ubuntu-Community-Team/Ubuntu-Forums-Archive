---
title: "Help, Don't know exactly what happened"
date: 2005-06-28
forum: Desktop Environments
---

### Post by n8qxb on 2005-06-28
I downloaded a icon theme to my home folder called icons. Next I wanted to move the file to usr/share/icons, so I used what I thought was the correct command. In the root terminal I typed, mv MacOS-X ~/.icons The file disappeared and I have know idea where it went. It's definitely not in the usr/share/icons.
Can anyone tell me where the file went and what I did wrong.
Thank you!

---

### Post by N'Jal on 2005-06-28
it's still in your home directory. you moved it to

/home/yourusername/.icons

It's in a hidden folder, folders that begin with a . are hidden. So

```
sudo cp ~/.icons/MacOS-X /usr/share/icons
``` 

Should do the trick.

If you just wanna check open nautilus and type /home/yourusername/.icons into the address bar and make sure it is there.

---

### Post by n8qxb on 2005-06-28
I followed the directions and still no file in /.icons

---

### Post by davahmet on 2005-06-28
[QUOTE=n8qxb]I followed the directions and still no file in /.icons[/QUOTE]
 Since you did this in the root terminal, the files should be in /root/.icons/.  The easiest way to find them is from a root terminal, run 'ls ~/.icons'.

---

### Post by n8qxb on 2005-06-28
Thank you...I found the files in root/.icons as you said and deleted them!

---

