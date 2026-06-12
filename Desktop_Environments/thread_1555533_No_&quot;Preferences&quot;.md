---
title: "No &quot;Preferences&quot;"
date: 2010-08-18
forum: Desktop Environments
---

### Post by berlinick on 2010-08-18
Hello!

I am very new to Linux, so please be patient ;)

I have a little problem: I wanted to install Russian keyboard layout on my xubuntu 9.10 and probably even did it correctly. But I can't find the shortcut to change keyboard layout. In relation to this: I have found that there is no "Preferences" option in my "System" menu, where the keyboard shortcuts' settings should be (System -> Preferences -> Keyboard Shortcuts, right?).

I will be glad about your replies.


Nick

---

### Post by stinkeye on 2010-08-18
Right click on the main menu > edit and check it is ticked.

Alternatively alt+F2 to bring up the run application dialogue and run
```
gnome-keybinding-properties
```

[COLOR="Red"]Oops didnt notice you were using xubuntu.[/COLOR]

---

### Post by berlinick on 2010-08-18
> **stinkeye said:**
> [COLOR=Red]Oops didnt notice you were using xubuntu.[/COLOR]

Do you know, how to do it under xfce?

---

### Post by stinkeye on 2010-08-18
> **berlinick said:**
> Do you know, how to do it under xfce?

No, sorry never used xfce.

---

### Post by Spice Weasel on 2010-08-18
Settings > xfce4 Settings Manager > Keyboard should do fine.

---

### Post by berlinick on 2010-08-18
> **stinkeye said:**
> No, sorry never used xfce.

No problem. I'm just experimenting on my older laptop. Dell Latitude, about 6 years. A very good machine actually, a weak graphic card though. Normal Ubuntu just didn't run properly on it :( Xubuntu flies like a butterfly :)

---

### Post by berlinick on 2010-08-18
> **Spice Weasel said:**
> Settings > xfce4 Settings Manager > Keyboard should do fine.

Cool, thanks! I'll try that out tonight. Will post my experience report here :)

---

### Post by 3Miro on 2010-08-18
For keyboard layouts under XFCE:

Right-click on the top or bottom panel and select "add new item". Then look for "Keyboard Layouts". This should display a small US flag indicating that you are using English Layout. Right-click on the flag -> Properties and then Add would give you a list of choices for languages and keyboards.

If the Keyboard Layout applet is not on the list, you can install it via synaptic, look for xfce4-xkb-plugin, or type in terminal:
```
sudo apt-get install xfce4-xkb-plugin
```
or install xfce4-goodies
```
sudo apt-get install xfce4-goodies
```
which comes with a lot of nice xfce stuff.

---

### Post by berlinick on 2010-08-18
Great, thanks!
I just hope, these apps are not too hardware-demanding... They schouldn't be, right? It's just keyboard layout after all...

---

### Post by 3Miro on 2010-08-18
> **berlinick said:**
> Great, thanks!
I just hope, these apps are not too hardware-demanding... They schouldn't be, right? It's just keyboard layout after all...

The layout app is very light, the rest of the goodies package varies. At any rate the only apps that will run are the ones that you put on the panel or select for auto-run anyway, so you can experiment.

---

### Post by berlinick on 2010-08-18
Got it! Thank you :)

---

### Post by berlinick on 2010-08-18
"Settings > xfce4 Settings Manager > Keyboard"

It turns out, I did it already before the original post, when I turned on the very option to have the Russian layout. It adds the layout to the keyboard, but doesn't show the current layout on the panel and doesn't let you change it.
However, without this instruction it makes no sense to look for how to include the layout indicator to the panel :)

Thank you for the hint!

---

### Post by berlinick on 2010-08-18
> **3Miro said:**
> For keyboard layouts under XFCE:

Right-click on the top or bottom panel and select "add new item". Then look for "Keyboard Layouts". This should display a small US flag indicating that you are using English Layout. Right-click on the flag -> Properties and then Add would give you a list of choices for languages and keyboards.

If the Keyboard Layout applet is not on the list, you can install it via synaptic, look for xfce4-xkb-plugin, or type in terminal:
```
sudo apt-get install xfce4-xkb-plugin
```or install xfce4-goodies
```
sudo apt-get install xfce4-goodies
```which comes with a lot of nice xfce stuff.

I did it through the panel. Worked perfectly.
Lot's of other pleasant things there :) I'll check them out first. Next thing - goodies :)

---

