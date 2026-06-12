---
title: "Keyboard language(layout)"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Pana_Ruplahlava on 2008-08-09
Hello :)
I have a problem, i just migrated from windows, and i can't find out how to switch keyboard language (layout) like it is in Win - ALT+SHIFT...
Is there only one possibility by using mouse?!?!?
Thanx :)

Ps. Sorry about my english :)

---

### Post by Rhubarb on 2008-08-09
Make sure you've got the keyboard layouts you require in System --> Preferences --> Keyboard.  You can add multiple layouts there.


**By mouse (the best and easiest option for you):**
Right click on an empty part of the panel (the bar at the top of the screen), select "**Add to Panel...**".
Select "**Keyboard Indicator**", then press the **+Add** button.
Then all you have to do is to click on the indicator to change your keyboard layout.


**By keyboard:**
Press **Alt + F2**, type this in for US english layout:
```
setxkbmap us
```
This will work for your current session, until you logout.


**To permanently change the default keyboard layout:**
```
sudo dpkg-reconfigure console-setup
```
(You can change it back by running this command again if you wish).

---

### Post by Pana_Ruplahlava on 2008-08-09
Well, i have this shortcut on a panel, but in windows is possibility to change it using keybord shortcut... While i'm pressing alt+shift, my keyboard layout changes to 'en' and then doing it again back to 'CS'...
Is in ubuntu something like this? :)
Thanx :)

---

### Post by jesuisbenjamin on 2008-08-09
Hey there,

Go to **System>Preferences>Keyboard**
Then select the **Layout** tab and (if you have already added alternative layouts) select **Layout option**.
In the list of options, the option select **Layout switching**. If this option is bold then you already have a default keyboard switching shortcut, if you cause to show all possible shortcuts you will be able to see/change your shortcut.
[I]Suggestion: use the Left Win Key as it (generally) useless in Ubuntu.
[/I]
To add some visual you may add the Keyboard Indicator on your Panel.

Good luck.

---

### Post by yotam on 2009-05-07
Is it possible to have more than two keyboard layouts defined in
[FONT="Courier New"]/etc/default/console-setup[/FONT]
by setting:
  > XKBLAYOUT="layout1,layout2,layout3"
  XKBVARIANT="v1,v2,v3"
  XKBOPTIONS="grp:alt_shift_toggle,grp_led:scroll"
and the toggle actually cycles thru the 3 layouts?

I tried this, but when I ran: 
[SIZE="4"][FONT="Courier New"]dpkg-reconfigure console-setup[/FONT][/SIZE]
I got some warning about undefined layout.
But when I used just any two of these layouts, I did not get such warning.

---

### Post by atri on 2009-06-15
Seems I have a similar problem ! Have you solved yours ? Or does anyone have a solution :
I have to work with different keyboard layouts , the layout indicator is on the panel and a key defined to switch between layouts . But it would be more convenient to have a specific shortcut to get a specific layout , like e.g. Alt+F2 for English , Alt+F3 for Hindi etc. . Could anyone help ?
Would it be possible to define a Custom Shortcut under System , Preferences , Keyboard Shortcuts ? But I would have to have a ‘ command ’ and I don’t know what that could be :-) .
Thanks for helping !

---

### Post by markoturso on 2010-03-31
jesuisbenjamin explained everything well.

---

