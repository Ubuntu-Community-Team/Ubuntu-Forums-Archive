---
title: "Question about changing my username"
date: 2009-01-27
forum: General Help
---

### Post by blueshiftoverwatch on 2009-01-27
I activated superuser from the terminal and used the **usermod -l newloginname oldlginname** command to change my username.

But the name of my home directory is still my old name. And after going into 'System > Administration > Users and Groups' I found that the main group that my username belongs to is also the same as my old name.

Is there a way to change my username and have every instance of my old username being used on the computer changed to the my new username as well?

Is there a way to change the name of my username's main group to my new username for consistency purposes? For example, if I'm ever following a tutorial that deals with users or groups sometime in the future it would probably assume that my username and main group name are the same. Which might cause a slowdown because I'd have to keep remembering every time my group name came up that it's different from my username. Which wouldn't be a real problem, but somewhat of a nuance.

Also, could changing my username (or computer name) cause problems with certain applications that might be used to my old username and not know what to do now that I'm trying to access it with a new username?

I'm pretty sure that I'm just going to change my username back to what it was originally. But I figured that this would present a good opportunity for learning if I asked some questions.

---

### Post by carolinason on 2009-01-27
[COLOR="Red"]**always back up data**[/COLOR]

**quick way** is to delete the new user and use the adduser command, but you'll have to import your old settings```
sudo adduser newusername
```

or to keep at it do this, it might not be the most efficient, but it's how i would do it. 

**add the new group** with the same UID as the newuseraccount if the newuseraccount has uid 1001 then use it```
sudo addgroup --gid 1001 newaccountname
```
**add the new group to the new username**, mind you it is the same as the newusername```
adduser newusername newusername
```**change the home directory name** of the old /home/dir to the new one```
sudo mv /home/oldaccountname /home/newaccountname/
```
**change the ownership** of the newly renamed directory to the new username and group recursively to include the subdirectories ```
sudo chown -R newaccountname:newaccountname /home/newaccountname/
``` 
**assign the newly renamed folder to the new account** ```
usermod -d /home/newaccountname newaccountname
```

i THINK that should do it


if you type the below code then you'll see instructions for adding/appending a group. ```
man usermod
```  You also want to look over adduser ```
man adduser
```

---

### Post by blueshiftoverwatch on 2009-01-27
Thanks for all of the help so far.

When I logged into my new account instead of my oldaccountname folder being my newaccoutnname folder my oldaccountname folder was inside my newaccoutnname folder. So I deleted most of the files out of my newaccountname folder and copied+pasted them from my oldaccoutnname folder into the newaccountname folder.

But so far there seems to be one thing wrong. I don't have access to the sudo command under my new name. And I don't know how to give my new account the same privileges my original one had by logging as superuser over the command line.

So if I can just get sudo privileges for my new account I think that everything going to be ok.

---

### Post by dcstar on 2009-01-27
> **blueshiftoverwatch said:**
> 
........
So if I can just get sudo privileges for my new account I think that everything going to be ok.

System-Administration-Users and Groups-Properties-User Privileges, tick the "Administer..." box.

---

### Post by blueshiftoverwatch on 2009-01-27
> **dcstar said:**
> System-Administration-Users and Groups-Properties-User Privileges, tick the "Administer..." box.
I tried doing that before posting. But since 'Users and Groups' is a system configuration program you need sudo privileges to access it in the first place.

Besides, wouldn't ticking the administer box give my account full time admin privileges? I only want temporary admin privileges through sudo. Having them on all the time could be a security risk.

---

### Post by blueshiftoverwatch on 2009-01-28
Nevermind, I got it to work. Just did a web search and found the command I needed.

---

