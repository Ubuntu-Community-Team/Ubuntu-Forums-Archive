---
title: "Root terminal"
date: 2009-05-09
forum: General Help
---

### Post by deerhunter on 2009-05-09
I am a new Ubuntu user and I am having problems with the root terminal. When I try to open it, I get the window for the password but the terminal does not open. I am still learning the Ubununtu comands. If any body can help me I would appreciate it. I must tell you that I am not a computer wizar but i know enough to understand.

I am glad that my friend turn me to Linux, I like it way better than Windows.....

---

### Post by atragorn on 2009-05-09
How are you opening a terminal window btw ?
Applications -> Accessories -> Terminal ?
If you want to do a command that requires root access you can use Sudo
sudo <Command here>
password: blah

if you have several commands to execute you can use
sudo -s
password:

this will give you a root terminal just use "exit" to get out of the root terminal and exit again will exit the terminal completely.

You can also do Alt-F2 then use gksudo it will prompt you for the command etc...

What are you trying to do anyway ?
Perhaps we can help more if we have more information.

---

### Post by ibuclaw on 2009-05-09
> **atragorn said:**
> if you have several commands to execute you can use
sudo -s
password:

Sudo uses a timestamp on a per-tty basis, meaning for each terminal you open and use sudo, that terminal has unprompted access to run commands until a certain period of idle time has been reached. The default in Ubuntu is 15 minutes of idleness before the timestamp is invalidated (and you are required your password again). So if you are running several commands consecutively, '**sudo -s**' is not really needed.

Regards
Iain

---

### Post by deerhunter on 2009-05-09
Thanks, I guess I was a little confused about the root terminal. I was trying to type the command to install Bit-defender antivirus. I believe I need to go to Applications>Accessories>Terminal. Is this correct.
by opening the terminal, is this how I use Sudo?

---

