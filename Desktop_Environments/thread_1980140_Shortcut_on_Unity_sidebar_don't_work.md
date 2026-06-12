---
title: "Shortcut on Unity sidebar don't work"
date: 2012-05-14
forum: Desktop Environments
---

### Post by MRRT on 2012-05-14
Hello.

I have installed JMP for linux on ubuntu 12.04. The program is installed in the /opt directory.
When I run it his icon appears in the unity sidebar. I locked it there to keep it. After I have closed the program, clicking on the icon does not launch JMP.
How can I make it work?
I don't know if it is related but the original packages of this software were on RPM I converted it with alien and installed it by double-cliking in each one.

Thanks.

---

### Post by MRRT on 2012-05-15
I have come to a solution.
Since JMP was running in terminal, I have created the following script on Gedit.

cd ~/(JMP directory)/app
./jmp

After giving it permission to execute this worked but before opening JMP appeared a window asking me if I want to execute the file or open it with Gedit.

To resolve this I created a shortcut (or launcher) to my script.
This worked fine and I could lock the shortcut on my unity sidebar.

I don't think this is the best solution but it is fine by my programing limitations.:)

---

