---
title: "Direct Rendering on an NVIDIA 8800 GTS. Is it possible?"
date: 2009-03-22
forum: General Help
---

### Post by Broadlore on 2009-03-22
Hello everybody.

I recently installed Ubuntu. I'm a complete newcomer to Linux of any kind, so forgive me if this solution seems somewhat obvious to anyone. 
To be frank, my system runs very slow. When i scroll in firefox, type in twitter boxes etc it seems very sluggish. Moving windows around, it's the same.
I have installed the latest graphics driver for my card, but all that let me do was enable the fancy effects. With or without these, i still have issues.

I have checked, and direct rendering is disabled. Found this out when playing WoW (Wine is a nifty program). Does this have any adverse affect on the issues I'm having? I'm fairly certain this is graphics related, but maybe the fact I'm installed under Windows is another issue. If graphics are the problem, how could i enable direct rendering? I have a feeling that maybe it's passing the job over to onboard graphics?

Thank you.

---

### Post by Broadlore on 2009-03-22
Just updating to say that Ubuntu performs exactly the same on a liveCD boot using a much older machine.

---

### Post by Monsieur Gonzalez on 2009-03-22
Open a terminal and check the output of the command glxinfo. First lines should look like these:
"name of display: :0.0                                              
display: :0  screen: 0                                             
direct rendering: Yes                                              
server glx vendor string: NVIDIA Corporation                       
server glx version string: 1.4                                     
server glx extensions:"

If you're not getting direct rendering, then maybe something went wrong with the NVIDIA drivers install. Have you checked you've enabled the restricted driver and restarted the computer?

---

### Post by MaxIBoy on 2009-03-22
You need to install the closed-source nVidia drivers.

Option 1 (More stable:)[INDENT]Go here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Select "linux" for your operating system, find the correct graphics card, and it should give you the right driver. (There's a difference between 32 bit and 64 bit, make sure you pick the right one!)

The page you should see will have instructions for how to install the driver.


[/INDENT]Option 2 (More risky but more cutting-edge and possibly easier:)[INDENT]You can also use envyng, a program that auto-magically installs and configures the latest beta drivers. Just remember that autoconfig programs aren't always correct.

Run the following terminal commands:
```
sudo apt-get install envyng-gtk 
gksudo envyng
```"Sudo" and "gksudo" both run a command as "root," which is like the Windows Administrator user. "Root" is always a separate username in Linux. In Ubuntu, the first username you create will be allowed to run commands with "sudo," using the same password as it normally uses. "Gksudo" is for graphical programs, "sudo" is for text-based programs.
[/INDENT]

---

### Post by Broadlore on 2009-03-22
Are the closed-source drivers the ones that NVIDIA provides and aren't open source? Because i installed the latest one that Ubuntu mentioned, and this was the result i got. I'll try these methods soon though, thank you for the help.

---

