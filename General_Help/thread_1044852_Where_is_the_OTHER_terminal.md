---
title: "Where is the OTHER terminal ?"
date: 2009-01-19
forum: General Help
---

### Post by zami on 2009-01-19
Okay, I know the terminology is odd - but where is the OTHER terminal?

Not gnome-terminal, not konsole, but the full screen terminal outside of the X-server?

I thought it could be pulled up with CTRL+Fsomething, or ALT+Fsomething, but I'm failing at finding the combo.

Isn't there some way to pull it up without restarting the X-server session?

Thanks for any help!

-zami

---

### Post by steveneddy on 2009-01-19
CTRL + ALT + F1 should get you into one.

Actually F1 through F6 are all virtual terminals with F7 being the GUI and F8 the system messages.

---

### Post by zami on 2009-01-20
Perfect, thank you.

And your right, it still wasn't what I was looking for and had to restart in "failsafe terminal".  But not recalling the key combo was driving me crazy - so thanks!

-zami

---

### Post by DizzyEwok on 2009-01-20
Talking about the OTHER terminal, I was told to do something in it, so I brought it up, and it says login:
and password:
So i entered them both correctly and it just fills the screen with stuff like "UBUNTU HAS NO WARANTEE" and stuff like that, how do I actually use it like a terminal?

---

### Post by PriceChild on 2009-01-20
> **DizzyEwok said:**
> Talking about the OTHER terminal, I was told to do something in it, so I brought it up, and it says login:
and password:
So i entered them both correctly and it just fills the screen with stuff like "UBUNTU HAS NO WARANTEE" and stuff like that, how do I actually use it like a terminal?
Yep that's the standard message of the day when you log in. Look at the bottom and you'll see your bash prompt.

---

### Post by druellan on 2009-01-20
BTW, I decreased the number of terminals from 6 to 2. I was wondering if all 6 are needed somehow somewhere, because having 6 key-combinations that can pull out a beginner user out of the GUI could be problematic (bah, I don't know how many people actually stumbled upon a terminal without knowing it).

---

### Post by DizzyEwok on 2009-01-20
I thought that, but as in the normal terminal, there is an error, there is in this one, therefore disallowing me to view the command line! Even if I type something, it does not respond!

---

### Post by PriceChild on 2009-01-21
> **DizzyEwok said:**
> I thought that, but as in the normal terminal, there is an error, there is in this one, therefore disallowing me to view the command line! Even if I type something, it does not respond!
What error? Could you write it down and copy it in here?

---

### Post by cariboo on 2009-01-21
Reducing the number of console is not going to make your system run any faster, and now you are limited to only 2 consoles. What if you need more. On my server with no gui I usually use 3 consoles to get things done.

Jim

---

### Post by druellan on 2009-01-21
Oh, I was experimenting with resources, not speed, and the question was aimed to desktop usage, since if you don't have gui the use of the console is out of question. I don't want to hijack the thread, so, never mind. Thanks for the answer!

---

### Post by PriceChild on 2009-01-22
> **cariboo907 said:**
> Reducing the number of console is not going to make your system run any faster, and now you are limited to only 2 consoles. What if you need more. On my server with no gui I usually use 3 consoles to get things done.

Jim[http://packages.ubuntu.com/intrepid/screen](http://packages.ubuntu.com/intrepid/screen)

---

