---
title: "&quot;Titlebar Buttons Placement&quot; setting doesn't affect all windows (18.04)"
date: 2018-10-20
forum: Desktop Environments
---

### Post by citizensnips on 2018-10-20
I am running Ubuntu 18.04.1 LTS and want to move the window titlebar buttons from the left to the right.  I followed the directions on this page:

[https://askubuntu.com/questions/1036070/how-to-move-the-window-control-buttons-in-18-04](https://askubuntu.com/questions/1036070/how-to-move-the-window-control-buttons-in-18-04)

But it only affects the titlebar button placement for the Tweaks window itself.  Other windows I have open, and new windows opened after making the change, are unaffected.

Does anyone know how to fix this?

---

### Post by Qew on 2018-10-20
I presume that you've logged out and logged back in again after changing that setting? I don't remember that being necessary or not, but often you have to do that kind of thing for some settings.

---

### Post by citizensnips on 2018-10-20
It turns out I was still using Unity after the upgrade to 18.04.  This was apparent when I clicked on the gear icon next to the "Sign In" button at the login prompt, which gave me the following choices:

Ubuntu
Ubuntu on Wayland
Unity

After selecting "Ubuntu", the Gnome desktop manager loads and the titlebar button placement setting works on all windows as expected.

Before checking this, I also changed my display manager from lightdm to gdm3.  Based on my searching, gdm3 is the default for 18.04, so the lightdm must have also been leftover from 16.04.  I'm not sure if changing the display manager is required to fix the issue described in the title and first post.

---

### Post by Qew on 2018-10-21
No, lightdm doesn't affect that issue. I'm using Ubuntu's default desktop and have the window buttons set how you like them set, but I still use lightdm rather than gdm3.

---

