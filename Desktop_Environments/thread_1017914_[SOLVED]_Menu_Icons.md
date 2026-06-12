---
title: "[SOLVED] Menu Icons"
date: 2008-12-21
forum: Desktop Environments
---

### Post by bovinomu on 2008-12-21
Hi everyone!
Can i change the size of the icons in the principal menu of ubuntu?

thanks all and sorry for the bad english! =)

---

### Post by 73ckn797 on 2008-12-22
> **bovinomu said:**
> Hi everyone!
Can i change the size of the icons in the principal menu of ubuntu?

thanks all and sorry for the bad english! =)

I know you can right click on desktop icons and resize them but I am not sure about on the menus. Do you mean the upper and lower task bar icons? You can change the height of those and the icons will grow proportionately.

---

### Post by Vantrax on 2008-12-22
Depending on what you mean you can right click on a panel and click properties then change the height of the panel. The icons will grow to match.

---

### Post by 73ckn797 on 2008-12-22
> **Vantrax said:**
> Depending on what you mean you can right click on a panel and click properties then change the height of the panel. The icons will grow to match.


That was what I said but I typed in "to" instead of "the" in my comment.

---

### Post by jay li on 2008-12-22
What ubuntu version and theme do you have?

---

### Post by bovinomu on 2008-12-22
Well, i'm using the intrepid ibex. and i dont want to resize the panels. i want to resize the icons in the principal menu... 

And thanks for all the replys, folks! i realy apreciate the support!

(sry for the bad english again)

---

### Post by jay li on 2008-12-22
Great! you just answered  my first question.  
Now, how about to give an answer for second question? 
- What theme do you use in ubuntu? 
- Is it "Human" or something else? 

and by the way your English is just fine as much as mine, so don't feel to be sorry for that.

---

### Post by bovinomu on 2008-12-23
Sorry for that... my bad.

Well, i'm not using the human theme. i made a mix with a lot of other themes.

Controls = Dust
Window borders = MythUbuntu
Icons = Mac4Lin_Icons_V0.4
Cursors = DMZ Black

Some of these themes came with the script "Ubuntu Perfeito"
[http://hamacker.wordpress.com/ubuntu-perfeito-versao-804/](http://hamacker.wordpress.com/ubuntu-perfeito-versao-804/)

Thaks for the reply!

---

### Post by jay li on 2008-12-23
Check if you have on this path the "Dust theme"
- usr/share/themes/[COLOR="Red"]_***Dust***_[/COLOR]/gtk-2.0/gtkrc

---

### Post by bovinomu on 2008-12-23
Yep!

I have this path...

hehehe... there's a huge configuration file in there... =)

---

### Post by jay li on 2008-12-23
Open termianl and type 
- sudo gedit /usr/share/themes/Dust/gtk-2.0/gtkrc2
- type your password
- In line 12, you should find the option: "[COLOR="DarkRed"]_**gtk-icon-sizes = panel-menu=[U]24,24_**[/U][/COLOR]" 
- Change it to: [COLOR="DarkRed"]_**gtk-icon-sizes = panel-menu=[U][B]14,14**_[/B][/U][/COLOR]

Save & exit.

---

### Post by bovinomu on 2008-12-23
I maded it and restarted the theme. It works well. 

Thanks again for the tips!

---

