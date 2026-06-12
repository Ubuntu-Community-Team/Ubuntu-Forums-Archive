---
title: "gui for wine??"
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by hobieone on 2007-04-17
i was wondering if anyone else that uses wine knows of a graphical interface oone can use use with  wine to make installation of progrms a little easier? instead of through the command line. sometimes i wish it was alittle easier than spending time doing it manually which i do currently.


i do use cedgea also but it seems lately that wine is better and prehaps a bit ahead of cedega in terms of compatibilty and if wine had  or would develope an easy to use interface i think cedega popularity would probably fizzle out. as more people would be more keene to using wine.

---

### Post by alecjw on 2007-04-17
What do you need a GUI for? It's just wine <program name>.exe. It can't really get much easier than that.

---

### Post by Darkdelusions on 2007-04-17
I would have to agree with Alecjw wine <program name>.exe is all that is needed.  Do you run into an issue when tryign to install? What would be the over all need?

---

### Post by christhemonkey on 2007-04-17
Or if wine is associated with .exe files, (i cant remember how or if this is even possible, just seem to remember it worked at some point for me) then you can just double click on the .exe files.

---

### Post by AmyRose on 2007-04-17
Uh, yeah, Wine should be associated with your exe's already and you should just be able to double-click them to run them. Have you even tried that?

---

### Post by chiefwhosm on 2007-04-17
I personally found that in comparison to command prompt wine, double clicking an exe (with wine associated) gave me less succesful results with getting windows programs installing. So I also reccomend just using the console for it (had same thing when I used to be a cedega/winex user and found games usually ran properly if I didn't use their gui).

---

### Post by hobieone on 2007-04-17
it not so much as installing apps i have an issue with. it more trying to have the application  in a shortcut in folder on the destop or in the home folder someplace easy i keep forgetting where to find them. i am somewhat new to using wine. and so far like it better than cedega performance wiseand have gotten more thing to run  on it. also was mainly thinking of as for being easier to customize how the application is run sort of like one would do using cedega interface.

---

### Post by simplyw00x on 2007-04-17
There's wine-doors, if you really want, although it's not developed enough yet to be truly functional. Also, wine creates icons by default. If it doesn't, file a bug.

---

### Post by bastiegast on 2007-04-17
For me it creates Icons pretty randomly. Anyway, a desktop shortcut is easily made. As you probably know wine apps are stored in /home/username/.win/drive_c/Program files, if you want to create a shortcut, rightclick the desktop, click new starter and type in the command field "wine /path/to/executable.exe"

---

### Post by YokoZar on 2007-04-17
> **chiefwhosm said:**
> I personally found that in comparison to command prompt wine, double clicking an exe (with wine associated) gave me less succesful results with getting windows programs installing. So I also reccomend just using the console for it (had same thing when I used to be a cedega/winex user and found games usually ran properly if I didn't use their gui).
This is due to one of two reasons, both of them bugs that are more easily fixed than creating a Wine gui:

1) a bug in nautilus in edgy refuses to run the application (see [http://tuzakey.com/~scott/wine_without_mime.png](http://tuzakey.com/~scott/wine_without_mime.png))
2) a bug in Wine doesn't set the working directory properly when launched.  Many applications expect the current directory to be wherever they reside in.  This is fixable by a patch to Wine (I may get around to it myself very soon), or by running from the terminal.

---

### Post by hobieone on 2007-04-17
> **simplyw00x said:**
> There's wine-doors, if you really want, although it's not developed enough yet to be truly functional. Also, wine creates icons by default. If it doesn't, file a bug.

i think i'll have to bug it then. i'm using edgy atm at the last few version of wine i used both with dapper and edgy have never produced any icons and due to this i never knew that it did and thought it was normal. the ducumention i read at winehq.org never mentions that it suppose to make an icon.

---

### Post by yummy on 2007-04-18
A good web site about wine is (apart the official one):
[HTML]http://frankscorner.org/index.php[/HTML]

You have also a link to WineXS : a gui for Wine

---

### Post by chiefwhosm on 2007-04-18
> is is due to one of two reasons, both of them bugs that are more easily fixed than creating a Wine gui:

1) a bug in nautilus in edgy refuses to run the application (see [http://tuzakey.com/~scott/wine_without_mime.png](http://tuzakey.com/~scott/wine_without_mime.png))
2) a bug in Wine doesn't set the working directory properly when launched. Many applications expect the current directory to be wherever they reside in. This is fixable by a patch to Wine (I may get around to it myself very soon), or by running from the terminal.

Hmm, have to admit it was ages ago, before Ubuntu even exsisted! Always been a KDE user up until ubuntu due to my dislike of gnome (ubuntu changed all that for me) :D 

Just got into the way of console commands from then on, though to be honest I stick with windows and dabble in linux every couple of months (like I plan on tomorrow with 7.04 final coming out :) ).

---

