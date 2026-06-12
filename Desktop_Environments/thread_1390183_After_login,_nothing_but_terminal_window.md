---
title: "After login, nothing but terminal window"
date: 2010-01-25
forum: Desktop Environments
---

### Post by kyldere on 2010-01-25
I had to resize the root partition of a 9.10 install (who knew that Xilinx took up so much room). All seemed to go well until after a reboot over the weekend. For whatever reason, the UUID had changed for the swap partition. I've since updated /etc/fstab so that the UUID is correct, but now after I login (gdm), I get a desktop with a terminal window and nothing else. Any ideas?

---

### Post by slooksterpsv on 2010-01-25
In the terminal window can you start gnome-panel or that?

---

### Post by kyldere on 2010-01-25
I can start gnome-panel (or gedit or whatever), but the terminal window has no window border and clicking on the desktop does nothing (no popup menu).

---

### Post by slooksterpsv on 2010-01-25
> **kyldere said:**
> I can start gnome-panel (or gedit or whatever), but the terminal window has no window border and clicking on the desktop does nothing (no popup menu).

Try: sudo gdm-bin

---

### Post by kyldere on 2010-01-25
sudo gdm-bin returns
sudo: gdm-bin: command not found

---

### Post by kyldere on 2010-01-25
So I added a new user and the desktop is behaving normally for that user. Can I get the desktop back to a 'working' state for the previous user? Should I create a new user and assign that user the same /home directory?

---

### Post by kyldere on 2010-01-25
Problem solved. I copied the user account out of the home directory and created a new user account. I then deleted the old user's home directory. For whatever reason, the problem persisted when I recreated the old user account. To work around this, I've just relocated the important information to a new user account and will not re-createt the old user again (at least until after I reboot the machine).

---

