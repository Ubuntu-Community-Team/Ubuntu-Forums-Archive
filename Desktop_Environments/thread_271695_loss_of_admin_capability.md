---
title: "loss of admin capability"
date: 2006-10-05
forum: Desktop Environments
---

### Post by mihaisofti on 2006-10-05
Having successfully installed Dapper, I now find that administrative control is no longer possible.  When I login I notice first that sound no longer works, then when I attempt to enter System>Administration, most of the menu items are no longer there.  The only items I see are Device manager, network tools, printing, system log, and system monitor.  All the usual admin tools are missing.  In a console window I cannot use sudo, the system just ignores my command line if I use sudo.  I am therefore unable to edit smb.conf, or make any other admin changes.  It is behaving exactly as though the setting for user privileges has removed the tick from "Executing system administration tasks"
As I cannot alter any settings as user, I am effectively locked out .

Can anyone point me in the right direction, please?

Mihai

---

### Post by henriquemaia on 2006-10-05
Reboot in recovery mode. If you manage to login, then edit your sudoers file with the command **visudo**. Add your user to the list os sudoers.

Check here how to add an user with visudo:

[http://www.ubuntuforums.org/showpost.php?p=42141&postcount=2](http://www.ubuntuforums.org/showpost.php?p=42141&postcount=2)

---

### Post by cotcot on 2006-10-05
And make sure you have the "admin" group and your user added to this group.

---

### Post by mihaisofti on 2006-10-05
since sudo doesn't  work, I can't edit the sudoers file (access denied).  I must read Catch22 again....

Thanks, though, for the suggestion.

Mihai

---

### Post by mihaisofti on 2006-10-05
Sorry, not paying full attention.  Will reboot in recovery mode and try from there.  Thanks again.  Will report back in a few minutes, I hope.

Mihai

---

### Post by mihaisofti on 2006-10-06
I managed to boot into recovery mode using the CD up to the point of getting a # prompt, but the machine froze at the start of the edit process.  I tried again, with the same outcome, so have now reinstalled from scratch.  
The problem seems to relate to use of the Users and Groups applet.  When I use [SIZE="1"]usermod [/SIZE]from the command line, although the changes are immediately effective from the xp client end, they are not always reflected in the User and Groups applet.  Modifying users on the command, then using the applet appears to confuse the whole system, resulting in the loss of admin privileges.

Anyone else had this problem?

Mihai

---

### Post by ggeldenhuys on 2006-10-06
Hi,

I had the exact problem a week ago.  I installed Firebird RDMS and added my use to the *firebird* group.  In the process it removed me from the admin list and ended up in the same boat as you did.

You don't need to boot from the CD.  Whe you computer boots up, their should be two options for each kernel version in the GRUB boot menu. The second option is a "failsafe" mode, that boots directly to the command prompt with root access.  Once I was there, I edited the /etc/group file and added my login username to the admin group.  I reboot the computer, and I had my full access again. The sudo command also works now. :-)

Hope this helps.

Regards,
  - Graeme -



> **mihaisofti said:**
> I managed to boot into recovery mode using the CD up to the point of getting a # prompt, but the machine froze at the start of the edit process.  I tried again, with the same outcome, so have now reinstalled from scratch.  
The problem seems to relate to use of the Users and Groups applet.  When I use [SIZE="1"]usermod [/SIZE]from the command line, although the changes are immediately effective from the xp client end, they are not always reflected in the User and Groups applet.  Modifying users on the command, then using the applet appears to confuse the whole system, resulting in the loss of admin privileges.

Anyone else had this problem?

Mihai

---

### Post by mihaisofti on 2006-10-06
The penny has finally dropped!  

When using usermod on the command line, I used the -G option.  When using this option to become a member of a supplementary group, all other group memberships besides the primary one are lost.  To overcome this, use the -a option to append the additional supplementary group:

$ sudo usermod -g primary_group -G supplementary_group -a user_name

This information is actually in the man usermod file.  I must pay more attention!

Thanks to you all for your replies

Mihai

apropos of nothing
The one who steals from Peter to pay Paul can always depend upon Paul's support

---

### Post by aysiu on 2006-10-06
For future reference, this tutorial details getting into recovery mode and adding yourself back to *admin*:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

