---
title: "How to return Close, Max, and Min to right side"
date: 2010-04-20
forum: Desktop Environments
---

### Post by xVehemencityx on 2010-04-20
Hi.  Just reinstalled 9.10 as I've been having issues with Windows, and the fact that the Close, Minimize, and Maximize buttons are in the left kinda bothers me. I know I should be used to it by now, but I'm anti-mac and it reminds me of a "Mac-ish" feel, and I would love to return them to the right side.

---

### Post by lazymangaka on 2010-04-21
Ha! I actually did exactly the opposite today, so I'm now well versed in this. *not anti-Mac at all* :D

Press Alt+F2 to bring up the Run Application dialog box, enter  &#8220;gconf-editor&#8221; in the text field, and click on Run. 

Go to apps -> metacity -> general and the key to look for is "button_layout". Double click it to edit it and change the value to "menu:minimize,maximize,close". Easy peasy.

---

### Post by g_knap on 2010-04-21
Same as above but :
"menu:minimize,maximize,close,[COLOR=Red]spacer:"

[/COLOR]Worked better for me.

---

### Post by highlandsun on 2010-04-24
Anyone know how to do the corresponding change for Xubuntu? (xfce)

Never mind. After I closed gconf-editor it took effect. Strange that it didn't have any effect before.

---

