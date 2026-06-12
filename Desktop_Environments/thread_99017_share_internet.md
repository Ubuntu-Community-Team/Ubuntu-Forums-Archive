---
title: "share internet"
date: 2005-12-04
forum: Desktop Environments
---

### Post by César en Linux on 2005-12-04
Hi

how i can share internet with Ubuntu, a person recommend me use IPTABLE, but i cannot find that option

---

### Post by billpoo90 on 2005-12-04
what?

---

### Post by migueljacq on 2005-12-04
if you're talking about getting a second computer to be connected to the internet, on your local network, the easiest way is to install firestarter

sudo apt-get install firestarter

then when following the wizard, click 'enable internet sharing'

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=César en Linux]Hi

how i can share internet with Ubuntu, a person recommend me use IPTABLE, but i cannot find that option[/QUOTE]
"iptables" is a command line program.  If you have done any basic shell scripting, it is not too hard to use.  If you would rather walk barefoot over broken glass than use the command line... well, you are probably better off trying to use Firestarter in that case, as it has a graphical option that works in many simple cases.

If you search around the forums for "Internet Connection Sharing", "IP Masquerading", or "NAT", you should find what you need to use iptables.  If you still have questions, feel free to post more specific questions.

---

### Post by wgrant on 2005-12-04
I am quite experienced with iptables, so don't hesitate to ask.

cwaldbieser, how is CLI like walking barefoot on broken glass?

William.

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=fujitsu]I am quite experienced with iptables, so don't hesitate to ask.

cwaldbieser, how is CLI like walking barefoot on broken glass?

William.[/QUOTE]
It isn't to me, but some people really don't like using it.  For people who like CLI, there is iptables.  To people who don't like it, there is GUI.  Maybe in the future, voice recognition like on Star Trek will be the next big thing.  I never understood how they were supposed to program the computers without keyboards.  I would think if I talked at the computer all day, I'd lose my voice!

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=fujitsu]I am quite experienced with iptables, so don't hesitate to ask.

cwaldbieser, how is CLI like walking barefoot on broken glass?

William.[/QUOTE]
On another note, would you have any idea if what the fellow in this thread is asking is possible with ip tables?  I am just guessing at this point:
[http://www.ubuntuforums.org/showthread.php?t=98760]("http://www.ubuntuforums.org/showthread.php?t=98760")

---

### Post by César en Linux on 2005-12-07
there is graphic mode of the IPtables command, becouse i don`t know much about that

---

### Post by matid on 2005-12-07
Installing ipmasq (*sudo apt-get install ipmasq*) with Universe repositories enabled and then restarting the computer should be enough.

---

### Post by César en Linux on 2005-12-09
how I use the ipmasq???  i don`t understand

---

