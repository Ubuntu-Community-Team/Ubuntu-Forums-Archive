---
title: "Few KDE questions (possible bugs)"
date: 2005-10-24
forum: Desktop Environments
---

### Post by escobar on 2005-10-24
1)Samba

-Seems like whenever I add a user in kcontrol, save, exit, then come back, the user I entered is gone. This also occurs when I use "kdesu kcontrol" as well. I thought I could add a samba user in terminal but it doesn't seem to work as I cannot still access any of my shares. To manually set things up I used the 'How To' laid out here:

[http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

But no dice. I'm not sure if the user was succesfully added or not because the "Users" pane in the Samba prefs is still blank. Since things aren't working for me I will assume no users were added successfully. It will retain any shares I add though.

2)KMail & Wallet.

-Not entirely sure where the issue lies here but EVERYTIME I open Kmail it asks for my username and pw before retreiving mail. This occurs even after I told Kmail it's ok to store my username and pw. Wallet also has this info stored, but I can't seem to make this stop. Even if Wallet's closed/open before I open Kmail it will still prompt me. It doesn't say Wallet is asking for access, it says Kmail is. 

This won't really kill me but just curious to see if anyone else was experiencing this.

That's about it for now. Thanks to any and all that respond.

*EDITED for clarity.

---

### Post by mlomker on 2005-10-24
> Even if Wallet's closed before I open Kmail it will still prompt me. IT doesn't say Wallet is asking for access it says Kmail is. 


Yeah, Kmail irritates me to no end.  I tried to not use kwallet (even uninstalled it) but kmail refuses to save the password if you don't use the wallet.  I just gave up and made a one-character wallet password to save my sanity.

I'm not sure about your other issue because I never have a reason to add users.  Have you tried **useradd** from the command line instead?

---

### Post by escobar on 2005-10-24
[QUOTE=mlomker]Yeah, Kmail irritates me to no end.  I tried to not use kwallet (even uninstalled it) but kmail refuses to save the password if you don't use the wallet.  I just gave up and made a one-character wallet password to save my sanity.

I'm not sure about your other issue because I never have a reason to add users.  Have you tried **useradd** from the command line instead?[/QUOTE]

Would this be proper for Samba purposes? I'm not sure if my question was clear, but it won't remember any users I add under the Samba option in Kcontrol.

---

### Post by escobar on 2005-10-25
bump

---

### Post by mlomker on 2005-10-25
[QUOTE=escobar]Would this be proper for Samba purposes? I'm not sure if my question was clear, but it won't remember any users I add under the Samba option in Kcontrol.[/QUOTE]

Are you running kcontrol using **kdesu kcontrol**?  I ask because smb.conf seems to be owned by root, so I wonder if it is a permissions problem.

---

### Post by escobar on 2005-10-25
[QUOTE=mlomker]Are you running kcontrol using **kdesu kcontrol**?  I ask because smb.conf seems to be owned by root, so I wonder if it is a permissions problem.[/QUOTE]

Yes. When I do so I can add a user, but if I hit 'apply' then leave that pane and come back...the user I just added will be gone.

---

### Post by mlomker on 2005-10-26
Yup, it looks broke.  They are transitioning away from kcontrol to systemsettings and neither of them work for much at the moment.  I just opened systemsettings and I see that they have a file sharing option that is supposed to replace the samba section of kcontrol but it's all grayed out, even as root.

You can file a bugzilla on this one if you like, but I'd imagine that they know that most of the control panels are broken.  I might need to drop by the Kubuntuforums to see what they are saying about this kind of thing.

You can use the [command-line]("http://www.samba.netfirms.com/addusers.htm") for now.

---

### Post by mervc on 2005-10-26
[QUOTE=mlomker]Yeah, Kmail irritates me to no end.  I tried to not use kwallet (even uninstalled it) but kmail refuses to save the password if you don't use the wallet.  I just gave up and made a one-character wallet password to save my sanity.

I'm not sure about your other issue because I never have a reason to add users.  Have you tried **useradd** from the command line instead?[/QUOTE]

You can save your password in KMail in the configuration.  Go to Accounts - Receiving - Modify  and supply the password in its box.  Be sure to save it.

It looks like KMail asks Kwallet for the password before it checks its config however.  if Kwallet has been opened previously, the logon to your mail is seamless. In a new session Kwallet has to be opened by some program,  Konq., Kmail etc and then all requests for passwords are hidden.  I think Kwallet is great, it now has about 50 passwords stored away and I seldom have to open my little notebook.

---

### Post by mlomker on 2005-10-26
> You can save your password in KMail in the configuration. Go to Accounts - Receiving - Modify and supply the password in its box. Be sure to save it. 

Yes, that's how it is supposed to work.  It doesn't.

Kwallet would be worthwhile to me if Firefox used it, but Konqueror doesn't really do the job for me.

---

