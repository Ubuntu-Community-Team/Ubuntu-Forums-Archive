---
title: "all menus and dialog boxes completely black in Lyx"
date: 2007-07-09
forum: Education &amp; Science
---

### Post by dannemil on 2007-07-09
I feel really stupid. I am using lyx-xforms in Ubuntu Feisty. When I went to the dialog boxes that allow me to choose the bibliography file or the bibliography style, the text was invisible, so the current file or a new file that I choose would be invisible. No good. In an attempt to get some visible text, I tried to change the Lyx preferences, colors, GUI background and GUI text, but inadvertently set the background to black. Now all of the menus everywhere in Lyx are invisible - completely black. Lyx-xforms is now unusable. I can use Lyx-qt, but I really like Lyx-xforms better. I tried uninstalling and reinstalling Lyx-xforms, but the preferences must persist because everything is still black.

Any ideas where these preferences live or how to go about getting a working version of Lyx-xforms with menus that I can once again see? After I get that, does anyone know whey I would get invisible text in the dialog boxes for choosing the bibliography files (the oroiginal problem that led to the secondary problem)?

Thanks,
Jim

{problem solved as follows: 

exit lyx-xforms
>cp ~/.lyx/preferences.xform ~/.lyx/preferences.xform.old
>rm ~.lyx/preferences.xform 
restart lyx-xforms
}

---

