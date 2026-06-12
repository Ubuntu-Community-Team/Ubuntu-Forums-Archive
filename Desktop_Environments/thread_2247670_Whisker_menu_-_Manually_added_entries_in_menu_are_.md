---
title: "Whisker menu - Manually added entries in menu are not editable."
date: 2014-10-09
forum: Desktop Environments
---

### Post by Sparrowhawk536 on 2014-10-09
Hello

Yesterday I did fresh installation of Xubuntu 14.04.1 on my Asus 1225B netbook. Everything works great, but I have some problems with new Wisker menu. I installed eclipse in /opt directory. I created soft link to /usr/local/bin/. Next, I created new menu entry by MenuLibre creator. Now, I see the app in menu, and I could run it from there, but if I go to MenuLibre, and I want to edit entry, I can't. There is no entry which was created earlier. So I can't edit or remove entries manually added.

---

### Post by amanchesterman on 2014-10-09
I too have had problems trying to edit entries using MenuLibre. I've got round it by editing the .desktop files with Mousepad or similar editor. From memory the .desktop files are in the /home/[your username]/.local/share/applications directory, but maybe others can confirm that.
(NB directories that begin with a dot like '.local' are hidden, so if you are using Thunar use the View menu and the 'show hidden files' option to see them.)

---

### Post by Sparrowhawk536 on 2014-10-09
Thx for reply and help. I was looking for those files in wrong directory. Now, I can delete or modify those entries.

---

