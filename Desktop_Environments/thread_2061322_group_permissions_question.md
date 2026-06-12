---
title: "group permissions question"
date: 2012-09-22
forum: Desktop Environments
---

### Post by andrewjs18 on 2012-09-22
Hi,

I'm running ubuntu desktop as a web server for the first time and have a question regarding group permissions.

currently all the files hosted from my server are for my own sites, but I plan on hosting two sites for two different friends of mine as I used to host their sites when I had shared hosting.  right now I have their directories set up and have them as the owner of those directories, but what I'd like to do is be able to have my account that I use for my website directories to also be able to modify the directories I set up for my friends.

so for example, when I sftp into my server with my username, I'd like to be able to add/edit/remove files from not only the directories that I'm the owner of, but also the directories for my friend's sites.

is this possible?  if so, how?

sorry, I'm trying to get back into the swing of using linux more often so forgive me if this is a simple task.

---

### Post by Lars Noodén on 2012-09-22
You can make a group for each site and then add people to the group to allow them to edit.

```

sudo addgroup website1

sudo gpasswd --add andrewjs18 website1
sudo gpasswd --add friend1 website1


sudo chgrp -R website1 /var/www/website1/
sudo find /var/www/website1 -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www/website1 -type f -exec chmod g=rws  "{}" \;

```

If you want to allow them to edit the Apache virtual host file for their site, then you have to add similar group permissions for just that one file.

---

### Post by andrewjs18 on 2012-09-22
> **Lars Noodén said:**
> You can make a group for each site and then add people to the group to allow them to edit.

```

sudo addgroup website1

sudo gpasswd --add andrewjs18 website1
sudo gpasswd --add friend1 website1


sudo chgrp -R website1 /var/www/website1/
sudo find /var/www/website1 -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www/website1 -type f -exec chmod g=rws  "{}" \;

```If you want to allow them to edit the Apache virtual host file for their site, then you have to add similar group permissions for just that one file.

thanks.  I'll try it out after I get some sleep.

---

