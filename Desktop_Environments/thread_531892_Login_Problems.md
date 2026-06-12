---
title: "Login Problems"
date: 2007-08-22
forum: Desktop Environments
---

### Post by dedtr9 on 2007-08-22
Just recently i had a problem with my computer not being alble to display the graphical part (Something along the lines of "Cannot start X server"). I followed the steps in a different post, and it   started working again. The login screen was set to default, but I saw nothing else out of order. The problem is that when i try to login with my normal account, it just sits there most of the time, and other times, it just pops up a white box in the upper left corner, and when I put my mouse over it, it turns into a bar cursor. It reminds me one of those note boxes that i put on my side bar. 
The only other thing is that i cannot log into root. On the login screen, it says wrong password. When i try to use sudo on the command line and i get the password right, it doesn't do anything at all, just gives me back my prompt.

---

### Post by prince_niceguy on 2007-08-22
Does it happen also in the recovery mode. Try login in to the recovery mode and type the following command

$ startx

if it starts the x server then you should be able to login into UI with root.

Use it to correct the xserver xorg.conf or any other config issue.

---

### Post by dedtr9 on 2007-08-23
Ok, good. That worked, but I need some help on what part of it to fix, or what part is broken. Is there an error message somewhere that i can post?

---

### Post by zoobave on 2007-08-23
run the following command in recovery mode and replace the old xorg file to new one
# X -configure

regards,
Zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

### Post by dedtr9 on 2007-08-23
That command runs, but I am hesitant on replacing my config file with the one that generated, because when I test it like it suggests, nothing happens; it sits at the thatched background with the 'X" shaped cursor.

I also noticed that my preferred user can login and everything comes up right, but only when i use the failsafe gnome.

---

### Post by prince_niceguy on 2007-08-23
If fail safe gnome is working then there is something wrong with the normal profile. If you do not worry about your setting then try deleting the 

.gnome
.gnome2 

from your preferred user home directory and try.

If you are skeptical about reconfiguring X like stated by zoobave then you can take a back up of the  /etc/X11/xorg.conf. This is the file which will be rewritten.

If something goes wrong then just revert back to this file in recovery console.

---

### Post by zoobave on 2007-08-24
> **dedtr9 said:**
>  it sits at the thatched background with the 'X" shaped cursor.


Yes, you are correct, while you testing with xorg.conf.new file. nothing will happen except 'X' shaped cursor. But, after replacing the original config file with the new one, try to restart the machine or X server. I am damn sure that, it will works.

regards,
Zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

