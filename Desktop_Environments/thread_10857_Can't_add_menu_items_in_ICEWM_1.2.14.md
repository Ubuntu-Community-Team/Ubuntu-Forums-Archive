---
title: "Can't add menu items in ICEWM 1.2.14"
date: 2005-01-12
forum: Desktop Environments
---

### Post by mcollins on 2005-01-12
Any ICEWM users? I've been configuring it by modifying my config files in the .icewm folder, and doing pretty well. Except for for this one thing, when I add a menu item to the menu file, it doesn't appear in my menu, and neither does anything below it! I comment it out and everything appears again. This is what I'm entering in the menu file:
menu "Control Panel" folder

It's driving me  nuts. I didn't find any documented bugs about that.

Matt

---

### Post by keyshawn on 2005-01-13
can you edit icewm at all in the configuration editor [gconf] ?

[not sure, I haven't installed icewm onto ubuntu, just installed ubuntu yesterday for 1st time]

---

### Post by jonrkc on 2005-05-21
[QUOTE=mcollins]Any ICEWM users? I've been configuring it by modifying my config files in the .icewm folder, and doing pretty well. Except for for this one thing, when I add a menu item to the menu file, it doesn't appear in my menu, and neither does anything below it! I comment it out and everything appears again. This is what I'm entering in the menu file:
menu "Control Panel" folder

It's driving me  nuts. I didn't find any documented bugs about that.

Matt[/QUOTE]
 I hope you've solved this by now, but if not...

It looks to me as though the word "folder" is the problem.  In the menu file, the name of the menu item (in this case "Control Panel") is followed by an icon reference, in quotes.  If you don't have an icon, you can put nothing between the quotes, but the quotes need to be there:  

```

menu "Control Panel" ""

```

...and after that, the curly braces and the command for the application, etc.

At least that's how mine works.  :)

If you can manage to install IceWMCP (not always easy, take it from me), you'll have a very fine tool for configuring ALL sorts of things in IceWM.  I struggled and got it going under Mandrake/Mandriva then when I moved to Ubuntu last week I managed to transfer it over "here" and get it working--I practically fell out of my chair.  The phrase "dependency hell" came from apps like IceWM.  But the end result of all the frustration installing it is well worth it, I think.

---

### Post by wilhelm on 2005-05-23
i suggest installing icepref and iceme...

help me get all my menu's correct when installing anything ... :razz:

---

### Post by jonrkc on 2005-05-23
[QUOTE=wilhelm]i suggest installing icepref and iceme...

help me get all my menu's correct when installing anything ... :razz:[/QUOTE]Good idea.  I should have thought of that, too.  Both do a good job and are NOT a problem to install.

---

