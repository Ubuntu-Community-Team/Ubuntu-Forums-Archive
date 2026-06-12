---
title: "Change Lockscreen-mask"
date: 2013-01-22
forum: Desktop Environments
---

### Post by Matze208 on 2013-01-22
Hey,

this is my first post and iam not a native speaker so excuse my bad english :(

I use Ubuntu 12.04 on my Toshiba Satellite Notebook as a parallel installation with windows. I really like ubuntu, but i've a question about the Lockscreen of Ubuntu. With STRG + ALT + L you can lock your workspace. You'll see your desktop wallpaper and you have to enter your password in a mask. But my mask is white-colored and covers peaces of the background picture, so is it possible to change the color of this ? Maybe no color (transparent). 

Thank you very much
Matze208

---

### Post by stinkeye on 2013-01-23
Possibly have a look at xtrlock.
From man page...
> DESCRIPTION
       xtrlock locks the X server till the user enters their password  at  the
       keyboard.

       While  xtrlock  is  running, the mouse and keyboard are grabbed and the
       mouse cursor becomes a padlock.  Output displayed by  X  programs,  and
       windows  put  up  by new X clients, continue to be visible, and any new
       output is displayed normally.

       The mouse and keyboard are returned when the user types their password,
       followed  by Enter or Newline.  If an incorrect password is entered the
       bell is sounded.  Pressing Backspace or Delete erases one character  of
       a  password  partially  typed; pressing Escape or Clear clears anything
       that has been entered.

       If too many attempts are made in too short a  time  further  keystrokes
       generate bells and are otherwise ignored until a timeout has expired.

       The  X  server  screen saver continues to operate normally; if it comes
       into operation the display may  be  restored  by  the  usual  means  of
       touching a key (Shift, for example) or the mouse.


---

