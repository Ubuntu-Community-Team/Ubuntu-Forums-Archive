---
title: "How restart the configurations to default in login?"
date: 2009-05-23
forum: General Help
---

### Post by gaiterin on 2009-05-23
Hi!
I like install Ubuntu in a snack bar.
The computer will be used by more people and I like do it (free) because it will be a good point for the contact between ubuntu & new users.

Will be perfect a guest session in GDM, but it can't :(
[https://bugs.launchpad.net/baltix/+source/gdm-guest-session/+bug/264835](https://bugs.launchpad.net/baltix/+source/gdm-guest-session/+bug/264835)

I like create a user wihout privileges, but the pleople can change the wallpaper, remove panels... This is more dangerous for next sessions! :(

Then I think the solution of restart the configuration of a user to default in the login, maybe a script that remove configuration directories of applications in the login???
By example, remove .mozilla restart the configuration of Firefox :O

I think too create a launcher in sessions with this line:
/usr/share/gdm/guest-session/guest-session-launch
for open it in the login user, but if the user logoff, the user password dialog appear :( it isn't a solution.

Any ideas please? Thanks very much!

---

### Post by KhurramM on 2009-05-23
make a user but without admin powers and without password login

man sudoers

this will detail u.

Hope this helps....... :p

---

### Post by gaiterin on 2009-05-23
Thanks by answer, but the user can be remove things as panels, change wallpaper... :O

---

### Post by gaiterin on 2009-05-25
Hi!
I did this for have a "guest" false session with GDM Login:

1.- Create a count without privileges (example Guest).

2.- Configure this count (Guest).

3.- Add all files (included hidden) to a .tar file and save it (example /etc/init.d/guest.tar)

4.- Create this file /etc/init.d/guest.sh
With this context:
```
#!/bin/sh
rm -rf /home/guest
mkdir /home/guest
chown guest:guest /home/guest
tar -C /home/guest -xvf /etc/init.d/guest.tar
```

5.- In terminal:
```
sudo chmod +x /etc/init.d/guest.sh
sudo update-rc.d guest.sh defaults
```


With this 5 steps, all configuration user is restart to "default" (in .tar file), in each restart :)
Cheers!

---

