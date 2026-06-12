---
title: "Java rage!!! Accept eula in command line window????????"
date: 2011-11-18
forum: Desktop Environments
---

### Post by Moozillaaa on 2011-11-18
(take deep breath)

How do you accept EULA in CLI window.

Highlight <ok> at the bottom of the agreement, and press 'Enter' does [SIZE=3]**NOT**[/SIZE] work.

---

### Post by docbop on 2011-11-18
Probably using curses. did you tab down to the OK button and hit return?

---

### Post by Moozillaaa on 2011-11-18
Not sure what you're asking there docbop...

I did this (from 1st post):
> ME

Highlight <ok> at the bottom of the agreement, and press 'Enter' does [SIZE=3]**NOT**[/SIZE] work. 	

Is this what you're asking?

---

### Post by Moozillaaa on 2011-11-18
That machine locked up at the CLI EULA.

Reboot would not start - recovery mode fixed X-server on 4rth try.

EULA came up in recovery, somehow 'Accepted'.

Now back at configuring Java installation.






NOT Solved (work-around)................................................

---

### Post by hansdown on 2011-11-18
Hi, Moozillaaa.

If you are trying to, install,

```
ubuntu restricted extras
```

you need to, accept the terms, and agreements, of,

mscorefonts.

Is this, where the problem starts?

---

### Post by Moozillaaa on 2011-11-18
> **hansdown said:**
> Hi, Moozillaaa.

If you are trying to, install,

```
ubuntu restricted extras
```you need to, accept the terms, and agreements, of,

mscorefonts.

Is this, where the problem starts?

Don't know where the problem starts hansdown...

***mscorefonts COULD be the problem; Java.org test page works, EXCEPT for TEXT in test box.........***

---

### Post by Moozillaaa on 2011-11-18
ed.1:
installed ttf-mscorefonts-installer (with EULA prompt)

working..............

================

Ok - found ttf-mscorefonts-installer package in Synaptic.

This is necessary for Java (or IcedTea NPR Java equivalent)???

---

### Post by Moozillaaa on 2011-11-18
I got TEXT in the JAVA.ORG test page!!!

My bank website still will not complete JAVA / scan initiating script (Windows does this properly).

This is an FF setting I believe - I get certificate warnings, although I click on 'Accept Publisher'...

Help?

---

### Post by hansdown on 2011-11-18
Good work, Moozillaaa.

You need to, 

scroll down, till you see the box, that needs to be checked.

Hope, that didn't sound weird.

---

### Post by Moozillaaa on 2011-11-18
Yes hansdown - I did check "Always run script/program from this website/publisher, but it continues popping back up.

Will resume diagnostics tomorrow - thanks there................

---

### Post by hansdown on 2011-11-18
> **Moozillaaa said:**
> Yes hansdown - I did check "Always run script/program from this website/publisher, but it continues popping back up.

Will resume diagnostics tomorrow - thanks there................

O.K., Moozillaaa.

Tomorrow, is a new day.

A fresh start, can make problems, look smaller.

I may have been mistaken.

```
ttf-mscorefonts-installer (with EULA prompt)

```

Did you successfully install this?

Sorry, if I'm misunderstanding.

---

### Post by Moozillaaa on 2011-11-18
Yes - the ttf-mscorefonts-installer has properly installed.

The Java.org function test page DOES now properly display as it should, indicating working Java application.

But at least one particular web site, the pop-ups persist.

I click to 'Always accept...', but the pop-ups persist, and the window does not load all applets necessary.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207490&d=1321630383[/IMG]

---

### Post by hansdown on 2011-11-18
That is strange.

---

### Post by dniMretsaM on 2011-11-18
Use the Tab key to highlight the <OK> "button" and then hit Enter.

---

### Post by Moozillaaa on 2011-11-21
> **dniMretsaM said:**
> Use the Tab key to highlight the <OK> "button" and then hit Enter.


Huh? Not exactly sure what you mean there mastermind...

From my first post:

> **Moozillaaa said:**
> (take deep breath)

How do you accept EULA in CLI window.

**[SIZE=3]Highlight <ok> at the bottom of the agreement, and press 'Enter' does [/SIZE][SIZE=3]NOT[/SIZE] work.**

---

### Post by typhoon_tip on 2011-11-21
Have you typed "yes" and pressed enter ?

Question should be like "Do you accept the EULA ?", it was like this in the installer when setting Java 1.4 alongside 1.6 from the .BIN file.

---

