---
title: "meme"
date: 2009-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by meme427 on 2009-03-09
we have a Dell Ubuntu Mini, we are new to linux and the person who set up the password did not write it down nor does anyone remember it.  There is only one user on the system and it keeps asking for the password when i try the sudo passwd root
so does anyone know how i can reset the users password without knowing the current one?

I appreciate your help
:(

---

### Post by sirebral on 2009-03-09
:popcorn:

That is a security feature.  No hard feelings here, but I wish you bad luck in finding in answer.

I do suggest you reformat.  You might even want to talk to DELL about replacing it if you have a warranty as of yet.  Sorry about the wishes. :(

---

### Post by albandy on 2009-03-09
> **meme427 said:**
> we have a Dell Ubuntu Mini, we are new to linux and the person who set up the password did not write it down nor does anyone remember it.  There is only one user on the system and it keeps asking for the password when i try the sudo passwd root
so does anyone know how i can reset the users password without knowing the current one?

I appreciate your help
:(

When you type sudo it's specting your user password
when you type sudo passwd root
sudo ask for your password
then passwd ask for the new root password
and then ask for the new root password again

BUt remember that root is disabled in ubuntu by default, all your root tasks are done by sudo

---

### Post by ugm6hr on 2009-03-09
There are ways to change your password in Ubuntu, but I don't think it is possible with the Dell Mini.

This is because the Dell Ubuntu has a default 0 countdown to enter the Grub menu, so you have 0 seconds to press Escape (i.e. not enough time). This means it is essentially impossible to enter the (passwordless) recovery terminal.

The only solution I can think of is to use a LiveUSB on the Mini, mount the Mini's internal SD card, edit /boot/grub/menu.lst to change the 0 timeout, then reboot into recovery mode.

Then this will get you through the rest: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Of course, it may be just as easy to reinstall!

---

