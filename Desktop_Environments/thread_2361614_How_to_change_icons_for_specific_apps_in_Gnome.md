---
title: "How to change icons for specific apps in Gnome?"
date: 2017-05-18
forum: Desktop Environments
---

### Post by orange2k on 2017-05-18
It used to be easy to change icons in Gnome 2, but I don't see clearly how to change an icon for an app in Gnome 3...
I installed the Faenza icons, and I would like for instance to change the default icon for Firefox to this (available in the set):
[IMG]https://cn.pling.com/img//hive/content-pre1/135969-1.png[/IMG]
Where should I look: dconf editor? or somewhere else...

---

### Post by ajgreeny on 2017-05-18
Like you I have no idea about the GUI way to make that change, or even if it's possible, so look for the **/usr/share/applications/firefox.desktop** file and open it in a text editor of your choice as root (after backing it up just in case it all goes wrong).
Find the line which is probably **Icon=firefox** if you have the default file and change that to wherever that Faenza icon is sitting, which if the same as mine is **/usr/share/icons/Faenza/apps/64/firefox-original.png**; there are several differently sized versions of that icon, so make your choice.

---

### Post by orange2k on 2017-05-18
Thanks, I'm comfortable with that solution, this way I can also set the settings for other programs, not very elegant, though...
Would be nice if there was a GUI solution, too, if someone knows one...

---

### Post by Hagar Delest on 2017-05-18
Alacarte should allow this kind of tweak. But better create custom .desktop files. You can also place them in your ~/.local/share/applications folder, it avoids tweaking a global setting. And it's easy to backup this folder to restore it later after an upgrade.

---

### Post by orange2k on 2017-05-19
Alacarte (or Main Menu) is nice, but it lacks some functionality...A recent article on Dedoimedo.com ([http://www.dedoimedo.com/computers/gnome-edit-theme.html](http://www.dedoimedo.com/computers/gnome-edit-theme.html)) is an interesting read about overall theme edits, and what it takes to do it. It is basically simple (for people comfortable with CSS), so I think it won't be long before Alacarte or some other GUI tool gets enhanced, so you can perform such tasks as icon changning with even more ease and available choice...

Quote from the article:
> The font is too pale. Basically, gray on gray, which seems to be popular nowadays, probably because most software people are young, use huge monitors for their code work, and they do not spend as much time using their products as designing it, **plus they have not been electrocuted enough**.

---

