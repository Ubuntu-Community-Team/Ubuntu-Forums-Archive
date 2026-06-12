---
title: "Can't Customize Window Buttons"
date: 2012-03-07
forum: Desktop Environments
---

### Post by ubunt10 on 2012-03-07
Hi:

I am trying to move my minimize, cascade, and close buttons to the uppoer-right corner of a window, like Windows XP. I found this explanation and it seemed simple enough. 
[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

When I pressed Alt + F2, I did not get the same thing that popped up. Instead, I see this. 
[http://img134.imagevenue.com/img.php?image=170916522_screenshot_122_393lo.jpg](http://img134.imagevenue.com/img.php?image=170916522_screenshot_122_393lo.jpg)

Unfortunately, there is no "Run" button visible anywhere. And when I type "gconf-editor" (without quotes) into the box and press Enter, the only thing that happens is what you see in the image above. I do not see an editor anywhere. It is as if nothing happened. 

I also tried only typing "gconf" (without quotes) by itself and it just closed the without (to my knowledge, that I can see) running any program or editor at all. 

Am I missing a "Run" button? How do I open the gconf editor? Why is the Run box closing when I type "gconf" and press Enter? But not closing when I type "gconf-editor"? Thanks.

---

### Post by wojox on 2012-03-07
Try from the terminal (Ctrl + Alt + T):
```
sudo apt-get update; sudo apt-get install gconf-editor
```

---

### Post by ubunt10 on 2012-03-07
I clicked the "Dash Home" icon, typed in "Terminal", and when it opened, I typed the command [quote]gconf-editor[quote]

The command prompt itself actually told me that it was not installed and stated the exact sudo command with all of the parameters. I typed it in and it worked. Thank you.

---

