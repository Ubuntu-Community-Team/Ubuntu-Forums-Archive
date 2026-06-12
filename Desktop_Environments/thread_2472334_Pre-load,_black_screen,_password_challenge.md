---
title: "Pre-load, black screen, password challenge?"
date: 2022-02-24
forum: Desktop Environments
---

### Post by dbee on 2022-02-24
So i was fixing an issue on my ubuntu system and had to reset the BIOS.

Now I can't logon without entering a password on a black screen with a lock on it on boot up. I know the password and everything. But it's annoying.

Is this some sort of pre-OS-loading, harddrive authentication or something? I had issue with proprietary nvidia drivers on this system before. So maybe resetting the BIOS deleted a previous fix i had in place for this issue in grub?

Anyway, how do i get rid of this authentication?

---

### Post by ajgreeny on 2022-02-24
At what point do you see this black screen and password request, and is this password, which you say you know and are able to enter, the same as your user password used to login to your session?

It sounds as if you or someone else may have enabled a BIOS password but as you know what it is, did you do this at some point but have forgotten that you did so?

I think it is also possible to set a password for grub but I have never used it, if it is possible, so I will have to search for information about that before saying any more.

---

### Post by dbee on 2022-02-24
Yeah. I set the pass at some point so by that logic. It must be a bios setting right?

The pass screen occurs pre-os load up.

What's the best way to get into grub? "Enter" gets me into the bios. How can I get into grub easily?

---

### Post by ajgreeny on 2022-02-24
I doubt that making changes to grub is what you need to do unless you set a password to protect your grub menu, in which case see [https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords).

If this is a password you set to protect the BIOS you will need to disable that password requirement in the BIOS settings, not in grub.

I have never used a password to protect BIOS/UEFI not a stop changes being made to grub so have no personal experience of this, and unfortunately for you, there are many different BIOS systems and their settings pages all look very different so you will have to search from page to page of the BIOS setup to find anything about passwords.

---

