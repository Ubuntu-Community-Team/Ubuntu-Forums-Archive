---
title: "Deploying Ubuntu Workstations in Corporate Environment"
date: 2013-02-26
forum: Desktop Environments
---

### Post by jla0 on 2013-02-26
We are starting to deploy more and more Ubuntu 10.04 workstations for our employees but need a better way to lock the machines down similar to how we can use Group Policy to lock down a windows machine. Below are a few of the immediate questions i have.

We are using Likewise enterprise for authentication with active directory and to allow us to run scripts against a machine.

1. How can i allow a user to read USB storage or CDROM drives but block them from writing to these devices unless i explicitly grant them this right.

2. How can i prevent a user from changing the root users password if i grant the user sudo permissions?

---

### Post by grahammechanical on 2013-02-26
This forum has a section called Networkg & Wireless. You may meet more experienced people there. But before you go any further, please think about this fact. 

Although Ubuntu 10.04 server is supported up to April 2015, the desktop is only supported up to April 2013. Why are you installing 10.04 workstations when you should be installing 12.04 workstations which will have a support life of 5 years from April 2012?

By the way, ever thought of putting those kind of issues in an employee's conditions of employment and making disobedience a disciplinary offence? When the high street store that I use to work in first got a computer I had to sign a company policy statement on how the machine should be used.

1) Do not give them administrator privileges. Especially managers.
2) Uninstall/remove all programs and utilities that are not necessary for normal work activities. Such as Users and Groups, Software Centre, Terminal. All that kind of stuff.
3) Use Remote Access to do all the administrator stuff.

Check this out

[http://www.ubuntu.com/business/desktop/remix]("http://www.ubuntu.com/business/desktop/remix")

> it&#8217;s just a convenient starting point that includes many common changes made by IT administrators deploying Ubuntu in a corporate setting.

> while removing social networking software, file sharing apps, games and development/sysadmin tools

> The result is a simple base image that can be deployed into your corporate environment or used as a starting point for further customisation. Users also benefit from great new features like built-in Microsoft Windows RDP 7.1 support and the Microsoft Visio diagram importer in LibreOffice Draw.

Regards.

---

### Post by jla0 on 2013-02-26
Thanks i will post in the other forum you suggested.

We are deploying Ubuntu 10.04 because the software we need only works on that version (Altiris,Symantec, PGP, etc..).

We have made disobedience a disciplinary offense but we also want to prevent any opportunities for data leakage. We dont want to rely on the honor code alone.

Our users are developers with legitamate reasons to have local admin access.

Thanks

---

