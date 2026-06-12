---
title: "[SOLVED] GTK and menu bars."
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by 3ark on 2007-08-21
I couldn't find a thread that dealt with this. I am running the imetal theme currently but have noticed this on quite a few themes. I want to have translucent panels as I love the look of them. But with some themes such as the excellent imetal the menu bar in the top left (App, Places System) wont go translucent, it still has this nasty grey in the background and it sticks out like a sore thumb. I have tried to change a few things in an rc file and whenever i lose the background of that menu it also messes up the menus in my open windows. I'm kinda lost with the code for these themes but with some instructions I feel I could "get er' done". Any help would be greatly appreciated.

My current them can be found here.
[http://www.gnome-look.org/content/show.php/imetal?content=63734](http://www.gnome-look.org/content/show.php/imetal?content=63734)
Its the gradient one.

---

### Post by Lord Illidan on 2007-08-21
What you could do is make a transparent png with GIMP and set it as the background for your menu bar.

---

### Post by 3ark on 2007-08-21
Would that not effect the menu of my open windows? It seems now that whenever I change something for one it also effects the other. Keep in mind I have no idea what I'm actually doing with these RC files, just trial and error really. :P  It's amazing how addictive changing your desktop can be...

---

### Post by SkiesOfAzel on 2007-08-21
First of all, thank you for the kind words about my theme, i am glad you like it :) .

  As i am a macmenu user, i didn't notice this strange behaviour ...
 Anyway , here is the fix ;)

Go to line 1323 of gtkrc and paste this
```
  	engine "pixmap"
	{

		image
		{
			function	= BOX
			file		= "Panel/panel-bg.png"
			border	= { 0, 0, 0, 0 }
			stretch	= FALSE
    		}


 	} 
```
 Please , next time post your problem in the comments section on gnome-look or deviant-art. It's hard to improve something when there is no feedback.

[EDIT]
I updated the theme with the fix.

---

### Post by 3ark on 2007-08-24
I will comment on gnome-look in the future. Thanks for the help guys! And thanks for making an awesome theme, definitely my favorite so far.

---

