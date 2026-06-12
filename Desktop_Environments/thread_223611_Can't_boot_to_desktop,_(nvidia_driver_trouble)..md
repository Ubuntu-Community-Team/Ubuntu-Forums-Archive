---
title: "Can't boot to desktop, (nvidia driver trouble)."
date: 2006-07-26
forum: Desktop Environments
---

### Post by Senesence on 2006-07-26
Nvidia GeForce2 MX/MX 400
Ubuntu 6.06

I used Synaptic to install the "nvidia-glx" package, in order to enable hardware acceleration. Then as per instructions on the [BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia), I went to terminal and entered "sudo nvidia-glx-config enable".

The result was an error that went along the lines of: "Error: Your X system has been altered, if your not sure that this is supposed to happen enter this command: update md5sum........." I don't remember what the command was exactly, but I entered it (the "update md5sum..." command) and then I once again tried the "sudo nvidia-glx-config enable" command. This time I didn't get an error as I did before when I ran the same command.

I restarted my system in hopes that I would now have hardware acceleration, but this time instead of booting to desktop I was presented with a blue screen that told me about how "X" was not configured properly and so on. After this I was thrown directly into the console, about which I really know very little.

I'm new to Linux, so I am asking help on how to:

A) Get back to the Ubuntu desktop enviroment.
B) Get hardware acceleration working right with my nvidia card.

Thank you.

---

### Post by Dubbayoo on 2006-07-26
Edit /etc/X11/xorg.conf and change the driver from nvidia (i think) to nv or vesa.

---

### Post by _simon_ on 2006-07-26
to edit it, use sudo nano /etc/X11/xorg.conf and yes change nvidia to nv

---

### Post by Senesence on 2006-07-26
Could you be a little more detailed about how to do that?

I tried "sudo nano /etc/x11/xorg.conf", but that didn't give me any options to change. I am completely new to linux, so I would really appreciate step by step instructions.

Do I have to maybe change directories or something in order for the "sudo nano /etc/x11/xorg.conf" command to give me options to change?

Right now my prompt looks like "login@computer:~$".

---

### Post by IDontKnow9998 on 2006-07-26
First type in your username (hit enter), then when it will ask for your password, enter it.

Once you are logged on, do the sudo thing they are telling u 2 do...

---

### Post by Senesence on 2006-07-26
I know that.

The prompt that I get to when I log on is "login@computer:~$", then at that prompt I type "sudo nano /etc/x11/xorg.conf", but that does not give me any options to change anything from nvidia to nv.

I need clarification on that.

---

### Post by jc750kwak on 2006-07-27
If your card is AGP then you've installed the driver but you haven't fully configured it for your system

I have exactly the same card and configured my GeForce2 using this guidance (method 1):

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

The problem you are suffering is because you have to edit the xorg.conf file and add in the device specific lines (item 4 under the Problems section in this guide)to get it to work. These don't get added by just installing the ubuntu driver

Also make sure to put the correct bus id. Do "sudo lspci" and look for the bus id for your GeForce2. Mine was at 1:5:0

Ctrl-Alt-backspace didn't work for me so I did a system reboot and my GeForce2 worked fine. I could test it with glxgears and install and play Unreal under Cedega

John

---

