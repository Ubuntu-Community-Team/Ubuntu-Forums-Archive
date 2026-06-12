---
title: "Cannot log on the internet"
date: 2005-09-10
forum: Desktop Environments
---

### Post by lou1204 on 2005-09-10
I have a Winmodem, but I found a way for my PC to recognize it (I have Kubuntu Linux). But now, when I use KPPP, it dials and everything, but in the terminal, it shows this message:

"Couldn't find ppp0 interface"

Do you have an idea of how I can fix it?


Also I found this info in another forum:

[I]To solve this problem, I created a new account under the "Accounts" tab 
In the Accounts pop-up, I entered the name and phone number and selected the "Login Script" tab 

The "Login Script" window has a pull down menu with the various acceptable Hayes-compatible commands and a place to enter options to that command. Using this I created the following script: 

Expect name: 
Send <My Login> 
Expect code: 
PWPrompt Passcode: 
Expect Pool> 
Send ppp 

Admittedly, this is a trivial script, but it works  I recommend checking out the manual (mine came with the distro). They have many examples that helped me get my config working. 

The conversation goes as follows: 

kppp expects a string containing name: When it gets it, it sends my login name. 
kppp then expects a string containing code: (my modem pool sends "Passcode:" instead of "Password:") When kppp gets code: it opens up a dialog window and asks for my Passcode. (My modem pool uses SecurID, so my password changes every 60 seconds). 
kppp finally expects the string "Pool>" to which it responds ppp This causes the ppp session to be established. 

This seemed to work for me...hope it helps you as well.[/I]

**My question is: How do I put these parameters in my login script?? Help! I'm just a newbie!**

Your suggestions are highly appreciated  :-P

---

