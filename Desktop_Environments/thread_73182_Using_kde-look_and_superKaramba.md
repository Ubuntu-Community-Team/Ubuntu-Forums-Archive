---
title: "Using kde-look and superKaramba"
date: 2005-10-08
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-08
I have this prog downloaded and in use..kinda.
I went to kde-look .org and found a tone of things i would like.. Some themes some icons apps, alot....
But i have no idea how to use them..
Its easy enough when its just the included ones in SK....But when you DL them I dont know what to do with the files????
They are tar.gz files..?
Can someone point me to a tutorial...

thanx

---

### Post by stoeptegel on 2005-10-08
You can just fire up karamba and use the 'load theme' or similar link.

---

### Post by floyd27 on 2005-10-08
What if its not a SK theme??
Some are icons and other things that are not related to that app..?

---

### Post by N6546R on 2005-10-08
[QUOTE=floyd27]What if its not a SK theme??
Some are icons and other things that are not related to that app..?[/QUOTE]

Packages on kde-look and kde-apps usually have a 'How To Install' link, look over to the right-hand side of the page.

For things like icons or themes you can use the Control Center to select and install the files.

Perry

---

### Post by floyd27 on 2005-10-08
I have tried to install things and i have had no luck..
Can someone please tell me how..
If i can get 1 to work i will be able to do the rest myself..
thanx

---

### Post by Omnios on 2005-10-08
[URL: Super Karumba How to Script page]("http://netdragon.sourceforge.net/sinfo.html")

 Basicly with Kuramba aand Super Kuramba you download  the tar.gz and unzip it into a File  you create to hold all your Karumba themes. Then run Kuramba/Super Kuramba and chose the file you want to run xxxxx.theme.

 A few tricks  you may have to modify the file to work with your systems. 

 In run terminal and type sensors the  out put will be what your system is using ex mine  uses  M/B for  mother board temp which is different from what most of the apps  use. Now right click the Kurumba app and chose edit / edit theme. Now you will have to go through the theme file and find what you have to change which is usualy in <group> sections. What you are looking for starts with sensor=sensor type=#### the type part is what you are looking for to change and there is usualy a few entrys  pertainging to Text/Bar/Graph entrys. The same holds   true for network where you haave ppp0 and eth0 where you maay have to change the type pertaing to what your net is set up as. I would recomend reading the Super Karambe creation page "Link Above" to understand more of how it works.

---

### Post by floyd27 on 2005-10-08
thanx for that..
I hate to bother you again but...
o.K I am trying to get a mac osx dock..Its there but do i use SK for that too..?
Does EVERYTHING on kde-look use SK...Or are some able to be used on there own?
How do you know?
sorry but im lost at this point...

---

### Post by Omnios on 2005-10-08
Think basicly anything Super Kuramba need  SK to run. Nice part of it is if you set it up and save your sesion it will load with KDE. I think SK apps with buttons such as icons use  python   scripting to work so I  would check how  much a load a bar puts on yoru system. 

 Most of the basics I learnt from reading the web site and reading a lot of theme  files to see thinks in application. I started learning about a week ago and have already created two apps, its rather simple.

---

### Post by floyd27 on 2005-10-08
So, if i download ANYTHING off kde-look it will open in SK...no question........

Every app,theme,skin,icon uses SK to work...?

---

### Post by Omnios on 2005-10-08
Oh didn't 100% undersand

 Anything under (listed as)  Kuramba, Super Kuramba, should be able run from Super Kuramba be it a sensor or a bar weather app. Things  under different sections will not as  far as I know. Super Kuramba and Kuramba have there own scripts to access sensors and layout the graphs sensors etc which  reqquire the Kuramba/Super Kuramba program. Also there are apps that need certain higher versions thaan those available on synaptic and will not run on the one available in synaaptic

 If it isnt listed as Karumba or Super Kuramba it will not work.

---

