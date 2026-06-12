---
title: "cannot position eterm where i want it....help"
date: 2007-06-07
forum: Desktop Environments
---

### Post by aggie333 on 2007-06-07
hi guys,
   i am using feisty with fluxbox....my problem is that i cannot position the eterm window at the top left corner...even when i use the -g option with x and y co-ords as 0, the window gets positioned at the middle of the screen....when i tried moving the window i observed that the screen some how has multiple sections...ie it has multiple x=0,y=0 points....this is very strange to say the least.....also i want the terminal to display only the $ prompt instead of [email]user@machine$........and[/email] finally can i also know if it is possible to change the icons used by rox...if yes how and where can i find a few....someone please help me...thanks in advance

---

### Post by RedSquirrel on 2007-06-07
> **aggie333 said:**
> hi guys,
   i am using feisty with fluxbox....my problem is that i cannot position the eterm window at the top left corner...even when i use the -g option with x and y co-ords as 0, the window gets positioned at the middle of the screen....when i tried moving the window i observed that the screen some how has multiple sections...ie it has multiple x=0,y=0 points....this is very strange to say the least.....

I use xterm instead of eterm, so I don't know an awful lot about it or why its settings aren't working. However, in Fluxbox you can save the position, dimensions, etc. of windows. Put the eterm window where you want it, then right-click on the titlebar, Remember -> Position. You might also have to select "Save on close".


> **aggie333 said:**
> also i want the terminal to display only the $ prompt instead of [EMAIL="user@machine$........and"]user@machine$........and[/EMAIL] 

See [http://www.gentoo.org/doc/en/articles/prompt-magic.xml](http://www.gentoo.org/doc/en/articles/prompt-magic.xml)


> **aggie333 said:**
> finally can i also know if it is possible to change the icons used by rox...if yes how and where can i find a few....

I don't use rox, so someone else will have to help with that.

---

