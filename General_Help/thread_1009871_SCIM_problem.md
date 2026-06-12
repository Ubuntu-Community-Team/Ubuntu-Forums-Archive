---
title: "SCIM problem"
date: 2008-12-13
forum: General Help
---

### Post by azathrael on 2008-12-13
Hello,

I'm currently posting thisfrom my iTouch so sorry if I get lazy and not fix all my typing errors

I was trying to activate my laptop's built-in mic but when I tried to open up synaptic, I got a cannot validate Xaurhorization error.  I figured Ubuntu got screwed up so I restarted

Now, I can't open any application at all without it either crashing or taking too long

I looked at the system monitor and scim is in Zombie mode and scim-bridge is taking up all my CPU. I can't switch languages using the scim menu on the top right and basically my laptop is like a zombie that I can't do ANYTHING with

How did my scim get messed up for trying to get my built-in mic to work and how do I fix this problem?

Thanks!

---

### Post by azathrael on 2008-12-13
I found that scim-bridge is necessary for some programs to run and also, obviously, to type.

I found that killing the scim-bridge process will make programs run until scim-bridge automatically reboots itself.

What is going on??? I can't even use the terminal and since I'm not so good with computes, this problem is really troublesome as I need to use my laptop ASAP

Does Ubuntu have a system restore program?

---

### Post by azathrael on 2008-12-14
Problem still not solved

I can't even access firefox right now so any help would be appreciated

---

### Post by azathrael on 2009-01-01
I'm sorry, but this problem is STILL not solved.

I'm currently using Ubuntu with SCIM completely uninstalled and hence I have no access to other language input methods.

Nobody has any idea what's wrong with Ubuntu?

---

### Post by azathrael on 2009-01-04
This is so annoying... BUMP

---

### Post by azathrael on 2009-01-05
BUMP again.

This is the most inconvenient way to get help ever.  I have to send out an urgent e-mail in Korean and I'm NOT going to reformat just to have SCIM working again.

Again, if anyone has any idea to fix this problem, please help me out.

---

### Post by azathrael on 2009-01-08
Bump

---

### Post by azathrael on 2009-01-08
To people who might have the same problem as me, this is for your reference:

What I did was first uninstall everything. Restart.

Then go to Places -> Home Folder (Your username) -> ctrl + H (Shows hidden files) -> Look for foreign language folders such as .anthy or .pinyin or whatever, delete those folders.  Look for .xinput.d and delete all files in that folder.

Reinstall everything and restart.

Something must have been messed up in one of those folders because this fixed all problems.

GG me.

---

### Post by mdurham on 2009-01-08
azathrael, I'm sorry that I haven't seen your post before and that no one replied to you. I would have suggested creating a new user and setting SCIM up for that user to see what happened.
Anyway, too late & thanks for the info. If you ever need to type pinyin and see it on the screen (my wife does this for teaching pinyin) I know how to do it. I guess not many people need to do that though!
Cheers, Mike

---

