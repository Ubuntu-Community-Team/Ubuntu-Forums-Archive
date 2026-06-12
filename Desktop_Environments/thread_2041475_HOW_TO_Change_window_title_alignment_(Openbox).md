---
title: "HOW TO: Change window title alignment (Openbox)"
date: 2012-08-12
forum: Desktop Environments
---

### Post by Mortesins93 on 2012-08-12
For some people this thread could seem very simple and kind of stupid, but I decided to write it since I spent so much time trying to find out how to change the alignment of the window title in lubuntu 12.04 with openbox window manager.
So, many of you might know that changing the button order (which includes the window title) is pretty simple, you just have to go in the **openbox configuration manager** under the **appearance** tab, but what I found out is that the actual alignment of the title depends on the theme you choose.
This is what you have to do to change it:
-First of all, choose your theme (for example Bear2)
-Now, in **/usr/share/themes** you should find a folder with the theme's name (for example **Bear2**).
-Inside of this folder, you should find an **openbox-3** folder.
-Inside of this folder, open with your favorite text editor the **themerc** file.
-In the file, under general, you should find a ***.text.justify** field, change it to either **Right**, **Left** or **Center**.
**BTW:** if the theme you are changing is a pre-installed theme you'll find it in /usr/share/themes and so you'll need root privileges (sudo something) to edit the file. Otherwise you should find the theme in **~/.local/share/themes**.

[http://openbox.org/wiki/Help:Themes](http://openbox.org/wiki/Help:Themes)

---

### Post by Paddy Landau on 2012-08-19
Thank you for the how-to. You may want to [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others wanting the same solution.

---

### Post by Mortesins93 on 2012-08-19
No problem

---

