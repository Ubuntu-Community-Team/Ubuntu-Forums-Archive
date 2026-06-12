---
title: "Bluetooth Problems-newbie..."
date: 2009-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-03-12
Hi,
maybe some oy know that i had problem with my dell mini 9 ubuntu. Still, i found yesterday some link how to  pair Apple Wireless Bluetooth keyboard, and it was working just fine.

But today, i installed completely new version of Ubuntu 8.04 (not dell mini lpia, but full version), and i have problems with bluetooth. E.g. every time after reboot i need to pair my bluetooth mice, apple keyboard is not working....
Does anyone knows if i have to install some additional drivers or something? So this is my start for the first time with Ubuntu/Linux full version....
Thanks

---

### Post by vickoxy on 2009-03-12
Ok guys, this is the tread that i found useful:

[http://ubuntdsuforums.org/showthread.php?t=224673](http://ubuntdsuforums.org/showthread.php?t=224673)

Crucial was to my ubuntu this part:

[COLOR="DarkOliveGreen"]Enter the following stanza at the end of the file, replacing BD_ADDR with your BD_ADDR from the clipboard:

Code:

device BD_ADDR {
    name "Apple Wireless Keyboard";
    auth enable;
    encrypt enable;
}

When you're finished, save the file and close gedit.[/COLOR]

After that everything went just fine-have to read careful instructions and everything will be ok...
Hope that after restart this will be all  functional...

---

### Post by vickoxy on 2009-03-12
Ok, after restart bluetooth does not function-i need to pari my mice couple times, then remove batteries and put them again and then it is all right. 
I noticed when i in terminal type: bluetooth restart, then pop out by bluetooth icon a message: "device can be connectable". Normally that poped up (on my older dell mini 9 ubuntu) after restart, and mice and keyboard paired automaticcaly.
So, please if someone can help me...

---

### Post by vickoxy on 2009-03-12
Now the thing is-it connects randomly with bluetooth devices-sometimes after restart just fine, sometimes i have to pair keyboard and mice for several times-it pop up error window, but sometimes eventually computer connect itself to mice and keyboard. Can anyone tell me what can i do to make this devices be automatically connected? As said-with previously Ubuntu LPIA version, everything was just fine....

---

### Post by vickoxy on 2009-03-12
Sorry for my monologue:
UPDATE: Apple Wireless Keyboard and Bluetooth Mice are working if i shut down computer, and then turn it on.
BUT, if i restart/reboot it -then it doesn´t work. So, hoping to hear some suggestions...
Regards

---

