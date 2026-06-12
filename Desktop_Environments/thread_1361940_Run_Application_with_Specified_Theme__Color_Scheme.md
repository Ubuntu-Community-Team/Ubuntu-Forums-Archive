---
title: "Run Application with Specified Theme / Color Scheme"
date: 2009-12-22
forum: Desktop Environments
---

### Post by undoIT on 2009-12-22
I usually run dark themes / color schemes, like Obsidian Coast / Oxygen in Kubuntu. Some programs are problematic when running dark color schemes. One of the things I liked about previous versions of Kubuntu is that Gnome applications would open in a separate theme (Raleigh), so I could use a dark color scheme for KDE and run some of the programs I use most i.e. Firefox / Open Office and the dark scheme wouldn't interfere with the Gnome applications.

However, now that Open Office is integrated with KDE color schemes as of 9.10 Karmic, I can't override the dark scheme for Open Office. This is particularly unusable for Calc, because the background of the spreadsheet is black and the background colors specified for Custom Styles are not visible. I set Widget style to Raleigh in System Settings > GTK+ Appearance and also unchecked Apply colors to non-KDE4 applications in Colors > Options. This works for Firefox but not for Open Office.

In Gnome, it is possible to open specific apps with a user-specified theme using the following command in the launcher:

```
env GTK_RC_FILES=<path> command
```

Is there something like this in KDE so that I can run only Open Office Calc with a non-dark theme / color scheme?

---

