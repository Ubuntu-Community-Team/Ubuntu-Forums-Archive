---
title: "Can't use administraitive powers anymore"
date: 2005-12-29
forum: General Help
---

### Post by SZF2001 on 2005-12-29
(I know I've posted this in the Beginner talk, but no one there seems to care. Maybe someone here will)

So, I've got my DSL hooked into Ubuntu through the ethernet cord, and whadda know, it won't pick up.

I go into networking, enable it, tell it it's DHCP or whatever, connect it...

Nothing.

So I restart the whole computer.

AND GUESS WHAT POPS UP? A little box that states:

"Could not look up internet address for ColemanNetwork (my network name).
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
ColemanNetwork to the file /etc/hosts/"

Then is asks me if I want to "Log in anyway" or "Try again".

Try again does nothing.

Log in anyway will not let me use any administraitive things, like the Synaptic package manager or the Network settings (WHICH IS WHAT I WANT TO USE ANYWAY GRRRR)

So. I screwed myself over. Help?

---

### Post by jrib on 2005-12-29
Did you change your hostname?  I've seen some people have some problems because they forget to update that file that the error message mentions, /etc/hosts.  Instead when changing a hostname some people only edit /etc/hostname (I think this is the location since I'm not on ubuntu right now) and forget about /etc/hosts.  Make sure ColemanNetwork is in /etc/hosts.

[edit] If you need superuser privileges to edit that file and can't get them, just boot from the livecd and mount your drive.  Then edit /etc/hosts and reboot.

---

### Post by SZF2001 on 2005-12-29
[QUOTE=_jason]Did you change your hostname?  I've seen some people have some problems because they forget to update that file that the error message mentions, /etc/hosts.  Instead when changing a hostname some people only edit /etc/hostname (I think this is the location since I'm not on ubuntu right now) and forget about /etc/hosts.  Make sure ColemanNetwork is in /etc/hosts.

[edit] If you need superuser privileges to edit that file and can't get them, just boot from the livecd and mount your drive.  Then edit /etc/hosts and reboot.[/QUOTE]
OK... So I went into /etc/hostname and it only says "ColemanNetwork". Without the little " things, but you get my point.

In /etc/hosts, it says, "# The following lines are desirable for IPv6 capable hosts" and nothing else.

---

### Post by jrib on 2005-12-29
[QUOTE=SZF2001]OK... So I went into /etc/hostname and it only says "ColemanNetwork". Without the little " things, but you get my point.

In /etc/hosts, it says, "# The following lines are desirable for IPv6 capable hosts" and nothing else.[/QUOTE]

okay I'm on windows right now, but I used explore2fs to get /etc/hosts and /etc/hostname from a clean ubuntu install.  The hostname is "caramulo".  See if you can adjust your /etc/hosts accordingly.

---

### Post by SZF2001 on 2005-12-29
I hate to sound like a retard, but I didn't get a whole lot out of that... Sorry... I'm not to bright when it comes to Linux.

---

### Post by jrib on 2005-12-29
[QUOTE=SZF2001]I hate to sound like a retard, but I didn't get a whole lot out of that... Sorry... I'm not to bright when it comes to Linux.[/QUOTE]

can you post your /etc/hosts?

---

### Post by ninotob on 2005-12-29
There is something worse going on than a network not working if you can't access the admin functions.  What exactly happens if you try to select "networking" from the admin menu -- do you get a chance to enter your password?

---

### Post by SZF2001 on 2005-12-29
[QUOTE=ninotob]There is something worse going on than a network not working if you can't access the admin functions.  What exactly happens if you try to select "networking" from the admin menu -- do you get a chance to enter your password?[/QUOTE]
Nope, no chance at all, like it used to before this happened.

[QUOTE=_jason]can you post your /etc/hosts?[/QUOTE]
I already told you. Thats it.

---

### Post by ninotob on 2005-12-29
Do you have a Live-CD version?  Get that if you don't.  This will tell you something important.  If you run it and the network works fine, your current system is borked (my guess since you aren't asked for your admin password).  If you run it and the network won't work, then perhaps your hardware won't work -- I assume you are given an IP address by DHCP from your ISP. 

If it looks like your system is fouled up -- the question becomes how much time have you invested in it?  If it's just a few copied bookmarks and some easily backed up data but otherwise a fairly default configuration -- I'd just re-install.  Always choose the path of least resistance.  ;-)

---

### Post by ninotob on 2005-12-29
You could always give this a shot before running the live-cd:

in the terminal, type:

```

sudo /etc/init.d/networking restart

```

It should ask for your administrator password.
(you are logged in as the administrator right?)

Make note of the output.

---

### Post by jrib on 2005-12-29
[QUOTE=SZF2001]Nope, no chance at all, like it used to before this happened.


I already told you. Thats it.[/QUOTE]

I don't really understand what caused this, but you can try backing up your /etc/hosts and using my /etc/hosts (except change caramulo to your hostname).  Reboot and at least you can see if this is all there is to the problem or not.

---

### Post by SZF2001 on 2005-12-29
When I type that in the terminal, it doesn't ask for a password, but it says:

sudo: unable to lookup ColemanNetwork via gethostbyname()

---

### Post by sciurus on 2005-12-29
Edit /etc/hosts to say ```
127.0.0.1 localhost.localdomain localhost ColemanNetwork
```

---

### Post by SZF2001 on 2005-12-29
I think I'll try that.

But first I'm going to get my boot cd and see if maybe it can restore default settings, or something.

---

### Post by jrib on 2005-12-29
SZF2001, in reply to your private message I posted my /etc/hosts in an earlier post as an attachment ["hosts.txt"]("http://www.ubuntuforums.org/attachment.php?attachmentid=4926&d=1135904413") but it essentially boils down to doing what sciurus said.

---

### Post by SZF2001 on 2005-12-29
_jason, sciurus, ninotob... I love you all.

Thank you.

Now I will download and install emulators for SONIC TO RULE MY COMPUTER.

Thanks guys! I won't forget this!

---

