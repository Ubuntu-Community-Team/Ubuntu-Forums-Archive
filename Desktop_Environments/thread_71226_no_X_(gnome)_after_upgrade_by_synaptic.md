---
title: "no X (gnome) after upgrade by synaptic"
date: 2005-10-02
forum: Desktop Environments
---

### Post by flying_nomad on 2005-10-02
Gentlemen,

My Ubuntu installation asked me by 'synaptic' for an update of 64 packages who were ready to install

Just followed the suggestion (other times this was no problem)

--

Only next time i booted up there were 3 balck screens occuring and after that a message wich was (it was in dutch, so i will translate it but maybe it's not exact as it apears in the english version normaly)

```

I can't start the X-server, probably your configuration 
is damaged. Do you want to view the log from the X server

YES / NO

```

The problem is that Ubuntu did break the program here and i end up in console, so no possible (by my tiny knowledge) to view X servers log.

(by booting in recovery mode there was nothing helpfull either, 
just ended up the same way !!)

--

Below some info i gathered wich will hopefully give some insight for more knowledged people out there in what is wrong and how t resolve.

I did sudo dmesg to look at the boot.log for answers.......

--

23.06:34:704 [W] hald.c:302: Your kernel does not support capabilities; some features will not be available

--

in the logfile /var/log/Xorg.O.log the following messages poped up as some fault.

Fatal: module nvidia not found

----------------------------------------------------------------------------

Please, can anybody help me out (just hints etc), because i don't feel good about just giving up and simple reinstall everything, i want to learn but need just some help in this.

Besides that, isn't it stupid after all that a simple use of 'synaptic'and upgrade of a few programs damage you ssytem like this.

p.s. Synaptic gave one warning about mozilla 1.0.7 wich wasn't correct and skipped to upgrade

thankyou in advance

Patrick

---

### Post by Hairy_Palms on 2005-10-02
try doing sudo-reconfigure xserver-xorg

---

### Post by Zwack on 2005-10-02
Quick temporary workaround... go into recovery mode and edit /etc/X11/xorg.conf
find the line 
Load nvidia

and put a # at the front of it...   That might let it come up.  It sounds like your nvidia support was stomped by something.  You'll then need to re-install your nvidia support.

I hope that this helps,
   Z

---

### Post by rjwood on 2005-10-02
sudo apt-get install nvidia-glx

---

### Post by flying_nomad on 2005-10-02
Oke,

i'm posting this from Ubuntu again :) 

I realy don't know what happend.........

in console i did : sudo apt-get remove mozilla.firefox

*because that part gave a error message during synaptic*

and that did it, mozilla was removed and (amazingly) a lot of other stuff come in processing, it seems (i could not get a log) that all kind of things were added or renewed.

after that the console apeared and i just thought, let's try : startX and Voilla !!!

---

The only thing is, i don't have multiple desktops anymore ??!! some is still not realy healthy, have to find out what it is, but it seems (imho) that mozilla.firefox 1.0.7 was in some kind of way responsable for the mess !!!

I am looking now at some postings at this forum howe they resolved that...

---

thx for your kind help and if any of you still have some comments or suggestions you are more then welcome !!

---

### Post by Dolphin on 2005-10-02
[QUOTE=flying_nomad]Gentlemen,[/QUOTE]

That's presumptuous on so many levels. :)

---

### Post by flying_nomad on 2005-10-03
[QUOTE=Dolphin]That's presumptuous on so many levels. :)[/QUOTE]

I ment it friendly and polite, anyway english is not my native, so maybe i am missing some of the underlying gramatic use of this. sorry

---

