---
title: "removing the border around user icons"
date: 2024-10-06
forum: Desktop Environments
---

### Post by scoobert7 on 2024-10-06
hello, i'm trying to get rid of the blurred circular  border/background/whatever around the user icon on the login and unlock  screens:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294340&stc=1[/IMG]

based on what i found [here]("https://github.com/GNOME/gnome-shell/blob/0f923a6a2d5112e6034ef4163c2614ea38f7ea00/data/theme/gnome-shell-sass/widgets/_misc.scss#L8") and [here]("https://github.com/GNOME/gnome-shell/blob/0f923a6a2d5112e6034ef4163c2614ea38f7ea00/data/theme/gnome-shell-sass/widgets/_login-lock.scss#L298") in the gnome-shell source code, i created a new theme with the following for gnome-shell.css:

[HTML].user-icon, .user-avatar {
  background-color: transparent !important;
  box-shadow: none !important;
  border: none !important;
}[/HTML]

it actually works in alerts:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294341&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294342&stc=1[/IMG]


but no luck for the login or lock screens. i'm using ubuntu 24.04 and gnome shell 46.

---

