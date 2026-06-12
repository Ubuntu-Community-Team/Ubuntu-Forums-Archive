---
title: "Increase window resize region"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by jimmy the saint on 2007-10-21
I have a laptop so most of my mouse work is done with a touchpad.  I didn't notice this on problem so much on my old dell under fiesty, It seems that under gutsy though, the window edge regions that you use to resize windows is incredibly small.  This is especially true of the little corner at the bottom.  Is there any way to adjust this in gnome?  Ive looked through the Compiz settings and couldn't find anything.  I would love to either add a larger region at the bottom corner or expand the edge sections a few pixels.

---

### Post by jimmy the saint on 2007-10-23
Is there a way to override the way that windows are drawn to force a resize region similar to the one that appears in some programs, such as Rythmbox and many other gnome apps?

---

### Post by thomas.ene on 2008-02-09
I would like to know if this is possible also. That tiny little resize lower-right corner is just too damn small... and for some reason the default dpi rate of the mouse is not that big making it very easy to skip the resize area if one does not position the mouse over it with really really slow movements - sometimes drawing a closing imaginary spiral with the center in that window corner, Blast :)

---

### Post by nofrendo on 2008-02-23
Bump.

There was a tutorial on how to do this, but for pre-installed themes only. 

I need to know how to use it on a theme with custom window borders

For the people who want to do it on default themes (Human as example):

sudo gedit /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

For the other ones, just go to usr/share/themes and look for the metacity-theme.xml file

Then you edit this part

  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

And change the values to 7-10

The only thing is, custom metacity themes do not appear in this folder...

Help anyone?

---

### Post by allo2u on 2008-05-20
Pressing Alt+F8 will trigger a resize function.
Hope this helps

---

### Post by jolx on 2008-05-20
> **nofrendo said:**
> Bump.

There was a tutorial on how to do this, but for pre-installed themes only. 

I need to know how to use it on a theme with custom window borders

For the people who want to do it on default themes (Human as example):

sudo gedit /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

For the other ones, just go to usr/share/themes and look for the metacity-theme.xml file

Then you edit this part

  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

And change the values to 7-10

The only thing is, custom metacity themes do not appear in this folder...

Help anyone?

custom themes are located in /home/*user*/.themes

---

