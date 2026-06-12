---
title: "Really Screwed my System This Time!"
date: 2007-09-11
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-09-11
Been trying to get this cron DISPLAY problem sorted, and I changed t he permissions on ALL the files in my Home dir, and now it wont even display the folders as folders! is this fixable?
Dont know what Ive done, but I had to logon as my backup user as I couldnt even logon as me at all. 
Please Help!
Steve

---

### Post by raja on 2007-09-11
You really need to provide more information for anyone to understand the problem. If the problem is with the permissions on the files in your home folder, can you tell us what you have set the permissions as? You should be able to log in as root and change them again.

---

### Post by merlinus on 2007-09-11
You might try this:

```

sudo chmod -R 755 /home/username

```

---

### Post by mister_p_1998 on 2007-09-11
Yeah tried that,
Thanks! It worked a treat!
Must stop messing around with permissions!
Any idea how to solve my other problem with Cron?

[http://ubuntuforums.org/showthread.php?t=547489&highlight=cron](http://ubuntuforums.org/showthread.php?t=547489&highlight=cron)

Im getting an error msg from cron saying it cant access DISPLAY:0 so none of my tasks will run.

---

