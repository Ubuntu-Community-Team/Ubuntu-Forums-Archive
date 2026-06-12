---
title: "Change username on login screen"
date: 2006-01-19
forum: General Help
---

### Post by ubuntu irv on 2006-01-19
Can someone tell me if this is possible and if so how to do it.  I am a newbie so be gentle.
Irv

---

### Post by chammi on 2006-01-19
Do you mean that you want to change the name that you have to enter to log-in? 

If so, read the following bit:

If you JUST started using, you might consider a reinstallation. That said, I'm pretty sure there's a workaround.  Have you taken a look at the USERS & GROUPS applet (it's under System>Administration, at the of your screen)? 
 You'll need to use the password you created during the install to access it, btw.

The following is **pure speculation**, so *don't* try it until a few other people have had a chance to respond with better ideas:

1. open the users and groups applet.
2. create a new user, with the name you'd like to appear
3. go back to the original user name, select it, click "properties"
4. under advanced, change the UID from 1000 to some other number, say 1002
5. go to the new user name and do the same, but change its UID to 1000. 
...
That's just a thought. I wouldn't try it out just yet. Basically, what it does is create a new user. But Linux uses an internal numbering system to identify users. The first user is "1000" so you're changing that to the new user name too.

---

### Post by majed on 2006-01-19
Hi,

You can use the "User Accounts Admin" utility from the system admin menu..

Choose your account, click on properties, then change the "Real Name" field if this is what you want to change.. or the username if its what you mean..

Good luck!
majed

---

### Post by ubuntu irv on 2006-01-19
Thanks for the help.
I was able to go to System, Administration, Users and Groups.  I added a new user using the same password. It works fine .

Can I delete the original user?  I am concerned as the UID on the new user is set to 1001 and the original user to 1000.  If I can how would I do that?
Thanks again

---

### Post by chammi on 2006-01-28
Can you just swap out the UID #s?

---

