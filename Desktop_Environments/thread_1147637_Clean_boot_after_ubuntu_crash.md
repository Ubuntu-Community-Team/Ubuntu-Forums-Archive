---
title: "Clean boot after ubuntu crash"
date: 2009-05-03
forum: Desktop Environments
---

### Post by gabrielu on 2009-05-03
Hi,
I just installed Ubuntu 9.04 and while installing doing some packages install (from the repository list) it crashed. The problem is that when I restart I keep seeing the last scrambled screen that was when it crashed.
How can I do a clean boot, or any other way to fix this issue. Now it just doesn't boot anymore, I keep seeing that scrambled screen immediately after boot. And I get no errors.

---

### Post by khelben1979 on 2009-05-03
Okay, the more in detail you describe this the easier it will be to help you in this.

Were you able to make a successfull install of Ubuntu Jaunty before you decided to install those packages?

---

### Post by gabrielu on 2009-05-03
Yes, I have it installed for about one day now. It was working for some hours with no problem.
It worked great since the crash. I just hit the shut-down button. And now I can't boot anymore.

Does it saves the running processes on crash ? I don't understand this behavior...

---

### Post by khelben1979 on 2009-05-03
It sounds like the filesystem has been damaged. So either you try to fix the filesystem in the shape it is right now, or... a complete reinstall of the whole Linux system.

You need [the fsck tool]("http://en.wikipedia.org/wiki/Fsck") to repair the filesystem.

```
man fsck
```
for instructions on how to use the command.

---

### Post by hictio on 2009-05-03
You can issue an fsck on your system by simply booting using the "Recovery Mode" from the Grub Menu, and then selecting 'fsck'.

When the system boots, and you see the Grub Menu, press the Esc key, and then select the Recovery option form the available menu, and press Enter to use it.
Then, on the new menu that appears, choose 'fsck' and press Enter.

It will take a while.

---

### Post by gabrielu on 2009-05-04
I had done that already, and it still doesn't work, this means I have to reinstall my Linux again... :( And it was just one day old...

---

### Post by khelben1979 on 2009-05-04
> **gabrielu said:**
> I had done that already, and it still doesn't work, this means I have to reinstall my Linux again... :( And it was just one day old...

Don't turn off your computer while it's in use next time. The system needs to be closed down in a system friendly way. You need more patience.

---

### Post by gabrielu on 2009-05-04
> **khelben1979 said:**
> Don't turn off your computer while it's in use next time. The system needs to be closed down in a system friendly way. You need more patience.

So theoretical the system should never crash, I just have to wait him to recover, no reset or forced shutdown ?

---

### Post by khelben1979 on 2009-05-04
> **gabrielu said:**
> So theoretical the system should never crash, I just have to wait him to recover, no reset or forced shutdown ?

I don't know about that, but it's the best way in preventing a system crash.

---

### Post by gabrielu on 2009-05-04
Ok,
Thanks for your help.

---

### Post by gabrielu on 2009-05-10
Ok,
I took you advice, and reinstalled Ubuntu. Worked one day, and tadaa, it crashed again; and this time I had done no reset. Just shut down and next morning nothing. The weird thing is that it shows me the loading bar, and when finished, a scrambled screen showing what was last graphic on the screen (for example I had booted in Windows XP and restart, then Ubuntu, and my scrambled screen show portions of Windows XP *shuting down*).

Well I have it installed on a Dell 1501 with ATI Xpress 1150. AMD Turion 64.

I will try to share with you my xorg.0.og if it helps.

Any thaughts where I should look for the problem. 
I mention that I can login from recovery, and the filesystem reports as intact.

---

