---
title: "lubuntu - refresh wallpaper problem"
date: 2013-06-15
forum: Desktop Environments
---

### Post by petodindo on 2013-06-15
[COLOR=#000000]I have this script, take a look at it please[/COLOR]

[https://docs.google.com/file/d/0B0yJBwpfE0WxUXdXdGlsUnZyOTQ/edit?usp=sharing](https://docs.google.com/file/d/0B0yJBwpfE0WxUXdXdGlsUnZyOTQ/edit?usp=sharing)

[COLOR=#000000]It is downloading picture from web, save file to disk and set up as desktop wallpaper. One file, same name. Downloading and saving works fine, but refreshing wallpaper on desktop works only once - only first time. The picture is saved in some cache and the system won't change it even the file is updated, on the desktop I see only the picture downloaded first time. After system restart, the picture will change.[/COLOR]

[COLOR=#000000]So is it possible to refresh wallpaper on desktop which has the same name?[/COLOR]

---

### Post by toxicbreakfast on 2013-06-19
Not sure if there is a better way but adding something like this will work

```

pcmanfm --wallpaper-mode=tiled; pcmanfm --wallpaper-mode=stretch

```

i.e. change the mode to something else, then back to the original.

---

### Post by petodindo on 2013-06-19
man you are great :) thanx for tip, but I have to edit it like this to work for me

pcmanfm --wallpaper-mode=center
pcmanfm --wallpaper-mode=stretch

---

