---
title: "Think I broke my Computer"
date: 2008-12-23
forum: General Help
---

### Post by Sisco55 on 2008-12-23
Alright, I was trying to uninstall Ubuntu off of my computer which had a dualboot with Windows XP. I like Ubuntu, just didn't have the space to run games. I do have it on another computer though. I am not going to get into specifics, but because I deleted the Ubuntu partition containing GRUB I cannot get into Windows or do anything really because I get "ERROR 17" at start up. Now yeah, I know what I did was stupid, I did it wrong, my fault bla bla bla... Anyway, is there ANYTHING I can do? Am I going to have to replace the drive in question because frankly, I cannot afford to do that. 

The Computer is a Dell, if that makes any difference.

---

### Post by unutbu on 2008-12-23
[list]
[*]If you have a Windows CD:
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

[*]If you have an Ubuntu CD:
[http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)
[*]Alternatively, boot the Ubuntu CD (version 8.10). Open a terminal (Applications>Accessories>Terminal) and type
```
sudo lilo -M  /dev/sda mbr
```

[/list]

---

### Post by Monotoko on 2008-12-23
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

---

### Post by Sisco55 on 2008-12-23
How do I "Boot from a cd"? Yes I am a n00b... How could I set the computer to do that if I can't get into it? 

Thanks for the reply's though.

---

### Post by Monotoko on 2008-12-23
Did you not boot from a CD when you were installing Ubuntu? Just turn it on with the CD inside, it should boot from it rather than the hard-disk (the hard-disk is where your getting error 17, it will still boot from CD nicely)

---

### Post by unutbu on 2008-12-23
Go to the BIOS menu. You may have to press F2 or F10 (or some such key) to get to the BIOS menu. The particular method varies from computer to computer. Change the boot order to boot from the CD first. Some computers also have a "Temporary boot menu" (maybe reachable by pressing F12?), from which you can set the boot order for just one boot.

---

### Post by Sisco55 on 2008-12-23
If I no longer have my Ubuntu disk would it work if I downloaded another copy? 

I also don't have the windows disk.

---

### Post by unutbu on 2008-12-23
Yes, if you can burn a new Ubuntu LiveCD, it should do the job just fine.

---

### Post by Sisco55 on 2008-12-23
Thanks a ton guys, you're awesome. Will tell you if it works.

---

### Post by Tanker Bob on 2008-12-23
You can get a boot disk for Windows XP from Micro$oft [here](http://support.microsoft.com/kb/310994).

---

### Post by Sisco55 on 2008-12-26
Put my Ubuntu disc in and nothing different happened. How do I make the disc bootable? I can't do it from my computer because I obviously cannot get into either Windows or Ubuntu. What do I do? 

Still does the same thing it has been doing, error 17.

---

### Post by Monotoko on 2008-12-26
Okay...how did you install ubuntu in the first place?

---

### Post by Sisco55 on 2008-12-26
I put the live cd in. Honestly cannot remember how I set it up, this was some months ago.

---

### Post by Monotoko on 2008-12-26
And putting the LiveCD in isnt working this time?

---

### Post by Sisco55 on 2008-12-26
Nope, just does the same thing, says error 17. Maybe I burned it to the cd incorrectly?

---

### Post by Monotoko on 2008-12-26
Maybe, try again at a slower speed.
Also check your BIOS (press an F key at startup, it could be F9 or F12, but it should tell you, if not just try them all until you get to something that looks like a settings menu) check the boot order and make sure it is booting from disk before the hard-drive

---

### Post by Sisco55 on 2008-12-26
I'll try that, because it wasn't the boot sequence. That was correct.

---

### Post by Sisco55 on 2008-12-26
By the way, how fast should I set the burn speed to?

Sorry for the double post.

---

