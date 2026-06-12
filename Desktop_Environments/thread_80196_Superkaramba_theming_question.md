---
title: "Superkaramba theming question"
date: 2005-10-21
forum: Desktop Environments
---

### Post by Navyblue on 2005-10-21
Hi all,

How do I make clock appear in 12 hour mode?

How do I make a text appear in bold.

Is there a how-to on theming Superkaramba other than the one on the Superkaramba site?

Thanks. :)

---

### Post by raggamuffin on 2005-10-21
Which theme exactly are you using?...there's probably dozens of different SK clock themes...Some themes have an "Configure Theme" options available...and for some, you'd have to manually edit the theme script...

kde-look.org is a great site for finding plenty of superkaramba themes...

---

### Post by SGC on 2005-10-21
[QUOTE=Navyblue]How do I make clock appear in 12 hour mode?[/QUOTE]
Add **ap** to the format string, which will be replaced by am or pm.

```
text x=0  y=0 sensor=time format="hh:mm ap"  color=255,255,200  fontsize=175
```
 
If you don't want to show the am/pm add two or three tabs before the ap
```
format="hh:mm                                   ap"
```

[QUOTE=Navyblue]How do I make a text appear in bold.[/QUOTE]
I'm not sure, but it seems that there is no way to make a bold text in superkaramba

---

### Post by Navyblue on 2005-10-22
[QUOTE=raggamuffin]Which theme exactly are you using?...there's probably dozens of different SK clock themes...Some themes have an "Configure Theme" options available...and for some, you'd have to manually edit the theme script...

kde-look.org is a great site for finding plenty of superkaramba themes...[/QUOTE]

I am using "sysinfo" theme as the skeleton and modifying it to my own taste, weird but somehow, I couldn't find a theme that shows in 12 hour mode there. :confused:

---

### Post by Navyblue on 2005-10-22
[QUOTE=SGC]Add **ap** to the format string, which will be replaced by am or pm.

```
text x=0  y=0 sensor=time format="hh:mm ap"  color=255,255,200  fontsize=175
```
 
If you don't want to show the am/pm add two or three tabs before the ap
```
format="hh:mm                                   ap"
```


I'm not sure, but it seems that there is no way to make a bold text in superkaramba[/QUOTE]

Thanks, that does it. :)

For the bolding, I googled for it and I think I get something like enveloping the text with "*", for example *Good Morning!*, but that doesn't work. :???:

---

