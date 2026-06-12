---
title: "Applications menu disappeared Gnome Gutsy"
date: 2007-10-15
forum: Desktop Environments
---

### Post by Homie Bongo on 2007-10-15
in my Ubuntu Gutsy I got the whole Applications menu disappeared. when I click "Applications" it shows only a little white square. When I add the single button menu (only the Ubuntu logo, the one without text labels) to my panel and open it, it reveals the "applications" entry is all gone.

I think this happened after I launched "Main Menu" from System > Preferences and the program crashed. I am unable to open the program now.

I didn't find where the hidden folder with menu entries could be. Just to see if there are any entries, or if there isn't lockfile or so... Could anybody tell me?
thx

---

### Post by chrisxtj on 2007-10-16
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/14833](https://answers.launchpad.net/ubuntu/+question/14833) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Similar problem.
Can anyone help?

---

### Post by burn0xdc on 2007-10-16
same problem

---

### Post by burn0xdc on 2007-10-17
Solution:
```
cd /home/user/.config/menus/
rm applications.menu
```

---

### Post by fogster on 2007-10-21
I don't have an applications.menu file.

Following the advice about cleaning out /usr/local/lib didn't bring back my Applications menu, and in fact broke a bunch of other stuff. (But I was able to undo it.)

There's got to be an easy fix?

---

### Post by Homie Bongo on 2007-10-21
great, this works! thanks

---

### Post by fogster on 2007-10-21
It seems like there might be multiple things that cause this.

For me, creating a new user and logging in as them doesn't fix anything. The brand-new user still just gets a tiny little (2 pixels square, maybe?) block as their "Applications" menu. Some others have reported that creating a new user does fix it.

Is there somewhere I should be looking for logs?

---

### Post by fogster on 2007-10-23
Anyone?

---

### Post by chrisxtj on 2007-10-23
> **burn0xdc said:**
> Solution:
```
cd /home/user/.config/menus/
rm applications.menu
```

this solve my problem, too! thanks. but I really want to know how it works...

---

### Post by sayyidhassan on 2007-12-25
[B]cd /home/user/.config/menus/
rm applications.menu[/B]

the same also worked for me.thanks

---

