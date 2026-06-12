---
title: "Session Not Saving"
date: 2008-07-11
forum: Desktop Environments
---

### Post by slumbergod on 2008-07-11
Just wondering if anyone out there is experiencing this problem or can suggest something i can try to fix it.

Session Saving in Xubuntu Hardy is not working correctly. I have "Automatically save sessions enabled". When I log in, I am using "Last Session". The ~/.config/xfce4/desktop/icons.screen0.rc has read and write permissions for my username.

The behaviour is that everytime I log in again, *many* of the desktop icons have reset their position and I have to move them back to where I want them. The odd thing is that some of them stay in the correct position!

If I look in the icons.screen0.rc file after I have moved them all where I want them, the changes are indeed recorded. But upon logging out and back in again *some* have reset. 

It's not like I would ever give up using Xubuntu because of this weird behavious...it's just annoying. 

Any suggestions?

---

### Post by joshzam on 2008-07-14
I'm experiencing the same thing on Ubuntu. I'll report back if/when I find a solution.

---

### Post by rfdparker2002 on 2008-07-14
Certainly under Gnome (Ubuntu) at least, if your using Compiz (desktop effects), then session restore won't work as Compiz is not compatible with Gnome's session restore (of running programs).

Edit: Ah, you don't mean that sort of session restore.

---

### Post by stargirl51 on 2008-07-14
Did you try looking in the login window settings to be sure that you have it marked as the session you want?

---

### Post by slumbergod on 2008-07-14
rfdparker2002: my laptop is too old to run Compiz so the problem definitely not related to that in my case.

stargirl51: I am using "Last Session" at the login. 

I will keep looking for a solution...at least to confirm whether this is unique to my installation or common to all Xubuntu Hardy installs.

---

