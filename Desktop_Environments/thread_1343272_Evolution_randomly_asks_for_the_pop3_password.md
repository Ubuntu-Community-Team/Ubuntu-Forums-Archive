---
title: "Evolution randomly asks for the pop3 password"
date: 2009-12-01
forum: Desktop Environments
---

### Post by keep-on-smiling on 2009-12-01
Hi

Just wondering if anybody has a work-around for this issue:

I am running Ubuntu 9.10 and generally have few problems except that totally randomly Evolution pops up a password query. Email works via a pop3 / smtp server. I have multiple accounts and as I say, randomly, one or the other account will wobble in Evolution and I get this password query.

What used to happen prior, is that Evolution would wobble, delete the password from the keyring and then pop up a query window asking for the password. Due to having multiple passwords, I sometimes was stuck and had to wait until I got home to get the password re-entered again.

What I have done now is to go into seahorse and set evolutions access as read-only, which at least means it does not delete the password anymore ! Now I merely deny it access to the keyring when it asks. The next send/receive after this works fine again... 

However, what I am aiming to find is some sort of fix for this - maybe there is a setting I can tweak so make Evolution wait a bit longer for a server response (I am assuming that the servers sometimes are too busy to reply fast enough and this is confusing Evolution ?). As more and more of my friends are asking me to install Ubuntu for them, I would really like to find a fix for this !

One comment I can make is that this does not seem distro specific as I has OpenSuse installed with Gnome and the problem was there too.

Thanks for any help anybody might be able to offer

---

### Post by maxsideburn on 2009-12-01
I've got a really simple answer for you...uninstall Evolution.

Just get a Gmail account and be done with it. BY FAR the best email service around.

---

### Post by keep-on-smiling on 2009-12-02
Hello

Yes agreed, that might be the easiest. In past installs of 9.10 I have used Thunderbird - it was what I used in XP and really just works, at least for me - snag is that Evolution comes with Ubuntu so folk kinda wonder when on a fresh install I go ahead and remove one of the main bits of software ! It casts doubt on the rest of the system...

OK guys and gals, any other ideas ?

---

### Post by lisati on 2009-12-02
Whenever evolution asks me for a pop3 password, it's usually because of some problem accessing the server, and there's nearly always some error message in the box. I usually click "cancel" and try again in about a minute or so. Far easier than messing around trying to transfer settings to another client.

---

### Post by keep-on-smiling on 2009-12-02
Hi Lisati

Agreed - this is what I do at the moment - as per my original post.

Seahorse is set to only allow read access for Evolution and I just click cancel when it queries the password.

I just wish there was a way to set Evolution to wait longer, or to retry X number of times first before throwing the error.

All suggestions welcome however.

---

### Post by keep-on-smiling on 2009-12-02
Just an update...

I installed Thunderbird again, with Evolution still onboard, by way of comparison. Thus far Thunderbird has been flawless. When I see another Evolution update I will try it again, subject to any suggestions of course !

---

### Post by Alexandre Putt on 2009-12-03
It might be a problem with POP mail exclusively. I don't remember it occurring on IMAP. I used Mozilla mail before and didn't like the idea of one account-one big file arrangement for my mail. I think it is preserved for Thunderbird as well.

---

### Post by anselm on 2009-12-03
I have this problem with evolution every now then, I think it is on the server side.

I think Evolution is better than Thunderbird  at handling spam.

---

