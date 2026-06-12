---
title: "Installer Problem: User Creation"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Strag0 on 2005-12-03
Edit: So I just reinstalled Ubuntu and the installer let me past that point. So It looks as if it's 'fixed'.


I'm having some odd issues with the installer. This is my second attempt at installing Ubuntu on my machine. The first attempt went flawless, minus me somehow messing up the App-install program ( Or it messing up, but I blame myself ). 

The installer acts as if it's stuck in a loop when it comes to creating a username and password. When I got to the step that it asks for my full name, username, and password. The installer would loop back to the full name entry once I typed my password in twice. At first I thought it was me putting in the wrong password. However, it wouldn't stop even when I did. Thinking the installer had created a user I used the "<Go Back>" 'button' and finished the install. Rebooted and then was prompted by the second phase install for the need of a password, it claimed I had an "Empty Password". So when I typed mine back in an error appeared below quickly. "....Group does not exsist". Shortly after that I pressed "<Go Back>" and was thown into a command prompt. 

Not being a seasoned linux user I did some research on finding out how to create a user and group for myself, thinking it would easy to do. I got the user made and password set. Rebooted. The second phase of the install finished and Gnome was wanting me to login. Though when I used my Username I manually created. I was told that my home directory was set, and that I could use "/" but it was likely that nothing would work. Correct that was! Nothing worked... not even loging in. 

So now i'm left with a command prompt, and poorly created user and usergroup without a working home directory. The installer still hates me!

Any ideas towards a solution? 

Thank you!********

---

### Post by Ampersand on 2005-12-03
What command did you use to add a user? Did you specify a home directory in it ('--home /home/username' or something similar)?

Since it's a clean install, it might be easiest to try installing again.

---

### Post by Strag0 on 2005-12-03
At the time I didn't specify a home directory. 

That was my issue. 

I ended up reinstalling... and now it works. So i'm pleased.

Thank you for the reply

---

