---
title: "Make system require root password instead of user password for admistrative tasks"
date: 2009-05-01
forum: General Help
---

### Post by J.Vega on 2009-05-01
Hi,

I've just returned to Ubuntu after trying various other distributions. So I'm somewhat used to entering the root password when performing administrative tasks. Now Ubuntu asks me for the user password every time I want to start a system application, which I find is too insecure. I want the system to require a root account for those things.
The problem is that Ubuntu can't start the application at all, if I disallow "Administer the system" in the users-admin properties of my account.
To make it short: Currently I have 2 options:
-give privileges to user so he can perform administrative tasks with his password
-disable the ability so I have to login as root before I can do anything

What I want is this:
Login as the user, but when launching an application that requires privileges, ask for the root password.

The only option I see is that I use "gksu -w" to start the applications. But then I'd have to edit all the menu entries to use "gksu -w ...", which I don't think is the best way to do it.
Is there another way to tell the system that I want to enter the root password when performing administrative tasks?


**SOLUTION:** Here's the link to the post with the solution: [http://ubuntuforums.org/showpost.php?p=7190413&postcount=10](http://ubuntuforums.org/showpost.php?p=7190413&postcount=10)

---

### Post by DeMus on 2009-05-01
> **J.Vega said:**
> Hi,

I've just returned to Ubuntu after trying various other distributions. So I'm somewhat used to entering the root password when performing administrative tasks. Now Ubuntu asks me for the user password every time I want to start a system application, which I find is too insecure. I want the system to require a root account for those things.
The problem is that Ubuntu can't start the application at all, if I disallow "Administer the system" in the users-admin properties of my account.
To make it short: Currently I have 2 options:
-give privileges to user so he can perform administrative tasks with his password
-disable the ability so I have to login as root before I can do anything

What I want is this:
Login as the user, but when launching an application that requires privileges, ask for the root password.

The only option I see is that I use "gksu -w" to start the applications. But then I'd have to edit all the menu entries to use "gksu -w ...", which I don't think is the best way to do it.
Is there another way to tell the system that I want to enter the root password when performing administrative tasks?

As you have found out Ubuntu does not use a root password. When you install Ubuntu you are asked for a username and a password. This user is a user with special privileges: his/her name and matching password are used to perform administrative tasks.
Why do you think this is not secure enough? You can't perform any special tasks without having to type the password first. If it's your password or a second password just for Root is not important. As long as you don't give your password away to somebody else it is secure.
Are you talking about a home computer which you use alone or is it an office computer with which you login to a network?
What I do here at home is I log in automatically (without using the log in screen and having to type the password) and when needed I type my password and become "Root". I know it is not safe to log in automatically, but that's just lazy me, I like to have things automated.
Still nobody can do anything bad to my computer because they still would need my password. How much safer do you want it to be?

---

### Post by gwbennett on 2009-05-01
I think what he wants to do is to have another user logged in who does not have administrative (sudo) rights, but still be able to su to root in order to do things without having to relog in.

If this is the case, just leave yourself with sudo permission, don't give it to the other user, then to execute administrative commands from the limited account su to yourself first, then sudo from there.

Ie, Jack is admin, Jill is not.

Jill$ su jack
Password for jack
Jack$ sudo su
Password for jack
Jack#

Advising you on any other way of accomplishing what (I think) you are trying to do is forbidden by ubuntu forum policy, but is easy to find elsewhere on the internet.

---

### Post by zvacet on 2009-05-01
You can find some interesting informations about sudo and root [here.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Paqman on 2009-05-01
> **J.Vega said:**
> Ubuntu asks me for the user password every time I want to start a system application, which I find is too insecure.

Why not just use a strong password for your user account?

---

### Post by J.Vega on 2009-05-01
I just wanted to know if there's a way to do it like I want it to do.... I didn't want to start a discussion on why I like it or not...

I have enabled the root account and gave it a password, but I want the gksudo dialogs to ask me for the root password (not for mine), because it is an administrative task, I modify system settings and this was always limited to the superuser.
One reason why I chose Linux is the possibility to do everything you want with your account without the fear that you wreck your system. If you don't login as root, you can't modify critical settings and such things. On WinXP for example, you need to always use an admin account, because you can't do anything if you have an unprivileged user. This was so much better in Linux... until Ubuntu changed it to what it is now.
Now please... I know that Linux is still safe (if you consider "safe" as "safer than windows") even if I give my normal user privileges, but I like the way other distros handle it (with the root account) and I want it to be the same on my computer. Please don't try to convince me that I don't need it. I want it and I just want to know if there's a way.

---

### Post by DeMus on 2009-05-01
> **J.Vega said:**
> I just wanted to know if there's a way to do it like I want it to do.... I didn't want to start a discussion on why I like it or not...

I have enabled the root account and gave it a password, but I want the gksudo dialogs to ask me for the root password (not for mine), because it is an administrative task, I modify system settings and this was always limited to the superuser.
One reason why I chose Linux is the possibility to do everything you want with your account without the fear that you wreck your system. If you don't login as root, you can't modify critical settings and such things. On WinXP for example, you need to always use an admin account, because you can't do anything if you have an unprivileged user. This was so much better in Linux... until Ubuntu changed it to what it is now.
Now please... I know that Linux is still safe (if you consider "safe" as "safer than windows") even if I give my normal user privileges, but I like the way other distros handle it (with the root account) and I want it to be the same on my computer. Please don't try to convince me that I don't need it. I want it and I just want to know if there's a way.

In that case i can not help you. I know other distro's use a real root account, while Ubuntu uses a user account with root privileges, which is just as secure.
I hope you find what you are looking for. If so, please post it here.

---

### Post by Paqman on 2009-05-01
> **J.Vega said:**
>  I like the way other distros handle it (with the root account) and I want it to be the same on my computer. Please don't try to convince me that I don't need it. I want it and I just want to know if there's a way.

The simplest solution would be to just run a distro that uses the security model you like.

---

### Post by lisati on 2009-05-01
> **J.Vega said:**
> Now Ubuntu asks me for the user password every time I want to start a system application, which I find is too insecure.
How would you define "secure"? :confused:
It could be worse - it could ask for a password for every keystroke or mouse click.

---

### Post by sisco311 on 2009-05-01
You can set the Authentication Mode for gksu in *gksu-properties.*


EDIT:
You can also set sudo to prompt for the root password. 

Add the *rootpw* flag to the *Defaults* line in the sudoers file.
(Always edit the file with the visudo command)

EDIT2:
[s]I'm not sure how to change it in PolicyKit.[/s]

I believe that you can change the Authentication Mode in PolicyKit by

changing the *<define_admin_auth group="admin"/>* line in /etc/PolicyKit/PolicyKit.conf to 
*<define_admin_auth user="root"/>*.

Backup the file before editing it!!!

---

### Post by J.Vega on 2009-05-01
Thanks a lot sisco311, that was exactly what I was searching for! :)


> The simplest solution would be to just run a distro that uses the security model you like. 
That was one of the reasons why I quit Ubuntu a while ago... The problem was that the other distros had other flaws that were more annoying than those of Ubuntu :(


> How would you define "secure"?
It could be worse - it could ask for a password for every keystroke or mouse click. 
Just because there is something worse doesn't mean it is good ;) But I may have used some misleading sentences in my problem description.
I just got used to the way thing were treated a while ago. This way I can change system settings without the need to logout and back in as root, but I can also say "here's my user password, I need you to change something in my account, because I cannot do it myself". Like I said, there are reasons for and against this, it's just a matter of taste and thinking ;)

---

### Post by ashmew2 on 2009-05-01
Well i appreciate the OP's thirst for knowledge and all , but wouldnt it be just easier to set the user's password , same as the root password and not tell anyone about it ?

---

### Post by J.Vega on 2009-05-02
I think I've already answered that question, but here's another try:
I use my user account all the day, maybe use the same password for other things (probably use the same for user-account-related things) and enter it multiple times for the simplest things. Don't you think it's much easier to find out my user password than the root password I use maybe 3 times a day? Of course, I could lock my laptop with a bios password and then don't use any other passwords at all. Still nobody else than me could turn it on.
It's a matter of how you want to define the security changes on your computer. If you want every user to be able to do everything, you don't need a password at all. If you want your main user to be able to do everything, you need 1 password for him. If you want the root user to be able to do everything, you need a seperate password for him and another one for you main user.
I like the last possibility most. That's all.
It would be easier to use no password at all, but I don't think that such an amount of security is enough for the data on my computer ;)
I think that the last possibility has the best security/work ratio for me.

---

### Post by dcstar on 2009-05-02
> **J.Vega said:**
> I think I've already answered that question, but here's another try:
I use my user account all the day, maybe use the same password for other things (probably use the same for user-account-related things) and enter it multiple times for the simplest things. Don't you think it's much easier to find out my user password than the root password I use maybe 3 times a day? Of course, I could lock my laptop with a bios password and then don't use any other passwords at all. Still nobody else than me could turn it on.
It's a matter of how you want to define the security changes on your computer. If you want every user to be able to do everything, you don't need a password at all. If you want your main user to be able to do everything, you need 1 password for him. If you want the root user to be able to do everything, you need a separate password for him and another one for you main user.
I like the last possibility most. That's all.
It would be easier to use no password at all, but I don't think that such an amount of security is enough for the data on my computer ;)
**I think that the last possibility has the best security/work ratio for me.**

And as you have discovered, you can change Ubuntu to do exactly what **you** want - rather than what others "recommend", so you get a system that satisfies **your** needs - with all the risk/benefits that **you** accept by doing this.

I'm glad you found out how to enable the root password on your own, because when I posted how to do it a few weeks back I got pinged with a forum infraction - because posting that information is taboo here (since last year, as I subsequently found......)

Now that you (and I, also) have Ubuntu systems with enabled root accounts be aware that these are apparently "unsupported" and we will have to live with this crippling reality....   ;-)

---

### Post by J.Vega on 2009-05-04
Wow, that was new to me :?
Can you (or anyone reading this) tell me where I can find an explanation for that "rule"?

---

### Post by sisco311 on 2009-05-04
[thread]716201[/thread]

---

