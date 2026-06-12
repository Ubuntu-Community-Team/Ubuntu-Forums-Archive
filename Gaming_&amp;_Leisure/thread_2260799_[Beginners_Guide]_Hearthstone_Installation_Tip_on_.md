---
title: "[Beginners Guide] Hearthstone Installation Tip on Playonlinux"
date: 2015-01-14
forum: Gaming &amp; Leisure
---

### Post by nemexs on 2015-01-14
Hello,

If you are like me and have a hard time installing Hearthstone and only way to run it is through playonlinux, yet it doesn't register and create a shortcut there is a way to solve it.

First of all please make sure that all libraries are in tact using this method:

1. Install Hearthstone using the "Install" button on playonlinux. This will install first the battle.net client and then Hearthstone itself. However whenever you exit the Battle.net you would think this might be the last time and you have to repeat the process next time, nope. 

2. Open "Configure wine" on playonlinux, I've highlighted it, just in case.
[IMG]http://i.imgur.com/oX4f7Lg.png[/IMG]

3. First access your Hearthstone virtual drive and under the tap "wine" click "Configure Wine" 
Under the tab library type "dbghelp" and "msvcp100" under the "New override for library:" section, last click "Add" 
Once you've done click on the "dbghelp" and then click "Edit..." from there chose "Disable"
Click "msvcp100" and then "Edit..." from there chose "native, builtin"
[IMG]http://i.imgur.com/5Jk3NuA.png[/IMG]
This process might not be necessary for you however still might be good to try.

4. Once you've done that return to "PlayOnLinux configuration" window and under the "General" tab click "Make a new shortcut from this virtual drive" 
[IMG]http://i.imgur.com/ORo95IN.png[/IMG]

5. Navigate to find "Battle.net Launcher" and click "Next". Once you've done that you can find the Shortcut not only in the PlayOnLinux menu, but also on your Desktop.
[IMG]http://i.imgur.com/qaRLwB4.png[/IMG]

From that point on you can access your Battle.net easily and without any trouble.
[IMG]http://i.imgur.com/Pq2OjyE.jpg[/IMG]

This might seem like a stupid guide, however that took me awhile to get it by myself, hopefully this will save time for other people. 

Thank you and have a nice day :).

---

### Post by Bubbelgum on 2015-01-14
Worsk great, i just did it and step 3,4 where already done so i dident need to change abit =)

---

### Post by nemexs on 2015-01-15
Was the shortcut created too?

---

### Post by Bubbelgum on 2015-01-15
Yes, worked perfektly all i hade to do was to get a heartstone icon so it liked nice

---

### Post by nemexs on 2015-01-15
[IMG]http://i.imgur.com/9fvgbHj.jpg[/IMG]

---

### Post by forever3 on 2015-01-16
The game is running with low FPS if you go to the ingame settings and see the default setting "medium" under "graphics" 

I wanted to set it to "high" but the game crashes. Any fix?

---

### Post by oldrocker99 on 2015-01-17
A **very** fine job ye did, too. Once again, the benefits of this here community shine through!

---

