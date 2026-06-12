---
title: "Can't Right Click or Open App Menu"
date: 2006-08-12
forum: Desktop Environments
---

### Post by derouge on 2006-08-12
I installed Xubuntu the other day and it worked fine. Today I boot up and login, try to right click to open terminal and the right click does nothing (instead of opening up the applications menu. I then tried opening the Applications menu, but that also didn't work. I'm guessing I (or someone in the house) accidentally shutdown a process that is needed. I would've thought rebooting would solve that but it hasn't. Any suggestions?

---

### Post by DJiNN on 2006-08-15
I'm having this problem as well, both with the older (Beta) release & also the latest release of Xubuntu..... i can't find any way of making it work yet, and there's no way of accessing the settings panel to see if there's something there that could make it work again....

If i find an answer i'll be sure to post it here, but if anyone else is reading this & has an answer...... HELP!!!! :)

DJiNN

---

### Post by derouge on 2006-08-15
Try this:

Open /home/*username*/.config/xfce4/desktop and see if there is a menu.xml file. If so, delete it. Log out and log back in. See if your menu works. If it does, great. It probably won't though .. hehe, so open the terminal. 

```
xfdesktop
```

I think that is the command. You may need a paramenter, -r maybe. I think this is what got my menu working again. I guess it's a known bug that XFCE4 might "eat" your menu if you try using the menu editer. I hope this works for you .. I tried so many things until I got it working, so I'm not sure this alone will do it. I'm also on a Windows system right now so I can't check the proper commands. Ugh. Let me know how it goes. :)

---

