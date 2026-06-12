---
title: "ubuntu catches &quot;up arrow&quot; command"
date: 2009-10-18
forum: Desktop Environments
---

### Post by shakayoda on 2009-10-18
Hello,
 
I have some weird problem happening in a window manager as well as in terminals or outside window manager. Every 4 seconds, it is as if ubuntu catches an "up arrow" keyboard command. Disconnecting the keyboard or mouse doesn't change anything. While typing this text I had to move the cursor down every 4 second to correct the movement of the cursor. This is driving me mad. Does someone have a sugestion to correct this behaviour?

System: Jaunty on a Dell Dimension 9200.

S.

---

### Post by shakayoda on 2009-10-20
Even more strange: this behaviour never occurred on my laptop (also Dell) and it appears to be occasional (e.g. it doesn't happen right now).

---

### Post by shakayoda on 2009-10-31
As the number of replies remained low so far, and because the same issues persists during the installation of Karmic Koala (preventing me to introduce a password correctly) I suppose that I have to reformulate the issue.

What happens during the installation is this. I can start from the LiveCD without any problems, and all my hardware is recognized fine (Dell Dimension 9200 with Soundblaster X-Fi music and NVidia graphic card). I can even select the correct language and keyboard lay-out without having any trouble. However, once the desktop of the LiveCD appears and I actually launch the installation, problem arise:
- When I put the cursor in a text box, every 2 or 3 seconds the cursor is moved to a text box higher up on the screen. the selection moves upwards every 2-3 seconds.
- When I arrive at the language selection dialog,
- When I select the advanced options to select the partitions to which I want to install 9.10, I have to do it quickly before my selection is changed to the one just above my selection. It continues moving up one row at a time until it reaches the partition at the top.

In Jaunty Jackalope, I did not have this issue upon installation, but it developed later on. So when I look at my emails, every 2-3 seconds I see that the selected email is changed to the one that is located one row higher up to screen. The same happens in Firefox with the screen being scrolled back a bit every 2-3 seconds. Same behaviour in openoffice. When I tried to go to a terminal (Alt-F2) the same occurred: a previous command appeared on the CLI.

I already tried plugging in the mouse and keyboard into another USB port without success. Unplugging these devices do not interrupt the behaviour. I also tried switching off bot screens as they provide USB ports, but to no avail. Lastly I even unplugged all USB devices (mainly hard disks) but this did not provide a solution to the problem.

Could the BIOS be responsible? But if so, why does it not occur before the LiveCD is loaded (e.g. I don't have this issue when I select the keyboard layout)? Any suggestions?

---

### Post by shakayoda on 2010-02-25
Well, now I tried Kubuntu and the problem remains. So it doesn't seem to be related to the window manager. As I added a SB x-fi card since ubuntu 9.4 I suspect it could be implicated, but I have no clue where exactly things go wrong with that piece of hardware. Anyone has an idea?

---

