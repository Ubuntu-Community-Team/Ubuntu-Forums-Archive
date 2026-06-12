---
title: "Uh oh - changed /etc/sudoers rights now I can't change them back"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Regord on 2006-09-19
Ok, so I was wanting to work through the Firestarter Guide and tried to change the /etc/sudoers file as suggested at the top of the guide. However, when I added the suggested line to the file:

username ALL=NOPASSWD:/usr/sbin/firestarter

then tried to save...the file said I can't save because it's a read only disk. Hmm...ok...so I know enough to be dangerous in Linux. So I simply went to /etc and executed:

sudo chmod 660 /etc/sudoers

and pressed enter. Ok so the permissions are changed but now when I try to edit the file I get the following:

sudo: /etc/sudoers is mode 0660, should be 0440

so I tried to do another chmod on it and I get the same message. Hmm....I'm stumped now.

Oh and now when I try to launch anything under System | Administration it won't launch. I think I know why...heh...permissions of the file....I don't even get prompted for my password. It looks like it's about to prompt me but then just stops and acts like I didn't just request something.

I also can't execute:

sudo su

I just get the same message.

Oh man...am I screwed??

---

### Post by hashimoto on 2006-09-19
You should modify the sudoers file only by using the command "visudo" command.

Try restarting to safe mode (thus becoming root) and then modifying the sudoers file using "visudo".

---

### Post by Regord on 2006-09-19
> **hashimoto said:**
> You should modify the sudoers file only by using the command "visudo" command.

Try restarting to safe mode (thus becoming root) and then modifying the sudoers file using "visudo".

Thanks for the suggestion.  Would you mind helping me with safe mode?? How do I do that??

I didn't reboot yet, but I opened a terminal window and typed visudo and it said:

visudo: /etc/sudoers: Permission denied

Tried it again with su visudo and got this message:

sudo: /etc/sudoers is mode 0660, should be 0440

---

### Post by Wolki on 2006-09-19
OK, you broke sudo, and without rebooting you won't get it back, unfortunately.

Restart, then select "failsafe" in grub. You should get to a root console, where you can fix the permissions (chmod 440 /etc/sudoers).

If that doesn't work for some reason (it should) next step would be using a live cd.

---

### Post by Regord on 2006-09-19
> **Wolki said:**
> OK, you broke sudo, and without rebooting you won't get it back, unfortunately.

Restart, then select "failsafe" in grub. You should get to a root console, where you can fix the permissions (chmod 440 /etc/sudoers).

If that doesn't work for some reason (it should) next step would be using a live cd.

That did work!!  Thanks I didn't realize there's an option at boot. #-o 

Thanks for the help guys!!  Nice to know I don't have to reinstall.

---

### Post by hashimoto on 2006-09-19
Sorry Regord, I was in a day long meeting so I couldn't reply. Glad you got the problem sorted out with help of wolki. And Wolki, thanks for stepping in!

---

