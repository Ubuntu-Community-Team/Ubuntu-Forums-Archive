---
title: "Duplicating user account"
date: 2009-01-06
forum: General Help
---

### Post by detroit/zero on 2009-01-06
Is it possible to duplicate a user account without installing every package by hand, having multiple copies of wallpapers & themes, etc, etc?

I have a computer running Hardy. I added a new user, and this new user is pretty taken with my choice of themes, my conky setup, some of the programs I have installed, so on & so forth.

How can I make available all these various things to this new account without copying everything  to the users' home folder? How can I make programs I have installed under my account available to the new user (or are they already)?

---

### Post by heindsight on 2009-01-06
you could put all the walpapers etc that you want to share between the users in a directory outside your home directories (you could for example create a directory called /home/shared) and set the permissions for this directory such that both users can access it.

as for programs you've installed, if you installed from the repos then they're available to all users.

---

### Post by detroit/zero on 2009-01-06
> **heindsight said:**
> you could put all the walpapers etc that you want to share between the users in a directory outside your home directories (you could for example create a directory called /home/shared) and set the permissions for this directory such that both users can access it.
Sounds easy enough. I guess I overanalyzed that situation and figured it would have to be more complicated than that... Good idea.

> **heindsight said:**
>  as for programs you've installed, if you installed from the repos then they're available to all users.
That's good to know. What about modifying sessions and startup programs for this new user? Is it possible for me to do that from the command line within my account without having to log out and log in as the new user?

---

### Post by heindsight on 2009-01-07
> **detroit/zero said:**
> 
That's good to know. What about modifying sessions and startup programs for this new user? Is it possible for me to do that from the command line within my account without having to log out and log in as the new user?
I suppose you could copy over a bunch of config files. i'm not sure which files you'd need to copy though. you'd have to remember to change the ownership of the files to your new user after you copy... i suspect it may be easier to log in as the new user.

---

### Post by detroit/zero on 2009-01-07
> **heindsight said:**
> I suppose you could copy over a bunch of config files. i'm not sure which files you'd need to copy though. you'd have to remember to change the ownership of the files to your new user after you copy... i suspect it may be easier to log in as the new user.
I was just thinking my compiz-fusion settings, emerald theme, icons, GTK theme, conky setups, so on & so forth. I guess a sudo cp & sudo chown -R of a batch of files would do the trick.

So, I think I, with a little help from you two, sort of answered my own question. Unless someone more knowledgable has some answers?

---

### Post by sdennie on 2009-01-07
If you anticipate on doing this more than once, you could also add all these settings to /etc/skel.  That will automate the process when new users are created.  (Though, it won't help for this particular user).

---

### Post by detroit/zero on 2009-01-07
> **vor said:**
> If you anticipate on doing this more than once, you could also add all these settings to /etc/skel.  That will automate the process when new users are created.  (Though, it won't help for this particular user).
That is to say.. copy, for example, my AWN & compiz folders from *~/.config* into */etc/skel/.config*, and it will install with my settings for any new user created?

Did I read that right?

If I, for example again, want a newly created user to have AWN with my current settings the first time they log into their account, I assume copying my settings over would have AWN start automagically when they sign in. What about deleting the bottom ubuntu panel?

Are these things that can be done by me, from my account, through the command line?

Does all this just come with experience, or is there a tutorial/admin-manual you can link me to?

I hate to bother people with questions when i can read an get my own answers.

---

### Post by sdennie on 2009-01-07
> **detroit/zero said:**
> That is to say.. copy, for example, my AWN & compiz folders from *~/.config* into */etc/skel/.config*, and it will install with my settings for any new user created?

Did I read that right?

If I, for example again, want a newly created user to have AWN with my current settings the first time they log into their account, I assume copying my settings over would have AWN start automagically when they sign in. What about deleting the bottom ubuntu panel?

Are these things that can be done by me, from my account, through the command line?


That's the idea, yes.  The description of this can be found in /etc/adduser.conf (the SKEL option).  I'm not sure how it does permissions but, if you do an "ls -la" in that directory everything is owned by root so, best to keep user added files as root as well.

> 
Does all this just come with experience, or is there a tutorial/admin-manual you can link me to?

I hate to bother people with questions when i can read an get my own answers.

I just stumbled upon so, I'm not sure.   :)

---

