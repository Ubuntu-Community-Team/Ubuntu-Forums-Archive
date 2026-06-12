---
title: "remapping keys on the keyboard"
date: 2009-04-25
forum: General Help
---

### Post by bigpook on 2009-04-25
I am using ubuntu 9.04 and want to remap a couple of keys on my model m mini.

What I want to do is remap the 'backslash bar' key that is right above the enter key with the 'backspace key'.

I can use: 
xmodmap -e 'keycode 22 = backslash' 
xmodmap -e 'keycode 51 = BackSpace' 

but I can't figure out how to get 'Shift + keycode 22' to return the bar | character.

Can someone help me out with this?

---

### Post by beartard on 2009-06-06
Not sure if you ever found the answer to your question, but I had the same problem and the following thread answered it...but created another problem in the process  ;)

[http://ubuntuforums.org/showthread.php?t=1010828&highlight=xmodmap+shift](http://ubuntuforums.org/showthread.php?t=1010828&highlight=xmodmap+shift)

---

