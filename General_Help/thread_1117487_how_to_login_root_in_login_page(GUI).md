---
title: "how to login root in login page(GUI)"
date: 2009-04-06
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-06
******how to login root user via login page in ubuntu 8.04.** Any one know means reply me..

---

### Post by sisco311 on 2009-04-06
[thread=716201]New forum policy on log-in-as-root tutorials[/thread]
[uhelp]community/RootSudo[/uhelp]

Why do you want to login as root?

---

### Post by suresh_vandiyur on 2009-04-06
> **sisco311 said:**
> [thread=716201]New forum policy on log-in-as-root tutorials[/thread]
[uhelp]community/RootSudo[/uhelp]

Why do you want to login as root?

i had finished RHCE..can u explain why did not login root in GUI Mode.. I want that reason. So only..

---

### Post by underage on 2009-04-06
Hey.

Well, I think you mean typing "root" on the login right... by default is disabled you need to enable it.

Go to System => Login Window => Security => "Allow local system Administrator login" (tip that).

Well as a good and reasonable human being I know you are, you'll come back and tell us if it worked for you.

Thanks,

UnderAGE):P

PS > suresh_vandiyur = Bro if you did RHCE you gave that on after Grub troubleshooting. The next topic was trobleshooting login in GUI Mode so... you need to pay more attention :-)

---

### Post by mb_webguy on 2009-04-06
The answer to your question is in the second link provided by sisco311.  

As a security measure, the root account is disabled in Ubuntu.  Temporary root privileges can be gained by preceding a command with sudo or gksu (for GUI applications).

underage:  Please read the first link in sisco311's post.  Ubuntu disables the root account for a reason, and forum policy prohibits informing new users how to enable it.

---

### Post by sisco311 on 2009-04-06
> **suresh_vandiyur said:**
> i had finished RHCE..can u explain why did not login root in GUI Mode.. I want that reason. So only..

Did you read the links in my previous post?

In short, the root account password is locked by default.

Also the login manager (gdm) does not allow root logins by default.



> **underage said:**
> Hey.

<...>

Thanks,

UnderAGE):P

PS > suresh_vandiyur = Bro if you did RHCE you gave that on after Grub troubleshooting. The next topic was trobleshooting login in GUI Mode so... you need to pay more attention :-)

You should also read the link above about the forum policy. :)

---

### Post by underage on 2009-04-06
Ya I got it bro.

But...

Dam why it's not allowed ? Why are we here for than ?

Anyway... sorry for the post but the mistake was already done.

If any Admin can just erase my post I would be grateful.

:-(:-(:-(:-(:-(

---

### Post by Peter09 on 2009-04-06
Logging in as root is considered a security problem, thats one of the problems windows has (you log in with admin privilege). 

A user running continuously as root is open to someone inserting a command with system wide properties without an real checks on who they are.

Ubuntu allows a user (who is identified by his initial login) to assume Admin rights on a temporary basis by using the sudo command. These rights then disappear soon after they are used, preventing someone using the terminal while a user is away.

This also means that a user will be alerted if anything tries to run with admin privilege as he will be asked for a password.

It is these mechanisms that go a long way to keeping Linux virus free.

---

### Post by Sef on 2009-04-06
There are no viruses for GNU/Linux; nevertheless, it is not in vulnerable.   It can be hacked and if you run as root, you have made the job of hacking your system so easy.   Once hacked, it can be used as part of a Linux Bot Network.

---

