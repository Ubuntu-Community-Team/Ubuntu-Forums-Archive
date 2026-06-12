---
title: "Can a user without a homedir be given environmental variables?"
date: 2009-02-28
forum: General Help
---

### Post by bobdobbs on 2009-02-28
Hi all.

I'm installing an experimental server software on an ubuntu box.
The server will be started by a user created for the sole purpose of running the server.

This user will have no homedir. 

I need to give this user a JAVA_HOME variable.

Normally, I would do this by editing the .bash_profile in the users homedir.
But of course, the user has no homedir.

So, how I do ensure that the users default shell is bash, and that the user will inherit variables that I want him to have?

Thanks.

---

### Post by lloyd_b on 2009-02-28
First, the default shell for the user is defined in the user configuration.  Look at "/etc/passwd" - the last parameter for each user is the default shell for that user.

As to making it work without a home directory - you could modify the file "/etc/bash.bashrc" (which is called from "/etc/profile", and thus invoked for all user logins), and add a conditional for that user:
```
if [ "$USER" = "nohomedir" ]; then
    export JAVA_HOME="/usr/java/whatever"
fi
```
Of course, you could leave off the conditional, and just arbitrarily set JAVA_HOME for *all* users - it's your choice as to whether this is desirable or not.

I am a bit curious - how can a user not have a home directory?  Or is this user just defaulting to "/" as the home directory, and you don't want to create a "/.bashrc"?

Lloyd B.

---

### Post by bobdobbs on 2009-02-28
> **lloyd_b said:**
> 

I am a bit curious - how can a user not have a home directory?  Or is this user just defaulting to "/" as the home directory, and you don't want to create a "/.bashrc"?

Lloyd B.

Hi Lloyd.
Thanks for the response.

And, your solution worked for me.

I've set up a user and a corrosponding group for that user.
A home directory has to be created explicitly by an option passed to useradd. I didn't set that option, because I don't think that the user needs a usergroup.

I understand that under some distro's, apache can be set to run as "nobody", and anonymous user for which no homedir exists.

It's a security thing that I don't fully understand.

---

