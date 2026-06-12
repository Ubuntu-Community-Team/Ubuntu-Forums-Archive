---
title: "Shell script won't start in Gnome"
date: 2006-01-21
forum: Desktop Environments
---

### Post by mark_g on 2006-01-21
I wrote a shell script that I use to set up my wireless network. It needs to be run with sudo and it works perfectly in the console.
I've tried adding it as a regular startup script, but that doesn't work, so I have now added it as a Gnome startup script, but that doesn't work either.

Also, when I open it in gnome, it doesn't do anything.
What am I doing wrong?

---

### Post by f76 on 2006-01-21
could you paste the commands you are using?

---

### Post by mark_g on 2006-01-21
This is the script I use:

#!/bin/bash
essid='myessid'
ifconfig eth1 up
iwconfig eth1 essid $essid
echo "Setting WEP-key..."
iwconfig eth1 key 'mykey'
echo "Acquiring an ip-addres from the DHCP-server..."
dhclient
echo "Setting loopback..."
ifconfig lo 127.0.0.1

Works perfectly when I execute it in a terminal window by typing:
sudo ./myscript

but double-clicking it in Gnome does nothing. Adding the directory it's in to the PATH variable didn't solve it either.

---

### Post by f76 on 2006-01-21
did you 
sudo chmod +755 myscript

chmod to make a file executable. Hope it helps.. in that case it must be the first time that a have an answer on this site instead of a question :p

---

### Post by mark_g on 2006-01-21
Yes, I have the permissions I need.

---

### Post by 23meg on 2006-01-21
[QUOTE=mark_g] 
I've tried adding it as a regular startup script, but that doesn't work,[/QUOTE]
To where did you add it and how?

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=mark_g]This is the script I use:

#!/bin/bash
essid='myessid'
ifconfig eth1 up
iwconfig eth1 essid $essid
echo "Setting WEP-key..."
iwconfig eth1 key 'mykey'
echo "Acquiring an ip-addres from the DHCP-server..."
dhclient
echo "Setting loopback..."
ifconfig lo 127.0.0.1

Works perfectly when I execute it in a terminal window by typing:
./myscript

but double-clicking it in Gnome does nothing. Adding the directory it's in to the PATH variable didn't solve it either.[/QUOTE]

You said it needed to run with sudo, but I don't see any sudo commands?

---

### Post by yoyoned on 2006-01-21
The problem is that gnome can't sudo for you.  Research how to start the script at boot up.

---

### Post by mark_g on 2006-01-21
Sorry. I made a typo, I always type:

> sudo ./myscript

to start it in the console.
I put the script in /etc/init.d and did 

> update-rc.d myscript defaults

Doesn't do anything. Oddly enough, I can't start any shellscript in Gnome, not just this one.

---

### Post by cwaldbieser on 2006-01-21
[QUOTE=mark_g]Sorry. I made a typo, I always type:



to start it in the console.
I put the script in /etc/init.d and did 



Doesn't do anything. Oddly enough, I can't start any shellscript in Gnome, not just this one.[/QUOTE]
What experiment(s) did you conduct/observe to lead to this conclusion.  A detailed explanation from your end will help with the analyisis of the problem.

---

### Post by mark_g on 2006-01-23
Well, I created a script that should create a text file:
> 
#!/bin/bash
echo "test" > testfile

and I can't start it in Gnome. Works perfectly when started from the console, though.

I used to get a dialog window asking me if I wanted to open the file with a text editor or if I wanted to run it, but I don't get that anymore when I double-click on the scriptfile in Gnome. It just doesn't do anything.

---

### Post by cwaldbieser on 2006-01-24
[QUOTE=mark_g]Well, I created a script that should create a text file:


and I can't start it in Gnome. Works perfectly when started from the console, though.

I used to get a dialog window asking me if I wanted to open the file with a text editor or if I wanted to run it, but I don't get that anymore when I double-click on the scriptfile in Gnome. It just doesn't do anything.[/QUOTE]
Hmm, try opening Nautilus and go to Edit -> Preferences -> Behavior Tab -> Executable Text Files section, and check "Ask Each Time".

---

### Post by mark_g on 2006-01-25
Thanks for the tip, but doesn't solve it. I quickly get to see the terminal window, but it disappears just as quick without executing the script. Must be a Gnome bug or something then.

---

### Post by dcstar on 2006-01-25
[QUOTE=mark_g]Thanks for the tip, but doesn't solve it. I quickly get to see the terminal window, but it disappears just as quick without executing the script. Must be a Gnome bug or something then.[/QUOTE]
Try putting in explicit paths to the binaries (use "whereis" to find them).

In a user terminal the search paths default to your profile settings, in Gnome I don't know where they are supposed to be found.

---

### Post by mark_g on 2006-01-25
Ok, I solved it.
You can let gnome sudo for you by using 

> /usr/bin/gksudo

and the absolute path of the script you'd like to start. To stop the terminal window from disappearing after executing, I just add the sleep command to the end of the script, so I have time to read the feedback.

---

