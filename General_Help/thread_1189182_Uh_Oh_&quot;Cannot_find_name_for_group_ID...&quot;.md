---
title: "Uh Oh &quot;Cannot find name for group ID...&quot;"
date: 2009-06-16
forum: General Help
---

### Post by rilesywilesy on 2009-06-16
I'm not super techy and am new to linux, so forgive me

So, I got WXP running in a VBOX and was trying to enable the USB use, so I went to administration and users and groups, tried to add a group, made a password for it, then it never showed any users in it (I assumed it would present me with the option of including the user which I normally am, riley, in the group, but it did not) and then didn't even show the group I had just created.  After that I was copy and pasting something from another forum, trying to fix my problem, using sudo and it told me I didn't have permission.  Then I tried to change some authorizations, which it also won't let me do.  I don't even receive an error message, it just acts like I'm not clicking when I click on the "grant" button.  Now when I try to go to root/riley it says I don't even have permission for that.  Apparently I don't have permission to do anything on my own dam computer.  I know I know, security reasons, blah blah blah it's just annoying
So at this point I talk to my friend who is somewhat more familiar with the inner workings of this linux business, though he uses fedora, and he had me enter the command "groups" which resulted in me getting this message:

riley@riley-laptop:~$ groups
riley id: cannot find name for group ID 4
4 id: cannot find name for group ID 20
20 id: cannot find name for group ID 21
21 id: cannot find name for group ID 24
24 id: cannot find name for group ID 26
26 id: cannot find name for group ID 29
29 id: cannot find name for group ID 30
30 id: cannot find name for group ID 44
44 id: cannot find name for group ID 46
46 id: cannot find name for group ID 104
104 id: cannot find name for group ID 106
106 id: cannot find name for group ID 112
112 id: cannot find name for group ID 121
121 id: cannot find name for group ID 122
122
riley@riley-laptop:~$ 

He said that is a bad bad sign.  So, do you think this is fixable, or am I going to have to reinstall?  

I would be happy just to get this problem alone fixed, but I would also like to know if there is a freaking SIMPLE step by step way to get a USB to work in a VBOX.  All the explanations I found were complicated and at some point in the process would not work for me.

Help a newbie out ;D

---

### Post by zvacet on 2009-06-17
If you installed Vbox from repos then you don't have USB support.You will have to remove it and follow [this]("http://ubuntuforums.org/showthread.php?t=1074160") guide to install.

---

