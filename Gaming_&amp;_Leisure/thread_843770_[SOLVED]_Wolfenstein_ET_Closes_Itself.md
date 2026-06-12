---
title: "[SOLVED] Wolfenstein ET: Closes Itself"
date: 2008-06-28
forum: Gaming &amp; Leisure
---

### Post by VexVishnu on 2008-06-28
So I just fixed my last problem, which was an Invalid GUID as shown here
[http://ubuntuforums.org/showthread.php?p=5281810#post5281810](http://ubuntuforums.org/showthread.php?p=5281810#post5281810)

When I fixed it, the game started and I could join sides and actually play.

BUT I exited the game and posted the solution and edited the original post so people would know I had already solved my problem. Now when I go to join a server and it gets to "Awaiting Gamestate" the screen turns black, flashes to my desktop and back to black a couple times and ET just disappears...

I have no idea what to do... Completely lost. HELP!

I'm gonna restart my computer and see if that helps... I'll post results.

Thanks in advance,
Vex

---

### Post by VexVishnu on 2008-06-28
So... no luck there. Restarting did nothing.

---

### Post by VexVishnu on 2008-06-28
I followed this...
[http://ubuntuforums.org/showthread.php?t=256790&page=2](http://ubuntuforums.org/showthread.php?t=256790&page=2)
and it still didn't work...

---

### Post by VexVishnu on 2008-06-28
Used this site's instructions to reinstall and it's still messing up.

[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

---

### Post by almostlinux on 2008-06-28
Try it from console and post the output when it closes out.

---

### Post by lillypop on 2008-06-30
Which version are you installing 2.55 or 2.60 ?

---

### Post by VexVishnu on 2008-06-30
Almostlinux: When I type et into the terminal I get
"bash: et: command not found"
I think it might be because I installed it as user and not under "sudo".
I just left that out because in this other thread I found with someone who had a similar problem, the person helping him try to fix it told him to so I figured it couldn't hurt anything and tried it too.
How else can I run it from the terminal?


Lillypop: I'm installing version 2.60

---

### Post by lillypop on 2008-06-30
i had 2.60 but i messed up my ubuntu and had to reinstall and i can't remember how i installed 2.60 because a friend helped me.
 So i installed 2.55 this time install was easier
I@m a noob at linux i'm afraid but i do know you need to make sure you can write to the .etwolf folder and its best if you change the install path for et to your /home directory.

---

### Post by VexVishnu on 2008-07-01
Cool, do you know how to make it so that I can write to the .etwolf folder?

I think I'm just going to Uninstall it, and Install it to the /home directory.

---

### Post by lillypop on 2008-07-02
Install with these commands just change the file name to your 2.60 one.
chmod +x et-linux-2.55.x86.run
sudo sh et-linux-2.55.x86.run

I have mine installed to /home and can write to my .etwolf folder although it is still be hidden so remeber to show hidden files.

---

### Post by VexVishnu on 2008-07-02
Alright, I'll try that.

---

### Post by lillypop on 2008-07-05
Vex did you get ET working ?

---

### Post by U&amp;T on 2010-04-15
I have same problem and wolfenstein installed to my home folder. Reinstall didnt do a thing.

---

