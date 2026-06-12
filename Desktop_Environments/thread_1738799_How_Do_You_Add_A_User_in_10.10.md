---
title: "How Do You Add A User in 10.10?"
date: 2011-04-25
forum: Desktop Environments
---

### Post by beeser on 2011-04-25
Hello!

So, I FINALLY got Ubuntu 10.10 installed and booted.  Now, I want to add a user.  Is there any way to manage users through the desktop GUI, or should I just head right to the Terminal app?  How is system administration done in 10.10?  All my desktop has are a group of icons off to the right side of the screen.  There's nothing anywhere to indicate any way to look at files, drives, etc.   Should I be using a different GUI?

Thanks

---

### Post by karthick87 on 2011-04-25
Goto [COLOR=Red]**System > Administration > Users and Groups**[/COLOR] and from there you can add the user.

---

### Post by beeser on 2011-04-25
Where do I find "System"?  Should there be an icon somewhere?  It's not in "Applications".

---

### Post by karthick87 on 2011-04-25
You will see that in your panel. [COLOR=Red]**Applications Places System**[/COLOR]

---

### Post by beeser on 2011-04-25
Where is this "Panel"?  I looked in the "Applications" icon found in the right side of my desktop, and there's no "Places" there.  At the top of my desktop are only the usual items found on the upper left corner: the clock, wireless status, my user name, etc.

I'm afraid you're going to have to walk me through this, step-by-step....

---

### Post by collisionystm on 2011-04-25
Wow... sounds like you changed the default install. Lets make this easy for everyone. Fire up terminal, type 
```

sudo adduser

```
if not prompted for a password type
```

passwd <username>

```

---

### Post by collisionystm on 2011-04-25
and if you need to change the groups the user belongs to...

```

usermod -G <groupname> -a <username>

```

---

### Post by beeser on 2011-04-25
Well, I was hoping there was a more, uh, "Mac-like" way to add a user.  (I already know how to do it at a command line.)  It seems my real question, then, is:  How do I get this "Panel" to appear on the desktop?  I've never seen it.  I've just checked the "Try Ubuntu Netbook" I had on the flash drive, and, aside from the "Install Ubuntu Netbook" icon in the upper left, it looks just like what I'm seeing here on the installed version.

So far, I've found Ubuntu to be EXTREMELY difficult to navigate.  Maybe that's only because I'm missing something from the install....

---

### Post by Krytarik on 2011-04-25
So, you are using the "Netbook Edition". Maybe you want to check out the "Desktop Edition", therefore log out of your session, click at your username and choose those as the "Session" option at the bottom.

Greetings.

---

### Post by beeser on 2011-04-26
Yes, sorry.  I should have said I'm running Netbook Edition on a Dell Inspiron 1545.

So, that's the difference?  I was thinking the Desktop Edition wouldn't have any sort of battery management or touchpad control.  The Desktop Edition is certainly more navigable, with "Applications", "Places" and "System" up there.  Now if I can just get this computer to see and be seen by the other computers in my network, we'll be about 3/4s the way there....

BTW - In Notebook Edition I was able to find "Control Center" under the "Applications" icon, and that's exactly what I was looking for.

Thanks for all the help, everybody!

---

### Post by Krytarik on 2011-04-26
> **beeser said:**
> 
So, that's the difference?  I was thinking the Desktop Edition wouldn't have any sort of battery management or touchpad control.
Yeah, that's the only difference, 'just' a different GUI. And since the most guides are written in respect of the interface of the "Desktop Edition", you may have some difficulties to apply them to the "Netbook Edition". But I guess if you just search for the name of the 'endpoint', in this case "Users and Groups", through the respective tool of the launcher, you will find them as well.

---

