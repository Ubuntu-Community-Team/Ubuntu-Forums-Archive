---
title: "show certain file types feature"
date: 2008-03-19
forum: Desktop Environments
---

### Post by alecz20 on 2008-03-19
First I want to say that I couldn't find any pertinent information to this issue.

I would like to know if there is a feature/program/extension in Ubuntu window manager that can make it show only certain types of files.

For example you enter directory and in it you have pictures and movies, but you only want to see the movie files. So you could choose (from a drop-down menu) what file type/extension you wish to see (the default being *.*)

If anyone knows of anything that can do this... please let me know.

Thanks!

---

### Post by lapubell on 2008-03-19
I use thunar, the XFCE default file manager and you could do this with a little python script that sets all the other images to hidden (puts a dot in front of the name) and another script to remove the hidden attribute.

if you want code, let me know.

---

### Post by alecz20 on 2008-03-19
Your option sounds interesting, but I think the main idea would be yo be able to switch between different file types rather fast.

If you have for example 5 different file types (.png, .zip, .ogg, .avi, .tar)
you would have a drop-down menu in the file manager that would offer you the following options:

- *.png
- *.zip
- *.ogg
- *.avi
- *.tar
- media (.avi & .ogg)
- archives (.zip & .tar)
- pictures (.png)

the feature would have to scan to see what files are in the directory and provide pertinent options.

If such a feature does not exist yet, I am willing to try and write one, but I don't know where to start... Would I have to recompile the file manager with the new feature or would I be able to embed it somehow separately (via a plug-in for example)?

Your idea with a python script is interesting but, would is provide a drop-down menu kinda thing?

---

