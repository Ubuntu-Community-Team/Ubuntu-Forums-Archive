---
title: "I think I broke it :("
date: 2012-07-25
forum: Desktop Environments
---

### Post by Ifaistos on 2012-07-25
Hey everyone :-)

Compiz is great, but it still has bugs.
One of them is that when I alt-tab, sometimes chrome or thunderbird can't be switched to.  I can see them on alt-tab, but can't get there in any way...

This is not the reason I am writing this.
I wanted to get rid of all the effects of compiz, so I went to ccsm, and turned it off, along with all the plugins.

It seems that I broke it, and now I only get one workspace, with no Unity bar or anything else.

How can I "restart" and have unity, without the staff from ccsm?
Thanks

---

### Post by nothingspecial on 2012-07-25
Try this

Press Ctrl-Alt-F1

login and type

```
unity --reset
```

then

```
sudo service lightdm restart
```

---

### Post by Ifaistos on 2012-07-25
It worked flawlessly !!

Thanks :-)

The only think I am missing from CCSM, is that plugin, where you choose a place on the screen, and when you move your cursor there, you can see all the apps in that workspace in tile mode.

Is there a way to have only that (which is bugged too btw) and nothing else?

** It's bugged because every time I restart I have to go to CCSM, Click on Scale plugin, disable and then re-enable otherwise it doesn't work.

---

### Post by Ifaistos on 2012-07-25
Don't answer that...
I just did it...

Thank you nothingspecial, for your lightning fast (and helpful) answer.

You are anything but "nothingspecial".

---

