---
title: "Not able to Login as Root"
date: 2007-09-19
forum: Desktop Environments
---

### Post by hellolijo on 2007-09-19
hi,
    i am new to the Ubuntu...
    when i type su in command window to work as root
    it is asking password
    but when i type my login password it is showing authentication failure message...
    Actually i donot know any root password....
 
so how i can rectify this problem ...................................

thanking You

---

### Post by ivelasco on 2007-09-19
The root account is disabled by default at ubuntu.
Open a terminal and
sudo su passwd
at the prompt write your own password once
after write the new root pass twice
that's all,now you are ready to login as root

---

### Post by Beggar on 2007-09-19
You shouldn't log in as root in ubuntu unless its really necessary, search the forums if you want an explanation of the benefits to using sudo.

---

### Post by fish2ways on 2007-09-19
Just to reinforce what the previous post said. There really is no reason why you should need to log-in as Root.
You can do everything you may need to do that needs Root permissions using sudo.

---

### Post by neaeo on 2007-09-19
You should NOT login as root. Instead, use:

sudo -i

---

