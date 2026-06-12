---
title: "Konqueror: icon size in file-tree uncontrollable (too large)"
date: 2007-12-11
forum: Desktop Environments
---

### Post by wankel on 2007-12-11
As in the subject: Konqueror views:
[LIST]
[*]tree
[*]info
[*]detailed list
[/list]
These views got an **icon size of 128 **instead of the **configured 16**.

This is actually the third time, on a third machine, where I come across this "problem", so I wondered if it bothered anyone else and if perhaps someone found a suitable remedy.

Each time it happens after customizing the desktop theme: in order to maximize destop real estate, I tend to minimize text and icons. It happened on my wife's laptop long ago (5.10/Breezy), where the solution was to delete the KDE files in her home directory; then on my 6.06/Dapper install, where I just left it and used text view. 

Now I got a new laptop, and after setting the theme to my taste it is broken again :-( Since I dislike throwing away the rest of my customization, set to explore a bit. Without much result though. 
The icon sizes are mentioned in
 ~/.kde/share/config/kdeglobals
Over there all sizes are either 16 or 22. Still my "tree" icons are of size 128 or thereabout. They still listen to the "doublepixels" switch.

This nice gadget that showed a list of similar problems on giving a subject, listed [**someone with a font problem**]("http://ubuntuforums.org/showthread.php?t=143049") (2006), no answers though.

Google and friends did not show up anything useful for me, maybe I used the incorrect keywords. I'll be gratefull for any help or comments!

---

### Post by GeneralZod on 2007-12-11
Can you give a screenshot?

---

### Post by wankel on 2007-12-11
Excuse me! I already prepared them, quite forgot posting them...

Attached you find a screenshot of the tree-view, compared to the "F9-list" of which I keep forgetting the name, and a screenshot of the GUI control for setting the icon size.

---

### Post by GeneralZod on 2007-12-11
Aha!

Tried 

View->Icon Size->Default Size

?

---

### Post by wankel on 2007-12-11
Thanks for your ongoing interest :-)

Defaults were my first try (after making a backup of my theme). 

To double-check, I tried a totally different. standard included theme. I noticed the icons stayed the incorrect size, but also that they did not change colour.

My conclusion is that I have to log out and in, before the icon cache is renewed (not knowing a direct command to enforce it), so that is my next step.

I'll be posting back in a minute or five.

---

### Post by wankel on 2007-12-11
There then... Some change, no success yet. Please refer to the attached screenshots:

1. Set my theme to another; not the icons are not refreshed at once (img ....2.png)
2. After log out/in, icon colours are different, probably matching the theme (img ....3.png)
3. Then changing the icon size of all (four) types of icons in my own them to 22, both in the tar-zipped archive and the directory next to it (~/.kde/share/apps/kthememanager/themes/wbktheme2)
4. Load my own theme, log out/in
5. My theme is there, but not "my" icons (that is, default colours, default size **except** for those icons in the tree view, see image ...4.png)

Any idea?

scuse me for the not-so-5-minutes five minutes... ;-)

---

### Post by wankel on 2007-12-27
Aargh.... It turns out I misinterpreted GeneralZods hint! Since I were changing the theme, I set the icons back to "default" in the theme config.

By coincidence I noticed on (yet another laptop) that the iconsize was set to "Huge". Setting it back to "Default" solved the problem on each setup.

Still wondering how it got to huge in the first place. I never (ever) set icons larger than they are, let alone "huge". There is a faint possibility my way of setting my theme triggers something to change the icons from default to huge instead of tiny, but since my recollection of steps taken while theming is fuzzy at best, filing a bug does not seem so useful.

Any way, end good all good :-)

---

