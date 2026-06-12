---
title: "Broken &quot;Desktop&quot; link in Places Menu"
date: 2009-05-29
forum: General Help
---

### Post by EricPope on 2009-05-29
Howdy!
When I switched to Japanese language and back to English the desktop folder link in my places menu didn't switch back to English. As you may know, when you switch over to Japanese you get the chance to let Ubuntu rename all your default folders in your user folder  in Japanese. So Desktop becomes &#12487;&#12473;&#12463;&#12488;&#12483;&#12503; and the videos folder goes to &#21205;&#30011; et cetera. Wanting to get the full experience I said yes to the prompt and my folders were renamed. 

Having experienced Ubuntu in Japanese I decided to switch back to jolly old American English. Sadly however there was no convenient folder renaming dialog to convert the folder names back into my native tongue! I set about changing the names myself, only to discover that the link to the desktop in the places menu was still pointing to a folder called /home/eric/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503; and not the English "desktop" 

Anyone know how to fix the desktop link in the places menu?

Domo arigato! ;)
Eric

---

### Post by VCoolio on 2009-05-29
Check the file ~/.config/user-dirs.dirs and see if the folders are properly named there. Just a guess.
Also see if you can edit the folders by rightclicking the menu and choose 'edit 
menu' (which is the same as system > preferences > main menu).
And try system > preferences > language settings, I think there is the option to control the user folders names (not on gnome now, can't check myself).

---

### Post by EricPope on 2009-05-29
Thanks for the response VCoolio, I didn't know about the user-dirs file... i'm still having trouble though. Here's what happened when I tried your suggestions:

> **VCoolio said:**
> Check the file ~/.config/user-dirs.dirs and see if the folders are properly named there. Yes, they were properly named there.

> **VCoolio said:**
> Also see if you can edit the folders by rightclicking the menu and choose 'edit menuThe Places menu didn't show up in this dialog... it just showed Applications and System.

Do you have any other ideas?

---

### Post by VCoolio on 2009-06-02
Hi, maybe you already solved your issue (if so, post the solution here for future readers). But this may work: in the same .config folder I have a file named user-dirs.locale which contains only "en_US" (without the ""). So I guess you have to put your locale there and restart x / login again. Hope that works.

---

### Post by EricPope on 2009-06-02
Hi again VCoolio. I don't have a user-dirs.locale file in my .config folder. 

I still haven't figured out how to fix the link yet. Maybe I should file this as a bug?

---

### Post by mcduck on 2009-06-02
Try running "xdg-user-dirs-gtk-update" in a terminal.

---

### Post by EricPope on 2009-06-02
Aiiyaaa~! :o mcduck, I am joining your fan club! The incantation you supplied fixed my problem.

---

### Post by mcduck on 2009-06-02
> **EricPope said:**
> Aiiyaaa~! :o mcduck, I am joining your fan club! The incantation you supplied fixed my problem.

Great that it worked. :)

I've understood that's supposed to run automatically after switching your language, but it doesn't seem to happen if you switch the language to English..

Still, it's nice to at least have a command to do the trick instead of having to update all configuration files by hand. :)

---

