---
title: "metacity suddenly not switching to compiz on xgl logins?"
date: 2007-10-28
forum: Desktop Environments
---

### Post by etherael on 2007-10-28
Hi All,

I've been using the compiz extensions for my login for about a week now and everything has been working ok, today though when I logged out and back in, metacity 2d stayed active and I had to run compiz --replace in order to get the 3d desktop back, I'm not sure what caused this or how I should go about correctly fixing it, should metacity realise when it's running on an X server with XGL extensions and thus switch to compiz? 

I'm assuming that this is the case based on the fact that if I login remotely via nomachine, I get a simple 2d interface using metacity without issue, so has something changed that stops metacity from being aware of the XGL extensions? is this a known issue of some other type? Any assistance greatly appreciated.

Regards
Eric

---

### Post by khughitt on 2007-10-28
Hi Eric,

What graphics card do you have? What driver is shown as being used under "system" -> "preferences" -> "screens and graphics?" Also, could you please the results of running the following command in the terminal: ** aptitude show xserver-xgl | grep State**

---

### Post by etherael on 2007-10-28
under preferences the nvidia driver is selected, when I tried to set it to NV, it didn't change anything, editing xorg.conf by hand worked I assume, but weirdly enough, XGL then failed to work, like loading compiz would report the extension was not available and quit.

I switched back to nvidia by hand and then implemented compiz --replace in the session string which is my fix for now, but that's probably going to break my remote logins.

Video card is an Nvidia Go 7300

Output from the command you gave me is;

eric@phoenix:~$ aptitude show xserver-xgl |grep State
State: not installed

Thanks for your help.

---

