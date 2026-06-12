---
title: "keepass autotype keyboard layout error"
date: 2011-12-27
forum: Desktop Environments
---

### Post by tried_everything on 2011-12-27
Hello,

after searching many webpages I was not able to solve my issue.
My system is a 64-bit system running ubuntu 11.10. I decided to use keepass in the future due to multi platform support. The OS is English and my keyboard is german.
The installed keepass (installed via software center) version is 2.16. Keepass started fine and I inserted a new entry. When the autotype function was launched it reported that I need to install the xdotool. 
Done via software center. Now when I launch the autotype the character z gets exchanged with the y (german vs. us keyboard). When I check my keyboard layout settings I only have one keyboard installed namely the german. I have the funny feeling that autotype interprets my keyboard as being us/uk since my OS is installed in english even my keyboard is in german.
While spending some reasonable time in the web I have read that this might have to do with the xdotool but Icould not solve the issue.
Anybody here who faced the same issue and was able to solve it?

Update 1: Now I added an additional keyboard deleted the german one. Added the german one again and deleted the other. Then it worked however now after the reboot auto-type behaves the same as before. 
Update 2: I have contacted now the xdotool user community and got the tip to enter at the terminal window "setxkbmap de". This works as a workaround needs to be done everytime after reboot. They suggested to add this to the login script. 
Update 3: I have added now the "setxkbmap de" to my login script ".profile" and everything works.

I hope this helps others facing the same issue.

---

