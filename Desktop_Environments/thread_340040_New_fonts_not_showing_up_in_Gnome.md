---
title: "New fonts not showing up in Gnome"
date: 2007-01-16
forum: Desktop Environments
---

### Post by ptader on 2007-01-16
I've installed some [SGI ]("http://www.linuxscope.com:/~ptader/files/sgi-fonts-1.0-749.noarch.rpm")fonts from another RPM-based linux disto (SuSe) after converting the RPM package with alien.  They installed in /usr/share/fonts/misc/sgi.  After trying all the tricks I could find (detailed below) I still cannot get them to show up in the Gnome "Font Preferences" dialog box.

What I've tried so far (not really in this order)

[LIST]
[*]Added the new directory to /etc/X11/xorg.conf
[*]Restarted gdm, rebooted, logged in/out
[*]Ran 'sudo fc-cache -fv' 
[*]Using Natutilus, opened "fonts:///" and copied the new fonts to that directory.  (re-ran 'fc-cache -fv ~/.fonts''
[*]Started an xterm with the font switch "-fn <sgi-font-name>" and the font was used.
[*]/var/log/Xorg.0.log doesn't complain about the new fonts.
[/LIST]

The fonts do show up with ```
xlsfonts | grep -i sgi
...
-sgi-screen-medium-r-normal--8-80-72-72-m-60-iso8859-1
-sgi-screen-medium-r-normal--9-90-72-72-m-60--ascii
-sgi-screen-medium-r-normal--9-90-72-72-m-60-iso8859-1
...
```

whereas before the install, they didn't.  I gotta believe that since I got this far already, I'm really close.

Thanks,
ptader

---

### Post by ComplexNumber on 2007-01-16
if all else fails, get the fonts and store them in /home/<your-username>/.fonts.

---

### Post by ptader on 2007-01-17
Yup, tried that too.  No-go.

---

