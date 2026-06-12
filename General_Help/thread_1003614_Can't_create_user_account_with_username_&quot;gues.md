---
title: "Can't create user account with username &quot;guest&quot;"
date: 2008-12-06
forum: General Help
---

### Post by eatdirt001 on 2008-12-06
For some reason when I try to create an unprivileged account under the username "guest", it tells me "User name "guest" already exists" and to "Please select a different user name." I have never tried to create another account before and there is no other folder under /home besides my own account folder. What can be the problem here? I'm usng the intrepid ibex version.

---

### Post by louieb on 2008-12-06
One of the new  features in 8.10 is the guest account. Go ahead and login as guest and see if thats what you want.

---

### Post by eatdirt001 on 2008-12-06
I know about that feature but I would prefer to have a guest account that can be logged in from the start screen rather than have someone go through my account first.

---

### Post by clegends on 2008-12-14
I agree... almost there folks, but not quite. In Hardy I set up a user account called Visitor... was great... but what on earth is the logic of the guest account being started through an active session? Great... so I can leave instructions for my house sitter to log into my account, with my system password, then please only use the guest account in INtrepid... good grief... this one was not well thought through...

---

### Post by vandyer on 2009-01-09
i'm on here trying to find how to add a standard user account....i have added an account using the "user and groups" programme but i can't log on using the username and passowrd i've just set. 

on the point of the guest session, i can only see one good reason for this - man on laptop suring his "favourite" web site, girlfriend wants to use laptop to check her facebook account, then the man simply logs her in under guest!! hey presto - no need for him to clear his web activities!!

---

### Post by patrickscott on 2009-02-09
I new to Ubuntu/Linux and confused. How do I create an account (restricted) so that I do not have to log in to Ubuntu 8.1 to use the restricted account?

Thanks.

---

### Post by clegends on 2009-02-09
Hi matey, welcome to Ubuntu. Sounds like you want to log into Ubuntu as root, with full admin priviliges. Ubuntu isn't configured to easily allow this, and you'll get precious little help from the forums trying to do this. The reason being is for your own safety, logging in as root is a great way to stuff up your system if you make a wrong move. 

In Ubuntu to access a root command, in the terminal you type:
sudo
then your command. I.e.
sudo nautilus
to open your file manager for root access. Personally I think the craze about root access being so gaurded is a bit silly, but that's my opinion. Puppy Linux is a very solid little distro that uses root as the standard user, however it's set up totally differently,and is ridiculously easy to restore should you stuff something. Ubuntu is a different kettle of fish, thus the root protections. Hope this answers your questions.

~Mitchell

---

### Post by tomsteemson on 2009-02-25
This falls into a very similar scenario to the one I'm trying to recreate.  The 'Guest' account facility in 8.1 is exactly what I'm after, but as has been mentioned above, has limited application given that, it would appear, someone has to log in first.

My scenario is that I want a machine that will, as the guest account does, allow access to browsing features with zero possibility of the user being able to change the configuration of the machine.  This account needs to be available from boot, without the need for any user input, so that should the user be the first in the morning to use the PC all they need do is switch it on.

This would also have applications from a retail perspective.  I used to be an IT manager for a large retail chain and we looked at having internet access for clients in our stores.  Having a hands-free login with a locked down GUI on boot would have been perfect for the job.

---

### Post by clegends on 2009-02-25
Hi tomsteemson, interesting thought. Firstly, I did see something similar as an add on program available to lock down a session, just can't remember where on these forms it was... search around and you're bound to find it, basically you can lock down a session, and control exactly what the user can and can't do.

Anyway, I think most of what you want to do can be set with permissions in any event.If you go to user accounts from the systems menu you'll be able to say what users can and can't do. I believe it's also possible in Intrepid (and I think Hardy also) to auto-login a session on bootup. I'd have to search to remember how to do it though. Please let us know how you go, and if you find an easy way to do this.

I'm not sold on Intrepid yet, too buggy and unstable, especially when it comes to printing. I haven't found the additonal features (like guest login) to be that beneficial yet, perhaps they would be to other users. I'm seriously considering reverting back to Hardy. Good luck.
~dinky

---

### Post by tomsteemson on 2009-02-25
> **clegends said:**
> Hi tomsteemson, interesting thought. Firstly, I did see something similar as an add on program available to lock down a session, just can't remember where on these forms it was... search around and you're bound to find it, basically you can lock down a session, and control exactly what the user can and can't do.

Anyway, I think most of what you want to do can be set with permissions in any event.If you go to user accounts from the systems menu you'll be able to say what users can and can't do. I believe it's also possible in Intrepid (and I think Hardy also) to auto-login a session on bootup. I'd have to search to remember how to do it though. Please let us know how you go, and if you find an easy way to do this.

I'm not sold on Intrepid yet, too buggy and unstable, especially when it comes to printing. I haven't found the additonal features (like guest login) to be that beneficial yet, perhaps they would be to other users. I'm seriously considering reverting back to Hardy. Good luck.
~dinky

I've been looking at this on and off all day.  Been playing with a HP printer under Ubuntu this afternoon.  I so hate HP drivers!  Love the printer but bloat-ware software sucks.  Anyway, back on topic, I think I may have found something useful under Kubuntu.  I'm not a great fan of KDE but Kubuntu apparently has a kiosk (there's the magic word to look for in searched :D ) mode that may be the answer to what I'm looking for.  Thanks for the feedback Dinky.

---

### Post by borateen on 2009-11-06
> **eatdirt001 said:**
> For some reason when I try to create an unprivileged account under the username "guest", it tells me "User name "guest" already exists" and to "Please select a different user name." I have never tried to create another account before and there is no other folder under /home besides my own account folder. What can be the problem here? I'm usng the intrepid ibex version.

I don't think anyone has come close in attempting to answer the original question here. I am having the same problem and would like to find a solution. I am using 9.10 Karmic Koala.

---

### Post by Tclarkie on 2009-11-06
the prob is that samba creates a user called "guest" to share files with unprivliged users

---

### Post by Tclarkie on 2009-11-06
try creating a user called "Visitor"
that should work

---

### Post by Tclarkie on 2009-11-06
sorry in my first post when i said unprivileged i meant users on other pcs that dont have the pswd

---

### Post by borateen on 2009-11-06
> **Tclarkie said:**
> the prob is that samba creates a user called "guest" to share files with unprivliged users
As I understand Samba is installed with Ubuntu. So does that mean the user account "guest" can never be used as an Ubuntu login? Then "visitor" it is I suppose.

---

### Post by Tclarkie on 2009-11-06
Yep

---

