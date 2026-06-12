---
title: "Description of the fields in kate schema files"
date: 2011-10-16
forum: Desktop Environments
---

### Post by chandra on 2011-10-16
I am trying to improve the schema and syntax highlighting available in kile which is based in part on kate.

I have come across various schema and syntax highlighting files and wish to know what, for example, the comma-separated values on the last line for the font in the Dark Oxygen schema by Riccardo Metere stand for:

```
[DarkOxygen]
Color Background=50,50,50
Color Highlighted Bracket=90,0,179
Color Highlighted Line=46,52,54
Color Icon Bar=136,136,136
Color Line Number=50,50,50
Color MarkType1=0,0,255
Color MarkType2=255,0,0
Color MarkType3=227,173,0
Color MarkType4=255,0,191
Color MarkType5=187,187,187
Color MarkType6=0,140,0
Color MarkType7=255,0,0
Color Selection=0,72,77
Color Spelling Mistake Line=255,0,0
Color Tab Marker=85,85,85
Color Template Background=187,187,187
Color Template Editable Placeholder=216,232,194
Color Template Focused Editable Placeholder=177,210,143
Color Template Not Editable Placeholder=255,204,204
Color Word Wrap Marker=85,87,83
Font=Monospace,10,-1,5,50,0,0,0,0,0
```

I trust the other values are rgb settings.

The corresponding section on LaTeX syntax highlighting file is:

```
[Highlighting LaTeX - Schema DarkOxygen]
LaTeX:Alert=10,,,,,,,,,,---
LaTeX:Ampersand=0,fff082b0,fff082b0,1,,,,,,,---
LaTeX:Bullet=0,fff082b0,fff082b0,1,,,,,,,---
LaTeX:Column Separator=0,fff082b0,fff082b0,,,,,,,,---
LaTeX:Comment=8,,,,,,,,,,---
LaTeX:Environment=0,ffffd500,ffffd500,0,0,,,,,,---
LaTeX:Error=10,,,,,,,,,,---
LaTeX:Keyword=0,ffffeb55,ffffeb55,1,0,,,,,,---
LaTeX:Keyword Mathmode=0,ff99dcc6,ff99dcc6,1,0,,,,,,---
LaTeX:Math=0,ff00cc88,ff00cc88,0,0,,,,,,---
LaTeX:Normal Text=0,,,,,,,,,,---
LaTeX:Region Marker=12,,,,,,,,,,---
LaTeX:Structure=0,fff29b68,fff29b68,1,0,,,,,,---
LaTeX:Structure Keyword=0,fff29b68,fff29b68,1,0,,,,,,---
LaTeX:Structure Keyword Mathmode=0,ffb1d28f,ffb1d28f,1,0,,,,,,---
LaTeX:Structure Math=0,ff77b753,ff77b753,0,0,,,,,,---
LaTeX:Structure Text=0,fff29b68,fff29b68,0,0,,,,,,---
LaTeX:Verbatim=0,ff00c4cc,ff00c4cc,0,0,,,,,,---

```

Again, what do the RHS fields stand for?

Thanks in advance.

---

### Post by norok2 on 2011-10-16
Hi there,

I don't exactly now what RHS values really stand for. However Kate
offer a handy way to set up a syntax highlighting profile through menu
Settings / Configure Kate / Fonts & Colors / Highlighting Text Styles.
You could eventually get to know what those values stands for.
Alternatively you should really ask a kate developer. Hope my answer
will be helpful.

---

