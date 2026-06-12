---
title: "Authenticate Login via Active Directory"
date: 2010-01-29
forum: Desktop Environments
---

### Post by gnunoob on 2010-01-29
I am running a small Linux lab at the school where I work. I am getting ready to setup a new 32 station lab running Ubuntu 9.10 on mostly Aspire One netbooks. I am being pressured to have the students use their normal Active Directory user account information to logon to the machine. Now the million dollar question....

Is is possible to have the initial login screen authenticate the credentials through active directory? I realize I could export the accounts and import them but that is going to get out of hand and will be a pain to maintain.

 I've read a little about Kerberos and setting up a realm but I can't really find anything doesn't get to a point where the tutorial only works with their specific setup. I'm also unsure if that is anything that I should be looking into as I may not really know the right questions to ask.

I'm not concerned about trying to include any groups or group policy or profiles or anything from Active Directory other than the user name and password. Is this something that is possible or am I going in the wrong direction?

Any advice or links to good documentation or tutorials would be greatly appreciated. I don't mind doing the work and reading the material I just don't know what I should be looking for.

---

### Post by cporter23 on 2010-01-29
You might want to give likewise-open a look.  It should be in the preconfigured repos.  I messed around with it a little bit when I was creating a testbed of virtual machines.  I was able to make the ubuntu VMs authenticate users using the corporate domain controller without too much trouble.

---

