---
title: "Official word on Breezy to Dapper upgrade?"
date: 2006-05-16
forum: Desktop Environments
---

### Post by catlett on 2006-05-16
Hello,
I was hoping to get an answer on the way the Breezy to Dapper upgrade happens June 1st. I have noticed alot of people asking and I realised I do not know the answer.
When June 1st comes do people with Breezy and Breezy repositories just run sudo apt-get dist-upgrade to acquire the Dapper upgrade?
Or do they have to change their repository list? If they change their repository list is it as easy as replacing the word Breezy with Dapper? Or are there more differences in the URLs than Dapper?
If you change your repository list from Breezy to "stable" will you always get upgraded to the stable version of Ubuntu no matter what it's name is? Or again are their more differences in the URLs than just the name?
What is the distributions recommended way for people to upgrade from Breezy to Dapper? Through apt-get dist-upgrade? Through aptitude dist-upgrade? Through installation of a Dapper CD?
Finally, if someone is happy with their Breezy install and doesn't want to upgrade, can they keep Breezy? If so do they have to change anything in their repositories? Do they keep the same list and as long as it says Breezy they will only get Breezy packages? Or do they have to stop using the updater and apt-get update to prevent Dapper packages from being installed.
Thank you in advance. I'd like to respond to people but I don't want to assume I know the correct way. I have my understanding of the upgrade but I would like to refer people to the official procedure so noone's install is compromised by uninformed advice.
Have a nice upgrade.

---

### Post by matthew on 2006-05-16
[quote=catlett]When June 1st comes do people with Breezy and Breezy repositories just run sudo apt-get dist-upgrade to acquire the Dapper upgrade?[/quote]No
> Or do they have to change their repository list? Yes
> If they change their repository list is it as easy as replacing the word Breezy with Dapper? Basically. See the wiki page I refer you to at the bottom of this post
>  If you change your repository list from Breezy to "stable" will you always get upgraded to the stable version of Ubuntu no matter what it's name is?No
> What is the distributions recommended way for people to upgrade from Breezy to Dapper? Through apt-get dist-upgrade? Through aptitude dist-upgrade? Through installation of a Dapper CD?Actually, any of these will work. Again, see the page linked below
>  Finally, if someone is happy with their Breezy install and doesn't want to upgrade, can they keep Breezy?Certainly
> If so do they have to change anything in their repositories? Do they keep the same list and as long as it says Breezy they will only get Breezy packages?Keep the same list. Only security updates will be given.

I am going to refer you to this wiki page for the official scoop.

[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by catlett on 2006-05-16
Thank you.  [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) That was exactly what I was looking for.

---

### Post by changlinn on 2006-05-16
I heard there was going to be an update available to breezy that automatically changed your repos, did a update then dist-upgrade anyone else heard this?

---

### Post by az on 2006-05-16
[QUOTE=changlinn]I heard there was going to be an update available to breezy that automatically changed your repos, did a update then dist-upgrade anyone else heard this?[/QUOTE]
Yes, the update manager will prompt you and ask if you want to upgrade to Dapper.


Your sources.list would then be changed automagically, if that is what you choose.

---

### Post by Sef on 2006-05-17
> Yes, the update manager will prompt you and ask if you want to upgrade to Dapper.


Your sources.list would then be changed automagically, if that is what you choose.

That will be so nice for so many Breezy users.

---

### Post by nocturn on 2006-05-17
[QUOTE=changlinn]I heard there was going to be an update available to breezy that automatically changed your repos, did a update then dist-upgrade anyone else heard this?[/QUOTE]

I used it on one machine and it worked great!

---

### Post by bluenova on 2006-05-17
Ok, so again, the mods of this forum are giving differnt opinions as to how to upgrade, which I've seen in all the upgrade to dapper threads that I've read.

So going on what was said by azz, Sef and nocturn we don't need to do anything. As soon as Dapper goes stable Breezy will ask us if we want to upgrade? (If the upgrade manager applet is running).

---

### Post by matthew on 2006-05-17
[quote=bluenova]Ok, so again, the mods of this forum are giving differnt opinions as to how to upgrade, which I've seen in all the upgrade to dapper threads that I've read.[/quote]That's because there are multiple ways to perform the upgrade. Our statements aren't actually in conflict one with another, rather we are each giving our individual perspectives and understandings--none of which contradict the other(s).

[quote=bluenova] So going on what was said by azz, Sef and nocturn we don't need to do anything. As soon as Dapper goes stable Breezy will ask us if we want to upgrade? (If the upgrade manager applet is running).[/quote]I'll let them answer this part. :)

---

### Post by bluenova on 2006-05-17
Thanks matthew, I understand that there are multiple ways, and also that there are new ways for dapper. I'm just looking for the simplest method (and an official method), and got a bit annoyed after seeing so many different opinions (in other posts). No disrespect was meant, and thanks for taking the time to reply.

---

### Post by az on 2006-05-17
> **bluenova]and got a bit annoyed after seeing so many different opinions (in other posts).[/QUOTE]

I blame the doc team (   said:**
>  we don't need to do anything. As soon as Dapper goes stable Breezy will ask us if we want to upgrade? (If the upgrade manager applet is running).

Yup.

---

