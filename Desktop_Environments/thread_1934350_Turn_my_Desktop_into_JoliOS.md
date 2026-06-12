---
title: "Turn my Desktop into JoliOS"
date: 2012-03-02
forum: Desktop Environments
---

### Post by osarusan on 2012-03-02
I tried JoliOS on my laptop and I liked the interface so much that I want to have that on my desktop too.

However, my desktop is x64, not x86, and Joli is really only meant for lightweight systems.

Is there a way that I can convert my regular Ubuntu desktop into something that pretty much works like the JoliOS UI, but without losing functionality?

---

### Post by DevilishDB on 2013-01-04
Hi, I'm a user of JoliOS, and I've used numerous other Linuxes before too such as Ubuntu and Fedora.
First thing is that actually JoliOS is a full-featured Ubuntu 10.04 desktop. The only difference is how it's config'd by default (and a few extra programs). But you said it won't work on your desktop and you don't wanna install it anyway. Here's how to get it anyway (assuming you use 12.04 LTS or 12.10):
1. Go on the software center and search 'Gnome' (click "show technical packadges" at the bottom-left)
2. Install 'Gnome Desktop Environment' (or similar)
3. Log-off and next to your name you'll see a small version of the Ubuntu logo. Click it and choose "GNOME Classic"
4. Log on as usual. You'll see the desktop looks very different, but this is the DE (desktop interface) that JoliOS uses, as Ubuntu used to use it before it switched to Unity (the default desktop)
5. Get Google Chrome or Ubuntu Chromium
6. Go to the web store and search "user agent", then click on "Extensions"
7. Install the first result
8. Right-click its icon and select "Options"
9. Type into the first box:
JoliOS
Second:
Mozilla/5.0 (X11; Jolicloud Linux i686) AppleWebKit/537.6 (KHTML, like Gecko) Joli OS/1.2 Chromium/23.0.1240.0 Chrome/23.0.1240.0 Safari/537.6
Third:
Chrome
Append?:
**Replace**
Fourth:
JOS
Then click "Add".
10. Close the tab and left-click the icon. Click on "Chrome" and then select "JoliOS"
11. Goto my.jolicloud.com - once signed-in you should see the extra icons, but they won't work
12. Goto here: [https://github.com/jolicloud/jolicloud-daemon](https://github.com/jolicloud/jolicloud-daemon) and download the folder as a zip
13. Extract it somewhere and run "setup.py". Select "run in terminal" if it asks
14. Logoff and log back on again once the setup has done. Open Chrom e/ium and goto my.jolicloud.com again
15. Hopefully it should let you do stuff. Unfortuanately I don't think you can get the webpage desktop, but there's not much difference on chrom e/ium

BTW I have not tried this and it is very unlikely to work, but it might do. If it doesn't work, you can just go back to using Ubuntu normally (switch back to Ubuntu default desktop the way you changed it). It might by chance work, but most stuff I think of doesn't work.

---

### Post by sudodus on 2013-01-04
> **osarusan said:**
> I
However, my desktop is x64, not x86, and Joli is really only meant for lightweight systems.

It should work to run an x86 (32-bit) system on an x64 (64-bit) system, but not the other way around. You might not be able to use all the RA memory as efficiently if you have 4 GB or more, but most of the time you won't need it. I have an old CD with Joli OS version 2.1, and I'm testing it in my workstation with 2x2 xeon CPUs and 4GB RAM. It recognizes all four cpus and can use 3.5 GB of RAM.

So try it!. Run Jolicloud live from the CD/DVD/USB drive and see if you like it.

---

### Post by grahammechanical on 2013-01-04
> Joli is really only meant for lightweight systems.

That statement would be accurate if you remove the word "only." Something that works very well on a lightweight system will work extremely well on a higher specification system.

Xubuntu and Lubuntu are more lightweight (as regards hardware specifications) than Ubuntu but I have installed both my system that runs Ubuntu extremely well.

Regards.

---

### Post by houseworkshy on 2013-01-04
According to this
 [https://en.wikipedia.org/wiki/Joli_OS](https://en.wikipedia.org/wiki/Joli_OS) 
Joli_OS is based on Ubuntu 10.04 and the support for 10.04 runs out in April, usually 'based ons'" depend on what they were based on for update and security fix support, if it's the same with Joli you would soon have to replace it unless they do another based on something more recent.
There seem to be rather a lot aimed at netbooks it may be worth looking at some of the others 
[https://en.wikipedia.org/wiki/Comparison_of_netbook-oriented_Linux_distributions](https://en.wikipedia.org/wiki/Comparison_of_netbook-oriented_Linux_distributions)
The other thing worth looking at is all the gdms available which are happy sitting on top of Ubuntu.
[http://en.wikipedia.org/wiki/Desktop_manager](http://en.wikipedia.org/wiki/Desktop_manager)
Some of them are very customisable so you could create a Joli experiance with something which has a lot of support left.
Not an answer I know but some ideas and a caution.

---

