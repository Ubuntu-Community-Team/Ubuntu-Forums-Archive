---
title: "Problem with keyboard layout"
date: 2009-05-17
forum: General Help
---

### Post by Shex Nivis on 2009-05-17
Hello fellows,
I got a little trouble with my keyboard layout. At graphic mode everything works fine, using 
Keyboard Model: Toshiba Satellite S3000, and Layout: EUA international Alternative (old us_intl). Not sure if names are right since I run the system on Portuguese, so I just translated it to English.
As I said everything works fine at the Graphic Mode even special characters such as ç and ã. The problem is when I change to text mode (CTRL + ALT + F1) when I am there the layout changes itself to Arabic or something like that which makes me unable to log in or do anything else. 
Some time ago, I had by mistake changed the keyboard layout to arabic wich made me not able to log in on graphical mode, because I wasnt able to type my login and password. But I fixed it by using a Live CD and changing some file that I can't remember right now at the etc folder. 
Doing that I got the graphical mode back to normal but as I said the text mode is unusable.
Any ideas?
Thanks for the help and the time, and sorry for any trouble with my English.
Yours,
Shex~

update: Fixed it. The solution was using sudo dpkg-reconfigure console-setup and manually reconfiguring the console

---

