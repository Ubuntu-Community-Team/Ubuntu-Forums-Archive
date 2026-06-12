---
title: "Xubuntu 18.04.2 vs Xubuntu 19.04 folder color"
date: 2019-06-09
forum: Desktop Environments
---

### Post by benbrockn on 2019-06-09
One thing that seemed to change when I was testing out Xubuntu 19.04 in a VM, is that the folder color was different than my Xubuntu 18.04.2 install.

So, I went to 'Appearances' on both the VM & the host machine to make sure I select the correct theme and icon sets, and I found out that they were both the using the same ones!

Just the folders are a different color...

[https://i.imgur.com/FVGyJVg.png](https://i.imgur.com/FVGyJVg.png)

[ATTACH=CONFIG]283403[/ATTACH]

So, I know this seems like a little thing to ask, but how do change the folder color from the tan/beige normal color to blue?

---

### Post by silentstone on 2019-06-09
xfce made some changes that limits color changes in theming, but i'd start by searching for the theme folders on each distro, and comparing the stylesheets and images there.  /usr/share/themes/[theme-name] is the usual folder, though i forget the specific default Xubuntu theme name. same with icons: check /usr/share/icons/[theme-name]

---

### Post by again? on 2019-06-10
You could install elementary-icons and see how that looks.

---

