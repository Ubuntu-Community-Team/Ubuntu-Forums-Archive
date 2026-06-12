---
title: "DHCP/Dynamic DNS not updating"
date: 2006-09-29
forum: Desktop Environments
---

### Post by qntgeek on 2006-09-29
I'm running dapper and I can get a DHCP lease with no problem.

I figured out the resolv.conf destruction problem and now have it so both my search domains are created with each new lease.

The problem I'm running into now is my hostname never gets put into DNS. All of the Windows boxen get their host-name updated with each lease but Ubuntu doesn't seem to manage it. This is my company network with DNS running on windows.

I've used the send host-name and the send fqdn.fqdn lines in dhclient.conf to no avail. I tried encoding on and off and server update on and off. Even the DHCP client identifier. Nothing in there seems to update the DNS.

The only thing I've read and haven't tried is installing winbind. After reading about it, I don't think it fits the bill of helping me to get my DNS entry updated. It seemed to help people with trouble resolving names without DNS.

I've done a bunch of googling and read the man pages for dhclient.conf and all related files. I'm not sure what else to read so I'm hoping someone else has run into this and was more successful than I was.

 ](*,) Thanks a bunch! ](*,)

---

### Post by dcstar on 2006-09-30
> **qntgeek said:**
> 
.......
The problem I'm running into now is my hostname never gets put into DNS. All of the Windows boxen get their host-name updated with each lease but Ubuntu doesn't seem to manage it. This is my company network with DNS running on windows.

I've used the send host-name and the send fqdn.fqdn lines in dhclient.conf to no avail. I tried encoding on and off and server update on and off. Even the DHCP client identifier. Nothing in there seems to update the DNS.
......

Windows clients communicate differently to the DHCP server than Linux ones AFAIK.

I think that there are option in the MS DNS and/or DHCP server applications to accept things from non-MS devices (I believe, I seem to recall seeing such things recently), so you may want to ask your company IT people to look into the issue.

---

### Post by qntgeek on 2006-10-02
> **dcstar said:**
> Windows clients communicate differently to the DHCP server than Linux ones AFAIK.

I think that there are option in the MS DNS and/or DHCP server applications to accept things from non-MS devices (I believe, I seem to recall seeing such things recently), so you may want to ask your company IT people to look into the issue.

That would seem to be the issue. I talked to the DNS admin and he is going to look into it. Me and my silly interoperability viewpoint, assuming things would conform to a standard. Geesh.

Thanks for the pointer.

---

### Post by changlinn on 2006-10-12
uncommenting and editing the line
*send host-name "computersname";*
in the /etc/dhcp3/dhclient.conf file fixed it for me.

---

