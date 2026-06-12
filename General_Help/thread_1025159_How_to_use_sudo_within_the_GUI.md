---
title: "How to use sudo within the GUI?"
date: 2008-12-29
forum: General Help
---

### Post by chrisbooth12 on 2008-12-29
I have been playing around with some themes lately and some of them require me to drag and drop a folder into the all users theme folder. The thing is i dont have the rights to do this. I could use the terminal with sudo but my linux commands are still new. Is there a way i can sudo copy files to protected directories without using the terminal?

---

### Post by eBoxNet on 2008-12-29
```
gksudo nautilus
```

but be VERY careful

---

### Post by chrisbooth12 on 2008-12-29
> **eBoxNet said:**
> ```
gksudo nautilus
```

but be VERY careful

how do i remove my rights after i am done?

---

### Post by fooman on 2008-12-29
> **chrisbooth12 said:**
> how do i remove my rights after i am done?

close nautilus.

---

### Post by tuxxy on 2008-12-29
Close the terminal window you ran the gksudo command from or nautilus window, now you will be back to normal.  You could run another normal nautilus at the same time anyway for example clicking the documents menu but this will be normal user privs as you didnt gksudo it.

---

### Post by Equiflux on 2008-12-29
What exactly is the difference between sudo and gksudo?

---

### Post by eBoxNet on 2008-12-29
sudo for text mode
gksudo for gui mode

---

### Post by Dr Small on 2008-12-29
> **eBoxNet said:**
> ```
gksudo nautilus
```

but be VERY careful
That was my favorite command when I first started Ubuntu! :D

---

### Post by Equiflux on 2008-12-29
> **eBoxNet said:**
> sudo for text mode
gksudo for gui mode

Can you further explain that please? When I use sudo nautilus, I see no difference between when I use gksudo nautilus.

---

### Post by eBoxNet on 2008-12-29
yes cause nautilus doesn't have a text mode.


you can read this for further explaining.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

and this : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tuxxy on 2008-12-29
> **Equiflux said:**
> Can you further explain that please? When I use sudo nautilus, I see no difference between when I use gksudo nautilus.

There are many apps that will run using just sudo like nautilus with no side effects, however if you wanted to do it correctly then gksudo :)

---

### Post by Agent ME on 2008-12-29
When you use sudo, it asks for the password on the terminal. When you use gksudo, a dialog box pops up asking for the password.

You have to use gksudo when you're not using a terminal.

---

