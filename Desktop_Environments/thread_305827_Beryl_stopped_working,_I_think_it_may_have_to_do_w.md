---
title: "Beryl stopped working, I think it may have to do with mono..."
date: 2006-11-24
forum: Desktop Environments
---

### Post by skelooth on 2006-11-24
Really quick history: 

I have an Nvidia 7950gt and wanted to try beryl, so I followed the guide in the wiki. Basically add the repos then apt-get the packages and run beryl-manager.

Well... that worked and worked great.

My friend recently ported and added to a game we had written a while back to C# but I couldn't run it because the mono in the repositories wasn't new enough. So I apt-get autoremoved mono and installed mono 1.2 to /opt/ right from the official site. Then I deleted the link in bin with sudo rm /usr/bin/mono

Well, all was well and fine... until I went to restart my box and it told me that my x config file was no good. I tried restoring my back up config w/ just the nvidia drivers but it didn't help, nor did replacing it with my original vga configuration and running nvidia-xconfig... so I had to recompile and reinstall the driver.

Now forward to the present, I'd really like to have beryl back on my desktop. Installing it goes fine, I follow the instructions from the wiki guide. But when I type in beryl-manager the screen locks up and I have to ctrl-alt-backspace out of it.

Sometimes it will lock up after spitting out errors, sorry i can't copy and paste them... BUT..... 

it complains about mono 1.2.1 not having version information for libpng12.so.0

I tried using synaptic to remove everything beryl related and reinstalled, no go. I tried sudo apt-get install mono and mono-runtime but... it doesn't seem to actually be installing it? (It does not add ANYTHING executable named just "mono" anywhere on my system, even after deleting my 1.2.1 installation).

any suggestions?

---

### Post by skelooth on 2006-11-24
bump :) 

Anyone? Would this question be better suited to a different board?

---

### Post by skelooth on 2006-11-24
No one has any ideas huh? :( I'll try asking on the programming board. Maybe they can better help with the mono issue.

---

### Post by skelooth on 2006-11-24
Problem fixed. Apparently it didn't have to do with mono, rather it had to do with the new kernel. Apparently it's becoming a somewhat common problem. The way to get Beryl to work again is to start it while in an xgl session, it magically no longer works with aiglx

Edit: Some food for thought. Beryl with the original aixgl configuration used approximately 2% of my processor resources at any given time. With xgl it spikes anywhere between 5 and 20% (running intel core2 duo 6400 and 7950gt gpu)

---

