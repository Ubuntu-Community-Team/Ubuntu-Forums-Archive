---
title: "No exec line in the session file: KDE"
date: 2009-02-21
forum: General Help
---

### Post by Inane_Asylum on 2009-02-21
I finally switched from KDE to GNOME, so I did a fresh install of Intrepid.  I went through the whole song-and-dance to get my /home partition set up.  After rebooting, I get the message ```
No Exec line in the session file: KDE
Starting GNOME Failsafe Session
```

Logging out and back in gives the same message, and Google brings up only one hit for a Mandriva forum.

Any ideas?

---

### Post by snova on 2009-02-21
What are the contents of **/usr/share/xsessions/kde.desktop**?

This is the only place I can imagine one would find an "Exec line" in relation to sessions. But it would have to be corrupt, which is extremely unlikely- unless the installer failed somehow.

---

### Post by Inane_Asylum on 2009-02-21
I think it's fixed now.  What I think may have happened is that before I reinstalled, my preferences (which were preserved on my /home partition) had me logging into KDE by default, as it was a Kubuntu installation before.  I set GNOME as my default session, and haven't had the problem since.

Now to get wifi working again... ](*,)

---

### Post by Moriator on 2009-04-26
> **Inane_Asylum said:**
> I think it's fixed now.  What I think may have happened is that before I reinstalled, my preferences (which were preserved on my /home partition) had me logging into KDE by default, as it was a Kubuntu installation before.  I set GNOME as my default session, and haven't had the problem since.

Now to get wifi working again... ](*,)

Can you explain more clearly? I meet this problem when I install Kubuntu after Ubuntu.

---

### Post by Inane_Asylum on 2009-04-26
In your case, when you first boot up, it should boot to KDM where you can choose which account to log in to.  There should be an option somewhere to choose a "session."  For me, after switching from KDE to GNOME, it still had KDE as my default session, though I didn't have KDE installed.  For you, you may still have GNOME selected as your default session.  Switch your session to KDE, and the problem **should** resolve.

---

