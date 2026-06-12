---
title: "Can't Change Password from GUI"
date: 2010-04-01
forum: Desktop Environments
---

### Post by chrisolof on 2010-04-01
Hello,

I think this is a bug but I wanted some feedback from the community before going to launchpad with this.

I had a new user call me up with a question on how he might change his password on his Ubuntu 9.10 system.  I walked him through the steps of going to System->Administration->Users and Groups->Click on his user account->Properties->Change Password.  Everything went well, but when he logged out and went to use his new password it clearly didn't reset the password.  He had to use his old password to get into the system.

I verified it on my system as well - changing my password through the GUI does not actually change my password.  The only way I was able to change it was through the passwd command, which is what I walked the user through.

So the question is:  Is the GUI method (gnome/ubuntu) for changing one's password broken?  Or did we miss something?


As a follow-up to this - it appears that changing a user's password through the command line with passwd does not change the password for gnome-keyring, which then asks the user for his/her password before NM can connect to wireless networks.  The only password that this dialogue box will take is the user's old password - which could be really confusing to an end user.

Is there a better, more comprehensive way of changing one's password in Ubuntu that would update the keyring settings at the same time?

---

### Post by Curbuntu on 2010-07-15
I had the same experience today in Ubuntu 9.10 and you're right -- this only works with a combination of the CLI "passwd" command coupled with changing the password change in the User and Groups dialog box.

It was a little frustrating, but not difficult.  And the more I thought about it, the more it seemed like a *good* thing that the user has to think about what s/he is doing, and do it carefully and methodically.  Still, it would be nice to have a help page (or a portion thereof) devoted to a) how to do this successfully; and, b) what pitfalls to avoid (the chief one being -- don't forget the new password!).

---

### Post by chrisolof on 2010-07-15
Hmmm... I wasn't able to get anywhere in the GUI.  Changing my password in the GUI (System->Administration->Users and Groups->Click on desired user account->Properties->Change Password) didn't actually change my password anywhere in the system.  This strikes me as a bug.

What I've found is that changing the Ubuntu system password through CLI was a start, but not enough for a desktop user.  It was also important that I update my seahorse password to match the new system password - otherwise I'd get prompted by seahorse for my old password in order to connect to my wireless network.

For those running 9.10 who wish to change their system password (this logs you into Ubuntu) and seahorse password (so seahorse doesn't prompt for the old password before connecting to saved networks), this is what I did:

[LIST=1]
[*]Open the Terminal (Applications->Accessories->Terminal)
[*]Type the command "passwd" in and press enter.  Follow the prompts to change your system password.
[*]Navigate to Applications->Accessories->Passwords and Encryption Keys
[*]Right click on "Passwords:login" and click "Change Password."
[*]Fill the form with your old and new passwords (your new password needs to match the new system password you just specified in the terminal) and click "Change."
[/LIST]

Hopefully that helps someone on 9.10.  I'm hoping this is fixed in 10.04 - but I haven't tested it yet.

---

### Post by karnamonkster on 2011-05-31
Hi,

I am trying to change my password thru my Ubuntu box running 10.04 LTS 64 Bit.
when i click on the change password thru GUI it does give me the following options
1. Current password -- > Authenticate
2. New Password 
3. Retype New Password
 Now even if i do not enter the correct current  password  and click on Authenticate tab, it accepts the same and goes on to New password and Retype New password fields. 
Though we cannot change the password(obviously, cause it does not fetch the right password)

Hence can we fix the script running behind Authenticate tab which fetches correct information and hence throws a " Incorrect password " for wrong current password.
and changes the LDAP password for correct input.

please suggest...

---

