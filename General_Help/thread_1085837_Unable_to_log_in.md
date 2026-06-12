---
title: "Unable to log in"
date: 2009-03-03
forum: General Help
---

### Post by Jaded Misanthrope on 2009-03-03
I'm in a bit of a pickle here: I can't log in. I type in my username and password -- both of which are correct -- and hit enter, but I get a black screen with white text about 'starting anacron' or something (I'll get the actual text if necessary) and then get pushed back to the login screen. I have a lot of important data on this computer, and since it's a laptop I can't remove the HDD to retrieve it: how can I log in again?

---

### Post by taurus on 2009-03-03
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Now, see if you are not running out of disk space.

```
df -h
```

---

### Post by Jaded Misanthrope on 2009-03-03
Just tried that and I can't log in there either. I enter my username and password correctly, but it just prompts me for them again. It's definitely correct, and if I deliberately enter a false username / password it says 'login incorrect' (or words to that effect). I really don't want to have to reinstall if it can be avoided. :|

---

### Post by taurus on 2009-03-03
Reboot your machine and at the GRUB menu (press the Esc key if you don't see the menu), highlight the recovery mode entry and boot from that.  Then, get into root shell.  Now, look to make sure you have your login name right.

```
ls -la /home
```
You can also change the password at the prompt, assuming your login name is jaded.

```
passwd jaded
```
Check your disk space also.

```
df -h
```

---

### Post by Jaded Misanthrope on 2009-03-03
I've plenty of free disk space -- 60% of roughly 10GB is used on the partition containing the system itself, 9% of maybe 90GB on the partition containing my home folder -- and I'm getting the name correct. The most worrying thing happens when I enter the 'passwd jaded' command: 'segmentation fault'.

---

