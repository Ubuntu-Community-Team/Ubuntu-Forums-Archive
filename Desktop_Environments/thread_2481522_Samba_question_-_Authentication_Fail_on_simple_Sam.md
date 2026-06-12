---
title: "Samba question - Authentication Fail on simple Samba setup"
date: 2022-12-01
forum: Desktop Environments
---

### Post by mike430 on 2022-12-01
[COLOR=#000000]Very simple Samba setup. My issue is with myself being owner/root of the remote machine and unable to connect. Whereas 3 other users are able to connect without issue.[/COLOR]

[COLOR=#000000]Username/passwords of remote Linux machine are the same as the Samba username/passwords.[/COLOR]

[COLOR=#000000]When I setup as a guest access only/ no password everything works fine. When I apply some level of security is where my login fails.[/COLOR]

[COLOR=#000000]Simply trying to access an mp3 on the remote machine. When I access the remote machine for the first time when start the client machine prompts for 'Authentication Dialog' when accessing the host through Samba. I enter my Ubuntu/Samba username/password and it works... I can play the mp3. After closing the mp3 file and the samba share, when I attempt to go back to the same share then prompts for "SMB Authentication" when trying to access the mp3 file - this is when my authentication fails. Would have to restart my machine to have access to the mp3 only on the first time.[/COLOR]

[COLOR=#000000]Below is my smb.conf and smb.log from the fail. Thanks for any help. mike430

```
[/COLOR][global]workgroup = workgroup
server min protocol = NT1
security = auto
server role = standalone
username map = /etc/samba/smb.user.map
log file = /var/log/samba/smb.log
max log size = 5000
log level = 2


[mp3]
path = /home/myUserName/mp3
browseable = yes
write list = myUserName

force user = myUserName[COLOR=#000000]
```

```
[/COLOR][2022/12/01 10:54:58.173932,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:54:58.175475,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.175855,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:54:58.176030,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:54:58.176195,  2] ../../source3/smbd/reply.c:707(reply_special)
  netbios connect: name1=myHostName.LOCAL    0x20 name2=               0x0
[2022/12/01 10:54:58.176245,  2] ../../source3/smbd/reply.c:747(reply_special)
  netbios connect: local=myHostName.local remote=, name type = 0
[2022/12/01 10:54:58.177476,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.178020,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:54:58.178186,  2] ../../source3/smbd/reply.c:707(reply_special)
  netbios connect: name1=myHostName.LOCAL    0x20 name2=               0x0
[2022/12/01 10:54:58.178235,  2] ../../source3/smbd/reply.c:747(reply_special)
  netbios connect: local=myHostName.local remote=, name type = 0
[2022/12/01 10:54:58.189100,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.190789,  2] ../../source3/auth/auth.c:323(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [myUserName] -> [myUserName] -> [myUserName] succeeded
[2022/12/01 10:54:58.191014,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.192263,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.192334,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.194072,  2] ../../source3/auth/auth.c:323(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [myUserName] -> [myUserName] -> [myUserName] succeeded
[2022/12/01 10:54:58.194214,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.195061,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.198158,  1] ../../source3/auth/token_util.c:1171(create_token_from_username)
  lookup_name_smbconf for  failed
[2022/12/01 10:54:58.234447,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:54:58.235891,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.236434,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:54:58.248865,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.250386,  2] ../../source3/auth/auth.c:323(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [myUserName] -> [myUserName] -> [myUserName] succeeded
[2022/12/01 10:54:58.250525,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.251387,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.264565,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.266391,  2] ../../source3/smbd/service.c:852(make_connection_snum)
  my-PC-Name (ipv4:192.168.X.X:XXXXX) connect to service mp3 initially as user myUserName (uid=1000, gid=1000) (pid 16489)
[2022/12/01 10:54:58.800907,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:54:58.802328,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.802864,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:54:58.816655,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.818909,  2] ../../source3/auth/auth.c:323(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [myUserName] -> [myUserName] -> [myUserName] succeeded
[2022/12/01 10:54:58.819132,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:58.820318,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.834110,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:58.835797,  2] ../../source3/smbd/service.c:852(make_connection_snum)
  my-PC-Name (ipv4:192.168.X.X:XXXXX) connect to service mp3 initially as user myUserName (uid=1000, gid=1000) (pid 16490)
[2022/12/01 10:54:59.822376,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:54:59.823753,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:59.824286,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:54:59.839320,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:59.841053,  2] ../../source3/auth/auth.c:323(auth_check_ntlm_password)
  check_ntlm_password:  authentication for user [myUserName] -> [myUserName] -> [myUserName] succeeded
[2022/12/01 10:54:59.841223,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:54:59.842131,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:59.853775,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:54:59.855485,  2] ../../source3/smbd/service.c:852(make_connection_snum)
  my-PC-Name (ipv4:192.168.X.X:XXXXX) connect to service mp3 initially as user myUserName (uid=1000, gid=1000) (pid 16491)
[2022/12/01 10:54:59.865371,  2] ../../source3/smbd/open.c:1524(open_file)
  myUserName opened file myMusicFile.mp3 read=No write=No (numopen=1)
[2022/12/01 10:54:59.907143,  2] ../../source3/smbd/close.c:824(close_normal_file)
  myUserName closed file myMusicFile.mp3 (numopen=0) NT_STATUS_OK
[2022/12/01 10:55:01.426010,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:55:01.427401,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:01.427944,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:55:01.448149,  1] ../../source3/auth/token_util.c:1171(create_token_from_username)
  lookup_name_smbconf for  failed
[2022/12/01 10:55:01.453876,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:01.463786,  1] ../../source3/smbd/service.c:353(create_connection_session_info)
  create_connection_session_info: guest user (from session setup) not permitted to access this share (mp3)
[2022/12/01 10:55:01.463825,  1] ../../source3/smbd/service.c:543(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2022/12/01 10:55:19.916114,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:55:19.917614,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:19.918170,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:55:19.931599,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:55:19.932478,  2] ../../source3/auth/auth.c:344(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [myUserName] -> [myUserName] FAILED with error NT_STATUS_WRONG_PASSWORD, authoritative=1
[2022/12/01 10:55:19.932513,  2] ../../auth/auth_log.c:635(log_authentication_event_human_readable)
  Auth: [SMB2,(null)] user [WORKGROUP]\[myUserName] at [Thu, 01 Dec 2022 10:55:19.932501 EST] with [NTLMv2] status [NT_STATUS_WRONG_PASSWORD] workstation [MY-PC-NAME] remote host [ipv4:192.168.X.X:XXXXX] mapped to [WORKGROUP]\[myUserName]. local host [ipv4:192.168.X.X:XXX] 
  {"timestamp": "2022-12-01T10:55:19.932570-0500", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 2}, "eventId": 4625, "logonId": "0", "logonType": 3, "status": "NT_STATUS_WRONG_PASSWORD", "localAddress": "ipv4:192.168.X.X:XXX", "remoteAddress": "ipv4:192.168.X.X:XXXXX", "serviceDescription": "SMB2", "authDescription": null, "clientDomain": "WORKGROUP", "clientAccount": "myUserName", "workstation": "MY-PC-NAME", "becameAccount": null, "becameDomain": null, "becameSid": null, "mappedAccount": "myUserName", "mappedDomain": "WORKGROUP", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": null, "passwordType": "NTLMv2", "duration": 5062}}
[2022/12/01 10:55:19.938246,  1] ../../source3/auth/token_util.c:1171(create_token_from_username)
  lookup_name_smbconf for  failed
[2022/12/01 10:55:19.942701,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:19.951429,  1] ../../source3/smbd/service.c:353(create_connection_session_info)
  create_connection_session_info: guest user (from session setup) not permitted to access this share (mp3)
[2022/12/01 10:55:19.951460,  1] ../../source3/smbd/service.c:543(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED
[2022/12/01 10:55:23.671421,  2] ../../source3/smbd/service.c:1123(close_cnum)
  my-PC-Name (ipv4:192.168.X.X:XXXXX) closed connection to service mp3
[2022/12/01 10:55:25.277926,  2] ../../source3/lib/tallocmsg.c:84(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2022/12/01 10:55:25.279351,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:25.279900,  2] ../../source3/lib/interface.c:343(add_interface)
  added interface enp3s0 ip=192.168.X.X bcast=192.168.1.255 netmask=255.255.255.0
[2022/12/01 10:55:25.292451,  1] ../../source3/param/loadparm.c:2519(lp_idmap_range)
  idmap range not specified for domain '*'
[2022/12/01 10:55:25.293367,  2] ../../source3/auth/auth.c:344(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [myUserName] -> [myUserName] FAILED with error NT_STATUS_WRONG_PASSWORD, authoritative=1
[2022/12/01 10:55:25.293403,  2] ../../auth/auth_log.c:635(log_authentication_event_human_readable)
  Auth: [SMB2,(null)] user [WORKGROUP]\[myUserName] at [Thu, 01 Dec 2022 10:55:25.293391 EST] with [NTLMv2] status [NT_STATUS_WRONG_PASSWORD] workstation [MY-PC-NAME] remote host [ipv4:192.168.X.X:XXXXX] mapped to [WORKGROUP]\[myUserName]. local host [ipv4:192.168.X.X:XXX] 
  {"timestamp": "2022-12-01T10:55:25.293458-0500", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 2}, "eventId": 4625, "logonId": "0", "logonType": 3, "status": "NT_STATUS_WRONG_PASSWORD", "localAddress": "ipv4:192.168.X.X:XXX", "remoteAddress": "ipv4:192.168.X.X:XXXXX", "serviceDescription": "SMB2", "authDescription": null, "clientDomain": "WORKGROUP", "clientAccount": "myUserName", "workstation": "MY-PC-NAME", "becameAccount": null, "becameDomain": null, "becameSid": null, "mappedAccount": "myUserName", "mappedDomain": "WORKGROUP", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": null, "passwordType": "NTLMv2", "duration": 4542}}
[2022/12/01 10:55:25.299435,  1] ../../source3/auth/token_util.c:1171(create_token_from_username)
  lookup_name_smbconf for  failed
[2022/12/01 10:55:25.303909,  2] ../../source3/param/loadparm.c:2864(lp_do_section)
  Processing section "[mp3]"
[2022/12/01 10:55:25.313673,  1] ../../source3/smbd/service.c:353(create_connection_session_info)
  create_connection_session_info: guest user (from session setup) not permitted to access this share (mp3)
[2022/12/01 10:55:25.313732,  1] ../../source3/smbd/service.c:543(make_connection_snum)
  create_connection_session_info failed: NT_STATUS_ACCESS_DENIED


[COLOR=#000000]
```
[/COLOR]

---

### Post by TheFu on 2022-12-02
If you don't have MS-Windows clients, don't use samba/cifs.  Use NFS or sftp or sshfs instead.  On Android, there are better answers for accessing streaming music. Just sayin'.  If you want to play music on the remote computer through those nicer speakers, use mpd and any of the mpd clients. I like M.A.L.P.  If you want to playback directly on the device, a media center server using DLNA or a proprietary method works great - something like jellyfin or miniDLNA or lots of others. Heck, I even provide read-only access using nextcloud to our music.

Back to samba ... 
Different MS-Windows clients support different levels of the CIFS standard.  Since Win7 supports v2.1, you don't want any lower protocol supported. It is a performance AND security thing.  I think Win10+ use v3.0 and higher.

Config files are picky.  There are a few syntax issues in the one you've posted. Fix those.  It would probably be easier to purge the current samba install, remove /etc/samba/ and do a reinstall to get a solid basic setup.  Then add the last [mp3] stanza and don't touch anything else. Something like this:

```

[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```

BTW, providing direct shares to directories under the HOME is a bad, bad, bad idea.  Use the "homes" stanza like above to let each user access their own HOME directory. There are undesirable side-effects providing remote samba below a HOME directory. Trust us. Don't do it. You've been warned.

If you want to share music with other accounts, move the music outside your HOME and share that directory.  I use /M/ myself. and sometimes /R/Music/.  I try to be consistent.

Don't forget that you need to add samba user accounts using the 'smbpasswd' command before this will work.
Also, Win10 and later don't use nmb anymore to locate network shares. MSFT has inflicted mDNS onto us, so you'll want to check your /etc/nsswitch.conf to ensure that's available.

While we can always use the cifs server IP address in our \\{server-ip}\ connections, with mDNS on Linux, the normal broadcast will be {hostname}.local, so I'd use \\hadar.local\ as the URL from a Windows machine if I used mDNS on my network.  Of course, if you have a real DNS server and it is configured, you can use \\hadar\ directly.  mDNS is installed and running on Ubuntu desktop flavors, but not on Ubuntu Server.  Avahi is the typical mDNS server (and probably client) used on Linux.

Lastly, any changes to /etc/samba/smb.conf requires restarting the smbd service.  I've read that sometimes this isn't sufficient and a full reboot is needed.  I haven't seen that myself, but I trust the source.

---

### Post by mike430 on 2022-12-02
I have dual operating system on mine and also my boys laptops for the purpose of them learning linux but also using windows for more mainstream computing. ie. gaming. 

All machines, mine included, run win 11 as the alternate to Ubuntu. 

Also before I forget, the DLNA stuff you mentioned, yes, I see your point for efficiency and ease. I do run a DLNA service on all my music and video media. It is served through these same samba shared directories. Up to this point it has worked spectacularly. Add/subtract files as needed then update the dlna service.

I have read through much of samba.org settings/configurations and although many of the settings available do not apply to my simple setup, I think I have an ok grasp on what might be needed.

I keep going back to the fact that really everything works other than myself as user/password on my client linux and the same on the linux server and failing after the first successful attempt.

Why in the logs does it have me logging on as guest? Why does the logs indicate no write or no read? Although redacted, why does the remote machine (my client machine) change the port number on 3 -4 different occassions?

Is Sherlock Holmes in the house????? Thanks for your help Fu.. .This is vcandy50 by the way. I knew we would cross paths again!

Me thinks, that your suggestion to purge and reinstall might do the trick. The server has run this way for many years. With updates, upgrades, and even an instance of me mistakenly running 'sudo su' at some point then running 'rm -R /*' ... the machine has been through a lot. Yes, I was half asleep on that one...

---

### Post by TheFu on 2022-12-02
I'm not a fan of the "force user=" option.  Seems lazy to me, but perhaps I'm too much of a purist?
I've never used the "auto" for the security model either and Since Win7, I've set the server min protocol to SMB2.  Win7 supports v2.1.

I do block all hosts on the LAN except those specifically that need Samba access too.  Wouldn't want a guest to have access, should the guest LAN segment accidentally have a firewall failure (or misconfiguration).  But people say that I'm overly paranoid.

BTW, the best way to see what settings samba is actually seeing is to run 'testparm' and post that output.  Some experts here can read that and see exactly what the issue is, if all client OSes/versions are listed too.  No me, but other people.

---

### Post by mike430 on 2022-12-04
> **TheFu said:**
> I'm not a fan of the "force user=" option.  Seems lazy to me, but perhaps I'm too much of a purist?
Perhaps, but I certainly don't see that as a bad thing.


On another note, [COLOR=#111111][FONT=Arial]got it to work it in pretty much the fashion I want.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]Purged Samba then reinstalled - like you suggested. I think this was unnecessary due to the issue still happening after the reinstall.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]I simply changed my Samba Password to something other than my Unix password. I just never tried this before I purged Samba.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]This creates more of a puzzle than anything. Although my issue is resolved would really like to know what is causing this conflict. I'd prefer to have one less password in my life and also thought the basis of a 'Standalone server' setup was in fact using identical username/password parameters for both Samba/Unix/Windows, no? All my other users are setup like this and it works for them.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]Appreciate you chiming in again Fu, and if you have anything to add by all means. Thanks mike/vcandy50[/FONT][/COLOR]

---

### Post by Morbius1 on 2022-12-04
It would have been helpfull had you provided some basic information so the folks here could better assist you. Some of the things that TheFu asked you like:

What OS runs the samba server.

What version of that OS you are using.

Did you create any samba usershares.

What OS and what version of that OS runs on the client.

Each Linux desktop environment has it's own issues being a samba client since they all refuse to hire a Samba subject matter expert.

In your case you are using KDE ( at least based on this post: [https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-22-04-jammy-jellyfish/desktop-environment-support/666933-samba-simple-setup-authentication-fail](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-22-04-jammy-jellyfish/desktop-environment-support/666933-samba-simple-setup-authentication-fail) ) - I should not have had to google that. You should have told us.

Anyhoo, each desktop environment has it's own issues. For example, KDE has a bug report that matches your symptoms: [https://www.mail-archive.com/kde-bugs-dist@kde.org/msg601724.html](https://www.mail-archive.com/kde-bugs-dist@kde.org/msg601724.html)

BTW your share definition makes no sense to me.
> [mp3]
path = /home/myUserName/mp3
browseable = yes
write list = myUserName
force user = myUserName


Samba will interpret that share this way:

Folder Shared: /home/myUserName/mp3
Guest accessible: No
Read only: Yes
Exception to read only directive: the user named myUserName

So far so good. You created a share that allows credentials users read only access except for one user that can also write.

Then you added "force user = myUserName"

You can use "valid users" and "force user" in the same definition because they occur at different times. But you can't use "write list" and "force user" at the same time because every credentialed client user will become that user which is also on the "write list"

---

### Post by Tadaen_Sylvermane on 2022-12-04
I think I didn't see this mentioned. As you run both systems in your home there is nothing wrong with running both Samba and NFS as needed. They will happily coexist. Use the proper tool for the target OS.

---

### Post by mike430 on 2022-12-04
> **Morbius1 said:**
> It would have been helpfull had you provided some basic information so the folks here could better assist you. Some of the things that TheFu asked you like:

What OS runs the samba server.

Ubuntu 20.04.5 LTS

> **Morbius1 said:**
> What version of that OS you are using.

same - it was a Kubuntu install, but the base is the same


> **Morbius1 said:**
> Did you create any samba usershares.

Yes, 3 users + myself.

> **Morbius1 said:**
> What OS and what version of that OS runs on the client.

I run dual operating systems on my boys (children's) laptops and myself. Both are equipped with the same version as mine (above) and all of us run on the side win 11. the only difference for win 11 is I run pro, they run home. All updated and current...


> **Morbius1 said:**
> In your case you are using KDE ( at least based on this post: [https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-22-04-jammy-jellyfish/desktop-environment-support/666933-samba-simple-setup-authentication-fail](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-22-04-jammy-jellyfish/desktop-environment-support/666933-samba-simple-setup-authentication-fail) ) - I should not have had to google that. You should have told us.

Agreed, sorry.

> **Morbius1 said:**
> Anyhoo, each desktop environment has it's own issues. For example, KDE has a bug report that matches your symptoms: [https://www.mail-archive.com/kde-bugs-dist@kde.org/msg601724.html](https://www.mail-archive.com/kde-bugs-dist@kde.org/msg601724.html)

This is my exact issue. I guess it is safe to say that until the dev team works this bug you have to use an alternate password per samba from the unix remote machine (but same username) if you want access on any subsequent logins from the first. This for some reason only affects the original user that is admin of the samba machine. All other users added do not have this issue. It's probably a permissions issue. 

> **Morbius1 said:**
> BTW your share definition makes no sense to me.


Samba will interpret that share this way:

Folder Shared: /home/myUserName/mp3
Guest accessible: No
Read only: Yes
Exception to read only directive: the user named myUserName

So far so good. You created a share that allows credentials users read only access except for one user that can also write.

Then you added "force user = myUserName"

You can use "valid users" and "force user" in the same definition because they occur at different times. But you can't use "write list" and "force user" at the same time because every credentialed client user will become that user which is also on the "write list"

This part is confusing to me, not sure if you are validating or confirming this is wrong. What I'd like is the most simplest setup for testing. I can tell you that there is a conflict between a user, myself, with sudo rights per samba server (Ubuntu 20.04.5) and myself logging in with samba credentials that mimic that of the Samba server. For what reason, I don't know. Thanks for response - Mike

---

### Post by mike430 on 2022-12-04
> **Tadaen_Sylvermane said:**
> I think I didn't see this mentioned. As you run both systems in your home there is nothing wrong with running both Samba and NFS as needed. They will happily coexist. Use the proper tool for the target OS.

I like this! .. was going to ask but you read my mind. Having never run NFS, this seems like would be perfect solution, for my win samba's shares work fine and my issue is with Linux client samba shares...

---

### Post by TheFu on 2022-12-04
The question about "usershares" is different than you think.  I believe that is a question of whether you used a GUI to setup the shares or only editing the /etc/samba/smb.conf file.  The "usershares" is typically setup using a GUI and doesn't touch the smb.conf file, to my knowledge.  Usershares have some oddness and have caused some issues that you can find in these forums for other users.  On one thread we spent 2 weeks trying to solve a permissions and deletion issue that was traced back to a samba "usershare" as the root cause.  The poster had forgotten about that setup and it was blocking all other attempts to solve his problem.

NFS is system-to-system, not user-to-system.  If you want user to system, use sshfs.  The old, slow, ssh and sshfs have been fixed. It is fast these days, but not as fast as NFS.

---

