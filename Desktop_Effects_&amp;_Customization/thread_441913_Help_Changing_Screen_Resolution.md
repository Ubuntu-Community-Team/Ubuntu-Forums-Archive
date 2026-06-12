---
title: "Help Changing Screen Resolution"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by bdk9246 on 2007-05-13
Hey, need help changing the screen resolution up in Feisty (running P4 2.4ghz + ATI Radeon 9800XT with restricted driver enabled). 
No option to go above 1280x800, but my monitor is 1680x1050. how can i make it higher?

cheers in advance.

---

### Post by Kobalt on 2007-05-13
Open up a Terminal and enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hiting the spacebar then validate with Enter. Restart X with Ctrl+Alt+Backspace, and you're done.

---

### Post by bdk9246 on 2007-05-13
n00b warning. 
sorry, i dont understand. 
i have run the terminal and have come up with "dpgk need an action option" and a list of options i know nothing about. 
can you please walk me thru the process in more detail? 
cheers

---

### Post by Kobalt on 2007-05-13
You just need to enter the command line exactly, and entirely, as I wrote it (copy/paste it to make sure) and you should be asked your password, then be taken to the resolution selection.

PS: the Terminal can be open from Applications > Accessories > Terminal

---

### Post by bdk9246 on 2007-05-13
ok. in more trouble now.
it asked for which driver to use, i selected fglrx 
doing that reduced the resolution to 1024x768 with no higher option.
thanks for the help, any idea what i do from here?

---

### Post by bdk9246 on 2007-05-13
Hey. have it figured out now. all working fine. 
thank you for the help

---

### Post by heimo on 2007-05-13
> **bdk9246 said:**
> Hey. have it figured out now. all working fine. 
thank you for the help

It'd benefit forums and community if you can share your solution with us. Thank you.

---

### Post by bdk9246 on 2007-05-13
> **Kobalt said:**
> Open up a Terminal and enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hiting the spacebar then validate with Enter. Restart X with Ctrl+Alt+Backspace, and you're done.

The instructions were correct (props to Kobalt), except it is not particularly apparent when to hit spacebar & enter when doing this for the first time, as i was. 

An explanation for others who are confused would be that,first you will be prompted to select which driver, after selecting the apparent driver (mine was fglrx)  the selections for resolution are like a check box and hitting spacebar toggles on/off. I was bumped down to 1024x768 because i misunderstood how the options were toggled.
i hope this helps anyone else

---

