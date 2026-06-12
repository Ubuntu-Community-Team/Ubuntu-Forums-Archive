---
title: "[SOLVED] Icon customizing"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by petit.padavoine on 2007-08-11
I installed an icon pack but I'd like to modify the icon for the terminal.

My icon pack is located in ~/.icons/<nameoficonpack>.

I replaced ~/.icons/<nameoficonpack>/scalable/apps/terminal.svg,
           ~/.icons/<nameoficonpack>/scalable/apps/gnome-terminal.svg, and
           ~/.icons/<nameoficonpack>/scalable/apps/utilities-terminal.svg with the icon I want, but none of it changed anything.

What should I replace?

Another question, how do I know / decide whether Ubuntu is using the .png icons or the .svg icons?

---

### Post by petit.padavoine on 2007-08-11
Bump.

---

### Post by petit.padavoine on 2007-08-11
Bump.

I looked at how it works with the Human icon theme.

Human inherits the terminal icon from the Tango icon theme

```

username@hostname:/usr/share/icons/Human$ head index.theme
[Icon Theme]
Name=Humant
Comment=Ubuntu default theme
Comment[fr]=Thème par défaut d'Ubuntu
Comment[it]=Tema di Ubuntu predefinito
Comment[pt_BR]=Tema padrão do Ubuntu
Inherits=Tangerine,Tango,gnome
Example=x-directory-normal

# Directory list
username@hostname

```

I looked at the Tango icon theme, and saw what terminal icons it had:
```

username@hostname:/usr/share/icons/Tango/scalable/apps$ ls *terminal*
gnome-terminal.svg  terminal.svg  utilities-terminal.svg  xfce-terminal.svg
username@hostname:/usr/share/icons/Tango/scalable/apps$ 

```

I put four copies of the icon I want for the Terminal in my theme's folder:
```

username@hostname:~/.icons/Neu/scalable/apps$ls *terminal*
gnome-terminal.svg  terminal.svg  utilities-terminal.svg  xfce-terminal.svg
username@hostname:~/.icons/Neu/scalable/apps$

```

I still see the old icon everywhere...

What can I do?

---

### Post by petit.padavoine on 2007-08-15
Okay it was using the .png icons. I just got rid of all the .png stuff and removed it from index.theme. Works like a charm.

---

