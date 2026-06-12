---
title: "Using gsettings to set wallpaper in terminal turned wallpaper blue"
date: 2019-03-31
forum: Desktop Environments
---

### Post by huff2 on 2019-03-31
Hi everyone!

I downloaded an image.png and wanted to set it as my wallpaper. I know that I can just open image.png through the gui and right-click to set as wallpaper but I wanted to get better with the terminal. 

I ran the following command:```
gsettings org.gnome.desktop.backgrounds picture-uri file:///path/image.png
```

The problem: My background just simply turned blue instead of image.png.

I have no idea why. Can someone please tell me how to resolve this and why it happened so that I can increase my understanding of Ubuntu?

FYI: I did just end up navigating to image.png through the file explorer, opening it and right clicking to set as wallpaper so that I'm not just staring at a blue screen. However, I really want to know how to do it through the terminal.

---

### Post by deadflowr on 2019-03-31
> gsettings org.gnome.desktop.backgrounds picture-uri file:///path/image.png 

Did you forget to set it?
```
gsettings set org.gnome.desktop.background picture-uri file:///path/image.png
```
And shouldn't it be background not backgrounds

---

### Post by huff2 on 2019-03-31
Ahhh, wow. I made so many errors. I don't understand what the process of "setting" it does. Would you be able to explain that to me? Or shoot me a good link on the topic? The other problem I think I had was that the file path that I typed was not a real path. I typed file:///Template/... when I should have realized that there is not a file called Template in the root directory, its in my home directory. So, I assume because of these two mistakes the computer resorted to default blue. 

Thank you so much for pointing that out.

---

### Post by again? on 2019-03-31
View the manual page.
_In terminal_
```
man gsettings
```

_Online_
[http://manpages.ubuntu.com/manpages/bionic/en/man1/gsettings.1.html](http://manpages.ubuntu.com/manpages/bionic/en/man1/gsettings.1.html)

When entering long commands in terminal, I find it better to copy and paste wherever possible and safe.
You can do the same with files in your file browser. Right click copy will copy the path.

You can also copy a dconf **schema** and key value to your clipboard from dconf-editor.
Will copy something like ...
```
**org.gnome.desktop.background picture-uri** 'file:///home/glen/Pictures/wallpaper/cartoon_mountain.jpg'
```

---

