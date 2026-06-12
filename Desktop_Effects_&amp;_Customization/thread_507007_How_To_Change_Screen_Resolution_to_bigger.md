---
title: "How To Change Screen Resolution to bigger???"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by b3k1 on 2007-07-22
First , I have Intel Graphic 915 Controller and i know that my monitor does support 1280x1024 screen resolution... but under ubuntu the biggest resolution i can choose is 1024x768...

so... if you can tell me how can i change into bigger screen resolution?? i would appreciate it...

thx...

---

### Post by trak87 on 2007-07-22
You could run the following from the terminal (command line):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And then select higher rez's when you get to that part. Then either reboot or press Ctrl-Alt-Backspace, which will restart the X server.

---

### Post by sunny_nwho on 2007-07-22
did u try the 955resolution it can be found on the repos

---

### Post by thecomputingexpert on 2007-07-23
Hi I just tried this with the code that trak87 gave:

sudo dpkg-reconfigure -phigh xserver-xorg

and its messed up my computer, whenever i start the computer it fails to start the x server. 

It says
It is likely that it is not set up correctly.

So I get to the command area and type in the same code as above to reconfigure it only it gives me the options that were there before so I cannot uncheck the resolutions which I set, please can someone help me urgently i need to use this computer tonight

Thank you

---

### Post by b3k1 on 2007-08-01
it's still not working .... anyone.... pls help....

don't know what to do....

thx for trying help...

pls...

thank you...

---

### Post by hunternet93 on 2007-08-02
I had the same thing happen to me. I'm used to Unix so at the command prompt I typed "fsck." (Without the quotes or period.) Whenever it asked me if I wanted to fix something, I pressed "Y." After that, it booted, but didn't give me the resolution I wanted. I hope this helps.

---

### Post by raustin on 2007-08-07
When you reconfigured your xorg.conf file it willhave created a backup, goto a command line cd to /etc/X11 and cp the backup file to xorg.conf - it will be as it was before you made changes after a reboot.

Once you have your xserver as it was - open a terminal and edit /etc/X11/xorg.conf, schroll down to the "Dispaly" section and for each "Depth" add the resolution you want - the format will be obvious to you.  restart X or reload and select the res you want from the menu

---

