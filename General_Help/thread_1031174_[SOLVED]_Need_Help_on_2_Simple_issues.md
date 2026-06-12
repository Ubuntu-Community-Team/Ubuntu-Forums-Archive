---
title: "[SOLVED] Need Help on 2 Simple issues"
date: 2009-01-05
forum: General Help
---

### Post by sendblink23 on 2009-01-05
Yeah 2 simple help issues.. I hope ***#1 has been Fixed***


***2nd.** [COLOR="Red"]I got a Cairo Dock issue[/COLOR]...  is it normal.. that certain folders you add, it appears files like multiplied inside of it (in the sub menu)..   and in the actual Folder you only have the file 1 time only?? look at my Print Screen you will see 1 file I have.. it appears 4 Times multiplied in the submenu (I only have that file 1 time in the actual Folder)


PrintScreen: [http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png](http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png)






**[COLOR="Red"]*[FIXED][/COLOR]** 
[COLOR="SlateGray"]1st.  Every time I open up *Firefox from the Icon .. it always opening up FULL SCREEN.. above the whole Monitor (I was playing around with Keyboard shortcuts.. this one is not coming off for FireFox)

PrintScreen: [http://i29.photobucket.com/albums/c272/sendblink23/FullScreenError.png](http://i29.photobucket.com/albums/c272/sendblink23/FullScreenError.png)[/COLOR]**[COLOR="Red"]*[/COLOR]**

Thanx to: *[COLOR="Orange"]mike2357[/COLOR]*

Process:
[COLOR="DarkOliveGreen"]I imagine there's a local setting that somehow went bad. I suggest doing the following:[/COLOR]

[COLOR="DimGray"]1. Using firefox, export your bookmarks to a file.
2. Shut down firefox, and then rename the directory that has all of your local firefox settings to something else. This can be done by:
Code:[/COLOR]

mv ~/.mozilla ~/.mozilla_bak

[COLOR="DimGray"]3. Restart firefox. This will cause the ~/.mozilla directory to be re-created.
4. Import your bookmarks from the file you saved in step 1.[/COLOR]




.................

I'll appreciate any help with these ;)

---

### Post by sendblink23 on 2009-01-05
**bump**

---

### Post by sendblink23 on 2009-01-05
At least help.. on the Full Screen ...  on my  FireFox issue..

I don't want to see that always happening when only clicking Firefox icon.. and boom.. covering up my whole monitor Screen .. then having to hit 2 time F11 to Resize it


Any help??

---

### Post by joshmuffin on 2009-01-05
I used to have that firefox issue, good to know its gone in jaunty alpha 2.
You could try about:config I'm pretty sure that'll do it though you'd have to do some research, I've never done it.

---

### Post by mike2357 on 2009-01-05
I imagine there's a local setting that somehow went bad.  I suggest doing the following:

1.  Using firefox, export your bookmarks to a file.
2.  Shut down firefox, and then rename the directory that has all of your local firefox settings to something else.  This can be done by:
```
mv ~/.mozilla ~/.mozilla_bak
```
3.  Restart firefox.  This will cause the ~/.mozilla directory to be re-created.
4.  Import your bookmarks from the file you saved in step 1.

Post back if this doesn't solve the problem.  If not, I'd be curious if you have this problem only in firefox or in other applications.

---

### Post by arno1991 on 2009-01-05
i would advise to just backup your bookmarks and to reinstall firefox if firefox would be the problem. I have the same problem too, with popups, but it is only when my Desktop-effects are enabled...

---

### Post by sendblink23 on 2009-01-05
That totally fixed it =) thnx


> **mike2357 said:**
> I imagine there's a local setting that somehow went bad.  I suggest doing the following:

1.  Using firefox, export your bookmarks to a file.
2.  Shut down firefox, and then rename the directory that has all of your local firefox settings to something else.  This can be done by:
```
mv ~/.mozilla ~/.mozilla_bak
```
3.  Restart firefox.  This will cause the ~/.mozilla directory to be re-created.
4.  Import your bookmarks from the file you saved in step 1.

Post back if this doesn't solve the problem.  If not, I'd be curious if you have this problem only in firefox or in other applications.

---

### Post by sendblink23 on 2009-01-05
Issue #1 has been fixed! =)

Now...   **Need help on Issue #2**


*2nd. I got a Cairo Dock issue... is it normal.. that certain folders you add, it appears files like multiplied inside of it (in the sub menu).. and in the actual Folder you only have the file 1 time only?? look at my Print Screen you will see 1 file I have.. it appears 4 Times multiplied in the submenu (I only have that file 1 time in the actual Folder)


PrintScreen: [http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png](http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png)

Any way of fixing that???

---

