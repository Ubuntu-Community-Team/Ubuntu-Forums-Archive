---
title: "MSN Netpassport and Gaim"
date: 2005-12-18
forum: General Help
---

### Post by ubuntu27 on 2005-12-18
HI guys/Girls  [Maybe I should change the way I always salute :P]

My computer has multiple user accounts...

When I log with the second user account, and try to log on to MSN protocol with Gaim. It tells me: "Unable to authenticate: .NET Messenger Service"

This doesn't happen with my first user account, the one that can do sudo.

I don't think there is a difference in the network configuration...
I don't have a Firewall either...

the only difference that I see between the first account and the second account is that
the guy who uses the second account have an e-mail that ends with @hotmail.com, and mine (first account) ends with @MSN.com

But both of them are from Microsoft!! So, I don't think it is related...

Note: all other protocols work, like Yahoo, & Google (Jabber)

PS.: I AM USING GAIM 2.0 CVS from here: [http://ubuntuforums.org/showthread.php?t=100899](http://ubuntuforums.org/showthread.php?t=100899)


Any ideas?

Thank you in advance. 
and thank you again for always helping me :)

---

### Post by BathroomNinja on 2005-12-19
I only get that error message when I use the wrong password.  Try creating a new account with the @hotmail.com, then attempt to login with that new account on that users profile.  Let me know what happens.

---

### Post by ubuntu27 on 2005-12-19
[QUOTE=BathroomNinja]I only get that error message when I use the wrong password.  Try creating a new account with the @hotmail.com, then attempt to login with that new account on that users profile.  Let me know what happens.[/QUOTE]
Thank you for the reply Ninja :)

my @MSN.com in my 1st account works, but not his @hotmail.com in the 2nd user account.

He just created his hotmail account two days ago... ><

---

### Post by BathroomNinja on 2005-12-19
Yes, what I'm saying is that I think he may be using the wrong password.  By creating a new, test account with the @hotmail.com, we can check to see if it's an issue your having with authentication, or if your problem is your password.  So I'm just trying to narrow down the problem.  So we need a new hotmail account created under his 2nd user account.  

Basically, this is the old 'swap with known good' trick.

---

### Post by ubuntu27 on 2005-12-19
[QUOTE=BathroomNinja]Yes, what I'm saying is that I think he may be using the wrong password.  By creating a new, test account with the @hotmail.com, we can check to see if it's an issue your having with authentication, or if your problem is your password.  So I'm just trying to narrow down the problem.  So we need a new hotmail account created under his 2nd user account.  

Basically, this is the old 'swap with known good' trick.[/QUOTE]
ok :) understood :)

Anyway, if he misspell the password, it gives the following error: e-mail or password not authenticated,, something like that.

but, when he puts the "correct" password, it just says: ""Unable to authenticate: .NET Messenger Service""

So, I don't it is about misspelled password... ><

---

### Post by BathroomNinja on 2005-12-19
[QUOTE=ubuntu27]ok :) understood :)

Anyway, if he misspell the password, it gives the following error: e-mail or password not authenticated,, something like that.

but, when he puts the "correct" password, it just says: ""Unable to authenticate: .NET Messenger Service""

So, I don't it is about misspelled password... ><[/QUOTE]


OK.  It might be some other issue on your end or theirs.  Go ahead and try to create a new test account anyway to see if the problem happens with that new account, or if it's only with the old @hotmail account.  Also, try the new account with different user accounts on that system to see if the problem follows all of your users.  Still just trying to narrow down the issue.

---

### Post by ubuntu27 on 2005-12-19
THanks. I'll do that :)

---

### Post by BathroomNinja on 2005-12-19
[QUOTE=ubuntu27]THanks. I'll do that :)[/QUOTE]


Be sure to post your results.

---

### Post by chinaski on 2006-08-16
UP!

just to say I had same problem until few minutes ago

then I changed the password of my hotmail  account and changed it in Gaim too

works perfectly now

---

