---
title: "How do I add and edit users?"
date: 2006-08-12
forum: Desktop Environments
---

### Post by ardchoille on 2006-08-12
In my never-ending quest to learn more and more about command line admin, I would like to spend this weekend on learning how to deal with users on the system via command line. I have Ubuntu 6.06.1LTS installed and will be working without the use of X (cli only). Here are my questions:

1. How do I add a new user (and the users' home directory) to the system:
username: debbie
group: debbie

2. How do I change Debbie's group to kathy?
username: debbie
group: kathy

3. How do I change Debbie's password after her user account has already been created?

4. How do I add debbie to the wheel group?

5. How do I remove debbie from the audio group?

6. How do I lock and unlock debbie's account?

7. How do I completely remove the user debbie from the system (along with her home directory and files)?

Are there any other things I need to know about user admin?

---

### Post by Fass on 2006-08-12
Gnome has a nice GUI for it in "Administration." It's called, aptly, "Users and groups."

If you want to do it manually, there is "useradd, usermod, userdel, groupadd, groupmod, groupdel" and so on. How they work is explained in their man pages.

---

### Post by ardchoille on 2006-08-12
> **Fass said:**
> Gnome has a nice GUI for it in "Administration." It's called, aptly, "Users and groups."

If you want to do it manually, there is "useradd, usermod, userdel, groupadd, groupmod, groupdel" and so on. How they work is explained in their man pages.

I don't want to use a gui app, that's why I specified several times in my original post that I wanted to do this via command line.

[COLOR="Red"]usermod -L[/COLOR] This puts a "!" in front of the encrypted password, effectively disabling the password.

[COLOR="Red"]passwd -l[/COLOR] This option disables an account by changing the password to a value which matches no possible encrypted value.

Which one should I use to make it so the user cannot log in? The problem with telling someone to "read the man page" is that they usually come with several choices, but they may not know which choice is the best one for a given situation. The reason I posted my questions to these forums was to get a response from people who have been using Linux long enough to know which is a better choice for a certain situation. Simply telling someone to read the man pages is not always the right answer.

---

### Post by maniacmusician on 2006-08-12
well i've never tried this but if you must, the first option looks safer, as it is looks to be easily reversible

---

### Post by ardchoille on 2006-08-12
> **maniacmusician said:**
> well i've never tried this but if you must, the first option looks safer, as it is looks to be easily reversible

Hmm.. good point. Thanks for pointing out the "easily reversible" part :)

---

### Post by nalmeth on 2006-08-12
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
Scroll down to command-line instructions

---

### Post by ardchoille on 2006-08-12
> **nalmeth said:**
> [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
Scroll down to command-line instructions

Thank you. That takes care of a few of my questions :)

---

### Post by Ptero-4 on 2006-08-12
Hi. A question. How do I force the installer (Dapper alternate) to allow me to create a username with capitalized characters and special characters (I know this can be done using the --force-badname argument in adduser, but I don't know if the installer ivokes that command and I don't know how to change the invocation to include that argument and get the installer to actually aknowledge that)? Or if it can't be done at install time. Can I safely (whitout breaking apps/services and losing the ability to gain admin access through sudo/gksudo) change the username and the name/location of my home folder after installing the OS?

---

### Post by ardchoille on 2006-08-12
> **Ptero-4 said:**
> Hi. A question. How do I force the installer (Dapper alternate) to allow me to create a username with capitalized characters and special characters (I know this can be done using the --force-badname argument in adduser, but I don't know if the installer ivokes that command and I don't know how to change the invocation to include that argument and get the installer to actually aknowledge that)? Or if it can't be done at install time. Can I safely (whitout breaking apps/services and losing the ability to gain admin access through sudo/gksudo) change the username and the name/location of my home folder after installing the OS?

Please don't hijack some else's thread. I am trying to learn more about command line administration. Please start your own thread :)

---

### Post by ardchoille on 2006-08-13
I still need answers to my original questions:

1. How do I add a new user (and the users' home directory) to the system:
username: debbie
group: debbie

2. How do I change Debbie's group to kathy?
username: debbie
group: kathy

3. How do I change Debbie's password after her user account has already been created?

4. How do I add debbie to the wheel group?

5. How do I remove debbie from the audio group?

6. How do I lock and unlock debbie's account?

7. How do I completely remove the user debbie from the system (along with her home directory and files)?

Are there any other things I need to know about user admin?

To add a new user, would I use adduser or useradd? What's the difference?

---

### Post by kabus on 2006-08-13
> **ardchoille said:**
> 
1. How do I add a new user (and the users' home directory) to the system:
username: debbie
group: debbie


Easiest would be to use the adduser command, it'll walk you through the process.

> **ardchoille said:**
> 
2. How do I change Debbie's group to kathy?
username: debbie
group: kathy


I'd just edit /etc/groups, but there's probably a better way.

> **ardchoille said:**
> 
3. How do I change Debbie's password after her user account has already been created?


man passwd

> **ardchoille said:**
> 
6. How do I lock and unlock debbie's account?


Remove her password (passwd -l).

> **ardchoille said:**
> 
7. How do I completely remove the user debbie from the system (along with her home directory and files)?


userdel -r

---

### Post by ardchoille on 2006-08-13
> **kabus said:**
> Easiest would be to use the adduser command, it'll walk you through the process.



I'd just edit /etc/groups, but there's probably a better way.



man passwd



Remove her password (passwd -l).



userdel -r

Oh, I didn't think of editing /etc/groups, that sounds easier to me, since I like vim so much :) 

So, passwd is the correct one to use for that? Cool.

Thank you very much for your replies. I'll be adding these things to my personal wiki asap :)

---

