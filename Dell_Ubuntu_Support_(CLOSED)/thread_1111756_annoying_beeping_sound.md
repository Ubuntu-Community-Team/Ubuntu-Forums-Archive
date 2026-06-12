---
title: "annoying beeping sound"
date: 2009-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Clueless163 on 2009-03-31
How can I get rid of the annoying beeping sound when I shut the computer off or press the delete button? I tinkered with ubuntu a long time ago, but installed a new copy just recently onto my Dell XPS m1710 laptop and quite frankly annoying by this beeping noise and would like to disable it. Any idea's?

---

### Post by Agent Smith on 2009-03-31
Go to System, Preferences, Sound. Choose System Beep tab and untick Enable System Beep.

---

### Post by Clueless163 on 2009-03-31
> **Agent Smith said:**
> Go to System, Preferences, Sound. Choose System Beep tab and untick Enable System Beep.
 
I looked through menus and can't find that...if I go to applications-->settings-->setting manager-->sound I get some sound options but no system beep tab
 
 
[IMG]http://i49.photobucket.com/albums/f264/92HondaEX/0331091147.jpg[/IMG]
 
[IMG]http://i49.photobucket.com/albums/f264/92HondaEX/0331091148.jpg[/IMG]

---

### Post by Agent Smith on 2009-04-01
Im not sure where the setting is for you as i see your using xfce and not gnome. The instructions were for gnome. Sorry

---

### Post by sisco311 on 2009-04-01
blacklist the pcspkr module.

edit /etc/modprobe.d/blacklist:
```
gksu mousepad /etc/modprobe.d/blacklist
```

and add this line:
```
blacklist pcspkr
```

save the file and exit.

reboot or remove the pcspkr module:
```
sudo modprobe -r pcspkr
```

---

### Post by Clueless163 on 2009-04-01
sweet, thanks for the help

---

### Post by durand on 2009-04-02
Next time you want to show something onscreen, use the PrntScrn button at the top right of your keyboard. Or go to Applications > Accessories > Take Screenshot in ubuntu. It will be in a similar location on Xubuntu.

---

### Post by Clueless163 on 2009-04-02
> **durand said:**
> Next time you want to show something onscreen, use the PrntScrn button at the top right of your keyboard. Or go to Applications > Accessories > Take Screenshot in ubuntu. It will be in a similar location on Xubuntu.

couldn't...I wasn't allowed to connect my laptop to the network I was on at that time.

---

### Post by durand on 2009-04-03
Ok, well you could use a usb stick. I guess that it's an old computer without usb support..

---

