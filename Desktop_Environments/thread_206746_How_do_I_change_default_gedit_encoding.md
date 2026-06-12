---
title: "How do I change *default* gedit encoding?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by xp_newbie on 2006-06-30
I know about the command line option --encoding for gedit, but I would like to be able to continue invoking gedit from nautilus - with encoding different than what was installed. 

How do I do that?

Thanks!
Alex

---

### Post by atoponce on 2006-06-30
[quote=xp_newbie]I know about the command line option --encoding for gedit, but I would like to be able to continue invoking gedit from nautilus - with encoding different than what was installed. 

How do I do that?

Thanks!
Alex[/quote]

How are you launching GEdit?  You can access the properties of the icon, if that is what you are using, and add the --encoding option to the command.

---

### Post by xp_newbie on 2006-06-30
[QUOTE=atoponce]How are you launching GEdit?  You can access the properties of the icon, if that is what you are using, and add the --encoding option to the command.[/QUOTE]

I do what I used to do in Windows: I double-click the text document. I rarely invoke gedit from the menu & then open the file.

Is there some parameter I can change in the way .txt files are associated with gedit, so that I can change the encoding parameter?

Thanks!
Alex

---

### Post by xp_newbie on 2006-06-30
OK, I solved the problem:

1. I right-clicked the .txt file and selected "Properties".
2. Selected the "Open With" tab.
3. Clicked the Add button 
4. Added "gedit --encoding=iso-8859-2

Works great. :)

---

### Post by atoponce on 2006-06-30
[quote=xp_newbie]OK, I solved the problem:

1. I right-clicked the .txt file and selected "Properties".
2. Selected the "Open With" tab.
3. Clicked the Add button 
4. Added "gedit --encoding=iso-8859-2

Works great. :)[/quote]

Glad you got it working!

---

### Post by str1der on 2008-04-15
It does not work for me :( 

I have nautilus 2.20.0

When I select the new gedit option I created it doesnt accept it and it defaults to open the file with firefox :(

---

