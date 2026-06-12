---
title: "Problem adding new applications to the applications menu"
date: 2005-01-22
forum: Desktop Environments
---

### Post by Sophisto on 2005-01-22
When I try to add new applications to the application menu with the "entire menue" -> "add new item to this menu" it does not appear in the menu! 

However, when I runn applications:/// in nautulus can see the extra items I've added!

I have installed amarok via using the hoary repositories.. but the rest is under warty. Can that have had any impact on the problem?

Another quick question: Ive added the debian marillat repositories in synaptic. When downloading software will there be some conflict between the different repositories? Say a program is in the ubuntu databases and also at the marillat ones.. from which do I get it? I suppose it must be better to get it from the ubuntu one..?

Please excuse my lack of knowledge :)

Thanks a lot

---

### Post by Perfect Storm on 2005-01-22
Works fine with me (just tested it), so perhaps some of the package you installed from hoary have something to do with it? I'm not 100% sure, but I suspect it. 


I can only talk for myself, but I've none -so-ever had any problems with debian marillat package.
But if you run into problems you can uninstall them very easy again.



.:=The AI Dude=:.

---

### Post by Dissonance on 2005-01-22
[QUOTE=Artificial Intelligence]Works fine with me (just tested it), so perhaps some of the package you installed from hoary have something to do with it? I'm not 100% sure, but I suspect it. 


I can only talk for myself, but I've none -so-ever had any problems with debian marillat package.
But if you run into problems you can uninstall them very easy again.



.:=The AI Dude=:.[/QUOTE]
 I have this problem a lot. 

For example, Azureus doesn't display.

---

### Post by A-star on 2005-03-31
Same problem here; anyone an idea?

---

### Post by Zwack on 2005-04-03
For me everything worked until I upgraded from Warty to Hoary.  Something seems to have gone wrong at that point.

All I have in the Applications Menu pop-up menu is "Add this launcher to panel" and "entire menu"

Anyone have a clue?

Z.

---

### Post by kassetra on 2005-04-03
[QUOTE=Sophisto]
I have installed amarok via using the hoary repositories.. but the rest is under warty. Can that have had any impact on the problem?[/QUOTE]

Most likely when you installed amarok - you had to upgrade glib?

There is a problem with the hoary and backport versions of glib; it causes the "custom" menu icons you create not to show up.

So far, I know of no way around it in Warty.

---

