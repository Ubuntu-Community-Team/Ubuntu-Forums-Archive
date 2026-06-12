---
title: "su or sudo does not authenticate"
date: 2009-04-12
forum: General Help
---

### Post by Danial on 2009-04-12
Hi,

First of all, Thanks in advance for the Time, Help and Guidance.  
Second, Sorry, I did not find any related article/post for my issues so I am posting it here. 
Third, and most importantly :(, I am fairly a newbie, and I may be doing something obviously wrong and not knowing it.  
So here are my two issues.

[B]Unable to login in su
How to find the path and set default application?
[/B]
1.  I can login with Admin passwords and can use Synaptic, Software Resources and / or Add/remove Program but when I try to login to terminal or konsole and try to use su, I always get "authentication failure" error.  This probably started when I started using gnome.  I initially installed kubuntu but than changed some of the settings and moved from kde to gnome.  

2.  How do I find and set default application?  For example, I wanted to open a pdf file from an e-mail and I was prompted to "save or open" file option.  When I choose open, it asks for application and always take me to home folder.  I seems to be unable to find Acrobat reader installation that way.  However, I can save it and open it from there without any problem (a double click opens file in acrobat).  so basically, my question is when I install a program, where it is installed (the path)?  This scenario is true for any other application for example VLC, 

If any of you guys/gals have any insight to my dilemma, please help!!!

Thanks in Advance...

Danial

---

### Post by paradigm2 on 2009-04-12
> **Danial said:**
> Hi,

First of all, Thanks in advance for the Time, Help and Guidance.  
Second, Sorry, I did not find any related article/post for my issues so I am posting it here. 
Third, and most importantly :(, I am fairly a newbie, and I may be doing something obviously wrong and not knowing it.  
So here are my two issues.

[B]Unable to login in su
How to find the path and set default application?
[/B]
1.  I can login with Admin passwords and can use Synaptic, Software Resources and / or Add/remove Program but when I try to login to terminal or konsole and try to use su, I always get "authentication failure" error.  This probably started when I started using gnome.  I initially installed kubuntu but than changed some of the settings and moved from kde to gnome.  

2.  How do I find and set default application?  For example, I wanted to open a pdf file from an e-mail and I was prompted to "save or open" file option.  When I choose open, it asks for application and always take me to home folder.  I seems to be unable to find Acrobat reader installation that way.  However, I can save it and open it from there without any problem (a double click opens file in acrobat).  so basically, my question is when I install a program, where it is installed (the path)?  This scenario is true for any other application for example VLC, 

If any of you guys/gals have any insight to my dilemma, please help!!!

Thanks in Advance...

Danial

will "sudo -i" work in getting you a root shell?

What does "cat /etc/sudoers" show?

When you do "groups" does it contain the word "admin" indicating you are in the admin group?

By default I believe the "root" account is disabled.  You have to use "sudo".

---

### Post by Diabolis on 2009-04-12
Application will install its "executable", which is actually just a small script in a bin folder. /bin for system commands and /usr/bin for user applications.

I believe that now Gnome supports file extension association, so right click on a PDF and select with which application you want to open it. After that, it should be used as the default chooice.

Still not sure why you needed to login as root, chances are that you will never need to. If you need root permissions for a task, just do it with the sudo command and you'll stay on the safe side.

---

### Post by Diabolis on 2009-04-12
> **paradigm2 said:**
> 
By default I believe the "root" account is disabled.  You have to use "sudo".

You are right, there is no root account actually, you have to create it manually. Ubuntu discourages working as root, so they don't give you a ticket for chaos.

**You don't need to quote the whole post if you are replying right below it.*

---

### Post by paradigm2 on 2009-04-12
> **Diabolis said:**
> You are right, there is no root account actually, you have to create it manually. Ubuntu discourages working as root, so they don't give you a ticket for chaos.

**You don't need to quote the whole post if you are replying right below it.*

Although it is discouraged (and can cause big issues, even if later disabled) I believe if he sets a passwd for the root account it will magically work, no?

About quoting the post, I understand what you are saying and can see where it might seem wasteful or annoying.  The main reason I do it on an active forum is because even though it looks as if there are no other replies when I hit reply, between the time from when I write and hit "submit reply" someone else might reply causing confusion.  Also because the user could edit the post.  I will reconsider this next time if it is a problem though.

---

### Post by Danial on 2009-04-12
> **Diabolis said:**
> Application will install its "executable", which is actually just a small script in a bin folder. /bin for system commands and /usr/bin for user applications.

I believe that now Gnome supports file extension association, so right click on a PDF and select with which application you want to open it. After that, it should be used as the default chooice.

Still not sure why you needed to login as root, chances are that you will never need to. If you need root permissions for a task, just do it with the sudo command and you'll stay on the safe side.

Thanks for help to both of you.  
sudo -i; did let me login, however, su (assuming a short cut for su - I may be wrong) does not.

Yes I am able to set the file association from file itself (downloaded  to desktop or home folder) but mostly I was getting the problem when I download a file and download manager prompts to choose an application to open.  The download file may be a *.pdf or *.flv and I was trying to use Acrobat / VLC (respectively) to open that particular file.  You gave me the path, so I am sure I should be able to  get to that.  I don't have anything to download right now, but I will check soon.

Once again, thanks a lot for direction.

Danial

---

### Post by coffeecat on 2009-04-12
**Danial**, here's a useful link for you that explains all about su, sudo and root in Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Danial on 2009-04-12
> **paradigm2 said:**
> will "sudo -i" work in getting you a root shell?

What does "cat /etc/sudoers" show?

When you do "groups" does it contain the word "admin" indicating you are in the admin group?

By default I believe the "root" account is disabled.  You have to use "sudo".

Here is the output:
abba@Amma-Betta-Computer:~$ cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
abba@Amma-Betta-Computer:~$ 

When I get into User and Groups settings, and checked the abba (login id), it shows the main group as 'abba'.  Do I need to change it to group 'admin'?  Also root shows as root in the main group, however, there is nothing checked in privilege tab.  

BTW, I am using FF 3.0.7
I hope I got all the information you were looking for.

Thanks 
Danial

---

### Post by Danial on 2009-04-12
> **coffeecat said:**
> **Danial**, here's a useful link for you that explains all about su, sudo and root in Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Thanks for the link, I will be reading this in detail.
Danial

---

