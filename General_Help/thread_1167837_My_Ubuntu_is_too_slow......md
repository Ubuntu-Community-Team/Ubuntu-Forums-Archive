---
title: "My Ubuntu is too slow....."
date: 2009-05-23
forum: General Help
---

### Post by facelesslucifer on 2009-05-23
Hi..

How do i do my ubuntu 9.04,My Ubuntu is too slow....

I use in Dell Studio(Core 2 Duo 2.0,Memory 3GB,VGA 512)](*,)

---

### Post by DeMus on 2009-05-23
> **facelesslucifer said:**
> Hi..

How do i do my ubuntu 9.10,My Ubuntu is too slow....

I use in Dell Studio(Core 2 Duo 2.0,Memory 3GB,VGA 512)](*,)

What do you mean with : My Ubuntu is too slow...?
You also mention Ubuntu 9.10 which will arrive in October of this year. We just witnessed the arrival of 9.04 (April '09).
Which version do you use and what is so slow?
Please give some more information so people can help you.

---

### Post by facelesslucifer on 2009-05-23
Yap....
When i open folder or application,i wait too long.

So what do i do?

---

### Post by DeMus on 2009-05-23
> **facelesslucifer said:**
> Yap....
When i open folder or application,i wait too long.

So what do i do?

Sorry to kept you waiting, just got a phonecall which was important.
First:
Open a terminal (Applications - Accessories - Terminal
Type
```
top
```
This will start a program which will show you which programs run and how much CPU power they take.
Make the terminal window a bit larger, both to the right and to the bottom to show more information.
Then with your mouse select all the info on the screen (top left to right bottom) and on the keyboard type ctrl-shift-c (press ctrl key and hold it while pressing the shift key and hold it also and type the letter c, all three at the same time) This will copy the text. Then paste it here in your answer so people here on the forum can see it.
You can stop the program top with the letter q.

When you say everything runs very slow they must be something which is eating all the CPU power. Top will show us which program that is.

Speak you later.

---

### Post by Mirge on 2009-05-23
After you run top, press shift+P, that will sort by CPU usage... highest at top when you first sort.

---

### Post by DeMus on 2009-05-23
> **Mirge said:**
> After you run top, press shift+P, that will sort by CPU usage... highest at top when you first sort.

Thank you, this one I didn't know yet. Well it proves, you are never too old to learn. :p

---

### Post by Mirge on 2009-05-23
> **DeMus said:**
> Thank you, this one I didn't know yet. Well it proves, you are never too old to learn. :p

No worries :) As you may have guessed, shift+M sorts by memory usage.

---

### Post by facelesslucifer on 2009-05-23
Hi...
This is my screenshot of my CPU usage and memory

[http://www.freeimagehosting.net/image.php?d85f3d6951.png]("http://www.freeimagehosting.net/image.php?d85f3d6951.png")
[http://www.freeimagehosting.net/image.php?b03cb79042.png]("http://www.freeimagehosting.net/image.php?b03cb79042.png")
[http://www.freeimagehosting.net/image.php?7f84de4faf.png]("http://www.freeimagehosting.net/image.php?7f84de4faf.png")
[http://www.freeimagehosting.net/image.php?4af65eaa49.png]("http://www.freeimagehosting.net/image.php?4af65eaa49.png")

---

### Post by DeMus on 2009-05-24
> **facelesslucifer said:**
> Hi...
This is my screenshot of my CPU usage and memory[IMG]http://www.freeimagehosting.net/image.php?d85f3d6951.png[/IMG]

[IMG]http://www.freeimagehosting.net/image.php?b03cb79042.png[/IMG]

[IMG]http://www.freeimagehosting.net/image.php?7f84de4faf.png[/IMG]

[IMG]http://www.freeimagehosting.net/image.php?4af65eaa49.png[/IMG]

Okay, I saw your pictures and this looks good. A maximum of 10% CPU usage is not bad and could not slow down the rest of the system.
Your computer is also more than adequate so it should be capable of good performances.
You wrote in an earlier post when you open a folder or program you have to wait too long. How long is that? What do you consider to be long? Is it one second, is it five seconds, or are we talking minutes here? I know for example that opening one of the Openoffice programs takes a long time, which is something I don't like about it.

I can't find anything wrong with your computer from the info you sent us. Please let us know how long you have to wait when you do something.

---

### Post by facelesslucifer on 2009-05-24
Thanks DeMus..

Eg,I used firefox and gedit.When I change firefox to gedit <Alt+Tab>.I waited about 3sec or 4sec.
I think it should not long.

---

### Post by DeMus on 2009-05-24
> **facelesslucifer said:**
> Thanks DeMus..

Eg,I used firefox and gedit.When I change firefox to gedit <Alt+Tab>.I waited about 3sec or 4sec.
I think it should not long.

No, ALT+TAB should work instantly. It does so on my computer and I have a 100% CPU usage because of a program I am running for the university of Berkely in California.
What I did notice when looking again at your pictures is that XORG takes up most of the CPU. Could it be you don't have the right videodriver?
You wrote you have a 512MB videocard, which one is it? Which driver did you install? A wrong videodriver can slow down the system because not the videocard does all the work but the CPU does it.
Type
```
lspci |grep VGA
```
in a terminal ans place the outcome here please.
Also copy the contents of your /etx/X11/xorg.conf file in your answer.
And tell us how you installed your videodriver.
We can work from there.

---

### Post by Wiley Hunter on 2009-05-24
Sorry, I can't contribute to a productive solution.  But I can confirm that even on my OLD POS Toshiba laptop an Alt-Tab action between ANY programs happens instantaneously.  So yes, even a few seconds would seem "too long" IMHO.

Good luck with this, if it can be fixed I'm sure this is THE PLACE to get the solution. :)

Wiley

---

