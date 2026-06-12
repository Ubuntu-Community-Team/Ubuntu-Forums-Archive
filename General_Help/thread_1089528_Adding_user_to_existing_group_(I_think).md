---
title: "Adding user to existing group (I think)???"
date: 2009-03-07
forum: General Help
---

### Post by portly on 2009-03-07
Hi, 

Just installed 8.10 over an earlier install (different distro) because of system issues...

Anyway, I can't seem to add my partners user account, I did do a search about this but for the life of me I don't understand what they're saying/explaining.

I'm not big with CLI and don't follow how I can make sure that her group is still there, as well as add her user account.

Can anyone point me in the right direction please ?

TVM

---

### Post by ssam on 2009-03-07
if you want to avoid the command line then you can control users and groups with System->Adminstration->Users & Groups.

---

### Post by portly on 2009-03-07
Hum? yes I found that.

Unfortunately it's still chucking up a dialogue that won't let me use her normal username - it gives me some error about using a different path.

If that means what I think it does then I still can't get her user account.

It's not that I don't want to use CLI, I just don't speak the "geek or nerd" dialects required by the man pages.

Surely there must be some way of forcing it to make the new username use the old user account and /home ?

---

### Post by sdennie on 2009-03-07
The addgroup command won't let you add an existing group so, the following should be safe:

```

sudo addgroup name_of_group
sudo adduser name_of_user name_of_group

```

If you are logged in as "name_of_user", you will need to logout before the adduser change full takes effect.

---

### Post by portly on 2009-03-07
> **sdennie said:**
> The addgroup command won't let you add an existing group so, the following should be safe:

```

sudo addgroup name_of_group
sudo adduser name_of_user name_of_group

```

If you are logged in as "name_of_user", you will need to logout before the adduser change full takes effect.

Tried that, but it didn't want to play.

So in the end I just deleted the "name of user" group and then just did the adduser thing which seems to have created her user account and allowed it to use her original /home directory.

Now all I have to work out is how to modify the groups/her memberships etc - which would be fine if the developers hadn't tried to make things "easy" - I now can't make the system modify her groups.

The "obvious" ways don't seem to work i.e. finding the users/groups option in the menu, which will only allow me to mod them from there. I can view my own account properties but that's about it, everything else is greyed out, as is everything in the "manage groups" dialogue box that appears if I click that button!

Damn, didn't couldn't "they" see that the kcontrol/kde3 way of admin was pretty much the most straight forward? - and no I have to use kde as I never have managed to get to grips with gnome!

---

