---
title: "Cannot Logout"
date: 2014-07-07
forum: Desktop Environments
---

### Post by mooreted on 2014-07-07
Running Ubuntu 14.04 x64.

I installed Xubuntu and most things work well however, I can't log out. When I click the logout button in the indicator plugin a window will pop up asking if I want to log out. I click "Log Out" and nothing happens. If I open a terminal and type "xfce4-session-logout" it will eventually logout, but it takes two or three minutes to do so.

I have checked all the system logs and can't find any errors related as far as I can tell. I removed the ~/.config/xfce4 directory to go back to default settings. Naturally I have rebooted many times.

Any idea where to look to determine why xfce won't let me log out?

---

### Post by mctiew on 2014-07-07
Happened to me also. I also have no idea if it is my own wrong doing or what.

---

### Post by Toz on 2014-07-08
> **mooreted said:**
> Running Ubuntu 14.04 x64.

I installed Xubuntu and most things work well however, I can't log out. When I click the logout button in the indicator plugin a window will pop up asking if I want to log out. I click "Log Out" and nothing happens. If I open a terminal and type "xfce4-session-logout" it will eventually logout, but it takes two or three minutes to do so.

I have checked all the system logs and can't find any errors related as far as I can tell. I removed the ~/.config/xfce4 directory to go back to default settings. Naturally I have rebooted many times.

Any idea where to look to determine why xfce won't let me log out?

First, try clearing your sessions cache. Since you are having troubles logging out, its better if we do this from outside of Xfce to be sure that its done correctly. 

1. When you are at the log in screen before you log in, press Ctrl+Alt+F1 to go to the first tty (a text screen).
2. Log into this text console using your username and password.
3. Enter the following commands (be extra careful using the "rm -rf" command):
```
cd .cache
rm -rf sessions
exit
```
4. Return back to the graphical log in screen by pressing Ctrl+Alt+F7.
5. Log in. 
6. Try logging out to see if its any better.

Background: Xfce creates and manages [user sessions]("http://docs.xfce.org/xfce/xfce4-session/start"). Sometimes these sessions get corrupted and need to be cleared. The process above is the manual method of clearing these sessions. An automated process exists (Settings Manager >> Session and Startup >> Sessions tab >> "Cleared saved sessions"), but in the case of log out issues, we can never be sure that the corrupt session information isn't being written back. Hence the manual method.

---

### Post by mooreted on 2014-07-08
Thank you, that enabled me to logout from the normal Xfce logout button. I don't know why the indicator plugin doesn't allow me to log out. I assume it's issuing the wrong command. But, I just won't use it.

Thank you for the help.




> **Toz said:**
> First, try clearing your sessions cache. Since you are having troubles logging out, its better if we do this from outside of Xfce to be sure that its done correctly. 

1. When you are at the log in screen before you log in, press Ctrl+Alt+F1 to go to the first tty (a text screen).
2. Log into this text console using your username and password.
3. Enter the following commands (be extra careful using the "rm -rf" command):
```
cd .cache
rm -rf sessions
exit
```
4. Return back to the graphical log in screen by pressing Ctrl+Alt+F7.
5. Log in. 
6. Try logging out to see if its any better.

Background: Xfce creates and manages [user sessions]("http://docs.xfce.org/xfce/xfce4-session/start"). Sometimes these sessions get corrupted and need to be cleared. The process above is the manual method of clearing these sessions. An automated process exists (Settings Manager >> Session and Startup >> Sessions tab >> "Cleared saved sessions"), but in the case of log out issues, we can never be sure that the corrupt session information isn't being written back. Hence the manual method.

---

### Post by Toz on 2014-07-09
Good to hear that it worked. 
> I don't know why the indicator plugin doesn't allow me to log out. I assume it's issuing the wrong command.
The Indicator Plugin doesn't have a logout option. Do you mean the "Actions Button" plugin? And by "Normal Xfce logout button", are you referring to the one in the Whisker Menu?

---

### Post by mooreted on 2014-07-09
There is a button in the indicator plugin as shown by the arrow below. When clicking logout the dialog opens. However, clicking "Log Out" does nothing:

[https://drive.google.com/file/d/0B7OBAVz87uTLS3Q4S0xSLUpIbzA/edit?usp=sharing](https://drive.google.com/file/d/0B7OBAVz87uTLS3Q4S0xSLUpIbzA/edit?usp=sharing)

---

### Post by Toz on 2014-07-09
Okay, that's the Action Buttons plugin. I'm having an issue with it as well on 14.04 on one of my systems. Perhaps best to just remove it from the panel and not use it. I'll see if I can figure out why its mis-behaving.

---

### Post by mooreted on 2014-07-09
> **Toz said:**
> Okay, that's the Action Buttons plugin. I'm having an issue with it as well on 14.04 on one of my systems. Perhaps best to just remove it from the panel and not use it. I'll see if I can figure out why its mis-behaving.

Oh, ok. My PIA VPN icon disappears if I remove it so I'll just ignore that part of it. So far I haven't found much online, but I was using "indicator plugin" in my searches. I'll try again.

Thanks for all the help.

---

