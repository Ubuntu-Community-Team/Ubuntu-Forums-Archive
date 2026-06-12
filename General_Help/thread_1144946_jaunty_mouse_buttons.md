---
title: "jaunty mouse buttons"
date: 2009-05-01
forum: General Help
---

### Post by maximalistic on 2009-05-01
Hello!
i have the logitech s510 mouse + keyboard combination, how do i get the back and forward mouse buttons working?

---

### Post by DeMus on 2009-05-01
> **maximalistic said:**
> Hello!
i have the logitech s510 mouse + keyboard combination, how do i get the back and forward mouse buttons working?

Can you find something in System - Preferences - Mouse, or do you find another program listed there or in System - Administration which is related to your mouse?

---

### Post by maximalistic on 2009-05-01
yes i have the mouse preferences but there is no really options regarding mouse buttons

---

### Post by DeMus on 2009-05-01
> **maximalistic said:**
> yes i have the mouse preferences but there is no really options regarding mouse buttons

Did you have to install a separate driver for this mouse? I just visited the Logitech site and saw Logitech (what a surpise) only has Windows drivers available.
Why companies don't want to accept there are other OS's as well?

It could be you will not be able to use the special buttons since you can not select the right function for them. Maybe somebody else has a better solution.

Good luck.

---

### Post by mgmiller on 2009-05-03
There have been many kludgy fixes for this over the years.  I understand the gnome developers have also been working on this and a fix may be available for Karmic (9.10).  In the meantime, I found this work around that doesn't seem too hard to implement.

[http://gaarai.com/2009/02/13/navigate-in-ubuntu-nautilus-using-the-mouse/](http://gaarai.com/2009/02/13/navigate-in-ubuntu-nautilus-using-the-mouse/)

---

### Post by BLTicklemonster on 2009-06-16
Thank you mgmiller, that's the easiest and most straightforward way I have seen yet to accomplish this.

---

### Post by regino on 2009-10-02
> **DeMus said:**
> Did you have to install a separate driver for this mouse? I just visited the Logitech site and saw Logitech (what a surpise) only has Windows drivers available.
Why companies don't want to accept there are other OS's as well?

It could be you will not be able to use the special buttons since you can not select the right function for them. Maybe somebody else has a better solution.

Good luck.


yeah  seem like it's easier to blame the companies than blame the ubuntu coders who think that a mouse is an optional component. There are 2 main companies that make keyboard and mouse,but the ubuntu coders haven't found a way to make them work properly yet.  I can't get my logitech mouse to work properly just by installing Ubuntu. I would need to read a lot , search, configure, compile  etc just to get the button to work ..  all the related softwares are useless for this . They get installed and i don't even see them anywhere after... WHY is there no options for back- forward buttons in that mouse config panel..  Does the makers of Ubuntu are aware that those buttons exist ?  they don't have any buttons on their mouse at work ? Do they still live in 1995  when there was no wheel and buttons on the mouse ? ,   yeah blame logitech and microsoft for not doing the job of the ubuntu coders..  Why put such a basic and rather useless mouse option panel . the button on my mouse would work without any special drivers on windows Me, XP, Vista etc..    but Ubuntu,  ho no,  to complicated to do I guess..

 I thought that Ubuntu would be at least a great choice to navigate on the web,  but it seem like even this simple task won't be possible because there is no support for buttons on mouse  unless you spend hours trying to manually compile something.

  jezz   another deleting of a ubuntu installation ,  i thought that this version would be "modern" but it seem like it's not. We should collect some money and buy a mouse with button to the ubuntu programmer.

---

### Post by mgmiller on 2009-10-03
That's a rather harsh indictment of the Ubuntu devs.  They work hard for something they give us for free.  

I can't speak about Logitech mice, I don't own any.  My decision to not use them was based on a lack of Linux compatibility with other Logitech items I had tried in the past.  But I do own multiple Microsoft mice with scroll wheels and back/forward buttons.  The scroll wheels work fine out of the box and the back and forward buttons have worked properly in Firefox for at least the last 2 years.  Getting the back/forward buttons to work in Gnome was and has been till recently a bit of a pita, but as of Ubuntu 9.10 alpha 6, they seem to work in Gnome out of the box also.  Zero configuration needed for full functionality, true plug and play.  You can't ask for more then that.

When using Ubuntu or any Linux distro, you need to do your homework on hardware compatibility.  Don't blame the devs if the interface for something, like the back forward buttons in Logitech are proprietary, and the manufacturers won't release any info to allow the devs to work with.  Reverse engineering something like this is not a trivial exercise.

The good people at Canonical have been working hard to improve mouse compatibility for a while.  Meanwhile, do your homework and buy what works.  Then send an email to the company that does not support Linux and tell them why you just equipped your office machines with a dozen Microsoft mice instead of Logitech product.

Put the blame where it belongs.....on the manufacturers.  Eventually, if they get enough flak and lost business, they will wake up.  But if you don't tell them, they never know.

---

### Post by peculiar penguin on 2009-10-03
I was able to get the tilt wheel buttons on my Logitech V220 mouse working with a simple HAL policy file defining the number of buttons it has (see [thread]("http://ubuntuforums.org/showpost.php?p=8008455&postcount=3")) - something similar may work for you.

---

### Post by sphynk on 2009-10-15
regino, how much did you pay for Ubuntu again? I think you miss the point of a community project... I just bought something called a Cyber Snipa mouse. Back and forward buttons work without configuration in Firefox and Chrome. Ubuntu can be frustrating to begin with, but once you get hold of it, it's fantastic. Hang in there and learn it, you won't be disappointed. These forums are brilliant with helping you get there too.

Does anyone know if there is any generic software to work programmable buttons on mice? This thing has extra buttons, which I'd like to use.

---

### Post by P4man on 2009-10-15
> **regino said:**
> yeah  seem like it's easier to blame the companies than blame the ubuntu coders who think that a mouse is an optional component. There are 2 main companies that make keyboard and mouse,but the ubuntu coders haven't found a way to make them work properly yet.  I can't get my logitech mouse to work properly just by installing Ubuntu. I would need to read a lot , search, configure, compile  etc just to get the button to work ..  all the related softwares are useless for this . They get installed and i don't even see them anywhere after... WHY is there no options for back- forward buttons in that mouse config panel..  Does the makers of Ubuntu are aware that those buttons exist ?  they don't have any buttons on their mouse at work ? Do they still live in 1995  when there was no wheel and buttons on the mouse ? ,   yeah blame logitech and microsoft for not doing the job of the ubuntu coders..  Why put such a basic and rather useless mouse option panel . the button on my mouse would work without any special drivers on windows Me, XP, Vista etc..    but Ubuntu,  ho no,  to complicated to do I guess..

 I thought that Ubuntu would be at least a great choice to navigate on the web,  but it seem like even this simple task won't be possible because there is no support for buttons on mouse  unless you spend hours trying to manually compile something.

  jezz   another deleting of a ubuntu installation ,  i thought that this version would be "modern" but it seem like it's not. We should collect some money and buy a mouse with button to the ubuntu programmer.

I have yet to come across a mouse that didn't work with all buttons with ubuntu. I have 3 logitech mice here, including an MX revolution, and I had to install diddly squat  to enable every button. I just assigned functions to them in system > preferences > keyboard shortcuts (admittedly, a strange name for an app where you can define mouse buttons too).  All of them (15 functions) work just fine in compiz as well, I only have to type in "button13" rather than picking them from the list as compiz config manager doesn't seem to be aware some mice have more than 9 "buttons".

By comparison, to get my mouse working properly in vista or windows 7, to be able to reassign mouse functions, I had to download 70Mb worth of bloatware. Just to reassign a mouse button.

---

