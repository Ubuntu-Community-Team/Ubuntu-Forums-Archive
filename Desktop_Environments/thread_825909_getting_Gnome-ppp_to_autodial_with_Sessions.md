---
title: "getting Gnome-ppp to autodial with Sessions"
date: 2008-06-11
forum: Desktop Environments
---

### Post by Raval on 2008-06-11
I have Gnome-ppp startup with Sessions using the default command gnome-ppp.

You get the prompt  to connect but I want to know the command (if any) to have Gnome-ppp connect on it's own.

Anyone know the command?

---

### Post by Mark_in_Hollywood on 2008-06-11
It seems to me that you have Gnome-PPP installed, so, if I'm understanding what you want to do (and I'm not quite sure), Open:

System/Preferences/Network. 

You should see the Modem as an option. Highlight the modem and then you can nose around it it's settings/config.

---

### Post by Raval on 2008-06-11
> **Mark_in_Hollywood said:**
> It seems to me that you have Gnome-PPP installed, so, if I'm understanding what you want to do (and I'm not quite sure), Open:

System/Preferences/Network. 

You should see the Modem as an option. Highlight the modem and then you can nose around it it's settings/config.

Yes Gnome-ppp is installed.

I want a command for Gnome-ppp to auto connect when you click on the icon instead of prompting you to hit the connect button.

---

### Post by Mark_in_Hollywood on 2008-06-11
So sorry, that's beyond my understanding.

---

### Post by Super R on 2008-06-18
I would also like to know how to get gnome-ppp to auto-dial my connection.

Thanks in advance

---

### Post by Mark_in_Hollywood on 2008-06-19
Get the Gnome-ppp window in front of you, and try right clicking. Select Preferences and look around and see if that's enough.

Or go to System/Administration/Network, select Modem and Edit.

---

### Post by Super R on 2008-06-19
Thanks for the respose Mark_in_Hollywood, but this does not solve the problem. There is a "setup" button on the main window, where options are available. Unfortunately there is not an option for automatic dialing when the program opens.

I was using KPPP, and there is a command line option for opening the program and connecting to an account (kppp -C yourconnection). I have tried this and many other things in the cli for gnome-ppp to no avail.

I stopped using KPPP because I had it start when the computer boots using the above mentioned command and it would fail to start the kde libs fairly often resulting in a reboot. This was obviously counter-productive, thus gnome-ppp. Now I can't for the life of me figure out how to get it to open and auto-dial.

Any other help would be greatly appreciated.

Super R

---

### Post by Genjinaro on 2008-08-28
Any updates on this?

---

### Post by Raval on 2008-08-28
> **Genjinaro said:**
> Any updates on this?

I plan to contact the developers for the program.

---

### Post by Super R on 2008-08-28
Thanks Raval.

---

### Post by Genjinaro on 2008-08-28
Awesome Raval, hopefully they're open to apply this convinience...

---

### Post by Raval on 2008-08-31
The URL listed in Add & Remove goes nowhere [http://www.gnome-ppp.org/](http://www.gnome-ppp.org/)

I also did a search and nothing. Can someone find me the link?

Also there is another app called:
Gnome PPPon
graphical wrapper around pon and poff  
gpppon is a utility that reads the names of the configured providers from /etc/ppp/peers and calls the pon and poff scripts with the selected provider as argument.

Can anyone better explain what exactly this app does?

---

### Post by Shazaam on 2008-08-31
I think wvdial might be what you want. man wvdial in terminal or...
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
You could probably make a desktop or panel launcher for it.

---

### Post by Raval on 2008-09-01
> **Shazaam said:**
> I think wvdial might be what you want. man wvdial in terminal or...
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
You could probably make a desktop or panel launcher for it.


No it isn't, we are users of Gnome-ppp a GUI program that we configure to dial. We are looking for the feature in Gnome-ppp.

---

### Post by Beanmonster on 2009-05-17
Sorry to bump this thread, but has anybody been able to find a solution?

---

