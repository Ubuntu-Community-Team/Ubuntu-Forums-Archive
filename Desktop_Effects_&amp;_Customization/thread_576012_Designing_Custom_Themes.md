---
title: "Designing Custom Themes"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by mazur on 2007-10-14
I must not be tickling the internet the right way today, because i can't find what I want.

I am trying to find a way to customize the theme used in Ubuntu Feisty. However, I want more control than is offered by the "theme" wizard. I want to change the "x" in the close box. I want to manually align the text in my window box. I want enough control to actually make design changes for a custom theme outside of changing the color and edge options native to the OS. I want to have a custom login flash screen.

Any direction to that end is much appreciated! :)

---

### Post by palintheus on 2007-10-14
for the custom login screen/splash try gnome-look.org

---

### Post by zdux0012 on 2007-10-18
I  also have been trying to find a way to do this. It seems to be a pretty complicated task. There are lots of widgets that you would have to access. I perfer gnome, so that is what I will target but I have heard that kde is easier to configure in this regard. 
Perhaps you can download a theme and edit it.
Sorry I cannot be of more help. I believe that the communitiy is just not this far yet.

---

### Post by zdux0012 on 2007-10-19
Ok I have slightly more information for you. 
As in 1.1 > 1

Gnome is a window manager. These themes (at least to the degree that I want to edit) are specific to the window manager. Gnome may use one of many window managers. 

See if you are using  metacity by  running  ps aux | grep metacity in a terminal.
If you have more than 2 results (grep will be the second result) then you are using metacity.

btw If you just want a simple theme, you can make one that changes things like the width of a menu. This can be based on the system's default colors. Check out SimpleBox from art.gnome.com and see the xml file. This sort of theme allows you to change less than you probablly want. But it's simple.

---

### Post by zdux0012 on 2007-10-19
It seems every theme is different. For me I want to change the high contrast theme from white on black to green on black. However this color is hard coded. I've found a collection of png files and a xml file that coorespond to the theme I want to change. 
It seems that there is too much freedom with these themes so how each one is implemented can be different. Thus we have difficulty. 
My suggestion is to find a complex theme download it, install it, find it then change it. 
(Also back up before doing it), you can pretty much tar up any directory, so have fun.

---

### Post by sturgman on 2008-02-15
Hello,
   Im no expert but it seems to me that if you want full control of your GNOME theme you should check the following tutorial fromt he GNOME art website:

[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

This is not an easy process and I believe there is no GUI alternative to modify these options. As others have mentioned the easiest thing would be to download a theme and start from there

-s-

---

