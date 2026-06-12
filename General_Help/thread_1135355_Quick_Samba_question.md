---
title: "Quick Samba question"
date: 2009-04-24
forum: General Help
---

### Post by pylon42 on 2009-04-24
If you "share" a folder using gnome, Ubuntu asks you to install Samba. Makes sense.

However, the share created doesn't show up in:
/etc/samba/smb.conf

What's that all about? Can I manually edit this share somewhere?

I've got a problem where all files created in the share by other systems on the network belong to "nogroup" "nobody". I'd like to correct it, but can't find anything to edit :(

---

### Post by jamessnell on 2009-04-24
> **pylon42 said:**
> If you "share" a folder using gnome, Ubuntu asks you to install Samba. Makes sense.

However, the share created doesn't show up in:
/etc/samba/smb.conf

What's that all about? Can I manually edit this share somewhere?

I've got a problem where all files created in the share by other systems on the network belong to "nogroup" "nobody". I'd like to correct it, but can't find anything to edit :(

Sounds like an incomplete implementation for that feature in nautils. Have you checked to see if there's a bug ticket for that?

I suggest you install some other samba config gui and use that for now.. Or just edit by hand.

That's a funny story though, lame too.

---

### Post by LowSky on 2009-04-24
install samba, then log out, log in, then llook for samba file, then edit, the reboot... 

really annoying process but has to be done

---

### Post by rturner on 2009-04-24
Normally, I install samba to begin with and add smbusers.  This time (with a clean install of Jaunty) I decided to let nautilus install samba to see what happened.  Like you, my share didn't show up in smb.conf.  So I just entered the share and permissions in smb.conf and changed WORKGROUP to my lan's workgroup, restarted samba and it's all working fine.

---

### Post by pylon42 on 2009-04-24
Yeah, just did the same thing. All is working now.

I'm still pretty new to Linux so I'm not entirely sure what's going on. For the heck of it, I tried using the gui to share the same folder after I got it working by editing smb.conf. It broke everything again, so I can only assume "it" gets priority over smb.conf. Whatever "it" is that is enabling the Samba share without editing smb.conf...

Anyway - thanks for the help guys :)

---

### Post by pylon42 on 2009-04-24
Does Nautilus have some kind of abstraction layer that lets it take in all these gui settings without making changes to the actual filesystem? There's so many things that I'm supposed to know at this point that I don't...

---

### Post by msun on 2009-04-25
I also noticed that Nautilus handles shares independently of the /etc/samba/smb.conf configuration file. Some tests reveals the following observations:-

1. If you create a share using Nautilus, the share emblem disappears if you login as a different user.

2. The different user cannot change or manage/delete that share which is now effectively not visable in Nautilus.

3. You have to run Nautilus as "root" e,g, "sudo nautilus", add the share, then remove the share to allow another user to manage sharing of that folder.

4. Managing the share using the /etc/samba/smb.conf (either directly or using some GUI config tool such as "system-config-samba" seems more reliable but there is no visibility of this under Nautilus.

5. Any shares created in Nautilus appear in /var/lib/samba/usershares

Cheers from Mike :)

---

### Post by m42h31 on 2009-04-26
3 days ago i rename mounted disk label. my old disk label is /media/_data/ than i rename to /media/MyData because on jaunty /media/_data/ detect as /media/%data/, my netbeans and komodo edit can't found it..since that, sometimes i can't logout from my user, error message come from samba, it can't found my new mounted disk. in this case samba still detect my old disk label(/media/_data) during logout. how to fix it ?

---

