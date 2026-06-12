---
title: "Login screen background change"
date: 2012-05-10
forum: Desktop Environments
---

### Post by siavashm31 on 2012-05-10
The fact that I can not change login screen background in Ubuntu 12.04 drives me crazy :(

I installed Ubuntu tweak tool, and when I change the login screen background in there, then after restart I even cannot see the default ubuntu background and there is just background color.

When I did fresh install of ubuntu 12.04 it did change the login background automatically to my desktop BG, but when I changed my desktop BG in GNOME3, then the feature didn't work any more and I'm stuck with ubuntu default BG :(

Does any one else have similar problem? Any solution for it?

---

### Post by zombifier25 on 2012-05-10
LightDM autochanging background will only work if your background is a default one; a.k.a. found in /usr/share/backgrounds

Start Nautilus as root:
```
gksudo nautilus
```
and copy any image you want to be your background in there. Then finally, set it via right-clicking on desktop -> Change Background

---

### Post by siavashm31 on 2012-05-10
Thanks for the reply,
But, I did this as well by logging in in root account, and it didn't work.

I tried your way as well, I launched nautilus as super user, and I moved my photos to the /usr/share/backgrounds, but I can't see them in my wallpapers when I right click on the desktop to change background.

---

### Post by zombifier25 on 2012-05-10
type this in the terminal:
```
ll /usr/share/backgrounds
```
and post the output. Your photo may not have the appropriate permission.

---

### Post by siavashm31 on 2012-05-11
Thanks, Solved,
After I ran the ll command I found out there is no permission set for my wallpapers. so I edit their permission to Read & write for the owner (root) then I could set them as wallpaper which would come to the login screen as well.

So it seams if I want to change the WP of login screen I should copy the photo into usr/share/backgrounds and then change it's permission

---

### Post by Jay Nnib on 2012-12-29
Can you say what to do in clear. Because, I have the same problem and can't understand what you guys really did

---

### Post by zombifier25 on 2012-12-29
Ok.

First, copy the image you're setting as a wallpaper to /usr/share/backgrounds , either graphically by launching Nautilus as root:
```
gksu nautilus
```
or the command line:
```
sudo cp /path/to/yourimg /usr/share/backgrounds
```

Then set the copied image as your wallpaper by right-click on the desktop > Change Background

Also, like siavashm31's case, it may not have the appropriate permissions (but such cases are rare), so if you're running Root Nautilus, right click on the file, choose "Properties" > "Permissions", and let the owner read and write it. Or run this command:

```
sudo chmod u+rw /usr/share/backgrounds/yourimg
```

---

