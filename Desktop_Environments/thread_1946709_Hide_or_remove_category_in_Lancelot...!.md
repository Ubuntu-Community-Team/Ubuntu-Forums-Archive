---
title: "Hide or remove category in Lancelot...?!"
date: 2012-03-25
forum: Desktop Environments
---

### Post by Chip88 on 2012-03-25
Hi there!

I installed today Lancelot. Because I am not using neither Contact nor Kopete, I would like to hide or remove / delete the category "Contact".

Unfortunately, this seems to be not possible under the "normal" settings. Is there anyway a possibility to hide / remove / delete the category "Contacts"?! Maybe I have just to edit a file of the widget...
&#8594; But which one and what to edit where?

Thanks in advance for all your support!

Have a nice rest of this Sunday! ;-)

Chipy

---

### Post by SeijiSensei on 2012-03-25
I haven't used Lancelot in a while, but if you right-click on the regular KDE launcher, you'll see the option to bring up the Menu Editor.  Perhaps that's true for Lancelot as well.  Otherwise, you can access the editor by typing "kmenuedit &" at a Terminal prompt.  You can then alter the menus to your heart's content.

---

### Post by Chip88 on 2012-03-28
@ SeijiSensei:
Thank you for your fast answer.

But your suggestion is not exactly what I meant.

I attached a screenshot and marked red what I want to remove.

Is there a possibility to remove that category???

Thanks in advance...
Chipy

---

### Post by Erik1984 on 2012-03-28
I'm not sure if that is possible (unless you dive into the code :P). I have Lancelot too and I can't find the option to configure those aspects either.

---

### Post by Chip88 on 2012-03-28
@ Euroman:
Thanks for your answer!

I would dive into the code, but which files should be edited???

Thanks in advance!
Chipy

---

### Post by SeijiSensei on 2012-03-28
Have you tried using kmenuedit?  When I switched from the standard Launcher to Lancelot and back again, I had the same menu structure in all cases.  That makes me think that if I had edited the structure with kmenuedit, both launchers would have changed accordingly.

In kmenuedit, I can right-click on a category and choose delete to remove it from the menus.  Does that not work with Lancelot?

---

### Post by Chip88 on 2012-03-28
Hey SeijiSensei!

I changed also to Kickoff again and tried to change the tabs with the kmenuedit, but it's not that what I want. With kmenuedit you can edit, add or remove APPLICATIONS, but not tabs...

I found this: [http://ubuntu.paslah.com/kde-kickoff-and-quick-access-menus/](http://ubuntu.paslah.com/kde-kickoff-and-quick-access-menus/) .

And more and more I think, it is impossible to remove the tabs for Favorites, Applications, Computer, Recently Used, and Leave.

---

### Post by SeijiSensei on 2012-03-28
I took a look at ~/.kde/share/config/kickoffrc and didn't see any way to control the tabs there either.

---

### Post by Chip88 on 2012-03-28
And I found this: [http://brainstorm.ubuntu.com/idea/13795/](http://brainstorm.ubuntu.com/idea/13795/) .

Already the first point says: "Allow users to switch between having a single icon to access Kickoff or displaying five separate icons, one for each tab."

So I checked again the settings of Lancelot and found the following:

I can choose between "Show categories" (no. 1) and "Just show the menu - icon" (no. 2).

If no. 2 is choosed, Lancelot appears as a compact application with everything in one tool.

Changing to "Show categories" makes it possible to decide, which categories I want to be shown (no. 3). I unchecked "Conact".

After pressing OK, an icon for every choosed category appear in the taskbar (no. 4).

So it IS possible to uncheck a category,
BUT: I don't want to have all the categories in the taskbar. I want just one application with the choosen categories inside!!!

Would this be possible by changing some files???

---

