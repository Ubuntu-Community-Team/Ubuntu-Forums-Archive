---
title: "attacching smb:// files to Thunderbird"
date: 2010-12-18
forum: Desktop Environments
---

### Post by manolomanolo on 2010-12-18
Hi.

I am trying to attach shared files to a Thunderbird mail.
The files are stored into a remote machine inside my LAN. The path is something like smb//:<something>

But when trying to attach the file I get a permission error:
"controllare i permessi di accesso al file"
(trad: "check the access permissions to the file")

Any suggestion, please?

Thanks.
Regards.

---

### Post by pfnorris on 2010-12-19
This looks like a permissions issue. From the wording of your question it appears that you are trying to attach the file by addressing the smb share directly from within Thunderbird. I think I am correct in saying that Thunderbird has no mechanism to pass any credentials to the remote smb server to authenticate you.

I suggest that you try mounting the remote share first as this will deal with the authentication issue. Then add the attachment in Thunderbird from the mounted share. This time Thunderbird will not need to authenticate you as that has already been dealt with through the mount.

---

