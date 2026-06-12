---
title: "Gutsy~my user name doesnt exist?"
date: 2009-02-07
forum: General Help
---

### Post by KEE on 2009-02-07
i tried to change  my user name but i logout thinking that it will change everying thing on its own.system>administration>user and groups. it didnt! 

 so im stuck with the cd because i cant change my home location to what I want because i dont have permission to and i cant login either because my login has changed but with no home directing because its not changed. Please help ! there must be a way to get permissions to change stuff like that :/ i mean i had to type my pass word to change my user name. i cant even login as root:/

i tried ```
sudo nautilus
```
 but i cant get into the home directory to change it because i guess im on the cd :/ again please help!

---

### Post by The Cog on 2009-02-07
Choosing recovery mode from the boot menu will give you access to the system, as root.

How did you change whatever you changed?

I think the files that need changing to change a username are /etc/passwd, /etc/shadow, /etc/group, and rename your home directory.

I did it once, and found that some apps store the full path to your home in their config files, which of course gets broken. Evolution was a nightmare to sort out.

---

### Post by KEE on 2009-02-07
> **The Cog said:**
> Choosing recovery mode from the boot menu will give you access to the system, as root.

How did you change whatever you changed?

I think the files that need changing to change a username are /etc/passwd, /etc/shadow, /etc/group, and rename your home directory.

I did it once, and found that some apps store the full path to your home in their config files, which of course gets broken. Evolution was a nightmare to sort out.
how do you choose the recovery mode? i have the cd but i cant find that option

---

### Post by KEE on 2009-02-07
> **The Cog said:**
> Choosing recovery mode from the boot menu will give you access to the system, as root.

How did you change whatever you changed?

I think the files that need changing to change a username are /etc/passwd, /etc/shadow, /etc/group, and rename your home directory.

I did it once, and found that some apps store the full path to your home in their config files, which of course gets broken. Evolution was a nightmare to sort out.
ok i got recovery opened but not sure open root :/ it basically terminal. whats the command to open it?

---

### Post by KEE on 2009-02-07
i changed the my user to something thing different but then logout without changeing the home/user so now i cant login. im in recovery but im not sure how to "sudo <commaned>" to create a user or restore my last user so can login. i f i can be able to make a /user/passwd,/user/shadow /user/group but i still dont know the "sudo <commaned> Please help!

---

### Post by funkyFlash on 2009-02-07
Something along the lines of ```
sudo useradd -m -s /bin/bash -G wheel iamareallycooluser
```  Maybe with a splash of ```
sudo passwd iamareallycooluser
```

---

### Post by KEE on 2009-02-08
> **funkyFlash said:**
> Something along the lines of ```
sudo useradd -m -s /bin/bash -G wheel iamareallycooluser
```  Maybe with a splash of ```
sudo passwd iamareallycooluser
```
ok sudo useradd opens up the list of commands and not sure conjoin them. I want change my username back to what it was before. password doesnt have to be changed so I can leave that out, I think. tell me if im wrong :)  
```
-G, --gid groups
-m, --create-home

```
i think thats it. do i need to do the shell? i even think the -m could go since the home directory is still there. yeah so if someone could tell me how  to conjoin this to a command to change my username from what it is now towhat i want :) please and thank you

---

### Post by The Cog on 2009-02-08
To open what? You should have a command prompt ending with a # symbol. This is roots command prompt. You have full power from there.

If you know what file you edited to make the change, you can use nano to edit the file and change it back:
**nano filename**

You still haven't said what you did to break the system while trying to change the username. That makes it hard to suggest how to fix it, other than "change it back again".

Assuming that you can get it back, I suggest that next time, you create a second user with admin rights before trying to change the first users name again. That way, you should be able to get back in easier if it goes wrong.

---

### Post by KEE on 2009-02-08
> **The Cog said:**
> To open what? You should have a command prompt ending with a # symbol. This is roots command prompt. You have full power from there.

If you know what file you edited to make the change, you can use nano to edit the file and change it back:
**nano filename**

You still haven't said what you did to break the system while trying to change the username. That makes it hard to suggest how to fix it, other than "change it back again".

Assuming that you can get it back, I suggest that next time, you create a second user with admin rights before trying to change the first users name again. That way, you should be able to get back in easier if it goes wrong.

i went into System>Administration>User and Groups, and i changed the user name and the real name. i tried ```
sudo useradd -G wheel <myusername>
```
but i get ```
useradd:user wheel exists
```

ok i got it ! but now when i login, i get a error message saying my session terminated ater 10 secs heres the error code ```
(process:5300): Gtk-WARNING ** this process is currently running setuid or setgid program instead, for further details, see:

http://www.gtk.org/setuid.html
Refusing to initialize GTK+

(process:5304): Gtk-WARNING ** this process is currently running setuid or setgid
This is not a supported use of GTK+, you must create a helper program instead. for further details, see:

http://www.gtk.org/setuid.html
Refusing to initialize GK+
/etc/gdm/Xsession: Begainning session setup--could not mode0700 on private per-user gnome configuration directory'/home/<user>/.gnome2_private/': Operation not permitted
```

---

### Post by The Cog on 2009-02-09
You have me confused now. Are you using Ubuntu?

In my Ubuntu (version 8.10), System>Administration>User and Groups does not allow me to change the username - it is greyed out. I can change the real name of course, but that wouldn't break anything.

And the wheel group is not used at all in Ubuntu. In Ubuntu, the admin group is used for much the same as wheel was in unix. There is no user wheel in Ubuntu either.

I don't understand the GTK error message either. It claims that you are running setuid or setgid, and I don't really understand how you could get to that situation. It also suggests that perhaps the user doesn't have access to the files in /home/<user>/.gnome2_private/ which suggests that maybe you have managed to scramble the userid configuration.

All I can suggest is that you have a close look at the files /etc/passwd, /etc/shadow and /etc/group and make sure they all have the same username for you. You can use the nano editor from the command line for this. Then find the user id from /etc/passwd (third field) and make sure that matches the userid that your home directory belongs to - the command **ls -l /home** will show you the userid the home folder is assigned to.

---

### Post by bapoumba on 2009-02-09
Threads merged.

---

### Post by KEE on 2009-02-09
> **The Cog said:**
> You have me confused now. Are you using Ubuntu?

In my Ubuntu (version 8.10), System>Administration>User and Groups does not allow me to change the username - it is greyed out. I can change the real name of course, but that wouldn't break anything.

And the wheel group is not used at all in Ubuntu. In Ubuntu, the admin group is used for much the same as wheel was in unix. There is no user wheel in Ubuntu either.

I don't understand the GTK error message either. It claims that you are running setuid or setgid, and I don't really understand how you could get to that situation. It also suggests that perhaps the user doesn't have access to the files in /home/<user>/.gnome2_private/ which suggests that maybe you have managed to scramble the userid configuration.

All I can suggest is that you have a close look at the files /etc/passwd, /etc/shadow and /etc/group and make sure they all have the same username for you. You can use the nano editor from the command line for this. Then find the user id from /etc/passwd (third field) and make sure that matches the userid that your home directory belongs to - the command **ls -l /home** will show you the userid the home folder is assigned to.

well its gone i just reinstalled :/ my old user was there but only the home directory and such, the only thing that was messed up was the username was replace with one that i wanted to replace it with but it immediately logged out and  i was getting that error. i tried making a user loggon but i figured ill stop half into it and just reinstall. i wasnt lossing much besides the updates and all.  thank for your help. a thank you is order but i think that option is gone. we should have achievements so helping another is more addictive =)

---

