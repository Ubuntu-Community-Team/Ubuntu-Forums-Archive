---
title: "[SOLVED] Show Desktop Custom Applet"
date: 2008-11-17
forum: Desktop Environments
---

### Post by jesuisbenjamin on 2008-11-17
*This is one of those threads i gonna regret starting, thinking 'What the hell are you busy with Benjamin?' but hey my stubborn and curious instinct have the upper hand.*

My computer insisted on having a transparent panel so i gave it to her, now she is complaining about the Shut Down and Show-Desktop buttons which are not very good looking and not transparent at all versus the rest of the panel.
The Shut Down button i solved already by recreating a new launcher with the *gnome-session-save --shutdown-dialog* command.
The show desktop however -as i have read on another thread- isn't a command but a function within a program. So i cannot use the same solution as the above button. 
However, Cairo Dock offers the possibility to create a launcher so as to simulate Show Desktop. It works by attributing a key combo to the command field, in this case: <Ctrl><Alt>d would do the trick.
This is provoking my curiosity and i really would like to know how i could do this with gnome launcher.
Attributing the launcher to a script that would simulate the key combo seems a bit cumbersome, there must be some simple way to achieve this.

For the sake of exercise, i find this problem quite cool actually. 
Has anyone any suggestion?

:)

---

### Post by jesuisbenjamin on 2008-11-18
bump! ):P

---

### Post by hictio on 2008-11-18
I'm sorry, I'm not that clear on what you want...
You want to create a script/ program that you can put on a launcher so, when you execute it, it will do exactly what <Ctrl><Alt><d> does on oyur box right now? That is, showing your desktop?

If so, I have done that a couple of years ago on FreeBSD when the faux Os X fever was high with me :D .
Had an applet added to the Gdesklet StarterBar, that, upon clicking on it, minimized all the windows, and, when clicked again, placed all the windows back in place.
Used 'wmctrl' for that, you can install it with 'sudo aptitude install', and this script as the launcher:

```

#!/usr/local/bin/bash

SWITCH="/tmp/_ON"

if [ -a "$SWITCH" ]; then

/usr/local/bin/wmctrl -k off && /bin/rm /tmp/_ON

else

/usr/local/bin/wmctrl -k on && /usr/bin/touch /tmp/_ON

fi
# EOF #

```

[Here](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/346009106631?r=346009106631#346009106631) is the whole story.

---

### Post by jesuisbenjamin on 2008-11-18
> **hictio said:**
> I'm sorry, I'm not that clear on what you want...

Oh yes you are :D Thanks very much i'm going to try this funny thing :popcorn:

---

### Post by hictio on 2008-11-18
> **jesuisbenjamin said:**
> Oh yes you are :D Thanks very much i'm going to try this funny thing :popcorn:

Ja ja ja, I'm glad I did. Good luck, be sure to customize the paths on the example above!

---

### Post by jesuisbenjamin on 2008-11-19
> **hictio said:**
> 

```

#!/usr/local/bin/bash

SWITCH="/tmp/_ON"

if [ -a "$SWITCH" ]; then

/usr/local/bin/wmctrl -k off && /bin/rm /tmp/_ON

else

/usr/local/bin/wmctrl -k on && /usr/bin/touch /tmp/_ON

fi
# EOF #

```



Hey thanks again,

The script was edited accordingly:

[LIST]
[*]bash is found in /bin/ rather than /usr/local/bin/
[*]and wmctrl is found in usr/bin/ rather than /usr/local/bin/
[/LIST]

Then i specified to open the script with *bash* in the script properties (i don't know how to do that with a command) and created the launcher, which should open the script.

Funny thing is: when i click on the script it works, when i click on the launcher it doesn't... i get the message: 
[QUOTE=Benjamin's computer][CENTER]**Could not launch application**
Failed to execute child process "/home/benjamin/show_desktop" (Permission denied)[/CENTER][/QUOTE]

How is this possible?
:-k

---

### Post by hictio on 2008-11-19
This is strange.
The "/home/benjamin/show_desktop" is executable, right?

Other thing you might try, is on the launcher settings, on the command one, adding the full path to bash in front of the full path to the script itself.

```

/bin/bash /home/benjamin/show_desktop

```

---

### Post by jesuisbenjamin on 2008-11-19
Yes, i turned the script into an executable with chmod -x
[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)
This last thing is working :) yes!

Funny to notice there is a little delay of execution in comparison with the gnome button. :-$

Thanks for sharing!

---

### Post by hictio on 2008-11-19
Cool,I'm glad it worked for you :D
I really don't recall if it was any slower than the Gnome's builtin... It was a long time ago.

---

### Post by edxabbey on 2009-10-25
> **jesuisbenjamin said:**
> **
...The show desktop however -as i have read on another thread- isn't a command but a function within a program...
However, Cairo Dock offers the possibility to create a launcher so as to simulate Show Desktop. It works by attributing a key combo to the command field, in this case: <Ctrl><Alt>d would do the trick.


Thank you for this!  You stimulated how I will add launchers too, as well as solving a major annoyance for the "show desktop" launcher.  I hve moved from AWN to Cairo, and was thinking that it was way better, but took more figuring out.  I guess the best things you have to work for.  Thanks again.

-ed

---

