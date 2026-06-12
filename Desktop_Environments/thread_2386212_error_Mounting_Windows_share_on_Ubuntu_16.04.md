---
title: "error Mounting Windows share on Ubuntu 16.04"
date: 2018-03-02
forum: Desktop Environments
---

### Post by giobaxx on 2018-03-02
A user mounted a windows share using the following command:

***sudo mount -t cifs -o domain=mydomain.com,username=Active_Directory_Username , iocharset=utf8,uid=id_local_user //192.168.x.x/share  /mount_point***

and it worked till some days ago. Now he receive the error below.


*[74982.605836] CIFS VFS: protocol revalidation - security settings mismatch*
*[74982.608695] CIFS VFS: session ffff885158534400 has no tcon available for a dfs referral request*
*[74982.610651] CIFS VFS: cifs_mount failed w/return code = -5*




he told he did only an update, and my collegue told me to try to  add the option sec=ntlm so i did

***sudo mount -t cifs -o domain=mydomain.com,username=Active_Directory_Username , iocharset=utf8,uid=id_local_user,[COLOR=#0000ff]sec=ntlm[/COLOR]  ** *[I][B]//192.168.x.x/share  /mount_point
 
[/B][/I]receiving new error

*[79103.990605] CIFS VFS: Unable to select appropriate authentication method!*
*[79103.990609] CIFS VFS: Send error in SessSetup = -22*
[I][79103.990625] CIFS VFS: cifs_mount failed w/return code = -22
[/I]
There is some error that i don't see? the only way to mount that share now is using the option [B]vers=1

[/B]
***sudo mount -t cifs -o domain=mydomain.com,username=Active_Directory_Username , iocharset=utf8,uid=id_local_user,[COLOR=#0000ff]vers=1[/COLOR]  ** *[I][B]//192.168.x.x/share  /mount_point

[/B][/I]Could you help to undestand what was happened?

Tanks

---

### Post by Morbius1 on 2018-03-02
Maybe the user updated his kernel. There was an update to the Linux Kernel version 4.13 that changed the default CIFS smb dialect from SMB1 ( vers=1.0 ) to SMB3 ( vers=3.0 ).

If the server cannot handle SMB3 then you will need to use an earlier dialect "vers=2.0" or in your case "vers=1.0".

---

### Post by giobaxx on 2018-03-02
Tanks. I will ask to our sysadmin

---

