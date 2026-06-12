---
title: "xfce panel clock config"
date: 2009-02-20
forum: Desktop Environments
---

### Post by fisherm on 2009-02-20
So I'm toying with XFCE now...I like it, but I want to customize my clock in the panel. In GNOME I went to the gconf editor and under apps>panel>clock something I could enter a custom format (and include code to make the clock text **BOLD**. Anybody know a way to do that in XFCE. I found a file (.config/xfce4/panel/clock-5.rc) that looked somewhat promising, but I couldn't figure anything out. Thanks in advance.

---

### Post by fisherm on 2009-02-22
Not a total fix but I'm happier. I used the "xfce4-datetime-plugin" instead of the regular panel clock. It allowed me to make the time bold, and have the date available. I just wish it would let me have the date next to the time...instead of above it. But hey, I'm smiling...

---

### Post by danillo on 2009-02-23
You could try adding Orage Clock to the panel. It's very customizeable and it's easy to make it look like you describe.

---

### Post by god=none on 2009-12-18
You can change the xubuntu default clock format.  Just left-click the clock, select 'properties' and select what you want. If you want to use the Custom Clock Options, the formats are in the 'date' manpage (type >man date) in a terminal window, look in the format section. Just enter the format that you like in the 'Clock Options' text box such as:

%c

or 

%a%m%d%H%M

Fix it up however you like according to the format specifications in the 'data' manpage.

---

