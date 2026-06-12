---
title: "Compiz - Only one workspace"
date: 2008-05-13
forum: Desktop Environments
---

### Post by okeven on 2008-05-13
I installed compiz, and now I only have one workspace.  I can change the number up or down, and it does change the number of workspace boxes on the lower taskbar, but only the first works.  The others are just gray boxes.  If I click on them, nothing happens.  Help!

---

### Post by okeven on 2008-05-13
And another thing beginner question.  How do I switch back from compiz to the default window control program?

---

### Post by pch0mey on 2008-05-13
> **okeven said:**
> And another thing beginner question.  How do I switch back from compiz to the default window control program?

System -> Preferences -> Appearance -> Visual Effects

---

### Post by okeven on 2008-05-13
> **pch0mey said:**
> System -> Preferences -> Appearance -> Visual Effects

That worked.  Thanks.  My other desktop workspaces are working now too, but only once compiz was turned off.  So, how can I get it working under compiz?

---

### Post by okeven on 2008-05-13
bump....

---

### Post by Stefan Stryjecki on 2008-05-13
Hi okeven.

According to my experience this happens due to compiz misunderstanding the "regular" workspaces (i.e., those created without compositing) and putting all its workspaces inside the first "regular" one. 

What solved the problem for me was:

1) disable Compiz (according to instructions given by pch0mey)
2) set only one workspace here
3) enable Compiz again
4) now set as many workspaces as you wish and you should be fine

Let me know if it worked for you.

---

### Post by okeven on 2008-05-13
> **Stefan Stryjecki said:**
> Hi okeven.

According to my experience this happens due to compiz misunderstanding the "regular" workspaces (i.e., those created without compositing) and putting all its workspaces inside the first "regular" one. 

What solved the problem for me was:

1) disable Compiz (according to instructions given by pch0mey)
2) set only one workspace here
3) enable Compiz again
4) now set as many workspaces as you wish and you should be fine

Let me know if it worked for you.


Just tried it.  Still did not work.  Each workspace I add still is just a gray box that does not when you click on it.

---

### Post by Urik on 2008-05-14
Check that you have "Gconf" and not "Flat file" in compiz configuration settings. It causes such problem.

---

### Post by okeven on 2008-05-14
> **Urik said:**
> Check that you have "Gconf" and not "Flat file" in compiz configuration settings. It causes such problem.

Just checked and I do have "Gconf" selected.  Any other ideas?

---

### Post by Newtt11_78 on 2008-05-14
I ran into something similar when I enabled desktop cube. Had to go into compizconfig settings manager, general options, desktop size (tab), horizontal virtual size which I set to 4 and then could access them.

---

### Post by okeven on 2008-05-14
> **Newtt11_78 said:**
> I ran into something similar when I enabled desktop cube. Had to go into compizconfig settings manager, general options, desktop size (tab), horizontal virtual size which I set to 4 and then could access them.

Weird.  Still did not work.  Now I have 1 working desktop, and 3 gray boxes that do nothing!

---

### Post by xored on 2010-01-07
When you using Compiz on normal or special mode (Karmic or Intrepid) you will not able to use wmctrl to use switch the desktops. I have described the way to accomplish that here

[http://wiki.impressive-media.de/doc/toggle-or-rotate-through-your-workspace-using-a-shortcut-while-having-compiz-activated-gnome](http://wiki.impressive-media.de/doc/toggle-or-rotate-through-your-workspace-using-a-shortcut-while-having-compiz-activated-gnome)

---

