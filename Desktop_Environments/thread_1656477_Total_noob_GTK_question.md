---
title: "Total noob GTK question"
date: 2010-12-30
forum: Desktop Environments
---

### Post by Kalimol on 2010-12-30
Okay, so I downloaded this gorgeous theme, [LaGaDesk N-12]("http://gnome-look.org/content/show.php/LaGaDesk-N12-GTK+Collection?content=136036"), and I wanted to tweak it slightly to make the windows a bit darker, more of a charcoal than an industrial gray.

The application background can be controlled by a pixmap, which is where it gets that sort of scuffed texture in the application backgrounds (something I added,) and all of the usual color controls in Appearance settings work, but I can't find anything in the gtkrc file that will let me change the window frame, title bar, and menubar, which seem to refer to the Clearlooks engine.

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Question.png[/IMG]

Anyone who understands GTK willing to put this in little words for me? = )

---

### Post by vashminted on 2010-12-31
ook....im not an expert, and i'm not even sure if i understand your question very well....but i think "gnome-color-chooser" is what you're looking for, it allows you to change the color of almost everything, background, letters, butons, entry boxes, scrollbars, etc...

you really should give it a try
it can be installed directly from synaptic

hope it helps you;)

---

### Post by Kalimol on 2010-12-31
Sorry, I guess my question was a bit oddly phrased. I'm just trying to understand the very-very-basics of tweaking GTK2 themes. I'll try that app - thanks!

---

### Post by 101011010010 on 2010-12-31
Hello.
The window borders etc are set using an xml file in the Metacity-1 folder of most themes. 
If there isn't a Metacity-1 folder it usually means that the theme uses one from another theme. 
I.E. If you look in the theme, if it has no Metacity-1 folder, open the "index.theme" file,  
you will see that near the bottom it says "MetacityTheme=????????". 
Have a look at this link it should help.

[http://library.gnome.org/devel/creating-metacity-themes/2.30/sec-introduction.html.en](http://library.gnome.org/devel/creating-metacity-themes/2.30/sec-introduction.html.en)

I hope this helps.

---

### Post by Kalimol on 2010-12-31
Excellent - thanks! And there is a Metacity folder in there. I'll check that out, then!

Edit - It worked. Thanks!

---

