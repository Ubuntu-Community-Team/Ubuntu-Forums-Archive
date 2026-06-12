---
title: "zeroconf / lisa problems"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Zym0tiC on 2006-06-23
I'm trying to configure network browsing in kde. First I tried to use the zeroconf daemon but everytime I open smb://workgroup I get the following error: "the process for the smb://server protocol died unexpectedly".

Because many people say that zeroconf isn't that secure I decided to make use of the Lisa daemon. In the past it worked for me :).

I installed lisa and followed the wizard. After that I had to remove libnss-mdns otherwise the smb://server protocol died unexpectedly error came every time.

Now I'm able to browse my network but there is one problem.... I can't open my mp3's in amarok. It has nothing to do with a codec because it isn't a problem to play mp3s on my own computer.

I hope someone can help me with my problem and / or tell me what the best option is to get easy networking in kde.

---

### Post by Zym0tiC on 2006-06-26
nobody? :(

---

### Post by AreEK on 2006-08-16
I'm experiencing the same problem myself. It looks like it's more widespread than just samba access. I belive that the problem lies in how NTLM authentication is done by KDE. I also get the 'protocoll died unexpectedly' from Kontact (Kmail authentication with Exchange 2003).
I've search for a solution, but though I find some examples of problems with NTLM and KDE, I haven't found anyting helpful yet...

---

