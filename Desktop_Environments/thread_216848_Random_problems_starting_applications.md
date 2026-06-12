---
title: "Random problems starting applications"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Nannygoat on 2006-07-16
Hello,

I found a huge amount of similar threads without a proper solution. I'm using KDE 3.5.2 on Kubuntu 6.06 and occasionally when I start some applications they remain kind of "hanging". There is the bouncing cursor and kicker notification of the program loading but it never appears. I noticed that this happens only to apps which require root privileges to run and entering password (adept, synaptic, konqueror in al+f2 sudo mode). It's very anoying and I'll appreciate some help. Thank you in advance!

Best regards,
Dimitar

---

### Post by stanz on 2006-07-16
Yeah...KDE & Kubuntu are different- like that...
But still... There's No Techie answer here...but- I'ld log in as root, and add my 'user',
to the owner or group privy sect- of what cha wanna use.
Thinking your home/pc user...?
~ also.. in your file browser...right click for properties, to permissions;
Leaving root- as the main owner...'FILE OWNER'.
and adding 'you', into group... "FILE GROUP".

..Even using the terminal, input "gksudo", before the program. 
My Quick - On Ubuntu Site : [Wiki Search on RootSudo]("https://help.ubuntu.com/community/RootSudo")
> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.
example:: ***rm /home/*/.{ICE,X}authority***
 To start a root shell (i.e. a command window where you can run root commands)
use:: ***sudo -i***  
Read & Search Away..!!!   :KS
I'm using gnome...but it should help some???    :-k

---

