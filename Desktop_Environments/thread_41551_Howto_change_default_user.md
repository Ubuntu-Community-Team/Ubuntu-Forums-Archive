---
title: "Howto change default user"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Jerrac on 2005-06-13
Ok, I want to get rid of the user I created when I installed Ubuntu. For reasons described in this topic: [http://ubuntuforums.org/showthread.php?t=39154](http://ubuntuforums.org/showthread.php?t=39154)

Here are the steps I take:
[list=1]
[*]Create an administrator in the Users and Groups gui.
[*]Log in as that new user, everything works fine.
[*]Then I delete my old user.
[*]Log out and in again.
[*]Now it will not let me do anything, like if I try to change any network settings it gives me an error after I enter my password. "Failed to run network-admin: Child terminated with 1 status".
[*]It also will not let me use sudo. "User is not in the sudoers file".
[/list] 
So, how can I change the default username and password? Since I am selling my computer, I want the new owner to be able to use their own username and password.

---

### Post by Joeb on 2005-06-13
It sounds like you deleted your original user without having added your new user to the sudoers list or creating a root account.  As such, you no longer have any root access.  One solution (there are probably others and even better ones), is to boot from the LiveCD and manually edit the /etc/sudoers file.  Another solution, if your new administrator id wasn't added to the admin group is to once again boot from the LiveCD and then manually edit the /etc/group file.  Scroll down to the line that begins admin and put your new userid at the end of that line.

In both options above, you will have to manually mount your Ubuntu partition to be able to do the editing.

---

### Post by Jerrac on 2005-06-13
eh, why wouldn't my new id be added to the admin group? As far as I could tell it should be... Since I set the group to administrator.

And I did try adding my user to the sudoers file with the live cd. Didn't seem to work. Can't remember exactly what I did.

Anyway, I need a easier way to do it that editing system files. Of course there may not be one...  So...

---

### Post by diebels on 2005-06-13
boot up in recovery mode(press escape while booting to get grub menu) and add the user to "admin". Users in admin is allowed to sudo.
You can see that in /etc/sudoers
First see which groups he's in:
**groups USER**
Then add him to admin(and keep membership of all the groups his currently in), something like:
**usermod -G audio,video,plugdev,games,dialout,lpadmin,admin USER**
You can use the users and groups gui tool later to check properties and user privileges.

---

### Post by Joeb on 2005-06-13
[QUOTE=Jerrac]eh, why wouldn't my new id be added to the admin group? As far as I could tell it should be... Since I set the group to administrator.

And I did try adding my user to the sudoers file with the live cd. Didn't seem to work. Can't remember exactly what I did.

Anyway, I need a easier way to do it that editing system files. Of course there may not be one...  So...[/QUOTE]

Did you add them to the group called "admin" when you set it up?  I don't have a group called "administrator".

---

### Post by Jerrac on 2005-06-14
Ah, I see. I was confusing groups with profiles...

But I still have a problem. I went into the users and groups tool as usual and did everything the same way, except that I set the users main group to admin. When I looked at the admin group properties it showed the new user under that group. So I logged in as the new user and deleted the old one. Logged in and out at it gave me the same errors as before. Apparently it didn't actually add my user to the admin group... What should I do?

Also, I am trying to edit the groups file as suggested in the first reply, how should I add my new user? I will do a search in a little bit, but I have other things to do right now. 

Thanks for the help so far!

---

### Post by Joeb on 2005-06-14
[QUOTE=Jerrac]Ah, I see. I was confusing groups with profiles...

But I still have a problem. I went into the users and groups tool as usual and did everything the same way, except that I set the users main group to admin. When I looked at the admin group properties it showed the new user under that group. So I logged in as the new user and deleted the old one. Logged in and out at it gave me the same errors as before. Apparently it didn't actually add my user to the admin group... What should I do?

Also, I am trying to edit the groups file as suggested in the first reply, how should I add my new user? I will do a search in a little bit, but I have other things to do right now. 

Thanks for the help so far![/QUOTE]

I, too, would think that adding the user to the group admin would have taken care of it.  I'm not sure why it didn't.  I do know that when you set a user up using the gui, that if you click on the properties button for that user and go to the security tab, you can set whether the user can use sudo or not.

As for editing the group file, does it still show your old id on the line that has admin?  If so, replace that id with the new id you created and see if that fixes it.

---

### Post by Jerrac on 2005-06-14
Security Tab? I don't see one. Do you mean the user priviledges tab? I don't see anything that says sudo there, would "Executing system administration tasks" be the sudo option?

---

### Post by Joeb on 2005-06-14
[QUOTE=Jerrac]Security Tab? I don't see one. Do you mean the user priviledges tab? I don't see anything that says sudo there, would "Executing system administration tasks" be the sudo option?[/QUOTE]

Yes, the priviledges tab and the Executing system administration tasks.  I wasn't at my linux computer when I typed that and tried it from memory.  I should have known better.

---

