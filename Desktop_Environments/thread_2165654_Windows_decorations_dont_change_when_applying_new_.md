---
title: "Windows decorations dont change when applying new GTK theme"
date: 2013-08-05
forum: Desktop Environments
---

### Post by relink2013 on 2013-08-05
I am trying out some new themes, but I'm running into an issue. I'm using gnome tweak tool to change my themes, but for many of my themes the window decorations will not change, but for some they will. For example when I set the theme to "greybird" everything works as it should, but if I try to use the "faience" or "Lion" themes, everything will change except the window decorations. 

I had this problem once before on 12.10 but I do not remember exactly how I solved it. I just remember adding a line to a hidden file in my home directory I believe. I am using Unity by the way. 

Here are links the the themes I mentioned:
[http://www.deviantart.com/art/Lion-GTK-3-8-386686956](http://www.deviantart.com/art/Lion-GTK-3-8-386686956)
[http://tiheum.deviantart.com/art/GTK3-Gnome-Shell-Faience-255097456](http://tiheum.deviantart.com/art/GTK3-Gnome-Shell-Faience-255097456)
grey bird is in the Ubuntu repos under shimmer.

---

### Post by Frogs Hair on 2013-08-05
Hello and Welcome 

What Ubuntu release ? The Lion theme is for Gnome 3.8 so , the title bar theme may not work in Gnome 3.6 . The second linked  theme should work in 12.10 or 13.04. I see Faience includes a gnome shell theme which you may know that won't work in Unity, but title bar and GTK theme should work .

---

### Post by relink2013 on 2013-08-06
Oh sorry, it's Ubuntu 13.04 64bit. I know the shell themes wont work, im just trying to use the GTK themes. I linked to a few screenshots that show the problem.

You can see in this screenshot that the window decorations did not change with the theme.
[http://s13.postimg.org/xrijhx8h3/Screenshot_from_2013_08_06_08_40_26.png](http://s13.postimg.org/xrijhx8h3/Screenshot_from_2013_08_06_08_40_26.png) 

But in this one, which is MediterraneanWHITE, works just fine. 
 [http://s24.postimg.org/gnub4ffr9/Screenshot_from_2013_08_06_08_40_56.png](http://s24.postimg.org/gnub4ffr9/Screenshot_from_2013_08_06_08_40_56.png)

Faience is the theme I really want to get working.

---

### Post by Frogs Hair on 2013-08-06
I have the same problem with Faience (13.04) , but not with the Claire and Ocre  variants. Strangely enough the Faience-mod title-bar works fine with the theme . [http://gnome-look.org/content/show.php/Faience-mod?content=157950](http://gnome-look.org/content/show.php/Faience-mod?content=157950)

I can't help with the hidden folder without more information. Some people keep their themes home/.themes , but I use usr/share/themes. There may be something in .config that triggers your memory.

---

### Post by relink2013 on 2013-08-06
Problem solved!!

Here is a link to the original page.
[http://askubuntu.com/questions/230845/faience-theme-12-10](http://askubuntu.com/questions/230845/faience-theme-12-10)

and here is how to fix it, this fix is specifically for the Faience theme, but I bet it would work for other themes as well. 

[COLOR=#333333][FONT=UbuntuRegular]A comment on the [/FONT][/COLOR][deviantART theme page]("http://tiheum.deviantart.com/art/GTK3-Gnome-Shell-Faience-255097456?")[COLOR=#333333][FONT=UbuntuRegular] explains how to fix this. It appears to be caused by the file[/FONT][/COLOR]metacity-1/metacity-theme-2.xml[COLOR=#333333][FONT=UbuntuRegular]. You can either remove it or rename it:
[/FONT][/COLOR]
 > [FONT=Ubuntu Mono]cd /usr/share/themes/Faience/metacity-1 # Or ~/.themes/Faience/metacity-1 if you installed it by hand[/FONT] sudo mv metacity-theme-2.xml metacity-theme-2.xml-OLD

---

