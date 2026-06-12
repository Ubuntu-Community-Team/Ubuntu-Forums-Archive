---
title: "Root terminal does not open"
date: 2017-06-06
forum: Debian
---

### Post by Floppyjoe on 2017-06-06
Running Debian 9 Stretch, When i run the root terminal and then close it, It will not open again unless I log out and log back in. Is there a way to fix this behaviour?

---

### Post by QIII on 2017-06-06
Hello!

How do you "close it"?

---

### Post by Floppyjoe on 2017-06-06
> **QIII said:**
> Hello!

How do you "close it"?

I believe I clicked on the "x". Are we supposed to only use exit command?

---

### Post by QIII on 2017-06-06
I always 

```
exit
```

Try that and see what happens.

---

### Post by Floppyjoe on 2017-06-06
> **QIII said:**
> I always 

```
exit
```

Try that and see what happens.

I tried that "exit" command, and it still behaves the same way. It will not launch root terminal again.

---

### Post by QIII on 2017-06-06
So you are logged in to the GUI under your normal user account, correct?

---

### Post by Floppyjoe on 2017-06-06
> **QIII said:**
> So you are logged in to the GUI under your normal user account, correct?

That is correct and the same behavior happens on a 64bit and a 32bit version of Debian 9 Stretch. When I try to launch the root terminal it asks for my password and then the screen clears and...nothing. The regular terminal works fine.

---

### Post by #&amp;thj^% on 2017-06-06
I remember this a while back testing it...but give this a try it worked for me.
Keyboard combo <Ctrl+D> To exit Root Terminal
Use:```

su your-username 


```  to get back to your user level (or a different user)


If you opted for a root password with the install this is how it ended up for me.
The next install I opted out of a Root password and sudo was installed...and worked the same way we see with Ubuntu.
(So No Root Password with install)
EDIT found some notes I kept and discovered this:


[LIST]
[*]logout if I used sudo su - 
[*]exit if I used sudo -s 
[/LIST]

---

### Post by Floppyjoe on 2017-06-06
> **1fallen said:**
> I remember this a while back testing it...but give this a try it worked for me.
Keyboard combo <Ctrl+D> To exit Root Terminal
Use:```

su your-username 


```  to get back to your user level (or a different user)


If you opted for a root password with the install this is how it ended up for me.
The next install I opted out of a Root password and sudo was installed...and worked the same way we see with Ubuntu.
(So No Root Password with install)
EDIT found some notes I kept and discovered this:


[LIST]
[*]logout if I used sudo su - 
[*]exit if I used sudo -s 
[/LIST]

When I use "su username" it goes to my normal user account. From there "logout" does not work, and "exit" just goes back to root user. Using "exit" twice closes the terminal and then I can't open the root terminal again during that session.

I can get to a root prompt using the normal terminal and typing "su root" and then the root password.

---

