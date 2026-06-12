---
title: "change password - encrypted homedir -&gt; login fails"
date: 2017-12-08
forum: Desktop Environments
---

### Post by herkules on 2017-12-08
Dear fellow linux-fans!

I've just encountered a "problematic" behavior and wonder if I'm the only one:
 - 1 week-old fresh install of kubuntu 17.10, only real change: kernel update to 4.14 (I need the latest stuff for my shiny new hardware), home directory encrypted during install

 - changed password via "system settings" -> account details
 - reboot
 - the computer boots to the login-screen, I enter the passwort and the computer freezes....

I've managed (using ctrl+alt+F1) to get to a shell. When logging in using this shell, I get the message that the system failed to deencrypt my home directory at login. There is also the command to decrypt the homedir (something with encypt-...-private...) . Once this is done, I call "startx" and plasma boots nicely. 
I can then use the GUI again to set my password back to the old one. Then everything works again

I tried it again to see if this is reproducible and ran into the same problem

--> It seems that setting the password does not change the necessary things to decrypt the homedir during login... 

Anyone else experiencing this problem? (And if yes, I failed on the kubuntu website to find a way to submit bugs...)

---

