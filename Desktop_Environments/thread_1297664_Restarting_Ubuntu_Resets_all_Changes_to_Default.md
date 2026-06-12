---
title: "Restarting Ubuntu Resets all Changes to Default"
date: 2009-10-22
forum: Desktop Environments
---

### Post by Holy_Nexus on 2009-10-22
I'm completely new to all things Linux/Ubuntu. This website is included, so I'm sorry if this post is in the wrong spot.

Anyway, I just downloaded the OS to my laptop the other day, duel with my vista. Unfortunately, I can't get any of my setting to 'stick' between sessions. 

Whenever I turn off/on my computer, whatever I've changed about my panels, my wallpaper, my screen saver, etcetera gets reset to default.

What can I do to fix this?

---

### Post by ad_267 on 2009-10-22
So you're definitely installed Ubuntu, you're not running the Live CD still?

Have you removed the install CD from the CD drive?

Do you log in using your username and password when Ubuntu starts?

Oh, and Welcome to the forums!

---

### Post by Holy_Nexus on 2009-10-22
> **ad_267 said:**
> So you're definitely installed Ubuntu, you're not running the Live CD still?

Have you removed the install CD from the CD drive?

Do you log in using your username and password when Ubuntu starts?

Oh, and Welcome to the forums!

Yup. Yup. Yup. And thanks :)

When I first tried to download the OS, the computer overheated and shut down right after the step where it asked if I wanted to replace vista or run the OS alongside.

It might also be unrelated, but whenever I try to download something, I get a message like this.

> There is not enough room on the disk to save /tmp/TLe1j1b4.part.

Remove unnecessary files from the disk and try again, or try saving in a different location

---

### Post by ad_267 on 2009-10-22
Ok, but the second time it worked all the way?

Hmm it could be that the installer didn't give Ubuntu enough space. I think it gives it the minimum possible space by default which is a bit silly.

Try loading up the live CD you used for installing and then go to System - Administration - Partition Editor. If the partition used by Ubuntu is full you can shrink the Windows one a bit and stretch out the Ubuntu one. I think there's also a partition editor that comes with Windows Vista you can use to shrink the Windows partition too, although I could be wrong about that.

And if you've got any important data make sure you backup before changing partitions.

Edit: Have a look at these for more information on resizing partitions:
[http://ubuntuforums.org/showthread.php?t=1143346](http://ubuntuforums.org/showthread.php?t=1143346)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

You can't use the Vista tool for resizing Ubuntu's partition however, as it uses a different file system that Windows doesn't recognise.

---

### Post by Holy_Nexus on 2009-10-23
> **ad_267 said:**
> Hmm it could be that the installer didn't give Ubuntu enough space. I think it gives it the minimum possible space by default which is a bit silly.

Yep. That's what happened. 

I loaded up the live CD went through half of the installation process, back to the step where it asked what amount of the system I wanted divided up between the duel-OS. My former download only gave Ubuntu barely enough room to turn on.

> **ad_267 said:**
> Try loading up the live CD you used for installing and then go to System - Administration - Partition Editor. If the partition used by Ubuntu is full you can shrink the Windows one a bit and stretch out the Ubuntu one. I think there's also a partition editor that comes with Windows Vista you can use to shrink the Windows partition too, although I could be wrong about that.

I'm not at all Ubuntu savvy, so I don't know what I would switch around without destroying either OS. 

I can't take a screenshot due to the lack of room, but here's the closest I could make by typing the Partition Editor into Excel on a different computer. I don't know if it helps.

[IMG]http://img132.imageshack.us/img132/7835/keybu.png[/IMG]

What do I extend and what do I shrink?  :confused: I'm guessing TOSHIBA SYSTEM VOLUME and linux-swap? 

> **ad_267 said:**
>  Edit: Have a look at these for more information on resizing partitions:
[~link]
[~link]

You can't use the Vista tool for resizing Ubuntu's partition however, as it uses a different file system that Windows doesn't recognise.

I'm guessing I won't be able to change Vista's from within Ubuntu, either?

---

### Post by John Bean on 2009-10-23
> **Holy_Nexus said:**
> I'm guessing I won't be able to change Vista's from within Ubuntu, either?You guess wrong. Gparted will happily resize your Vista partition for you :-)

---

### Post by earthpigg on 2009-10-23
> **John Bean said:**
> You guess wrong. Gparted will happily resize your Vista partition for you :-)

1) always *always* ***always*** have a solid backup before doing ***anything*** relating to partitions.

and see #9 [here]("http://gparted.sourceforge.net/faq.php").

it's a good idea to defrag your windows partition two or three times back-to-back immediately before trying to shrink it to make room for ubuntu. you dont ***have*** to do this, but it is a good idea.

2) remember that all linux filesystems need to have at least 5% of space free to function properly. this is the price we pay for needing to [defrag]("http://en.wikipedia.org/wiki/Defrag") once a ***decade*** instead of once every month or two as with windows. this command will show you your filesystem usage:

```
df -Th
```

since your ubuntu partition is 99.9% full, it is safe to say it does not have 5% free... so it is no surprise that things aren't working well for you.

3) depending on how much RAM you have, you may want to consider increasing the size of your SWAP partition, too. 2gb is a fairly standard size. 172mb is ridiculously small.




Ubuntu's installer tries to conserve hard drive space... many (myself included) think it goes to ridiculous extremes in that effort. 2.3gb / partition and 200mb swap by default? silly as hell, and bound never to work properly for very long on typical home desktop use.

i ***personally*** recommend that everyone always ***manually*** partitions to avoid these issues, but many people would disagree with me.

---

### Post by coffeecat on 2009-10-23
> **John Bean said:**
> Gparted will happily resize your Vista partition for you :-)

Gparted might be happy, but unfortunately [Vista may very well not be]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"). :( Scroll down in that link to see the "Windows failed to start" screen that many people get. This is repairable, but you need a "proper" Microsoft Vista install DVD with the repair utility on it. The restore DVD that came with the OP's laptop (if there was one) won't do.

**Holy_Nexus**, you'd be well advised to shrink the Vista partition from within Vista. [Here are some useful tips]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") if the Vista utility won't shrink it enough for you. And then you can use Gparted to expand your Ubuntu partition.

If by chance you've already shrunk your Vista partition, made it unbootable and can't repair it, you can download a Vista recovery disc [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

