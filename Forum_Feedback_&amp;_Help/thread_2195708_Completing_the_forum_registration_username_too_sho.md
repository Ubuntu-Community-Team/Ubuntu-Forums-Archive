---
title: "Completing the forum registration: username too short"
date: 2013-12-26
forum: Forum Feedback &amp; Help
---

### Post by alexei.colin2 on 2013-12-26
A potential issue with the authentication setup: after creating a new Ubuntu One account, couldn't complete Ubuntu Forums registration. The error displayed was roughly 'username must be longer than 3 characters'. Comparing to other accounts, in the broken case upon Login Using SSO, the open id screen lists only name and email, but not username.

Since I never was asked for a username, maybe it is trying to use my email username? Which is indeed less than three characters long: <snip>. If this is the case, then perhaps it should fail earlier and provide an option to pick a username.

---

### Post by Irihapeti on 2013-12-26
*Thread moved to **Forum Feedback & Help**.*

---

### Post by coffeecat on 2013-12-26
I see from your Resolution Centre thread that your problem is not so much the system creating a forum username from the email but that you did not use the correct email to link up with your old account. But I will post this for general information since it has relevance to new members.

This is all explained in the [SSO login sticky]("http://ubuntuforums.org/showthread.php?t=2164051") linked from the pre-login notice.

> [list][*]When you first login to Ubuntuforums with your Ubuntu One account, a forum account will be created for you with a username based on the Ubuntu One username (where your Ubuntu One account is an older one with a username field), or if this is a newer account with no username field, your Ubuntu One Full Name. If you untick the Full name box so as not to share it, the system will use all or part of the local part of your email address (the part before the @) to generate your forum username.

[br][/br]
[*]If you are not comfortable with having your real name used as your forum username, and if the local part of your email reveals your real name, then you will need to change your Ubuntu One real name to a nickname before you log in. You can change the Ubuntu One name back again once the forum account has been created.[/list]

The solution is: Don't untick the Ubuntu One Full Name box at the Personal Data Request page if you don't want the system using the local part of your email. As the sticky says, you can temporarily change your Ubuntu One name to a nickname if you don't want your real name used as the forum username.

---

### Post by alexei.colin2 on 2013-12-26
> I see from your Resolution Centre thread that your problem is not so  much the system creating a forum username from the email but that you  did not use the correct email to link up with your old account. But I  will post this for general information since it has relevance to new  members.

Right, I just noticed this so thought it was worth forking and bringing to your attention. What I didn't do is read the sticky, sorry -- guilty.

> If you untick the Full name box so as not to share it, the system will  use all or part of the local part of your email address (the part before  the @) to generate your forum username.

Weird. I'm fairly sure the full name was checkmarked. I don't remember unchecking it, so it must have been unchecked by default.

This thread is resolved. Thank you. 

EDIT: The only todo worth generating may be to communicate the information you quoted from the sticky to the user as the user goes through the registration/linking process. For example, I've read in the banner or somewhere that linking happens by email, so it would be nice if that same place mentioned this crucial info about how the username end up chosen.

---

