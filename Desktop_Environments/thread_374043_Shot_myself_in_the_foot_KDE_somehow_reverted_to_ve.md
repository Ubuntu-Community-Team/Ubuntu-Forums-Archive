---
title: "Shot myself in the foot: KDE somehow reverted to version 3.5.5, and not behaving well"
date: 2007-03-02
forum: Desktop Environments
---

### Post by monocongo on 2007-03-02
I have somehow misconfigured my system such that I now have KDE version 3.5.5 running, and I was using the latest version of KDE before I rebooted.  Before rebooting I tried uninstalling several packages using which I wasn't using via Adept Package Manager and the process hung at 52% with a message about replacing kdm.  No matter what I tried I couldn't get it to continue and ended up killing the Adept process.  Also I updated ntfs3g using Synaptic.  Other than that I can't think of anything which should have caused problems.  Now when I login I don't see the system menu or any other of the launch shortcuts I am used to seeing in my desktop panel, and when I iconify an application it disappears from the desktop rather than showing up in the panel along the bottom of my screen.

Can anyone suggest what I might do to back myself out of this mess?  Thanks in advance for any help.

---

### Post by Cene on 2007-03-02
I had the same kind of problem before too.

Only solution I found was booting to terminal, removing KDE and all that is linked to it and install the packages again. Slow, but worked.

---

### Post by monocongo on 2007-03-04
I ended up having to do a reinstall of Ubuntu.  I repartitioned my disk before I reinstalled with a separate partition for /home so hopefully this won't be as painful next time.

---

