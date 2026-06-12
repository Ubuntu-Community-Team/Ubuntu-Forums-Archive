---
title: "Ubuntu won't load - from Live CD OR Installation"
date: 2008-11-22
forum: Desktop Environments
---

### Post by Mikiupdown2 on 2008-11-22
Hello all,

I recently purchased a Viglen Contender desktop computer from my college. I wanted to use it as a small server (with a GUI, mind), so I downloaded the Ubuntu 8.10 Desktop Live CD last night.

After burning the disk image, I tried booting. The Ubuntu screen comes up, so I select language options and stuff (English, English UK keyboard, etc..) then the loading bar comes up.

Eventually, it shows the desktop background for like 10 seconds. Then the screen goes black with JUST the mouse cursor on it (the desktop background is not visible) and then just hangs like that until the computer is shut down.


I'd really appreciate if you could help me get this working. I've tried using Ubuntu in the past and loved it, but it's just unfortunate it seems to hang on this PC.

Thank you all,
From Michael.

P.S. PC specs are here: [http://www.linux-tested.com/results/viglen-contenderplus_24.html](http://www.linux-tested.com/results/viglen-contenderplus_24.html) but I have also installed an Edimax EW-7728LN wireless card in one of its PCI slots.

---

### Post by CandyKiller on 2008-11-23
My suggestion is that it was a bad burn of the CD.  Re-download the OS then follow the instructions on [this page]("https://help.ubuntu.com/community/HowToMD5SUM") on how to verify that your download was correct.  

Next, make sure that you're burning the disk at one of the slower write speeds, this will ensure that all the information is burned onto the disk correctly. 

My first burn of Linux was the same way, bad download/burn so had to do it all over again.  Hope this helps.

---

### Post by Mikiupdown2 on 2008-11-23
Thank you for your reply CandyKiller.

I've tried re-downloading and burning to a different CD - still no difference. Also eventually tried a different distro all together - no luck there either.

Set the burner as slow as it can go (4x) for all of the above cases. No difference.


I guess it's something to do with the PC / Linux. Possibly not agreeing with some hardware or having correct drivers.

---

### Post by natetheskate on 2008-11-23
when it gives your options for booting off the disc hit f6 and type all_generic_ide

it worked for me... hopefully it will do the same for you

---

### Post by Mikiupdown2 on 2008-11-24
Hi there Natetheskate, thank you for your reply.

I tried typing in "all_generic_ide" as you suggested. I heard a lot more DVD drive activity while Ubuntu was loading - but now it's the same problem.



So, anyone got any more suggestions? Cause otherwise I might have to stick Windows on it (which I really don't want - Ubuntu seems so much better for a home server).


EDIT: I'm installing Windows for now. It's not glamorous, but it works. This problem is with the Ubuntu Live CD AND disk installation so I can still try to fix the problem if anyone has any further suggestions.

---

### Post by natetheskate on 2008-11-25
Well, the thing to do now is to try Wubi. Download it from [http://www.wubi-installer.org](http://www.wubi-installer.org) and its self explanatory from there. The only thing about Wubi is that disk speed is slower than than what it would be with a normal install. That and the hibernation feature will be disabled. Wubi relies on Windows in order to work. When you want to use Ubuntu, just select it from the Windows Boot Loader. Hopefully you have better luck with this. But I am thinking it may be a hardware related issue.

---

### Post by Mikiupdown2 on 2008-11-26
I think you're right about that hardware related issue idea. This morning I recieved a proper Ubuntu 8.10 disk (which I don't even remember ordering to be honest). So I've tried that in it now and it's still the same outcome - loading cursor on a black background

I've tried Wubi as you suggested, Natetheskate, and it installs ok but on boot the bacgkround goes black and (yep you guessed it) the cursor just gets stuck on loading.

---

### Post by binbash on 2008-11-26
I had same kind of error, alternate cd install did the trick for me.

---

### Post by Mikiupdown2 on 2008-11-26
Thank you for your suggestion, Binbash. I'll let you know how it goes.

EDIT: ARGH! I used the alternative cd install. It all went ok - it finished and then the login screen came up.
"Yes, it's finally working!", I thought.

After entering my password and cautiously pressing enter, I can safely say that I am now back to square one - left only with a mouse cursor on a black background.

---

