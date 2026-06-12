---
title: "Samba log.smbd error"
date: 2009-01-10
forum: General Help
---

### Post by tulchan on 2009-01-10
Hi,

I am setting up Samba on Ubuntu 8.10 to allow centralised WinXP login on a small home network. 

This was a fresh install - and then follow the HOWTO guides.

The shares are set up, the users are set up in Ubuntu and Samba.

There are no printers on the Ubuntu box.

When I start Samba, the following shows up in the log.smbd

[2009/01/10 20:43:05,  0] smbd/server.c:main(1213)
  smbd version 3.2.3 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
ltdb: tdb((null)): tdb_open_ex: could not open file /var/lib/samba/group_mapping.ldb: Permission denied
Unable to open tdb '/var/lib/samba/group_mapping.ldb'
Failed to connect to '/var/lib/samba/group_mapping.ldb'
[2009/01/10 20:43:05,  0] groupdb/mapping_ldb.c:init_group_mapping(108)
  Failed to open group mapping ldb '/var/lib/samba/group_mapping.ldb' - '(null)'

The group_mapping.ldb file exists nowhere on the filesystem

Despite this, I can 'smbclient \\server\share -U user' successfully on the Ubuntu box and 'dir' the contents of the share. 

If I try a WinXP login, I get told 'The username does not exist'.

If I try to map directly to the share, I can.

Can anyone help?

---

