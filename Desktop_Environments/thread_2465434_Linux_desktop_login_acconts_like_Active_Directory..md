---
title: "Linux desktop login acconts like Active Directory."
date: 2021-08-01
forum: Desktop Environments
---

### Post by greene-dog on 2021-08-01
We are looking to build an internal network that is Ubuntu base for the servers, desktops and authentication to all computers.

We'd like to have several desktops available for standard users to use standard office apps and web browsers.
We'd like to have each user have their own account that can log onto any desktop with their own account. Not one account for all users
We'd like the accounts to be on the intranet and not local accounts on each desktop

We'd also like to be able to have a storage that can be used by all users and have a per-user permission.

Is there a design that will allow use to build this intranet?

I don't know all about Active Directory, so, is there an Ubuntu design that will be like Active Directory in a business's intranet?

---

### Post by grahammechanical on 2021-08-01
When we install Ubuntu we are required to give a user name and password. That user will need to put in his/her password when logging in and will work as a standard user. But when the user needs to do administrative tasks he/she will be asked to put in the password.

This is the same for the desktop and the server version. With the desktop we get utilities with a graphical user interface. With the server there is no desktop so work is done through entering commands. To do administrator tasks through commands we prefix the command with the word "sudo" and the OS prompts the user for a password.

This method prevents unauthorised people who gain access to a machine that is running an OS from making serious changes to the OS.

It is certainly possible to administer machines over a network. I do not have any experience of this. But others do have that experience. And there are tutorials and guides to explain how it is done and what software you need to run a network.

Likewise, I do think it is possible to install Ubuntu remotely on machines connected to the network. I have no experience of this.

If you are representing a commercial organisation you will need employees who are trained to set up and administer all of this. Or, you could hire the sponsor and developer of Ubuntu, Canonical, to do the job for you.

[https://ubuntu.com/#enterprise](https://ubuntu.com/#enterprise)

[https://ubuntu.com/server/docs/install/netboot-arm64](https://ubuntu.com/server/docs/install/netboot-arm64)

Regards

---

### Post by greene-dog on 2021-08-01
We understand about installing single Linux computers/server in gui or command and what the standard users can do and not do as well as the admin/root when on a local terminal or ssh in and sudo to root.

The request is to have an "active Directory" mimic in the Linux world so that when a user has an a network account he can log into all the desktops with the same account...not have a local account on each desktop.

As far as "you will need employees who are trained to set up and administer all of this"... I've been using Linux for 20 years... and the computers were all single devices.

---

### Post by him610 on 2021-08-01
> I don't know all about Active Directory

You might wan to look here, [https://ubuntu.com/server/docs/samba-active-directory]("https://ubuntu.com/server/docs/samba-active-directory")

---

### Post by ActionParsnip on 2021-08-02
You can add Linux systems to Windows AD. You can also run a Linux based LDAP server to manage logins

---

### Post by scorp123 on 2021-08-03
> **greene-dog said:**
>  I've been using Linux for 20 years... and the computers were all single devices.

If you have no understanding of central authentication mechanisms such as LDAP then this will not help you. You have to understand exactly what you are doing or every user on your network ends up being "Administrator" too, and then instead of having 1 x Administrator and 99 x users, you end up having 100 x Administrators with very conflicting ideas...

That's a nightmare waiting to happen and will not be fun for you at all.

The other suggestion was very good: Hire people who know what they are doing, e.g. experience with LDAP, Active Directory, client-server networks, centralised authentication. Since you will be dealing with many Linux devices at once I'd also throw in Ansible and/or Puppet. You cannot do any manual administration with so many Linux clients, you need something like Ansible to manage device configuration centrally.

---

### Post by scorp123 on 2021-08-03
In my own network I got around needing LDAP or Active Directory by doing everything in Ansible. E.g. users, their priviledges, their group memberships (e.g. if they can run "sudo" or not, if they can start/stop certain services or not, etc.), their passwords and which systems their accounts should be rolled out to or not get all defined in Ansible. And then I roll them out this way. Result is that I get kind of a hybrid setup. One one hand all the user accounts are in fact centrally managed by Ansible. On the other hand to each and every system all the user accounts appear to be local.

The advantage here is that I don't need to mess around with 3rd party authentication mechanisms such as Kerberos, Active Directory, LDAP or whatever. I basically just write an Ansible playbook that could run on 1 x system or on 100 x systems ... it doesn't matter. I get all the user accounts rolled out where I want, when I want.

Ansible is easy to learn and to pick up. Also it scales very well, it doesn't matter if you have 5 x systems in your network or 500 x systems. I'd recommend you take a look and start there.

---

### Post by TheFu on 2021-08-03
LDAP (or FreeIPA) and NFS are what you seek.

The first 2 are authentication directories.  NFS is for network storage so when a user logs in, they have their own HOME directory on any machine.  Check out autofs for the NFS deployment.

There are other solutions.  help.ubuntu.com ---> Server ---> look down the left hand column for topics and how to deploy those things.

In the 1990s, we used NIS for centralized user, group, netgroups, hosts, other "DB map file" management.  It integrates with all Linux system tools.  So does LDAP.  NIS is highly non-secure, so nobody should be using it today.  The next version, NIS+, is withheld and the servers only run on Solaris, but there are clients for all Unix systems.

Anyway, this question has been asked here a few times over the years.  Usually once per year or so.  Check out those answers.  Canonical has make integration with AD easy in 21.04, but prior to that, we had to manually setup everything.  The setup process on the server side is about 20 steps.  On each client system, it is about 5 steps.

---

