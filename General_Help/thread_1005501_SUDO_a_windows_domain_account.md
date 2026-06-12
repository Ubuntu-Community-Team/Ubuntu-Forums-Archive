---
title: "SUDO a windows domain account"
date: 2008-12-08
forum: General Help
---

### Post by blacklabelpaul on 2008-12-08
Noob here to Ubuntu and the forums so be nice here lol.

I've used likewise to successfully join my machine into a Windows AD domain.

Obviously, my ubuntu machine won't magically translate my account (which is a domain admin) to perform admin tasks locally on the machine.

I've tried sudo gedit /etc/groups and added the domain account in the form of domain\j.doe - however, my windows account cannot perform basic tasks that require elevated permission (i.e. changing desktop effects)

Don't know if I am subconsciously stuck in my Windows ways.  

Essentially I'm seeking a straightforward way to grant my windows domain account sudo permissions to add/remove programs, change desktop effects, etc on my ubuntu desktop.

Any advice on this would be super! Thanks! :o)

---

### Post by p_quarles on 2008-12-08
Whatever privileges a user has on the AD domain have nothing to do with changing desktop effects in Ubuntu. Or, to put it more accurately: the account on the Windows domain and the account in the Ubuntu isntallation are not the same account, regardless of whether they have the same name. 

I'm not sure what exactly you're attempting to do, but if you'll describe it, someone here should be able to help.

---

### Post by blacklabelpaul on 2008-12-08
No worries, I can describe in further detail.  Thanks for the quick reply btw

I've joined my Ubuntu desktop into my windows domain.

I am able to login to the desktop using my windows domain account.

At this point, my windows domain account is just a plain old user account, as I expected it to be.  

I am unable to do things in this windows account (add/remove software, enabling desktop effects or configure compiz)

I have the sudo'd local account that Ubuntu creates during installation - however I can't browse my windows network shares with that account like I can with my windows domain account but I am able to add/remove programs and do administrative tasks.

When logging into on my desktop utilizing the windows domain credentials, I'm able to browse my network shares just fine however I am not able to do add/remove programs or enable desktop effects.

I'm seeking the proper method to allow the windows domain account to be an admin for this laptop so that I may run admin tasks while utilizing the active directory credentials and not the local account.

In short - I want to login with my windows credentials and have that account have the same permissions as the account created during in the ubuntu installation.

---

### Post by p_quarles on 2008-12-08
> **blacklabelpaul said:**
> No worries, I can describe in further detail.  Thanks for the quick reply btw

I've joined my Ubuntu desktop into my windows domain.

I am able to login to the desktop using my windows domain account.

At this point, my windows domain account is just a plain old user account.  

I am unable to do things in this windows account (add/remove software, enabling desktop effects or configure compiz)

I have the sudo'd local account that Ubuntu creates during installation - however I can't browse my windows network shares with that account like I can with my windows domain account but I am able to add/remove programs and do administrative tasks.

When logging into on my desktop utilizing the windows domain credentials, I'm able to browse my network shares just fine however I am not able to do add/remove programs or enable desktop effects.

I'm seeking the proper method to allow the windows domain account to be an admin for this laptop so that I may run admin tasks while utilizing the active directory credentials and not the local account.
Okay, I understand you now -- you just want to give the new accounts the same privileges as the first account that Ubuntu created. 

To get the same sudo privileges as the first account, log into that account and run:
```
sudo adduser [newusername] admin
```
For full functionality, you may want to add the new user to all of the groups to which the original user belongs. You can get that list by running:
```
groups
```
By the way, manually editing /etc/groups is not recommended, as that does no error checking. The adduser/usermod command is the best way to go, or alternately the user/groups configuration tool in Gnome.

---

### Post by blacklabelpaul on 2008-12-08
Thank you so much.

You don't know how much I was seeking for such a simple answer.

This is why I've switched to Ubuntu.

Thanks again.

---

