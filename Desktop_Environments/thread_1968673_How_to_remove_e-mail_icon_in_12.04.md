---
title: "How to remove e-mail icon in 12.04?"
date: 2012-04-29
forum: Desktop Environments
---

### Post by Hvidemose on 2012-04-29
How do i remove the e-mail icon in the top panel? I did it in the 11.10 version via the terminal, but can't find a thread for how to do it in 12.04. Is it the same procedure as 11.10, and how was that?

---

### Post by Frogs Hair on 2012-04-29
I haven't tried with 12.04 , but command was as follows. ```
sudo apt-get remove indicator-messages
``` Logout and in afterwards.

---

### Post by Hvidemose on 2012-04-29
Frogs Hair you are a legend! Just use the code and restart...

Thanks mate!

---

### Post by tony430 on 2012-06-02
How do we get the email icon back to the top panel if we want it again?

---

### Post by typhoon_tip on 2012-06-02
```
sudo apt-get **install** indicator-messages
```

:)

---

### Post by tony430 on 2012-06-03
Haha. I realized after I asked the question. Thanks.

---

### Post by jtarin on 2012-06-03
you can just do this by deleting the notification area from the panel. To add it back just go via panel "add".But how to remove individual icons???

---

### Post by markbl on 2012-06-03
> **jtarin said:**
> But how to remove individual icons???
[http://www.omgubuntu.co.uk/2010/12/remove-unused-entries-from-the-ubuntu-messaging-menu](http://www.omgubuntu.co.uk/2010/12/remove-unused-entries-from-the-ubuntu-messaging-menu)

---

### Post by jtarin on 2012-06-03
> **markbl said:**
> [http://www.omgubuntu.co.uk/2010/12/remove-unused-entries-from-the-ubuntu-messaging-menu](http://www.omgubuntu.co.uk/2010/12/remove-unused-entries-from-the-ubuntu-messaging-menu)
Thanks, but that is only for entries in the menu that appears when right-clicking the notification area. I'm looking to remove individual icons...like the envelope.

---

### Post by satish_j on 2012-06-03
does anyone know how to remove the indicator for logged-in user in unitys top panel?

---

### Post by Frogs Hair on 2012-06-03
```
sudo apt-get remove indicator-session 
``` Restart

---

### Post by typhoon_tip on 2012-06-03
> **Frogs Hair said:**
> ```
sudo apt-get remove indicator-session 
``` Restart

I won't suggest to remove that indicator in this case, just hide it would be better. At least is what I did:
[http://ubuntuforums.org/showpost.php?p=11409257&postcount=6](http://ubuntuforums.org/showpost.php?p=11409257&postcount=6)

Precisely, just untick the "User show menu" item.

---

### Post by Frogs Hair on 2012-06-03
> **typhoon_tip said:**
> I won't suggest to remove that indicator in this case, just hide it would be better. At least is what I did:
[http://ubuntuforums.org/showpost.php?p=11409257&postcount=6](http://ubuntuforums.org/showpost.php?p=11409257&postcount=6)

Precisely, just untick the "User show menu" item.

That may be a better option , removing indicator-me in gnome 2 didn't have any side effects other than removing the name and list . Things may be different in Gnome 3.

---

### Post by typhoon_tip on 2012-06-04
> **Frogs Hair said:**
> That may be a better option , removing indicator-me in gnome 2 didn't have any side effects other than removing the name and list . Things may be different in Gnome 3.

I don't remember exactly how and when, but I run into some sort of issues related to that indicator missing in Gnome 3 env.

---

