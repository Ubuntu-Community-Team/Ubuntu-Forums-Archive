---
title: "Changing LightDM background image doesn't work"
date: 2012-11-18
forum: Desktop Environments
---

### Post by netrick on 2012-11-18
Hey, i have extremely strange problem. When I change background image in lightdm's config file (to 1600x1200 png), i just get black background in lightdm. What's more, when I leave it at default lubuntu-default-wallpaper.png and swap that file, I get black background on lightdm too! It is just change-proof, it just doesn't want user to change that ugly 12.10 wallpaper to 12.04's one.... The only thing that works is when I change background to some color, like background =#f597ff etc. I tried every possible location of file, resolution, compression, extension and nothing. Sometimes instead of black background with some files i get random stripes from that image... Once one of the wallpapers that shipped with lubuntu worked, but when i changed to another one it became black background again.

Is it known bug? Could you see if you can change lightdm background image in lubuntu 12.10? 

Thanks!

---

### Post by Paddy Landau on 2012-11-18
IIRC, I changed mine using Ubuntu Tweak.

---

### Post by daedalas1981 on 2012-11-18
> **Paddy Landau said:**
> IIRC, I changed mine using Ubuntu Tweak.

Ubuntu Tweak is what I used. Here is a link in the Ubuntu Software channel:

[https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/]("https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/")

:guitar:

---

### Post by robert shearer on 2012-11-18
Go here...
[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm)

and scroll down to the very last method....
> Ubuntu 12.10

This approach uses the dconf-editor, rather than gsettings. Changes to the unity-greeter must be done as the lightdm user. 

Works fine.

---

### Post by netrick on 2012-11-19
Thanks for answers! I found a simpler way though. Just editing /etc/lightdm/lightdm-gtk-greeter.conf works, but I had to enter in terminal "chmod 777 wallpaper.png" and voila, it works now! Thanks all for help and if anyone else experiences this problem, let you know that you don't need to install 1000 gnome 3 dependencies to use ubuntu tweak, because all you need is to chmod 777 your png file.

---

### Post by Paddy Landau on 2012-11-20
> **netrick said:**
> … I found a simpler way though…
Excellent. Thank you for sharing the solution.

Please [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

### Post by daedalas1981 on 2012-11-20
Don't hold me to it, but I think you can also chmod 777 the folder the images are in instead

---

