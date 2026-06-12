---
title: "Add/Remove programs problem"
date: 2009-02-05
forum: General Help
---

### Post by leepal on 2009-02-05
Hi, I'm a newbie to Ubuntu so sorry if this has been covered before.  I have Ubuntu 8.04 Hardy Heron.  When I try to run - **Applications -> Add/Remove** - I get the following error message;

[I][B]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/B][/I]


then when I try to run - **System -> Administration -> Synaptic Package Manager** - I get the following message;

[I][B]E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)[/B][/I]


Any ideas what the problem is and how I can fix it?

thanks

---

### Post by maciu on 2009-02-05
first try what synaptic wants you to do - fix broken packages, open Applications > Accessories > Terminal  and type 

```
sudo apt-get update
sudo apt-get install -f
```

then check for duplicate sources in sourcess.list

```
sudo gedit /etc/apt/sources.list
```

and they try running synaptic again :)

---

### Post by leepal on 2009-02-05
many thanks.  I got rid of the duplicates in sources.list and it's working now.

:)

---

