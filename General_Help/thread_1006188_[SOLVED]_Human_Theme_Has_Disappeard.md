---
title: "[SOLVED] Human Theme Has Disappeard"
date: 2008-12-09
forum: General Help
---

### Post by jdorenbush on 2008-12-09
My Human and Human-Clearlooks themes have disappeared.

I still see Human in 'Controls' and in 'Icons', but that is it. It isn't in the main 'Theme' window or the 'Window Borders' section.

---

### Post by eternalnewbee on 2008-12-09
My Human and Human-Clearlooks themes have disappeared.

I still see Human in 'Controls' and in 'Icons', but that is it. It isn't in the main 'Theme' window or the 'Window Borders' section.
Hi there.
What did you do before they diappeared?

---

### Post by jdorenbush on 2008-12-09
> **eternalnewbee said:**
> Hi there.
What did you do before they diappeared?

I was screwing around with a [broken package problem I have]("http://ubuntuforums.org/showthread.php?t=1006183").

---

### Post by jdorenbush on 2008-12-10
Above problem with packages ^ has been solved.

Still missing Human and Human-Clearlooks. Also just noticed DarkRoom is gone as well.

Solved by installed theme from [Ubuntu Packages]("http://packages.ubuntu.com/intrepid-updates/human-theme").

---

### Post by Ivo Moelans on 2008-12-10
Did you (try to) install the Blubuntu theme before you lost the others?

---

### Post by jdorenbush on 2008-12-10
> **Ivo Moelans said:**
> Did you (try to) install the Blubuntu theme before you lost the others?

I don't remember. I have been having problems with missing gtk2 engines and such when trying to install 3rd party themes. I may have accidentally installed something that removed Human theme.

I just reinstalled Human theme from [Ubuntu Package website]("http://packages.ubuntu.com/intrepid-updates/human-theme"). That fixed the problem with the missing theme, however...

What do you make of this problem:

After installing Elementary theme, in the Appearance Preferences > Theme window 'elementary' displays with a big ? over the thumbnail of the theme.

When I try to select it says, "This theme will not look as intended because the required GTK+ theme 'eGTK_0.4.2e' is not installed." The file I downloaded from [Elementary website]("http://www.elementary-project.com/") is eGTK_0.4.3, not 0.4.2e.

---

### Post by Ivo Moelans on 2008-12-10
The author forgot to update the index.theme. In the theme's directory is a file *elementary* which can be opened with Text Editor with superuser privileges (terminal: sudo gedit).
Line 9 reads

```
GtkTheme=eGTK_0.4.**2e**
```

but should read

```
GtkTheme=eGTK_0.4.**3**
```

The big ? is there because the same file says there should be a metacity theme

```
MetacityTheme=Elementary_Metacity_0.4e
```

But you probably don't have that and neither is there a Metacity included. But you could exchange *Elementary_Metacity_0.4e* with another Metacity theme, e.g. *Human*, that you know is on your system.

Or... you could download Metacity from the site, choose one, black or white and put the *metacity-1* directory in the theme's directory (/home/<username>/.themes/eGTK_0.4.3) and change the appropriate line to

```
MetacityTheme=eGTK_0.4.3
```

---

### Post by jdorenbush on 2008-12-10
Perfect. That fixed the problem. Thanks!

For anyone else wondering, in order to fix the gtk, metacity, and icon set the index.theme file called *elementary* should look like this:

```
GtkTheme=eGTK_0.4.3
MetacityTheme=Elementary_Metacity_White_0.7.2
IconTheme=Elementary_1.9.6.7.2
```

---

