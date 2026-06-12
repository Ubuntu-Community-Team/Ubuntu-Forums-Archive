---
title: "Changing User Name and Password"
date: 2006-04-20
forum: Desktop Environments
---

### Post by Weta on 2006-04-20
Hello

I would like to change the default username and password that our computer came with.  We run Hairy Hedgehog only.  There are no other users on our system.  I have looked through the forums and seen some advice, but the references to "root" and "sudo" make me hesitant to attempt to adjust anything.

Thanks

---

### Post by henryk69 on 2006-04-20
Whithout using the terminal you won't do anything. Don't hesitate, it isn't that hard. I I also would advise you to update to Breezy (5.10) version of the system - things would be much easier.

---

### Post by aysiu on 2006-04-20
What do you mean by "the default"?

Here's what you should do:

Open a terminal (Applications > System Tools > Terminal) and type ```
groups
``` It'll list out all the groups your current user belongs to.

Then, let's say you want to create a user called *newuser*. Type ```
sudo adduser newuser
``` and before pressing return, copy and paste all the groups your previous user belonged to.

I can't remember if it'll prompt you for a password, but I think you can set the password by typing ```
sudo passwd newuser
``` I'm not 100% sure on that, though.

Then, log out, and log in as your new user. If it works for a few days with no problems, go ahead and delete your old user.

---

### Post by Weta on 2006-04-21
Hello  Thanks for the advice.  I will change to Dapper.  "Default" referred to the only user name and account that our computer was supplied with.  I want to create an accountr with full aministrator permissions, and another for general use of the computer.

I tried doing this using "Users and Groups", and was able to create new users.  File Manager does not however allow me to to copy files from the initial users' /home directory into the new directories.  I assume that I need to do this before I remove the initial user.  The Users and Groups tool also enabled me to specify "Default" and "Administrator" users profiles - which I used for the new users (and, e.g., the Default  option doesn't allow access to Synaptic).  This looked like some progress to me..

I also create a new user following Aysiu's advice, although the system didn't allow me to list all of the group names as suggested.  Still, the terminal approach worked a bit as well...

I suspect that I aren't far from a solution, and will keep trying.  Any further advice welcome.  Thanks again for your help.

---

### Post by aysiu on 2006-04-22
[QUOTE=Weta]File Manager does not however allow me to to copy files from the initial users' /home directory into the new directories.  I assume that I need to do this before I remove the initial user.[/QUOTE] ```
sudo cp -R /home/olduser /home/newuser
sudo chown -R newuser:newuser /home/newuser
```

---

### Post by Weta on 2006-04-24
Thanks Aysiu.  That worked well.  I've now created new user accounts for each family member, and given each member ownership of their own files.  If you don't mind, can you know tell me what I need to do to enable all the new users to things like the modem or Xine, which work OK under the new administrator account?  Do I simply copy all of the relevant files in the administrator account into each other users account?  Or can I link them somehow?  Some files are already duplicated - e.g. ".nautilus" and ".openoffice", but I don't know how that happened.  

Finally, how can I check which users now have sudo privileges?

Thanks again for your help.  It's helping to make a big difference to our home set-up, which the users will appreciate, and to reduce the mystery of Linux.

---

### Post by aysiu on 2006-04-24
Privileges depend on what groups you belong to.

Go to a terminal and type ```
groups
``` to see what groups your user belongs to. Then go to Users and Groups and add the other users to those groups (except admin, unless you want them to have *sudo* privileges).

---

### Post by Weta on 2006-04-25
Hello again.   Thanks for your last piece of advice, which I have now followed.  The other users were still not able to use the modem (internal software type).  I was able to give them access though by adding them to the "admin" group - but I'd rather they did not have access to administration tools like Synaptic or to *sudo*.  Is there a way that I can give the other users access to System > Networking only?  Thank you.

---

