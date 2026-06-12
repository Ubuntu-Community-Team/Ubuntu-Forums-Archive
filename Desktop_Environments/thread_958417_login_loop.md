---
title: "login loop"
date: 2008-10-25
forum: Desktop Environments
---

### Post by twowheeljones on 2008-10-25
I am new to ubuntu.  I had been trying to install it and had been unsuccessful until i read something on one of the forums where someone had the same problem and logged in via gnome safemode.

My problem was that after installation, I would enter my username and password but ubuntu would return me to the login screen - in short, it was an endless login loop.

After getting in through gnome safemode, i went into the drivers area and saw that it had not installed a graphics/video driver because it was 'untrusted'.   I gave ubuntu permission to install this and rebooted.  It works now.  

I beleive what was happening was after entering the password, it was trying to display something requiring the graphics/video driver, that failed, causing it to loop back to login. 

I wanted to post this hoping that it would help the next person.

---

