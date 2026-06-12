---
title: "How do I get the &quot;Computer&quot; menu back?"
date: 2004-10-23
forum: Desktop Environments
---

### Post by farmer on 2004-10-23
I was editing the Gnome panels to my own liking, and I got rid of the "Computer" menu, thinking I could get it back, but I can't find where to add it back. It's not in the "add to panel: window, unless I'm missing it.

---

### Post by rolf on 2004-10-23
[QUOTE=farmer]I was editing the Gnome panels to my own liking, and I got rid of the "Computer" menu, thinking I could get it back, but I can't find where to add it back. It's not in the "add to panel: window, unless I'm missing it.[/QUOTE]

To restore *ALL* your panels to the default,  open a prompt to your home directory and type

sudo rm -r .gnome2/panel.d

I am not sure how to rebuild just one panel.

HTH.

---

### Post by Faramirtook on 2004-10-23
I found it, it was under "menu bar" or , right underneath main menu.

---

### Post by Cygnia on 2004-10-23
If you're talking about the custom menu bar with the gnome foot/applications/computer menu system, have you tried right-clicking the panel and adding "custom menu bar"? Sorry if I'm not understanding your question.

--
Bryce

---

### Post by nicholaspaul on 2005-01-09
oh boy.. i did the same thing. except i have 'no' menus at the top of my screen either. darn it. 
Good job i knew how to type 'firefox' in Terminal :p
I tried the sudo rm line, but it said there was no file or directory. 
Anyone?

---

### Post by farmer on 2005-01-09
All you do is right click on the panel, and then there's something about adding something to the panel, and its in the dialogue there. (I don't have Ubuntu in front of me)

---

### Post by Shaggy on 2005-01-09
[QUOTE=nicholaspaul]oh boy.. i did the same thing. except i have 'no' menus at the top of my screen either. darn it. 
Good job i knew how to type 'firefox' in Terminal :p
I tried the sudo rm line, but it said there was no file or directory. 
Anyone?[/QUOTE]

If you've still got the other panel on your screen just right click on that and hit create new panel.  Should make a new one for ya. THen you just right click and add whatever you want.

---

### Post by nicholaspaul on 2005-01-11
AAh. Now, there's my problem: I dont have any panels left, except the one at the bottom showing the open apps. 
I like it like that, but... this is a little impractical! Obviously I can open a terminal window (and type 'Firefox' to get here!) but thats about it. 

Heeeeelp!000

---

### Post by saBrEwolf on 2005-01-11
[QUOTE=nicholaspaul]AAh. Now, there's my problem: I dont have any panels left, except the one at the bottom showing the open apps. 
I like it like that, but... this is a little impractical! Obviously I can open a terminal window (and type 'Firefox' to get here!) but thats about it. 

Heeeeelp!000[/QUOTE]
 Is GNOME not giving you the option to create a new bar?

If not, unlock the window list by right-clicking on the widget on the end. drag it to the right a little, then right-click and the option should be there.

Hope this helps

---

### Post by nicholaspaul on 2005-01-15
Im an idiot.

After a few days sleep, I retried clicking around, and found that if i were to only click at the bottom of the screen SOMEWHERE, it would work. 'add panel' is indeed in the menu. 

See - I had also set the background of the panel to the same colour as the desktop, and didnt see it as the panel anyway. 

What a newbie... 

Thanks for the help:) I'm happy now!!

---

