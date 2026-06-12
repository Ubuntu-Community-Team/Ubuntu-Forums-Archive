---
title: "is there a way to rename a user?"
date: 2005-09-09
forum: Desktop Environments
---

### Post by pear-i on 2005-09-09
hey there -- just wondering if there's a way to rename a user -- that is change the user name.

>i was thinking of making a completely new account but i've already setup the settings for the first account so just need away to use a different username and still retain all the settings

thanks

---

### Post by XDevHald on 2005-09-09
[QUOTE=pear-i]hey there -- just wondering if there's a way to rename a user -- that is change the user name.

>i was thinking of making a completely new account but i've already setup the settings for the first account so just need away to use a different username and still retain all the settings

thanks[/QUOTE]
 if you're requesting for this account to be changed by it's user name here in the forums then yes. If you're requesting by your ubuntu desktop login then you can simply goto System > Administration > and create a new user and delete the old one but be sure to set the user to 1000 as it's going to need full priviledges.

If anyone finds this to be a different way than what they're doing and have a better setup, please feel free in providing that.

Thanks.

---

### Post by iimess on 2005-09-09
[QUOTE=][/QUOTE]
 I was wondering about that too but thought that some apps may include a full home path in their configuration files or use the user name as some keys, that would be too much hassle...

Has anyone tried just moving their home directory?

---

### Post by John Nilsson on 2005-09-09
There is absolutely no need to create a new user.

This command should do it for you:
```
usermod -u <oldname> -l <newname> && mv /home/<oldname> /home/<newname> 
```

If any application uses a full path to your home directory in a config file it's broken. the correct way to address a folder in your home dir is $(HOME)/<folder>.

If you want to make sure you can use grep to search for such configs.

```
grep "home/<oldname>" -R .*
```

---

### Post by iimess on 2005-09-09
[QUOTE=][/QUOTE]
 just did the grep "home/<oldname>" -R .* and returned .gconf/desktop, .gconf/apps, .gnome2/totem_config, .nautilus/metafiles/, .mozilla/firefox, some sessions and a bunch of others.

guess I shouldn't do that....

---

### Post by John Nilsson on 2005-09-09
You could try something along these lines:
```
grep -l "home/<oldname> -R ." | xargs sed -i.BAK 's|home/<oldname>|home/<newname>|'
```

The grep part is probly a little redundant, but it this case it has allready been proven to give sensible results.

---

### Post by John Nilsson on 2005-09-09
And you should probably not have your desktop running while doing this...

---

### Post by PaulieG on 2007-01-12
> **John Nilsson said:**
> There is absolutely no need to create a new user.

This command should do it for you:
```
usermod -u <oldname> -l <newname> && mv /home/<oldname> /home/<newname> 
```

If any application uses a full path to your home directory in a config file it's broken. the correct way to address a folder in your home dir is $(HOME)/<folder>.

If you want to make sure you can use grep to search for such configs.

```
grep "home/<oldname>" -R .*
```

Perhaps this should be more like:
```
usermod -l <newname> -d /home/<newname> -m <oldname>
```
-u accepts uid as parameter, and you can move the directory by using -d with the -m

Also, you may want to change the group name - by default the group name is same as user login
```
groupmod -n <newgroup> <oldgroup>
```

---

### Post by cyrano24100 on 2007-08-10
Wow this worked really well! Thanks PaulieG

---

