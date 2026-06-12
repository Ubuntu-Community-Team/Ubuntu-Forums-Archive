---
title: "What happens if I mistype commands on the terminal?"
date: 2011-06-10
forum: Desktop Environments
---

### Post by paul98 on 2011-06-10
Hi, 
I was trying to download a program using the command line. The original command was: su -c 'yum -y install liveusb-creator'

The problem is, I mistyped this command and didn't include the single quotation mark at the end. When I pressed Enter, a ">" appeared below the line, followed by the cursor. When I tried again and typed it comrrectly, the command line asked for my password, which I gave correctly, but it didn't accept it. It kept saying, "Authentication failure." 

Did I just damage my system? Do I have to re-install Ubuntu? And did I just expose my computer to a security flaw? I am running 11.04.

---

### Post by wojox on 2011-06-10
No your fine. Since your using Ubuntu and trying to install Fedora packages it didn't do anything. If you don't complete a command it will drop down to the > and wait for the next character.

You usb creator is already installed. Type:

```
usb-creator-gtk
```

---

### Post by paul98 on 2011-06-10
Thanks! I thought I was a goner there....

---

### Post by Rubi1200 on 2011-06-10
In this case, wojox is right.

But, a friendly word of warning, be very careful with commands in the terminal!

One wrong letter, switch (especially recursive parameters), or other syntax error and you could potentially cause serious damage.

Get into the habit, even when you are tired or in a hurry to do something, of always looking at the command again to make sure it is all correct before pressing Enter.

If in doubt, post a question here first and check if what you are about to do is okay.

Those extra couple of seconds may save you hours of frustration in the future.

---

