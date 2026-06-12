---
title: "Xfce keeps being turned off by Gnome"
date: 2007-07-15
forum: Desktop Environments
---

### Post by ela04cz on 2007-07-15
My Xfce keeps being turned off automatically, don´t know why.

Every time I fix this by ticking the ¨allow xfce to manage the desktop¨ but after reboot, it goes back to gnome desktop again:(

I tried ¨save the session for future¨ but it didn´t work.

Can someone please give me a hint?

---

### Post by merlinus on 2007-07-15
You have to make sure save session is unticked before exiting.

Also, when logging in and selecting xfce, it can be changed it to the default.

-merlin

---

### Post by ela04cz on 2007-07-15
no it doesn´t work....

---

### Post by Rui Pais on 2007-07-15
> **ela04cz said:**
> My Xfce keeps being turned off automatically, don´t know why.

Every time I fix this by ticking the ¨allow xfce to manage the desktop¨ but after reboot, it goes back to gnome desktop again:(

I tried ¨save the session for future¨ but it didn´t work.

Can someone please give me a hint?

Can you be a little more specific? 
Do you mean that when you login you are directed to gnome-session, or that after login to xfce the gnome desktop appears over xfce?

---

### Post by Dwood108 on 2007-10-20
You can try this, I had the same problem and it worked for me.

   1. In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."
   2. Log out and log back in.
   3. Click 'New Session' when the session selector appears, and name it whatever you want.
   4. The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.

once this works you can turn off the session selector at startup and go directly to your new session on future logins.

If you are using Nautilus run it using the comand nautilus --no-desktop

---

