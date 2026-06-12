---
title: "What is a &quot;Terminal?&quot;"
date: 2009-06-14
forum: General Help
---

### Post by Dan13 on 2009-06-14
Everybody says "just type it in terminal..." I'm new to Ubuntu and I don't know many of these words. Could some body tell me what is a "Terminal" and how can I access it?
Thanks!

---

### Post by merlinus on 2009-06-14
Applications/Accessories/Terminal.  It will open a window with a prompt where you can enter commands.  You press the Enter key after entering each one.  Some commands (those prefaced by suo, gksudo and the like), will bring up a line asking for your password.

The commands can give valuable information about your system, and enable you to do things such as install programs and troubleshoot.

You will need to use the keyboard, and backspace key for deleting characters, because your mouse will not work.  It is text-based.

---

### Post by camper365 on 2009-06-14
A terminal is basically a command prompt.

Applications -> Accessories -> Terminal

That will show you something like a command prompt. You type your commands there.

If you press Ctrl+Alt+F1, Ctrl+Alt+F2, etc. all the way to F6, you will get a terminal that is fullscreen. To get back to the graphics, press Ctrl+Alt+F7.

---

### Post by aysiu on 2009-06-14
Nobody should be asking you to *type* stuff in the terminal unless you lack an internet connection on your Ubuntu machines.

When you get terminal commands, save yourself the trouble and **paste** those commands into the terminal. Copy and paste will make your life a lot easier.

More details on where the terminal is:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by jmszr on 2009-06-14
Dan13,

This should be of help: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) .

---

### Post by nandemonai on 2009-06-14
If you feel like a little light reading on the subject then:

[http://en.wikipedia.org/wiki/Command_line_interface](http://en.wikipedia.org/wiki/Command_line_interface)

---

### Post by obocho on 2009-06-14
just to make it easier; paste is NOT "ctrl+V" :) [it took me quite a while till I managed to figure it out] 
 
paste --> ctrl + shift + V   : ))) 

have fun!

---

### Post by Cvcompany on 2009-06-14
> **Dan13 said:**
> Everybody says "just type it in terminal..." I'm new to Ubuntu and I don't know many of these words. Could some body tell me what is a "Terminal" and how can I access it?
Thanks!
Terminal is just a command prompt. for more information you can just google it.

---

### Post by lovinglinux on 2009-06-14
Using the Terminal for the first time might be a little bit scary. It was for me when I switched from Windows, but you will get used to it and will realize how easy is to do things with it. Additionally, the terminal allows you to have access to hidden features of most applications and perform sequential tasks dependent on each other, which considerable reduces the steps necessary to perform the same tasks through a graphical interface.

For example, instead of opening "System >> Administration >> Log Viewer", then browsing through the kern.log to find which network connections have been blocked by the firewall, I can run the following command in the terminal, which will give exactly what I want:

```
cat /var/log/kern.log | grep eth0
```

Ubuntu allows you to do several maintenance tasks just clicking buttons, but using the terminal is a lot easier and it is a lot easier to explain how. For example, if someone needs instructions on how to install a program all I have to do is tell to run this command in the terminal:

```
sudo apt-get install *program_name*
```

Telling someone to run the command above is much simpler than giving directions through the menus.

---

