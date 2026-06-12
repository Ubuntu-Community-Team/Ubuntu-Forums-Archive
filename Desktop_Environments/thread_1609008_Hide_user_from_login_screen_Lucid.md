---
title: "Hide user from login screen Lucid"
date: 2010-10-29
forum: Desktop Environments
---

### Post by MSPdwalt on 2010-10-29
So...

I actually got my boss to let me put Ubuntu on a laptop for a client and it works like a champ.  I have it all setup but there's one thing I'd like to do on it.  I have an admin user (the one I created during the install) and a desktop user (for the person receiving the laptop).  I would like to hide my admin user from the login screen, so when it boots up all the user sees is their name.  If I need to help them with something/install software I can choose other and login as my admin user.

It appears this was rather easy in 9.10 and previous but I can't figure out how to do it in 10.04. [COLOR=Red]**To be clear, I want to edit the user list, not disable it entirely.**[COLOR=Black]  I've tried changing the user id, I found a post that claimed IDs less than 1000 were not shown on the login screen, this proved un-true in my case.

Any help would be greatly appreciated.

DW
[/COLOR][/COLOR]

---

### Post by jrev on 2010-10-30
Just make an automatic login on the user you select in 
system/admin/login window.
The session will open automatically on the user

---

### Post by MSPdwalt on 2010-10-30
> **jrev said:**
> Just make an automatic login on the user you select in 
system/admin/login window.
The session will open automatically on the user
Thanks for the reply, but I want them to have to enter their password.  I want to have a user on their machine without them knowing and without enabling root.

---

### Post by MrEgg on 2010-12-09
Hey,

On Lucid, place the users you want to hide under the 1000 level (eg 999, 998, 997, etc.). They'll be removed from the login screen and from the Disconnect menu. Works in my case.

```
sudo usermod -u 999 username
```

Cheers,
Egg

---

### Post by Krytarik on 2010-12-09
How about this: [http://fedoraforum.org/forum/showthread.php?t=246103](http://fedoraforum.org/forum/showthread.php?t=246103)

Seems it should work in Ubuntu too, checked the gdm.schemas-file.

If that doesn't work you could still disable the user list at all, in a terminal type:
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

---

### Post by MSPdwalt on 2010-12-10
Thanks guys,

I'll give your suggestions a try if I can ever get my hands on that laptop again LOL.  I gave it to the customers CIO to test and see if he felt his user base could function in Ubuntu.  He loved it so much he won't give it back.

---

### Post by sisco311 on 2010-12-10
> **MSPdwalt said:**
> 
It appears this was rather easy in 9.10 and previous but I can't figure out how to do it in 10.04. [COLOR=Red]**To be clear, I want to edit the user list, not disable it entirely.**[COLOR=Black]  I've tried changing the user id, I found a post that claimed IDs less than 1000 were not shown on the login screen, this proved un-true in my case.

Any help would be greatly appreciated.

DW
[/COLOR][/COLOR]

Edit the /etc/gdm/gdm.schemas file and the admin user to the list of users of the greeter/Exclude stanza:
```
...
    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**username,**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>
...
```

---

### Post by Megaptera on 2010-12-10
If you look at Ailurus, available through Software Centre, it has the option to disable user list at log in. That way your boss would have to enter his/her log in name and get to his/her account. Provided your boss didn't know your log in name he/she couldn't access you account.
Would that be an option?

---

### Post by MSPdwalt on 2011-01-05
> **sisco311 said:**
> Edit the /etc/gdm/gdm.schemas file and the admin user to the list of users of the greeter/Exclude stanza:
```
...
    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>**username,**bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>
...
```

This did it! Thanks a lot sisco311!

---

### Post by Krytarik on 2011-01-05
Since "/etc/gdm/gdm.schemas" is included in the gdm install package, your modification will most likely get overwritten by an update of the package (just yet did further research).

Thus you should instead modify "/etc/gdm/custom.conf" by adding:
```
[greeter]
Exclude=user1,user2
```Those file will definetely not get overwritten by an update.

---

### Post by MSPdwalt on 2011-01-17
> **Krytarik said:**
> Since "/etc/gdm/gdm.schemas" is included in the gdm install package, your modification will most likely get overwritten by an update of the package (just yet did further research).

Thus you should instead modify "/etc/gdm/custom.conf" by adding:
```
[greeter]
Exclude=user1,user2
```Those file will definetely not get overwritten by an update.

I was able to confirm that the changes would be lost, I also found out on Ubuntu (at least on Lucid) you need to create the /etc/gdm/custom.conf file.  Also for some reason when I added my exclusion to custom.conf and removed it from gdm.schemas the user nobody started showing in the login screen even though it is excluded by default in the gdm.schemas and still was on my copy.

I added it to my custom.conf and this worked as desired.

Thanks again Krytarik this was very helpful.

---

### Post by Krytarik on 2011-01-17
Thanks for the feedback!

---

