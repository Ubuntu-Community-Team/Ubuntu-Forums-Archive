---
title: "How to get &quot;Shutdown&quot; in startup menu?"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by DapperMe17 on 2007-10-09
Kubuntu Edgy w/IceWM 

Hi,

I'm running IceWM on the top of Kubuntu. 

I'd like to know how to get a "**shutdown computer**" option in the start menu? At the moment, there is only a "logoff" option. I would like to shutdown directly from the start menu.


Thanks

---

### Post by DapperMe17 on 2007-10-10
bump....

---

### Post by Forlong on 2007-10-10
You could add a starter to the panel with this command:
```
gksu shutdown -h now
```

---

### Post by DapperMe17 on 2007-10-10
Thanks, I will try that.

---

### Post by DapperMe17 on 2007-10-10
Sorry, but that didn't work. 


The PC is running IceWM & Rox-filer. But, when I click on the Debian "start" menu, the only option is to "Log Off" the session. I would like to be able to have a "Shut Down Computer" option there as well....

Any ideas?

---

### Post by Forlong on 2007-10-11
> **DapperMe17 said:**
> The PC is running IceWM & Rox-filer.
So you don't have any DE running at all?

---

### Post by DapperMe17 on 2007-10-11
Yes, IceWM over the top of Kubuntu....

only "logoff" is listed when I go to the start menu. That only logs me off the session & from there I have to logout. I'd like the "shutdown computer" menu to be in the start menu, so that the PC shuts down directly from the IceWM desktop.

---

### Post by Forlong on 2007-10-11
> **DapperMe17 said:**
> IceWM over the top of Kubuntu....
Then you need to change the above command like this:
```
kdesu shutdown -h now
```

---

### Post by DapperMe17 on 2007-10-11
Will I need to do that from a terminal in Kubuntu, or while in IceWM?

---

### Post by Forlong on 2007-10-11
You can run that from any terminal you like. Then you won't even need the graphical sudo.
But I thought you wanted to use that with a starter in the panel.

Note that I do not have any experience with Icewm but I guess you can create starters, don't you?

---

### Post by DapperMe17 on 2007-10-11
No clue at all...all that I need is a IceWM menu button which allows me to click on it, so that the PC powers down.

I don't want to shutdown from the terminal, every time.  

I **WANT ** a graphical "shutdown" in the menu...how can I get it there?

---

### Post by jis on 2007-11-29
bump

---

### Post by jis on 2007-11-29
Editing sudoers file as suggested in [this post]("http://ubuntuforums.org/showpost.php?p=3860154&postcount=254") worked for me.

---

