---
title: "Evolution Mail Questions"
date: 2008-12-14
forum: General Help
---

### Post by TBSN on 2008-12-14
Hi all,

I'm a new Ubuntu user, and so far I love it. I need a linux replacement for Mail/contacts/calendar client. So far I've tried the built in Evolution program, and it seems pretty good. The first time I open it in a session, however, it prompts me for my password to access the "default keyring" or something, which is really annoying. What is that?

Also, what do people think of Thunderbird with the Calendar extension, compared to Evolution? What are your favorite mail clients for linux?

I just started using Evolution because it was built in, but I don't know if there are better alternatives available.

Thanks in advance!

---

### Post by plucky on 2008-12-14
> I'm a new Ubuntu user, and so far I love it. I need a linux replacement for Mail/contacts/calendar client. So far I've tried the built in Evolution program, and it seems pretty good. The first time I open it in a session, however, it prompts me for my password to access the "default keyring" or something, which is really annoying. What is that?


See this [thread](http://ubuntuforums.org/showthread.php?p=6369065#post6369065) for a solution.


Good Luck

p.s I use Evolution as a mail client.

---

### Post by TBSN on 2008-12-14
So, people generally think Evolution is the best?

---

### Post by blueshead on 2008-12-14
I like thunderbird..  very much

---

### Post by TBSN on 2008-12-14
> **blueshead said:**
> I like thunderbird..  very much

Do you use the calendar? That's what I'm most interested in. The mail part is pretty similar in all of the programs IMO.

---

### Post by TBSN on 2008-12-15
I still haven't gotten Evolution to stop asking me for my password. I went to System> Preferences >Encryption and Keyrings, and the drop down menu for "Default key" says "none. prompt for a key" and there are no other options in the menu. The other tab in the window is PGP Passphrases...

Help!!

---

### Post by plucky on 2008-12-16
Try **Applications > Accessories > Passwords and Encryption Keys > Edit > Preferences** and change the password to your login password.

Good Luck

---

### Post by TBSN on 2008-12-16
Thanks, that did it! I had to login as root to do it. I still have no idea what keyrings *are* though.

Thanks for the help. So far Evolution is pretty great, too bad it doesn't sync with the MobileMe Calendar as far as I know...

---

### Post by TBSN on 2008-12-16
> **plucky said:**
> Try **Applications > Accessories > Passwords and Encryption Keys > Edit > Preferences** and change the password to your login password.

Good Luck

Alright, I tried that, but it's still not working!

I logged in as root, went to **Applications**->**Accessories**>**Passwords and Encryption Keys**, then **Edit**->**Preferences**, then under **Password Keyrings** I clicked on the only entry, **Login**[I]:automatically unlocked when user logs in
[/I]

It is set to my user password, not the root. Still, every time I restart the computer and open Evolution it asks for my password.

In the other thread that was linked, it says to go to **Encryption and Keyrings** under System>Preferences, then make sure that the login keyring has the same password as my login password...

All I see in the encryption tab is "Default Key: None. Prompt for a Key."

There are no other options in the drop down menu.

I am at a loss, what should I try next??

Thanks for any ideas!

---

### Post by plucky on 2008-12-17
> **I logged in as root,** went to Applications->Accessories>Passwords and Encryption Keys, then Edit->Preferences, then under Password Keyrings I clicked on the only entry, Login:automatically unlocked when user logs in

Are you sure you are actually changing the correct password?

Is the root account enabled?

Did you login as root user? By the way,this is not recommended.

I have just tried this on my system and I was able to change it without resorting to using sudo as this is the keyring for my account.

Just login to your account,go to that location and delete the login keyring.Then add it and give it your login password.

Then logout and back in,if it works then it shouldn't ask for your keyring password when you open evolution.


Good Luck

---

### Post by TBSN on 2008-12-17
*Edit*

Alright, I figured it out. I was set to login automatically, and that did not unlock my keyring at startup. When I manually put in my username and password at startup, the keyring was automatically unlocked... weird.

Thanks!

---

