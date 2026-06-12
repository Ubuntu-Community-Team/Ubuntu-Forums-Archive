---
title: "Users in GUI tool"
date: 2009-06-13
forum: General Help
---

### Post by johnsd on 2009-06-13
Hi

I have been a Linux user for over 10 years now but this is the first time I have ventured away from the RedHat stream of distros. A question that is bothering me. When I installed Ubuntu I obviously created a user. I can see it in the /etc/passwd file with an ID of 501. When I look in the GUI tool (system->administration->users & groups) there is only the root user.

So - why doesn't the non-priviledged user I created show up here?

Thanks
John

---

### Post by synapsys on 2009-06-13
Did you login as root?

---

### Post by johnsd on 2009-06-13
> **synapsys said:**
> Did you login as root?
I clicked the "unlock" button if that is what you mean?

---

### Post by vijushimpi on 2009-06-14
Open terminal and see whether what name it says , as I made one account at installing and in terminal it says vijay@vijay .

---

### Post by johnsd on 2009-06-14
Yep - it has my normal account at the terminal (johnd@Cyclone). One would think that this user would show up in the GUI tool.

---

### Post by CatKiller on 2009-06-14
> **johnsd said:**
> So - why doesn't the non-priviledged user I created show up here?

I'm pretty sure that a user id of 1000 is configured to be the first "real" user on a default Ubuntu install, with numbers below that assumed to be system users. I'd imagine that you can change that in a config file somewhere, or to show all users in the graphical tools.

---

### Post by johnsd on 2009-08-03
> **CatKiller said:**
> I'm pretty sure that a user id of 1000 is configured to be the first "real" user on a default Ubuntu install, with numbers below that assumed to be system users. I'd imagine that you can change that in a config file somewhere, or to show all users in the graphical tools.

Yes - I have setup a new user and she has an ID of 1000. So now this makes sense - but it does not seem particularly sensible. The natural place for a user to go to change their password would seem to be system->administration->users and groups but the first user is not even there (but fortunately you can change your PW at system->preferences->about me).

---

### Post by The Cog on 2009-08-03
> **johnsd said:**
> The natural place for a user to go to change their password would seem to be system->administration->users and groups but the first user is not even there 
I think this is because you changed the users ID, presumably during install. I think the GUI by default shows user ids >= 1000, and I know for sure that by default, the first user is 1000.

---

### Post by johnsd on 2009-08-04
> **The Cog said:**
> I think this is because you changed the users ID, presumably during install. I think the GUI by default shows user ids >= 1000, and I know for sure that by default, the first user is 1000.
No - I certainly didn't change the UID - but I think I might have an idea of how this has happened - both machines I have installed Ubuntu on so far have had an existing /home partition. So could it be it has picked up the UID from there? Redhat based systems start UIDs at 500.

---

### Post by Sonador on 2009-10-25
> **CatKiller said:**
> I'm pretty sure that a user id of 1000 is configured to be the first "real" user on a default Ubuntu install, with numbers below that assumed to be system users. I'd imagine that you can change that in a config file somewhere, or to show all users in the graphical tools.

Hi, does anybody know how to solve it, where are those config files? I am coming from fedora too, and have some "50*" users. I would like to avoid a CHOWNing.

---

### Post by wersdaluv on 2009-11-01
Same prob here

---

