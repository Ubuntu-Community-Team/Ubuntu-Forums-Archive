---
title: "NetworkManager/Gnome-Do require auth. to access &quot;default keyring&quot;"
date: 2009-07-25
forum: Desktop Environments
---

### Post by FFighter on 2009-07-25
Hello forum!

I'm running Ubuntu 9.04 and whenever I start Gnome and the NetworkManager and/or the Gnome-Do processes are started, I get the following message dialog:

(In this case, the sample is for Do)

> The Application 'Do' (/usr/bin/mono) wants access to the default keyring but it is locked.

Password:_____________

Deny/OK


I don't remember when it started to happen, but it is really annoying and I have no idea on how to change this behavior. Another thing is that it is using an old password (I recently changed my account password).

Any help would be really appreciated :)

Thanks,

Marcelo.

---

### Post by directhex on 2009-07-25
> **FFighter said:**
> Hello forum!

I'm running Ubuntu 9.04 and whenever I start Gnome and the NetworkManager and/or the Gnome-Do processes are started, I get the following message dialog:

(In this case, the sample is for Do)



I don't remember when it started to happen, but it is really annoying and I have no idea on how to change this behavior. Another thing is that it is using an old password (I recently changed my account password).

Any help would be really appreciated :)

Thanks,

Marcelo.

The Default Keyring is where GNOME stores passwords for assorted services (e.g. network shares or wireless networks). It is unlocked on login, using the same password which you used to log in (note, I did not say "your password", I said "the password which you used to log in, i.e. autologin means no password to log in)

You can change the password on your default keyring through Accessories/Passwords & Encryption Keys

---

### Post by FFighter on 2009-07-25
> **directhex said:**
> The Default Keyring is where GNOME stores passwords for assorted services (e.g. network shares or wireless networks). It is unlocked on login, using the same password which you used to log in (note, I did not say "your password", I said "the password which you used to log in, i.e. autologin means no password to log in)

You can change the password on your default keyring through Accessories/Passwords & Encryption Keys

Thanks for the reply directhex.

So, I assume the operation to save the login password is a one-time one, and it saves the password the first time it is used. The password I used to login **is** the password of my account, and just after I do that, and the keyring dialog appears asking for the password, I have to type my old password in order to give NetworkManager and Gnome-Do access to the "default keyring".

Is there any way to disable or modify this behavior so that I don't need to type my password two times when starting my system?

Thanks again,

Marcelo.

---

### Post by ajgreeny on 2009-07-25
I think that provided you are aware of, and happy with the reduced security level, you can go to Accessories/Passwords & Encryption Keys and change the password of your keyring there to be blank, ie, don't enter anything in the box, just hit enter.  The request for the password will then disappear, I believe.

---

### Post by directhex on 2009-07-25
> **FFighter said:**
> Thanks for the reply directhex.

So, I assume the operation to save the login password is a one-time one, and it saves the password the first time it is used. The password I used to login **is** the password of my account, and just after I do that, and the keyring dialog appears asking for the password, I have to type my old password in order to give NetworkManager and Gnome-Do access to the "default keyring".

Is there any way to disable or modify this behavior so that I don't need to type my password two times when starting my system?

Thanks again,

Marcelo.

For whatever reason, the passwords have fallen out of sync. If you change the default keyring password to match your new one, then problem goes away

---

### Post by FFighter on 2009-07-25
Thanks ajgreeny and directhex for the replies.

> **ajgreeny said:**
> I think that provided you are aware of, and happy with the reduced security level, you can go to Accessories/Passwords & Encryption Keys and change the password of your keyring there to be blank, ie, don't enter anything in the box, just hit enter.  The request for the password will then disappear, I believe.

No way to disable this behavior? This would save me some keyboard hits, but the annoying dialogs would still pop up. This reminds me of Windows Vista "security" confirmation dialogs. 

Now, don't get me wrong. I'm sure gnome-keyring is a good piece of software and that it can be useful, it's just that in this context it is being annoying to me, and I just want to get rid of it. Putting my username/password when I login is enough, I don't want another layer of security other than the default Linux's one.

Thanks for the help!

Marcelo.

---

### Post by directhex on 2009-07-25
> **FFighter said:**
> Thanks ajgreeny and directhex for the replies.



No way to disable this behavior? This would save me some keyboard hits, but the annoying dialogs would still pop up. This reminds me of Windows Vista "security" confirmation dialogs. 

Now, don't get me wrong. I'm sure gnome-keyring is a good piece of software and that it can be useful, it's just that in this context it is being annoying to me, and I just want to get rid of it. Putting my username/password when I login is enough, I don't want another layer of security other than the default Linux's one.

Thanks for the help!

Marcelo.

If you set the password to be blank, then it won't ask you for a password (and will store any passwords you enter into things like network-manager in plain text)

If you set the password to be the same as your login password (i.e. your current one, not your old one) then it won't ask you for a password (and will be unlocked automatically on login)

---

### Post by xjgnsdof on 2009-10-17
I had this problem in Karmic beta. Clearing out the keyring password worked, though.

If you have a strong password at login (or, better yet, at boot-up), why would you even need a password for the network manager?

---

### Post by jessiebrownjr on 2009-10-18
On my laptop AND Desktop, I have auto login sense theres no way anybody will access my computers...  Now, on my laptop, once I turned it to auto login as user, the keyring pops up before I can use my wifi passwords..

---

### Post by directhex on 2009-10-18
> **jessiebrownjr said:**
> On my laptop AND Desktop, I have auto login sense theres no way anybody will access my computers...  Now, on my laptop, once I turned it to auto login as user, the keyring pops up before I can use my wifi passwords..

For reasons which have already been clearly stated, with workarounds which have already been clearly stated

---

