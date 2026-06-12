---
title: "Loggin In As Root"
date: 2006-03-14
forum: Desktop Environments
---

### Post by nakile on 2006-03-14
Well, I have a few questions.

When I start up Ubuntu, and it loads everything, I'm asked to log in every time. Now this is  a family computer, is there a way I can set it up so it automaticaly logs in and goes to the desktop?

Also, how do I log in as root? I've searched the forum for a little bit and tried a few of the things I've read, but now I can do anything that ask me for a password, I just enter my password and the box goes away and nothing opens, or it says the password is wrong.

Thanks.

---

### Post by 4dz0 on 2006-03-14
The root account is disabled to login by default in ubuntu, to gain root priveleges you need to use the sudo command. For example to open up gedit do:

sudo gedit

When asked to enter a password the password should be the same as your usual login password.

---

### Post by rjwood on 2006-03-14
You can set up an other user acct <system>administration>users&groups..
add user and make it a user name and password that everyone in the family knows  but don't make it too simple for security reasons. The default acct should be for you alone as the administrator. DON'T give that password out to anyone else. Not because they will intentionally harm your system, but may do something by mistake. In Ubuntu, you are an actual administrator not just a term as in (ah well you know what). Be smart-be careful and welcome to ubuntu!!

edit: don't go messin with root untill you are more comfortable with the system!!!Good Luck!!!

---

### Post by nakile on 2006-03-14
Ok, now how can I get my admin permissions back? I can't do anything.

---

### Post by ajgreeny on 2006-03-14
[QUOTE=nakile]Well, I have a few questions.

**When I start up Ubuntu, and it loads everything, I'm asked to log in every time. Now this is  a family computer, is there a way I can set it up so it automaticaly logs in and goes to the desktop?**

Also, how do I log in as root? I've searched the forum for a little bit and tried a few of the things I've read, but now I can do anything that ask me for a password, I just enter my password and the box goes away and nothing opens, or it says the password is wrong.

Thanks.[/QUOTE]

Open up the login screen setup from the menus in the panel and on the last tab of that you will see an option to login to the desktop automatically, with a few warnings about security.  If you're happy about that go ahead.  You need to do this as root so click the administrator icon? (I think that's what it's called) and put in your normal login password for the first user.  Next time you boot up it should go straight to the desktop

---

### Post by Ramses de Norre on 2006-03-14
Does the sudo command work? Can you do a sudo updatedb for example?
To login directly: system > administration > login screen setup  there is an option for it.

---

### Post by nakile on 2006-03-14
[QUOTE=Ramses de Norre]Does the sudo command work? Can you do a sudo updatedb for example?
To login directly: system > administration > login screen setup  there is an option for it.[/QUOTE]
It doesn't work from what I see. I'm locked out.

---

