---
title: "Display Help"
date: 2005-04-19
forum: Desktop Environments
---

### Post by anp on 2005-04-19
After I type in my username and password at the login screen, the screen goes blank and the it starts loading but after a while it just jumps back to login screen again. When i try going to the terminal, the display looks really weird and keeps changing from one form to another.
This does not happen on a test account i created. Could someone please tell me what to do

---

### Post by kassetra on 2005-04-19
[QUOTE=anp]After I type in my username and password at the login screen, the screen goes blank and the it starts loading but after a while it just jumps back to login screen again. When i try going to the terminal, the display looks really weird and keeps changing from one form to another.
This does not happen on a test account i created. Could someone please tell me what to do[/QUOTE]

Ok, what I'm going to have you do is temporarily move a file and see if you can login as yourself normally.

In a terminal window (even if it's weird) -  
 ```
cd .gnome2
mv session session.old
sudo init 6

``` 

That will temporarily remove your session file and you should be able to login as normal... *should*

---

### Post by anp on 2005-04-19
In the terminal it says that the session file does not exist. And one more thing is that to get into this terminal, i had to loging using my test account, go into my terminal and login again using my main account.
If i try going into the terminal straight from the login screen, it shows up for a second, the screen goes blank and then it returns to the login screen.

---

