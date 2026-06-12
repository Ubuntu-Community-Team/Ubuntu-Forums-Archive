---
title: "How to add custom Application to favourites"
date: 2022-01-05
forum: Desktop Environments
---

### Post by erosman on 2022-01-05
Ubuntu 21.10

In order to run Firefox Nightly, I have downloaded and unpacked it to 
```
/home/Apps/firefox/firefox
```

I have also created **nightly.desktop** in
```
/user/share/applications/nightly.desktop
```

It still doesn't show the icon anywhere (favourites or Show Applications).

What is the next step?

---

### Post by schragge on 2022-01-05
```
sudo update-desktop-database
```

---

### Post by erosman on 2022-01-05
Thank you. After above, nothing happened. I logged out/in but still the same.

When Nightly is launched the icon appears on the dock but I cant set it as favourite.
I have to go to **/home/Apps/firefox/firefox** every time to launch Nightly.

---

### Post by schragge on 2022-01-05
Show the contents of your **nightly.desktop**

---

### Post by vanadium on 2022-01-05
A .desktop file not showing up indicates a problem with it, e.g. Exec= line pointing to invalid executable, etc. To avoid having to work as root, (and not disrupting other users on the system with nightly builds), place your .desktop launcher under ~/.local/share/applications instead.

---

### Post by erosman on 2022-01-05
> Show the contents of your **nightly.desktop**
> A .desktop file not showing up indicates a problem with it, e.g. Exec=  line pointing to invalid executable, etc. To avoid having to work as  root, (and not disrupting other users on the system with nightly  builds), place your .desktop launcher under ~/.local/share/applications  instead.

I moved it to **.local/share/applications **

I found out there was a mistake in my [B]nightly.desktop
[/B]I had use **/home/Apps/firefox** instead of [B]/home/...USER.../Apps/firefox
[/B]
doh ....

Thank you everyone for the help[B] :)
[/B]

---

