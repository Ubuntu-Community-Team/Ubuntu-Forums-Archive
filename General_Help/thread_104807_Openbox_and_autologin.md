---
title: "Openbox and autologin"
date: 2005-12-16
forum: General Help
---

### Post by simpat1zq on 2005-12-16
I followed the steps in this guide:

[http://www.ubuntuforums.org/showthread.php?t=103806](http://www.ubuntuforums.org/showthread.php?t=103806)

Now I have a clean install with only OpenBox.
Everything works fine, but I was wondering if there was a way I could have it login automatically, and startx when I boot the computer.

---

### Post by simpat1zq on 2005-12-17
I have another question about OpenBox. How can I add things to the menu that can only be run as root? For example, synaptic. If I put the following into menu.xml, it locks up completely, and I have to hit the power button to be able reboot the computer (The mouse still moves, but everything else is locked up, I can't even press Ctrl-alt-backspace)

  </item>
    <item label="Install Packages">
    <action name="Execute"><execute>sudo synaptic</execute></action>
  </item>

If I put 'sudo' in front of any command in that menu, it locks up the machine. Is there any way I would be able to do this without using the Gnome Panel, or without having to type it into the terminal everytime?

---

### Post by simpat1zq on 2005-12-17
OK, it looks like it's not an OpenBox problem. I installed fbpanel, and created a menu using that. When I add something to the menu, and put 'sudo *anything*' as the command, it just locks everything up. When I hit the power button, it is still able to do a proper shutdown, so it's not a hard lock. 

I would appreciate any help with this. 

Thanks.

---

### Post by iced-tux on 2005-12-29
When you give the sudo command, the system waits for your password.
BUT since you haven't started sudo in a terminal eg "xterm -e sudo synaptic" or used gksudo you haven't a chance to enter your password.
In short use gksudo or start by x-terminal -e synaptic.

---

