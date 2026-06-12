---
title: "5 button mouse in nautilus"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Angry penguin on 2006-09-03
I have a GE (General Electric) 5 button mouse or 7 button mouse as dapper detects it. That said, it's a pretty generic mouse.

Anyhoo. I used xev to figure out what number each of my buttons were assigned to. 

button 1= left click
button 2= middle click
button 3= right click
button 4= scroll up
button 5= scroll down
button 6= nothing
button 7= nothing
button 8= thumb button
button 9= pinky button         (BTW I'm right handed)

I then created this file:

```
  sudo gedit /etc/X11/Xsession.d/57xmodmap
```

and pasted this text into it:
```

  #/bin/bash
  xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

I then made the file executeable with:

```
sudo chmod 777 /etc/X11/Xsession.d/57xmodmap
```

Then I restarted, and my forward and back buttons worked inside Firefox. 

Now I just gotta figure out how to get them working in Nautilus...
any ideas?

---

### Post by Anduu on 2006-09-03
Here ya go ;)

[http://www.ubuntuforums.org/showthread.php?t=44191&highlight=imwheel](http://www.ubuntuforums.org/showthread.php?t=44191&highlight=imwheel)

---

### Post by Angry penguin on 2006-09-04
with a couple modifications, that worked. Thanks\\:D/

---

### Post by Angry penguin on 2006-09-04
UNBELIEVABLE! I installed a bunch of updates, because I just did a clean install. Now my forward and back buttons don't work anymore in firefox or nautilus. WTF! 
Anyone know how to fix this? Undo updates, or figure out what the hell happened?

**EDIT: Now it it's working again. I wish this damn thing would make up its mind.:???:

---

### Post by Anduu on 2006-09-04
Glad to help :)

---

