---
title: "Previously Working Connectivity to Shares on Win7 Hosts Suddenly Stopped"
date: 2015-03-14
forum: Desktop Environments
---

### Post by neoforest on 2015-03-14
Can't open file-shares or print to printer-share hosted on two different Windows 7 domain computers.
Issue started 13 or 14 Mar 2015

=================================================================================
To summarize/pose a specific question...
Has anyone else experienced a sudden breakdown of the authentication for connecting to Win7 shares based on using samba username/pwd credentials that match a local username/pwd on the remote win7 host?

Another question might be:
Can anyone recommend a new/better way to authenticate and connect to win7 shares on Domain computers?
=================================================================================

The configs were working yesterday.
One Win7 host has the file share. A separate Win7 host has the print share.

Both Win7 hosts are in a Domain.
BUT... the share permissions are configured using a LOCAL USER on the Win7 hosts.

When i mount the smb share -> i would use the Local Username/Pwd combination [that matches existing local user account on the win7 host] and default 'WORKGROUP' in the workgroup box.
This has been a simple trick i've been using on all the Debian based distros [plus CentOS] for many years.
[That is... authenticate across the network using a username/pwd  combination that matches a LOCAL username/pwd on the remote computer] 

Both Win7 hosts have Norton Internet Security 2012.
Testing was done with both the Antivirus and Firewall components disabled.

Connectivity has suddenly stopped from:
Ubuntu 14.04, Debian 7, LMDE, Mint17, CentOS 6.6 and my Android phone.
Even when i test from a Win7 computer... I can no longer connect to the remote Win7 shares using the 'matching local username/pwd authentication trick'.

Been Googleing all day... no help yet :(

As i type this... It does sound like something changed on the windows 7 hosts from an automatic update or something.

=================================================================================

To summarize/pose a specific question...
Has anyone else experienced a sudden breakdown of the authentication for connecting to Win7 shares based on using samba username/pwd credentials that match a local username/pwd on the remote win7 host?

Another question might be:
Can anyone recommend a new/better way to authenticate and connect to win7 shares on Domain computers?

=================================================================================

Any ideas are appreciated.

Thanks for your time and thoughts.

neoforest - Homestead FL

---

