---
title: "Manage UBUNTU workstations through SMS 2003"
date: 2009-04-13
forum: Desktop Environments
---

### Post by malekana on 2009-04-13
Hi All!

we have got a bunch of UBUNTU workstations in our environment and we wish to manage all of them using the existing SMS 2003 servers. 

If you know the solution please kindly reply or you can also write to me at [email]anil.malekani@gmail.com[/email]

Thanks in advance.

Anil Malekani

---

### Post by antikristian on 2009-04-13
Well, good luck with that. I've got no experience with SMS 2003, But I guess you are talking about group policys as a way of managing them? Or is it Patch management?

I would look into Zenworks for linux (most likely only for suse and might need an edirectory directory server, anyhow, it's patch management I think) Or maybe even [http://reductivelabs.com/trac/puppet/wiki/AboutPuppet]("http://reductivelabs.com/trac/puppet/wiki/AboutPuppet") Allthough Puppet would need a Linux Server

If It's Active directory integration, that wouldn't be a problem, for user management that is, but it wouldn't give you any way to control the workstations.

As far as I've seen, Puppet is the way to go for group policyish managagement on Linux

---

### Post by malekana on 2009-04-14
Thanks for the reply ;)

we are currently using Microsoft SMS 2003 to manage Software deployments, patch and inventory management on Windows workstations. now we have a few UBUNTU box added to our LAN and we would like to manage them with SMS 2003 using some kind of Plug in/ Third party  product. 

i came to know about QMX for SMS/ SCCM but i'm not sure if that supports UBUNTU for sure, since they haven't listed UBUNTU in the list of supported products on their web page. 

Anil Malekani

---

