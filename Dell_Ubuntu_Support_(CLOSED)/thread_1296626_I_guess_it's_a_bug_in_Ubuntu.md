---
title: "I guess it's a bug in Ubuntu"
date: 2009-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Amandis on 2009-10-20
Hey Friends

I downloaded today ubuntu fron downloaddotcom it is the version that you can install on your current windows, anyway I installed it on my vista, and everything went very smooth and I really loved it, and will say enough to Mr Gits.
The only problem I have right now is that I can not see the desktop when I log in to Ubuntu, How did this happened?
I was playing with the desktop appearance, and I put 1440*xxx. I have a dell 19" monitor, so  everytime I log in to Ubuntu it gives me an error message that it cant generate that size of 1440*xxx. I tried to recovery Ubuntu but it did not work. it my first time using Linux I checked in documentations I did not find nothing or maybe I did not look in the right place.
Any Idea on how to fix this pelase and thank you?

Bou

---

### Post by superdav42 on 2009-10-21
So what you mean is Ubuntu boots up the login screen and then when you login there you cannot see anything?

I'm guessing it is set to a resolution that your monitor does not support so you cannot see anything. 

To fix it select the failsafe session in the menu at the bottom of the login screen.

Once you login you'll be greeted with a command line. 
Enter the command ```
gnome-display-properties
``` then you can change the resolution back to what it was and it should work again. Used ```
exit
``` to logout and back in again.

---

