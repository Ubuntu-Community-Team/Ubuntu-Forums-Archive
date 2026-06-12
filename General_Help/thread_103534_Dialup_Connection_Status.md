---
title: "Dialup Connection Status"
date: 2005-12-14
forum: General Help
---

### Post by Hygelac on 2005-12-14
Does Ubuntu come with a program to monitor dialup internet connections?  I used 'pppconfig' to configure a linmodem connection, and I use the commands 'pon' to connect and 'poff' to disconnect.  So, I'm wondering if there is a program I can use to monitor the status of this connection.

---

### Post by megrim on 2005-12-14
you can use the command " ifconfig " to get some informations for your connection. moreover if you go applications>system tools>network tools you will see the same as with the previous method.

---

### Post by Hygelac on 2005-12-15
Thanks, those programs have most of what I was looking for (mainly bytes sent/received), but I don't see any indicator of 'connection speed'.  Is there a place to view that somewhere?

---

### Post by mikeymouse on 2005-12-15
gkrellm  will tell you what you want to know.. 
 Hope this helps..
 mikeymouse

---

### Post by Hygelac on 2005-12-15
Thanks.  I've got gkrellm and now it's working beautifully.  :mrgreen:

---

### Post by towsonu2003 on 2005-12-15
I use conky to see what my dial up is doing, with a graphic and detailed speeds etc... ```
sudo apt-get update
sudo apt-get install conky
man conky
``` You will need to play around with the configuration file ~/.conkyrc a lot though (but it's simple :) )
[http://conky.sourceforge.net/](http://conky.sourceforge.net/) for screenshots and more reading.

---

### Post by Hygelac on 2005-12-16
Conky?  Alright, I'll have to take a look at that one too...

Thanks for all the suggestions!  \\:D/

---

