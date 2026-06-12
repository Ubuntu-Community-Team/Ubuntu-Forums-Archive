---
title: "Interesting sound problem"
date: 2006-10-07
forum: Desktop Environments
---

### Post by PCSpectra.com on 2006-10-07
Since I first installed a while ago, I have had no luck getting sound to work...except during startup, I would hear the default drum beat...

I'm not sure what I have done, but while playing with administration tools I somehow changed my default login user to non-root...

I can't get Application Install/Remove, synaptic or anything to work anymore...I can't delete files and I see my user (other than root) home directory in my desktop...

I appear to be running exclusively under a user account...???

Obviously this sucks as I can't install any applicaitons or anytihng...not sure if this is the norm, but I've be running as root since install...and some operations cimply required me to validate myself (I assumed to prevent malicious code from ever executing as root???)

The only bonus is I htink I may have located my sound issue I've been having since I started...

Sound always played at startup, that drum beat played...but after that everything seemed disabled and I often got totem errors??? Now that I appear to have permanently switched default user to normal user...Sound seems to work fine, as all wav's are played just awesome under Sound Preferences. Before sounds would only play under some admin panel, which is no longer availble...???

WTF is going on here? :P

First, how did I switch user to user instead of root, I liked being prompted occasionally when installing new apps, etc...but now I can't do anything...???

Secondly, why would sound work as a normal user and not as a root, except in the admin panel which let me specify login/logout sounds? Why would sound lpay at startup, but never at shutdown? Clearly the drivers are correct and hardware works, as I am now getting sound just fine...

One thing to note...

When I installed Ubuntu I didn't enter a default user, just a root user/pass (if I remember correctly I didn't bother doing normal user) and left user blank. After install I couldn't log in as root, so I was told to *adduser* and login as that...which I did and allowed me access into Ubuntu.

When logged in as a user though I appeared to have root privileges, as I was never prompted or told I couldn't do this or that (removing files, etc) only occasionally prompted to enter root password when I worked with synaptic, etc...

At the command line I did: *su root pass* to move files around, etc...???

Someone care to explain how I did what I did and how I go abouts fixing it...and have I discovered a bug of sorts?

Cheers :)

---

### Post by s_p_a_r_k_y on 2006-10-07
hi there, perhaps you managed to remove yourself from the group of users which has "sudo" access. Only people in this group can use the sudo command which allows regular users run things as root. Your version of how the setup ran is really weird, as I've done it many time and get prompted only for a user account, this user then has sudo rights.

From the command line, could you enter in 
sudo bash

and enter your password. Does it work?

---

