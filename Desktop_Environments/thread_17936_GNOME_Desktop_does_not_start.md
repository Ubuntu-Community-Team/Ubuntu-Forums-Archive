---
title: "GNOME Desktop does not start"
date: 2005-03-03
forum: Desktop Environments
---

### Post by puelly on 2005-03-03
Hey Guys,

I have been searching and while i find problems that are similar, I can't find any exactly like mine.  Most people at least have the Splash screen and the background start.

I recently install XFCE 4.2 using debs.  I tried it but wanted  to go back to GNOME.  However when I change the session to GNOME, nothing is loaded.  I can start XFCE and failsafe terminal, I also tried reinstalling gnome-panel and tried starting it from failsafe terminal.  Nothing happened.  I am able to start firefox from the terminal but it has now window manager.

I have also deleted the gnome profile information.  Anyone have any other methods or links that I can try to get my GNOME desktop back.

Thanks.

---

### Post by rosslaird on 2005-03-03
Are you starting (attempting to start) Gnome from the command line, from the login manager, or from a virtual console?

Linux users don't like to recommend rebooting, but often it does fix this sort of thing, especially if you installed other things when you installed xfce (like if you did a dist-upgrade, for example).

---

### Post by puelly on 2005-03-03
[QUOTE=rosslaird]Are you starting (attempting to start) Gnome from the command line, from the login manager, or from a virtual console?

Linux users don't like to recommend rebooting, but often it does fix this sort of thing, especially if you installed other things when you installed xfce (like if you did a dist-upgrade, for example).[/QUOTE]
 i am trying to start gnome from the login manager.  I tried rebooting and "apt-get install --reinstall gnome-panel" and neither has worked.

---

### Post by rosslaird on 2005-03-03
I'm not sure why the gnome-panel would be implicated here, unless it says so in your .xsession-errors file. So here are a few suggestions:

Check the .xsession-errors file (in your /home directory; note the dot)
Try to find an error message, either in the file above, or in /var/logXorg.0.log
(if you run xf86, it might be a different filename)
Try logging in as another user, and as root, to see if you have the same issue.

Xfce is really good at not messing up your system, so it may not be xfce. Also maybe try renaming .gtkrc-1.2-gnome2 (sometimes that helps). Also try the xfce forum:
forum.xfce.org

Report back...

Ross

---

### Post by az on 2005-03-03
"XFCE 4.2 using debs"

Did you use debian repositories?  If you mix repositories (ubuntu and debian) this thing can happen.

---

### Post by puelly on 2005-03-03
[QUOTE=azz]"XFCE 4.2 using debs"

Did you use debian repositories?  If you mix repositories (ubuntu and debian) this thing can happen.[/QUOTE]
 I used the repositories from here: [http://www.os-cillation.com/article.php?sid=37](http://www.os-cillation.com/article.php?sid=37)

I'll try the suggestions about and let you'll know how things go.

---

### Post by rosslaird on 2005-03-03
Those repositories worked perfectly on my system (Hoary).

---

### Post by puelly on 2005-03-04
I checked the logs and there wasn't anything identifying what the problem would be.  I was able to login using the "Failsafe terminal" and I exectuted "gnome-session."  The gnome interface started after about 10 mins, I could select items in the menu but none of them would start.

I am using Hoary.  I finally fixed the gnome install by updating the gnome packages using aptitude.  It not the solution that I was looking for because I wanted to pin point the problem but I guess it'll have to do.

Thanks for trying to help me out guys.

---

