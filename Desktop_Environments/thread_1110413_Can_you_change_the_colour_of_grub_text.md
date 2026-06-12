---
title: "Can you change the colour of grub text?"
date: 2009-03-29
forum: Desktop Environments
---

### Post by Mehashi on 2009-03-29
[COLOR=Magenta]Hi Guys[/COLOR]!

I was being bragged at by a college friend about his new system and he mentioned that his boot up text was blue. Naturally I asked him how to do this thing, but he is the kind of guy who likes to be better so would not tell me!

Anyone who has read my posts will realise I like pink and black, so I would like to know if I can change my grub text to [COLOR=Magenta]pink[/COLOR] and leave the background black?[COLOR=Black]

Thanks for any help!
[COLOR=Magenta]Domo[/COLOR]!
^_^
[/COLOR]

---

### Post by Tirk on 2009-03-29
You may just uncomment the line
**color cyan/blue white/blue**
in the /boot/grub/menu.lst file, for a try.
You need to be root (sudo) of course. For other colours just read man.
[http://www.gnu.org/software/grub/manual/html_node/color.html](http://www.gnu.org/software/grub/manual/html_node/color.html)

---

### Post by transmition on 2009-03-29
For pink, you would use magenta.

---

### Post by Mehashi on 2009-03-29
> **Tirk said:**
> You may just uncomment the line
**color cyan/blue white/blue**
in the /boot/grub/menu.lst file, for a try.
You need to be root (sudo) of course. For other colours just read man.

I was just a little worried that if I made a silly mistake I may not be able to boot to repair the damage? Although I have used ubuntu for a long time I have little experience in changing system files so I am still anxious!

Ill make a backup of menu.lst in the same directory called originalmenu.lst then try something...

[COLOR=Magenta]Thanks[/COLOR]! 
^_-

---

### Post by Tirk on 2009-03-29
Just edit only line with color and nothing should happen, even if you mess up with color beyond readable, you may just than wait to boot ubuntu default kernel and than fix it.
It is always wise to backup....:)

---

### Post by transmition on 2009-03-29
Worst case scenario you muddle things up, and have to boot into a live cd to repair the problem. Nothing difficult, all just restore the original boot file.

---

### Post by Mehashi on 2009-03-29
[COLOR=Magenta]Thanks Guys[/COLOR]!

I am now doing it, but I lack terminal skills and so far have managed to rename menu.lst to originalmenu.lst without copying so it may take me a little while! 

This is reminding me how long it has been since I have had to think using ubuntu! That is a good thing maybe?!

Thank you again!
[COLOR=Magenta]Arigato gozaimasu[/COLOR]!
^_^

---

### Post by transmition on 2009-03-29
Why are you doing it from the terminal? You could use a regular text editor like gedit, and then just run it as root.

```

sudo gedit

```

Or if you want to rename the file from within the file browser, like you normally would, use:

```

gksudo nautilus

```

Which will run the file browser with administrator privileges.

---

### Post by Mehashi on 2009-03-29
> **transmition said:**
> Why are you doing it from the terminal? You could use a regular text editor like gedit, and then just run it as root.

I did just that! Thank you again!

---

