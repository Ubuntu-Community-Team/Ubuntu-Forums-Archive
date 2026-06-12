---
title: "gnome terminal and beryl fps"
date: 2006-11-11
forum: Desktop Environments
---

### Post by eXisor on 2006-11-11
My gnome terminal is cutting fps by 30 under Beryl. What gives? When I maximise the terminal, I lose another 35. So 85 to 65 to 30 fps. Anyone else getting this kind of beryl benchmark behaviour?

This is even more odd because I lose only 3 fps when using a maximised firefox. Since gnome terminal is basically just a 2d text app, what gives with its painting routines? 

I'm running edgy, beryl 0.1.2 with aiglx, and a radeon 7000ve agp 64mb at 16 bit colordepth, and have 768mb memory. Scrolling is smooth as silk in everything except the gnome terminal. (I've tried setting the terminal current profile scroll list size and memory down and it makes no difference). Memory usage doesn't seem to be the issue.

Any ideas?

---

### Post by igknighted on 2006-11-11
Does Ubuntu (gnome) have transparency on the terminal?  I know a lot of distro's do it, and that might cause the drop you see.

---

### Post by eXisor on 2006-11-11
No, the transparency defaults to off in the gconf-editor. The beryl theme is transparent on the title bar, but that's the same for all apps.

---

