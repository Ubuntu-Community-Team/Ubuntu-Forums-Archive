---
title: "firefox won't open"
date: 2006-08-05
forum: Desktop Environments
---

### Post by frup on 2006-08-05
i am having a problem where firefox wont open... this includes the firefox i installed in opt/ and the default... i have tried sudo firefox sudo firefox %u and the non-sudo

all output run-mozilla.sh: Cannot execute /opt/firefox/firefox-bin-bin

i tried renaming firefox-bin to firefox-bin-bin and this just added an extra -bin to the message... all files firefox, firefox-bin and the .sh file have xxx 

i did a kernel update lastnight to .26 i think from .25 (this came in as an update as usual in synaptic or whatever) vmware stopped working but by running vmware-config.pl i was able to get it working again and that is how i am posting from my new edgy install :)

i'm guessing the kernel update is the problem, i havent noticed any other apps broken... i am thinking tht i should install another browser from synaptic and try use that to re-download the latest firefox .tar.gz ??? this is the only time ever i have seen a good reason for having IE built in to windows lol.. although in this situation the whole of windows would have gone bang ;)

any ideas/suggestions/help?

---

### Post by frup on 2006-08-05
All i can think of doing is a complete re-install which i dont want to do.

---

### Post by frup on 2006-08-06
i will bump this thread untill someone can help me... untill then i will have to unefficiently run firefox from VMware...

---

### Post by bbfuller on 2006-08-06
Although I'm fairly new to Ubuntu, I've been running Linux since 1998.

I had the kernel update you mentioned yesterday and my firefox still runs perfectly so I don't think it's that.

My firefox is located in /usr/local/fireox32 as I'm running 64bit here. The command /usr/local/firefox32/firefox-bin fails as does yours, executing /usr/local/firefox32/firefox works though.

I'd try renaming your firefox-bin to what it should be and then issue the command /opt/firefox/firefox and see what happens.

It seems usual for Ubuntu to install things in /usr and not /opt. /opt is completely empty on my installation. However, I've tried an install into opt  just out of curiousity but it works just the same.

---

### Post by frup on 2006-08-06
the opt installation is the tar.gz from mozilla.org which i installed myself when ubuntu's firefox was at 1.07 and mozilla had 1.5.03 or something... firefox %u is ubuntus default firefox i believe... in opt/firefox/ there is firefox-bin and firefox. 

If it is not the kernel it is something that got updated in the same update... i now have to run vmware-coonfig.pl every reboot just to open that too... and i have to open that to access the internet now. 

I'm having so many wierd things happen across my system right now that i just dont have the energy to explore and fix it all myself. In my edgy Vmware half the time its boot screws up and hangs on kernel.log or something (this is all ugly like a test screen on tv which i guess is on purpose) edgy's resolution is stuck at 1024*768 even though i edited xorg.conf the vmware problem and firefox...plus lots of things i think are hardeware related... i'm very busy right now and i'm the most frustrated with my computer in the year i have been using linux

---

### Post by frup on 2006-08-09
any help yet?... its still not working :(

---

