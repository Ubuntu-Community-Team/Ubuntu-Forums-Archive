---
title: "suspend hangs"
date: 2009-04-14
forum: General Help
---

### Post by l0ijoat on 2009-04-14
hey, im having a problem with my laptop. im running intrepid on a dual boot, and suspend used to work, but recently it just hangs and won't suspend. it just brings me to a black screen with a white square or box in the top left corner. i'm forced to turn the computer off manually and then back on again.
any help would be much appreciated! i really need the suspend feature for my laptop.
thanks,
hart

---

### Post by ostrm on 2009-04-14
Could you maybe give more details? 
Any proprietary drivers? Do you try to suspend through pm or through acpi?
Have you tried to suspend only from console, stopping X and removing all unneeded modules?

---

### Post by l0ijoat on 2009-04-14
thanks for the reply. i'm really new to ubuntu, so i can't really answer you very well. could you explain how i can find what drivers i have or if i've been using acpi or pm. i've tried to suspend from the console using sudo pm-suspend which gave me the same result. how can i stop X and remove unneeded modules?
thanks for your patience!
hart

---

### Post by l0ijoat on 2009-04-16
bump!

---

### Post by Paddy Landau on 2009-04-19
I have the same problem.

I looked at this thread:
[http://ubuntuforums.org/showthread.php?t=971814](http://ubuntuforums.org/showthread.php?t=971814)
but it didn't help me.

To answer ostrm's questions:

> **ostrm said:**
> Any proprietary drivers?
No, unless you count the wireless, which ndiswrapper runs.

> **ostrm said:**
> Do you try to suspend through pm or through acpi?
Two ways: When letting Power Management do it (after leaving the computer alone for a while), or explicitly choosing Shutdown -> Suspend.

> **ostrm said:**
>  Have you tried to suspend only from console, stopping X and removing all unneeded modules?
I don't know how to remove uneeded modules (or indeed how to identify them).

I restarted, used the "recovery mode" and chose "Drop to root shell prompt". I typed the command "suspend" and again the computer hung.

Edit: This is on a computer using Intrepid 8.10.

---

### Post by waxwing_user on 2009-04-21
Same problem here except in my case, the screen blanks out and then I get lines of code on the screen, then it hangs.  I have to press ctrl-alt-delete to restart.  It happens when I run ndiswrapper, but works otherwise.

Any advice out there?   Thanks

---

### Post by Paddy Landau on 2009-04-21
> **waxwing_user said:**
> It happens when I run ndiswrapper, but works otherwise.
I think you have something there! I disabled ndiswrapper and found that I had the same result as you; it works when ndiswrapper (or, rather, the wireless driver) is disabled.

I've also [started a thread]("http://ubuntuforums.org/showthread.php?t=1131084") in the Absolute Beginners area in the hope that someone knowledgeable will see it.

---

### Post by waxwing_user on 2009-04-21
I've just started something new.  According to [https://help.ubuntu.com/community/NetworkManager/]("https://help.ubuntu.com/community/NetworkManager/") two files must be created to handle the suspend problem.  I'm now trying to figure out how to make them executable as it says to do.  These are shell (.sh) files.  I haven't seen any indication of how to do that from gedit.  Any ideas here?

-Andrew

---

### Post by Paddy Landau on 2009-04-21
> **waxwing_user said:**
> I've just started something new.  According to [https://help.ubuntu.com/community/NetworkManager/](https://help.ubuntu.com/community/NetworkManager/) two files must be created to handle the suspend problem.  I'm now trying to figure out how to make them executable as it says to do.  These are shell (.sh) files.  I haven't seen any indication of how to do that from gedit.  Any ideas here?
I saw that on [the other thread]("http://ubuntuforums.org/showthread.php?t=1131084"). Unfortunately, it didn't work for me.

To answer your question, start terminal (Accessories -> Terminal) and enter the following commands:
```
sudo chmod +x /etc/acpi/suspend.d/07-network-manager.sh
sudo chmod +x /etc/acpi/resume.d/63-network-manager.sh
```

---

### Post by Paddy Landau on 2009-04-21
I've got the answer, at least if ndiswrapper is the problem, thanks to [unutbu]("http://ubuntuforums.org/member.php?u=518895").

See the thread:
[http://ubuntuforums.org/showthread.php?t=1131084](http://ubuntuforums.org/showthread.php?t=1131084)

---

### Post by waxwing_user on 2009-04-21
I checked the same file as unutbu (a good link thank you) and found these lines in my file:

> /usr/lib/pm-utils/functions: line 200: 10781 Segmentation fault      modprobe -r $1
# could not unload 'ndiswrapper', usage count was 0


That seems to mean that ndiswrapper is not being suspended like the others.  Is there no way to make that happen other than manually?  I went to the source file that directs the suspension (usr/lib/pm-utils) and found that one for shutting down **ndiswrapper** does not exist.  Shouldn't there be one or is the script for **10Networkmanager** supposed to take care of that?  Seems to me that something could be scripted to shut down ndiswrapper.  I will work with what I've found here.  Thanks for all the advice.

---

### Post by Paddy Landau on 2009-04-22
> **waxwing_user said:**
> ... Is there no way to make that happen other than manually?  I went to the source file that directs the suspension (usr/lib/pm-utils) and found that one for shutting down **ndiswrapper** does not exist...
Go to [this post]("http://ubuntuforums.org/showthread.php?p=7115963#post7115963") and see my reply.

---

