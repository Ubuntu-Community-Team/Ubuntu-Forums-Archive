---
title: "Unable to install runescape on Ubuntu 16.04"
date: 2016-05-08
forum: Gaming &amp; Leisure
---

### Post by isaiah-courtney96 on 2016-05-08
Well it took them 15 years, but Jagex has made a native linux client finally! I'm not able to install it though, I've posted on the game site's forums, but maybe someone here can help me. I get this error message when I try installing it.

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
runescape-launcher : Depends: libglew1.10 (>= 1.10.0-3) but it is not installable
E: Unable to correct problems, you have held broken packages."

Doesn't [FONT=arial]libglew1.10 have something to do with graphics? I'm using some generic intel hd (it doesn't even have a number) until my graphics card comes in the mail.[/FONT]

---

### Post by MikeCyber on 2016-05-09
libglew is a one click install with synaptic.

---

### Post by isaiah-courtney96 on 2016-05-09
How do I install it?

---

### Post by MikeCyber on 2016-05-09
install synaptic with the softwaremanager, in synaptic search for libglew, click install

Personally I have no clue why synaptic and softwaremanager are not merged...

---

### Post by Atitudes on 2016-06-29
Hi  Same error message here :(     

The solution mentioned in Jagex forum of removing libglew1.13 and manually install libglew1.10 made me end-up with a broken unity-desktop and consequently, a broken system.   I completely admit that I didn't know what I was doing and perhaps a simple solution could have solved the problem since I still had access to the terminal and virtual console. As I'm not an expert with Linux (but love it for years) I re-installed 16.04 from scratch. Fortunately, I did learn some things over the years and my /Home folder is in another partition :)      

Do you have any update about a potential solution for this issue?   
Probably an update will be made for the installer or I could simply install 14.04 alongside with 16.04 but I really prefer the performance of Xenial.      

Thank you in advance

---

### Post by acopulcogold on 2016-08-15
Libglew1.10 is actually not even force-able through Synaptic, as far as I've seen at least. I think it has to be back-ported manually via terminal.

---

