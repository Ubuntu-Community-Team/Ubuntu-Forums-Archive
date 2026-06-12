---
title: "ProFTPD: anonymous access with incoming folder"
date: 2005-07-10
forum: Desktop Environments
---

### Post by nnacht on 2005-07-10
hello, dear forum,
what I want to get is the following:
I want my ubuntu box to act as ftp-server with anonymous access actived, e.g. everyone can download files from the /home/ftp, but read only. The users have the opportunity to upload files to the folder /home/ftp/incoming. I found a lot of literature about in in the google, and changed the /etc/proftpd.conf, but it does not work, (e.g. upload is not successful). Can somebody tell me what is wrong with the conf-file?
The following is the section "anonymous" of the conf file:
<Anonymous ~ftp>
  User                        ftp
  Group                       nogroup
  UserAlias                   anonymous ftp
  DirFakeUser on ftp
  DirFakeGroup on ftp
  RequireValidShell           off
  MaxClients                  10
  DisplayLogin                welcome.msg
  DisplayFirstChdir           .message
#uncomment if you want the anonymous use have the right to write!  
<Directory *>
    <Limit WRITE>
      DenyAll
    </Limit>
</Directory>

<Directory incoming/>
            <Limit READ WRITE>
            DenyAll
            </Limit>
            <Limit STOR>
            AllowAll
            </Limit>
 </Directory>


#uncomment untile here.
</Anonymous>
Thanks  a lot
shaohui

---

### Post by frodon on 2005-07-10
Can you explain what you do to say "it doen't work" ? Did you test to connect yourself to the ftp server, what kind of errors have you got ?
If you want to collect more debug information : [http://www.proftpd.org/localsite/Userguide/linked/x1058.html](http://www.proftpd.org/localsite/Userguide/linked/x1058.html)
I give you a link of a thread about proftpd and anonimous access : [http://www.ubuntuforums.org/showthread.php?t=47099&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=47099&page=1&pp=10)

---

