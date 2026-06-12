---
title: "i broke x"
date: 2006-07-12
forum: Desktop Environments
---

### Post by maniacmusician on 2006-07-12
I was editing the xorg.conf file to enable composite, but that didn't work out so well. When I rebooted and logged into XFCE, all I saw was a blank blue screen (the same background that gdm has by default). I knew my XFCE session was open and working because when i turned it off using the power button, the blue screen went away for a second, showing my normal desktop, and then it shut down. so next time that I rebooted, i logged into fluxbox, which was working fine. so i opened up terminal, edited /etc/x11/xorg.conf, and commented out the last 3 lines for Composite. Right there, I must have screwed up some syntax while doing it because next time i rebooted, x wouldn't load and i was stuck with a command line interface. I made a backup of xorg.conf but the problem is, I can't get into /etc/x11. it says the directory does not exist. do i have to reinstall x or is there someway to get into the directory and either edit the current file or replace it with the backup?

thanks

---

### Post by taurus on 2006-07-12
Try to reconfigure your X again with
```

sudo dpkg-reconfigure xserver-xorg

```
Next time, make a back up copy before you edit anything!!!
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

---

### Post by nmilkosky on 2006-07-12
The X in /etc/X11/ has to be capitalized. That's why it cant find it. :D I you still want to edit it to fix it, then go ahead, or do what he says. Also, doesn't it always create a "xorg.conf~" when edit xorg?

---

### Post by maniacmusician on 2006-07-12
as I said in my post, I did make a backup, i just can't access /etc/x11 (it says the directory doesnt exist). but i will try what you said

nmilkosky: ah, gotcha. thanks. what a rookie mistake lol...

also, how do you edit files in command line without x? there have to be some command line editors, right?

---

### Post by nmilkosky on 2006-07-12
Use vi <filename> vi is a bit confusing, but press insert when you start vi so you can edit, and when you are done press escape once , then press shift : then type save <filename>.

---

### Post by aysiu on 2006-07-12
I use *nano*.

```
sudo nano /etc/X11/xorg.conf
``` To delete a line--Control-K.
To save--Control-X, Y, Enter.

---

### Post by nmilkosky on 2006-07-12
I'm just used to vi, because I didn't know of any others for a while... :o Is nano easier to use than vi?

---

### Post by aysiu on 2006-07-12
*vi* has always confused me. I prefer *nano*. I can't say whether it's easier or not than *vi*. It was for me.

---

### Post by maniacmusician on 2006-07-12
thanks for the replies, aysiu and nmilkosky, i'll try both of them out. 

My X problem is fixed, i just overwrote the current file with the backup i made and everything is peachy. 

now i wish someone could help me with [this problem]("http://www.ubuntuforums.org/showthread.php?t=213239"). It's bugging the hell out of me. basically, it lets me log on to this username (on this forum)on my windows machine, but not on the xubuntu box i have in the basement. i have a third xubuntu box, and that gets on randomly...sometimes it works, sometimes it doesnt. so everytime I want help on something or want to view an attachment, I have to use windows, which is quite annoying...

---

