---
title: "How to make wallpaper change every N minutes?"
date: 2009-11-13
forum: Desktop Environments
---

### Post by Screatch on 2009-11-13
I seen this feature in Mandriva and i am missing it in Kubuntu, how to make my wallpaper change randomly to ones in a specified folder every N minutes?

---

### Post by bluelamp999 on 2009-11-13
Take a look at this thread - [http://ubuntuforums.org/showthread.php?t=1281218](http://ubuntuforums.org/showthread.php?t=1281218)

---

### Post by Screatch on 2009-11-13
Doesn't works very well.
Returns me an error
> > &#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;&#1099;&#1081; &#1092;&#1072;&#1081;&#1083;.sh: 7: arithmetic expression: expecting primary: "  % (11 + 1) "

I am not very good with bash and i can't to seem to figure out what the problem is.
The line he is complaining on is 
random_num=$(( $RANDOM % ($length + 1) ))

---

### Post by Screatch on 2009-11-13
I think i found the application that does what i want, named Wally. ([http://kde-apps.org/content/show.php/Wally?content=98455](http://kde-apps.org/content/show.php/Wally?content=98455))

But i can't seem to get it change wallpapers, maybe i am doing something wrong?

---

### Post by Screatch on 2009-11-13
Got it working, had to switch in settings to Wallyplugin.
Problem solved.

---

### Post by verman on 2009-11-13
try this
=;
[http://linuxdesk.wordpress.com/2009/04/02/how-to-change-wallpaper-easily-with-wallpapoz/](http://linuxdesk.wordpress.com/2009/04/02/how-to-change-wallpaper-easily-with-wallpapoz/)

:P):P

---

### Post by gacb on 2011-08-02
You need to have Wally up and running to get it working. I started it as a command line, but didn't want to keep the terminal running, so I added it via alacarte (main menu).

---

