---
title: "Firestarter Problems"
date: 2005-05-20
forum: Desktop Environments
---

### Post by cacofonix on 2005-05-20
Its been a long time but I have come back to ubuntu, I now need help setting up Firestarter, I have done a search an have been unable to find out how people have fixed it. I seem to have the same settings as everybody else but no matter what I do it will not load on start-up

I have: 
my username ALL= NOPASSWD: /usr/sbin/firestarter in /etc/sudoers added via visudo

I have: 
sudo firestarter --start-hidden and its order 50 in sessions

What do I need to do to get it to start up with out needing to load the gui up manually?

cheers guys

cacofonix

---

### Post by hashimoto on 2005-05-20
AFAIK the Firestarter runs as daemon always (if installed and configured) even if the GUI doesn't. Check the running processes, it should be there. GUI provides a window to see what goes on, but isn't necessary.

---

### Post by cacofonix on 2005-05-20
[QUOTE=hashimoto]AFAIK the Firestarter runs as daemon always (if installed and configured) even if the GUI doesn't. Check the running processes, it should be there. GUI provides a window to see what goes on, but isn't necessary.[/QUOTE]

Thanks for the reply Hashimoto :) I know that it runs as a daemon and the gui isnt necessary I was just wanting have the gui load up so I can see whats going on :D 

cacofonix

---

### Post by mrtaber on 2005-05-20
No solution here---just commiseration and validation of your experience.  After "doing everything by the book," I still can't get the Firestarter gui to come up automat(g)ically.  I've pretty much given up, since I don't reboot or turn off my machine that often anyway.

Mark :)

---

### Post by cacofonix on 2005-05-21
Is it a bug or are we just unlucky lol  :-P 

cacofonix

---

### Post by TRINIDADUBUNTU on 2005-05-21
I can't get the GUI or the daemon up unless I start it from a terminal which I can't close.

If someone could explain the autoload it would be appreciated.

Thanks in Advance

---

### Post by mohaham on 2005-05-21
Type this in a terminal, and click the startup tab and add firestarter:
gnome-session-properties &


Refer to this HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=7812&highlight=firestarter)

---

### Post by stevenyu on 2005-05-21
A easy way of doing is add it in Sessions under System -> Preference -> Sessions

---

### Post by tread on 2005-05-21
> I can't get the GUI or the daemon up unless I start it from a terminal which I can't close. 

This will happen for any program .. if you want the program to run in the background and continue working in the terminal, type 
program-name &

If you forgot to do that, you can achieve the same effect with ctrl-z and then type bg

---

