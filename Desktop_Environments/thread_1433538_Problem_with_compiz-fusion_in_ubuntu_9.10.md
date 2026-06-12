---
title: "Problem with compiz-fusion in ubuntu 9.10"
date: 2010-03-19
forum: Desktop Environments
---

### Post by jeremy28 on 2010-03-19
Hi all

I'm using ubuntu 9.10;

I wanna add "compiz-fusion" effects to it, but I've not arrived yet!

I decided to "Complete-Remove" all packages related to "compiz" in synaptic and then installed all of them again
such the below image:
_[IMG]http://www.theimghost.com/view/720Screenshot_2.jpg[/IMG]_

But now I can't select the Extra or Custom option in the "System> Appearance> Visual effects" part and I face this
message:
[IMG]http://www.theimghost.com/view/4441.jpg[/IMG]

I think this is because once I removed "completely" the related component, so the appropriate driver isn't found!

I run "glxinfo | grep -i direct" command and the result was as below:
```
~$ glxinfo | grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missin
```My Graphics Card is "Intel GMA 950";

I've run "sudo apt-get install xserver-xorg-video-intel" in terminal to install the related drivers and the result was as below:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libalut0 libhildon-1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```But the problem isn't resolved yet!

What's the solution?

I think the problem is because I currently don't have 3D enabled drivers!

How and where should I install my appropriate drivers from?

Help me please...
Thanks in advance.

---

### Post by ajgreeny on 2010-03-19
First in a terminal run glxinfo to see if you get the output with something like this at the top:-
```
:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

```
The last line shown is the important part.  If it says No at the end, the lack of 3D is your problem, but I think the 950 should be OK for compiz, if I remember correctly.

You could also download the compiz-check script which double checks if your hardware is capable of running compiz, and gives clues about what is missing if it can't.  Compiz-check can be downloaded from Forlong's website here.  It is a very good place to find lots of info on compiz, along with this script file and another called compiz-switch, the latter of which I use all the time when I need to turn of compiz, or turn it back on: it's incredibly useful!
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

