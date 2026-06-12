---
title: "How to get application logo at top left corner of windows"
date: 2010-09-17
forum: Desktop Environments
---

### Post by luvshines on 2010-09-17
When I open any application, instead of getting the application logo at the top left corner of the window, what I get is a button which on clicking drops down to provide me couple of options. I am using Ambiance Theme

Can I move those options somewhere else on the top and get back the application logo at its place(which kind of looks smart and helps me differentiate between the applications in open windows faster)

I haven't checked it in KDE but I am using Gnome(default with Ubuntu 10.04). And as far as I remember, when I was using KDE with Fedora 11(a month ago), I used to get the logo

---

### Post by vince2678 on 2010-09-17
Gconf-editor:-

Key name: /apps/metacity/general/button_layout

Key owner: metacity

Short Description: Arrangement of buttons on the titlebar

[CENTER]Long Description: Duplicate buttons are not allowed. Unknown button names are silently ignored so that buttons can be added in future metacity versions without breaking older versions. A special spacer tag can be used to insert some space between two adjacent buttons. 

[LEFT]for example : **menu::maximize,minimize,close**
means that the icon+menu (they will always be that way) is at the left, nothing in the middle and the maximize,minimize and close buttons on the right.[/LEFT]
[/CENTER]

---

### Post by luvshines on 2010-09-18
Ok, if I can't move it anywhere at the top, can't I move menu to the right and get application logo on the left ??

---

### Post by luvshines on 2010-09-18
Maybe I am not able to make myself clear
I have attached a screen shot for left corner of the window opened for Mozilla firefox
Instead of getting the Firefox orange-blue logo in the left, what I see is menu button
Can't I get the logo to be displayed there ?

---

### Post by luvshines on 2010-10-02
Bump !!

---

### Post by 101011010010 on 2010-10-09
Hello.
I've been looking into this as well. Some of the default themes put an icon in place of the menu button, Dust-Sand, Clearlooks and New Wave, for example. If you want to change a theme to show icons instead of the menu button, you have to edit the xml file in:```
/user/share/themes/What-ever-theme/metacity/
```If you don't like any of the default themes, there are numerous ones out there to try. Hopefully you'll find one that you like.
(To change themes go to System/Preferences/Appearance/Theme).

Some extra themes:[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by luvshines on 2010-10-10
Whoopie !!

Thanks bud, you have made my day.

I looked into the New Wave xml file, copied the parts relevant to me and changed Ambiance xml file, /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml:
```

<draw_ops name="menu_button_icon">
<icon  x="(width-mini_icon_width)/2-2" y="(height-mini_icon_height)/2+1" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

<!-- Button Overlays -->
<draw_ops name="menu_focused_normal">
<[COLOR="Blue"]!--image filename="menu.png" x="0" y="1" width="object_width" height="object_height"/--[/COLOR]>
<include name="menu_button_icon"/>
</draw_ops>
<draw_ops name="menu_focused_prelight">
<[COLOR="blue"]!--image filename="menu_prelight.png" x="0" y="1" width="object_width" height="object_height"/--[/COLOR]>
<include name="menu_button_icon"/>
</draw_ops>
<draw_ops name="menu_unfocused_normal">
<[COLOR="Blue"]!--image filename="menu.png" x="0" y="1" width="object_width" height="object_height"/--[/COLOR]>
<include name="menu_button_icon"/>
</draw_ops>
<draw_ops name="menu_unfocused_prelight">
<[COLOR="blue"]!--image filename="menu_prelight.png" x="0" y="1" width="object_width" height="object_height"/--[/COLOR]>
<include name="menu_button_icon"/>
</draw_ops>

```

I commented out the [COLOR="blue"]BLUE[/COLOR] parts, which were overriding the default logos, added "menu_button_icon" thing instead and it worked. And to add to the pleasure, the application icon now works as the menu ;)

Really happy to mark it SOLVED :guitar:. Attaching a screenshot for new look

---

### Post by 101011010010 on 2010-10-10
Sweet!!!!
Well done, nice job. That's exactly the look that I was hoping for.
Thanks for posting the info, I'll try in a little bit. :popcorn:
Noticed that you updated the info, so I decided to try it and it worked perfectly. Thank you.:)

---

### Post by 101011010010 on 2010-10-11
Hello again.
I spoke too soon. On the theme I'm using, some of the bigger icons have the left side chopped off. 
So I changed the size of the icon (in line 2 of the above code). 
From
> x="(width-mini_icon_width)/2-2" y="(height-mini_icon_height)/2+1"To
> x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" (The same as Clearlooks).Now everything seems to look spot on. :)
A.

---

