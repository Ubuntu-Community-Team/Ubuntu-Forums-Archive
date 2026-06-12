---
title: "Bug in the places menu (screenshot)?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Laterix on 2006-06-07
Am I the only one who got this wierd label for Destop? It looks like a bug to me. My laptop says only "Desktop" and both computers have all latest updates.

Any ideas how to fix this?
[IMG]http://users.utu.fi/ljtaim/pics/desktop.png[/IMG]

---

### Post by mgmiller on 2006-06-07
What you are seeing is the default icon for the desktop in the Dapper human icon set.  It's not a bug, it's a feature!  If you want to change it, go to System>preferences>Theme and for your current theme, click the theme details button and then click the icon tab.  Select a different icon set.  They change as soon as you click on them, so you can try different ones quickly without exiting the themes menu.  There are lots of themes and icon sets available online all over the place, if you find one you really, like, download the file.  It will come in as a tar.gz usually.  With the themes application open, just drag the tar.gz file onto it and it will install the theme or icon set automatically (yes, it's that easy).  They are immediateley availabe for use.  I just installed a new icon set called dropline neu! That I really like.  You can get it here along with many other themes and icons:   [http://www.gnome-look.org/](http://www.gnome-look.org/)

Have fun!

---

### Post by mynimal on 2006-06-07
He's talking about the name, not the icon.

---

### Post by danyer on 2006-06-07
Oh, yes. It drove me crazy. I installed Dapper on a clean computer (repartitioned to erase Breezy) and there it was.
I've made some grep-s through the files system and I've found that label in some  locale for Australia. Hmmm, I thought I've selected British English...

Anyway, the solution was to go to System|Administration|Language Support and select English (UK) as the Default Language instead of English (Australia).

So, there are two bugs in one: It selects the default language to be English (Australia) and the label is wrong. You can avoid the first one if you live somewhere else, but if you live in Australia there is no solution to fix the label (it is in a binary file), please report it as a bug.

Regards,
Dan.

P.S. After submitting I saw that your location is Finland. Congratulations for Eurovision ;)

---

### Post by Laterix on 2006-06-08
[QUOTE=danyer]
Anyway, the solution was to go to System|Administration|Language Support and select English (UK) as the Default Language instead of English (Australia).

P.S. After submitting I saw that your location is Finland. Congratulations for Eurovision ;)[/QUOTE]
ROARRR.... it's finnish and means thanks ;).

And thanks for the tip, but it didn't change the text label for me. :(

---

### Post by danyer on 2006-06-08
Let's see if it is the same bug. When it happened to me,
1. the Wastebasket icon was renamed to Garbage Bin
2. the Desktop was renamed to Desktop|Desktop Folder
3. the default Language was set to English (Australia)

How many of the symptoms do you have?

Cheers,
Dan.

---

### Post by Rondonjin on 2006-06-08
[QUOTE=danyer]Let's see if it is the same bug. When it happened to me,
1. the Wastebasket icon was renamed to Garbage Bin
2. the Desktop was renamed to Desktop|Desktop Folder
3. the default Language was set to English (Australia)

How many of the symptoms do you have?

Cheers,
Dan.[/QUOTE]

That's exactly what I had! I changed the language preference to English (UK) in the menu (isn't that only for new acounts?) Logged out, changed the language on the login screen to English (UK) and logged back in and everything was fine.

Wayne

---

### Post by Laterix on 2006-06-09
[QUOTE=danyer]
1. the Wastebasket icon was renamed to Garbage Bin
2. the Desktop was renamed to Desktop|Desktop Folder
3. the default Language was set to English (Australia)
[/QUOTE]
I have it all. I have to try if logout helps.

---

### Post by danyer on 2006-06-12
Did logging out and in again work for you?

---

### Post by Laterix on 2006-06-12
[QUOTE=danyer]Did logging out and in again work for you?[/QUOTE]
Yes, it did! Now it's all nice again. Thanks for your help.

---

