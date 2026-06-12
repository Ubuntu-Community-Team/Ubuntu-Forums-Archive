---
title: "Stupid problem"
date: 2006-12-19
forum: Desktop Environments
---

### Post by Shriike on 2006-12-19
To start with I'm running Ubuntu (6.10, edgy) I wanted to try out KDE, so I installed it to test it out, messed around with it for a little while, then that's where my problem started, I didn't fully read the site on how to install it, so tried to just manually remove the components (I know stupid) but after I realized my mistake I went back typed in the simple command they give and uninstalled it and it said it worked.  But for some reason I still get a Kubuntu load screen when booting up, I don't think this is a serious problem, I don't think it's hurting anything, but it just got me thinking and I'm wondering if there is a way to manually change that load screen to something else (I just think it's ugly, and want some aesthetics to my computer).

Well if no one can help, that's cool, if you can awesome.  Thanks to anyone who reads this at least.

---

### Post by blue_shift on 2006-12-19
Just to clarify, are you using KDM or GDM? ie at log-in, is it a kde screen with user name / password, or the old gnome one?

---

### Post by raul_ on 2006-12-19
You mean the splash screen?

---

### Post by EnderTheThird on 2006-12-19
I think I'm having the same problem that you are with Kubuntu showing during boot but then it goes to regular GDM and Ubuntu after that.

---

### Post by paparucino on 2006-12-19
> **EnderTheThird said:**
> I think I'm having the same problem that you are with Kubuntu showing during boot but then it goes to regular GDM and Ubuntu after that.
Enter a terminal then goto to /etc/alternatives/ 
Here you should have a simlink named @usplash-artwork.so which points (in your case) to /usr/lib/usplash-theme-kubuntu.so
Change the above link so to point to /usr/lib/usplash/usplash-theme-ubuntu.so

---

### Post by Shriike on 2006-12-19
Ender was right about the problem, but paparucino how do I edit the link?

---

### Post by raul_ on 2006-12-19
```

ls -l

```

---

### Post by paparucino on 2006-12-19
> **Shriike said:**
> Ender was right about the problem, but paparucino how do I edit the link?
Enter a terminal then
```

rm /etc/alternatives/usplash-artwork.so
ln -s /usr/lib/usplash/usplash-theme-ubuntu.so  /etc/alternatives/usplash-artwork.so

```

and cross the fingers :-)

---

### Post by Shriike on 2006-12-19
thank you so much, gonna restart now and see how it worked :)

---

### Post by paparucino on 2006-12-19
> **Shriike said:**
> thank you so much, gonna restart now and see how it worked :)
If you crossed the fingers everything **[COLOR="Red"]SHOULD[/COLOR]** br ok

---

### Post by Shriike on 2006-12-19
Paparucino I forgot about that last step (crossing fingers) :( it didn't work, the link is pointing to the right file, but I guess that image is wrong :(

---

### Post by Shriike on 2006-12-19
I don't know how this worked, first I downloaded a new usplash deciding the current one was messed up, I found a good lookin one followed the instructions and restarted, same problem, so then I noticed there is a "Usplash" and "Usplash-ubuntu" in my package installer, reinstalled both of those and now it works perfectly.....I'm confused. (also not sure if this is my imagination or not but it seems to be loading faster)

---

### Post by paparucino on 2006-12-20
> **Shriike said:**
> I'm confused. (also not sure if this is my imagination or not but it seems to be loading faster)
Tha important thing is that now everything is ok. 
I tried to build a splash screen but wasn't able, so I used the original one.

---

