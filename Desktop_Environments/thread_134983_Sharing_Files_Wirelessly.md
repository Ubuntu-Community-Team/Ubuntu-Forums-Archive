---
title: "Sharing Files Wirelessly"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Jerrac on 2006-02-22
I have done some seaching and cannot find a good answer, so I will ask... :D

I have a wireless network. My desktop is plugged into the router with a cable and runs Breezy. My laptop has a wireless g pcmcia card, and runs windows xp home. 

I installed samba on my desktop, and shared a couple folders. I also have shared a couple folders on my laptop. The thing is that niether computer will detect the others shared folders. I go to network places on windows and it just shows the shared folders on itself. Ubuntu gives me a Windows Network icon, but doesn't show any computers under it.

I should also mention that when I was home from college on the wireless network there, I also could not share files with the windows desktop connected by cable to the router.

So, what can I do? 

Thanks! :D

---

### Post by jpkotta on 2006-02-23
I use WinSCP to manipulate files on a Linux machine from a Windows machine.  Samba would probably be the best way but I don't care to configure the server.  

For manipulating files on a Windows machine from a Linux one, I can just type "smb://*ip address*" in the address bar of either firefox or nautilus.

---

### Post by Jerrac on 2006-02-23
And how exactly do you get winscp to connect to the linux computer? 

Haven't tried the smb// yet...

---

### Post by lamego on 2006-02-23
You need to have openssh installed on the linux box, then just install winscp on windows and connect to it with your host, user, pass info...

---

