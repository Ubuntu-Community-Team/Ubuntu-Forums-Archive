---
title: "Look at this"
date: 2007-09-08
forum: Desktop Effects &amp; Customization
---

### Post by ortwein on 2007-09-08
bonehead@bonehead-desktop:~$ [COLOR="Red"]glxinfo[/COLOR]
name of display: :0.0
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17
bonehead@bonehead-desktop:~$ 


I have an ATI 9250 video card installed, and would like to get it running up to par.  I've tried 5 different guides on here and have yet to find one that will let me run compiz fusion.  I'm pretty sure the problem is with my ATI card...but I also think the Intel integrated graphics on my motherboard might be causing some trouble too.

What do you think?  How can I get GLX to work? Any suggestions?

---

### Post by banewman on 2007-09-08
You can only have one running at a time so disable the onboard graphics in the bios. Can you get into the bios?

---

### Post by ortwein on 2007-09-08
Oh...so i need to disable it in the bios, eh?  

I should be able to...

I'll give it a shot and let you know in a couple of minutes.

---

### Post by banewman on 2007-09-08
When you start the computer there is a screen that flashes up for 4 or 5 secs and somewhere on it it says press del to enter setup - or F1 or something - that takes you into the bios (bios means Basic Input Output System). Only make one change then save and exit. The comp will reboot with the change you made. (Took me five goes the first time to find and read what key I had to press!)

---

### Post by Mongo5000 on 2007-09-08
I hear ya banewman, especially some asus mobo's that have that splash screen during bootup.

---

### Post by ortwein on 2007-09-08
All right, no luck in the bios.

None of the work-around posts for ATI 92XX video cards I've found here and elsewhere work for some reason.

Here is where my system stands currently:

 1 - I do not have the [COLOR="DarkGreen"]fglrx[/COLOR] drivers installed...I'm running the generic drivers that come with ubuntu feisty.

2 - I use a Radeon ATI 9250 pro graphics card (they have issues)...BUT my Dell came with Intel integrated graphics.  <------- Could this be an issue?  I've tried disabling them in the bios, but the only options available are [COLOR="DarkGreen"]"Auto"[/COLOR] and[COLOR="DarkGreen"] "Onboard"[/COLOR]--[COLOR="DarkGreen"]no delete command.[/COLOR]

Here are some responses to commands:

[COLOR="Red"]lspci[/COLOR]

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

[COLOR="Red"]glxinfo | grep vendor[/COLOR]

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17

[COLOR="Red"]System >> Administration >> Restricted Drivers Manager[/COLOR]
 
It tells me "[COLOR="DarkOliveGreen"]Your hardware does not need any restricted drivers[/COLOR]" 

[COLOR="Red"]glxinfo | egrep 'OpenGL|direct'[/COLOR]

knucklhead@knucklhead-desktop:~$ glxinfo | egrep 'OpenGL|direct'
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17
knucklhead@knucklhead-desktop:~$ 

[COLOR="Magenta"]If you can think of any other terminal commands that might shed some light on my situation, let me know.  Otherwise, I don't know what to do.[/COLOR]

---

### Post by banewman on 2007-09-09
I don't use ATI cards myself but this program is often recommended :
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). :lolflag:

---

