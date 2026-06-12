---
title: "Stop Logging me out!"
date: 2006-12-05
forum: Desktop Environments
---

### Post by touchlikefire on 2006-12-05
Whenever I type the key combination **SHIFT + BACKSPACE**, even in a text input field, I am immediately, without question, logged off.:evil: 

I don't think this is default behavior, and as you can imagine it has put me in quite a state since I can barely get anything written w/o accidentally logging off.  If memory serves from my windows days (all of six months ago), I think it's a legitimate key combo in that OS.

Anywho, how do I stop this from happening?  I never want to log out with any key, whatsoever, if it will stop this combination from causing me so much misery.

---

### Post by yabbadabbadont on 2006-12-05
Check System->Preferences->Keyboard Shortcuts and see what the logout shortcut says.  By default, it is Disabled.

---

### Post by touchlikefire on 2006-12-05
That was my first thought, too.  But it is disabled there, and I have a third party plugin/option **System > Preferences > Advanced Preferences** which allows you to do shortcuts as well, but it's not in there either.

But it's confirmed that the key combo is not default behavior for X or Gnome?

---

### Post by 3rdalbum on 2006-12-06
No, it's not default behaviour for X or Gnome. It is, however, the default behaviour for XGL.

---

### Post by touchlikefire on 2006-12-06
Bummer...I suppose there's no way to turn it off, then?

---

### Post by CatKiller on 2006-12-07
> **touchlikefire said:**
> Bummer...I suppose there's no way to turn it off, then?

Well, there's at least two from a cursory search:

> **s_p_a_r_k_y said:**
> Edit /usr/bin/compiz-start and add this line at the end to fix this problem:


xmodmap -e "keycode 22 = BackSpace Delete" 

Or

> **woedend said:**
> try adding this to your "sessions" startup program, or to a script you may use to launch beryl.  This is for a standard US type keyboard.

setxkbmap -model pc105 -layout us -variant basic

There may well be more.

---

### Post by RAOF on 2006-12-07
What version of XGL are you using?  I'm now using Feisty's nVidia drivers, but when I was running XGL that problem had been fixed for **months**.

---

### Post by natrixgli on 2006-12-31
A great tool to help you fix this is xkeycaps

```
sudo apt-get install xkeycaps
```


-n8

---

### Post by iamhugeinjapan on 2006-12-31
Open a Terminal and put this in:

```
xmodmap -e "keycode 22 = BackSpace"
```

Then press Shift+Backspace

If you don't get logged out,  go to Systems - Preferences - Sessions then the Startup Programs tab. Click 'Add' and paste in the text I gave you. You shouldn't get logged out anymore.

On some systems even having that text in the Startup tab doesn't keep it. So what I do is save it to an executable script and put the script in the Startup folder.

To create the script:

Open a Text Editor and paste in the code above. Then save it to your home folder as something like nologout.sh
Then view your home folder and right click nologout.sh and choose Properties. Then the Permissions tab. Check the box by 'Allow executing file as program'
Then add nologout.sh to your Sessions - Startup folder.

---

