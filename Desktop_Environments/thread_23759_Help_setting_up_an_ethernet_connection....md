---
title: "Help setting up an ethernet connection..."
date: 2005-04-03
forum: Desktop Environments
---

### Post by gamingworld on 2005-04-03
Hey there. I'm a total newbie to Linux, someone recommended me as a good first, so I got into it. I just got it up a bit ago (hourish) and need help setting up a ethernet connection...

How it goes: My computer, cord connected from back connects to router, router has two cords into it, one from main, and one from mine. router has cord from modem , modem to...well...obvious

anyway, when I try to automatically configure dhcp on it, it just fails and I can't connect...same thing happened when I started installing on text only...one thing I can't understand it that it worked once when I entered local host, but it never worked again. Any help is appreciated.

---

### Post by Gandalf on 2005-04-03
[QUOTE=gamingworld]Hey there. I'm a total newbie to Linux, someone recommended me as a good first, so I got into it. I just got it up a bit ago (hourish) and need help setting up a ethernet connection...

How it goes: My computer, cord connected from back connects to router, router has two cords into it, one from main, and one from mine. router has cord from modem , modem to...well...obvious

anyway, when I try to automatically configure dhcp on it, it just fails and I can't connect...same thing happened when I started installing on text only...one thing I can't understand it that it worked once when I entered local host, but it never worked again. Any help is appreciated.[/QUOTE]
 well your router does not have dhscp activated, do you have any windows OS installed on any PC? if yes on windows
Start -> execute
type "cmd" without quotes
in cmd type "ipconfig /all" without quotes and copy all ip info, 
you need the PC ip, default gateway, netmask and DNS nameserver

---

### Post by gamingworld on 2005-04-04
[QUOTE=Gandalf]well your router does not have dhscp activated, do you have any windows OS installed on any PC? if yes on windows
Start -> execute
type "cmd" without quotes
in cmd type "ipconfig /all" without quotes and copy all ip info, 
you need the PC ip, default gateway, netmask and DNS nameserver[/QUOTE]

Forgot to say, for some interesting reason, ipconfig doesn't work on this computer. XP. Windows XP.

---

### Post by Gandalf on 2005-04-04
[QUOTE=gamingworld]Forgot to say, for some interesting reason, ipconfig doesn't work on this computer. XP. Windows XP.[/QUOTE]
 that's impossible is yor windows damaged???

---

### Post by gamingworld on 2005-04-04
[QUOTE=Gandalf]that's impossible is yor windows damaged???[/QUOTE]
 I don't use this one, my step dad does...anyway... I can type in ipconfig in the run box, I can see it come up, but then it closes...Please...any other suggestions?

---

### Post by thezo on 2005-04-04
At the run box, type cmd
At the command prompt type ipconfig.

---

### Post by Gandalf on 2005-04-04
[QUOTE=thezo]At the run box, type cmd
At the command prompt type ipconfig.[/QUOTE]
 well exaclty that's how i told you to run it, not run -> ipconfig but run -> cmd and in cmd -> ipconfig /all

---

### Post by gamingworld on 2005-04-08
I got ipconfig working, but I had to do alot...By the way, I have a router , but I cannot connect to ip 192.168.0.1 no matter what I do, which is what the problem is I guess...I tried putting ethernet into the manual box and nothing worked

---

### Post by gamingworld on 2005-04-10
guess no one knows, huh?

---

### Post by lorap on 2005-04-13
hi friend,i'll help you.
i've the same structure at home.
3com router connected to hardware samsung modem.
first of all don't choose auto dhcp.
before we begin work reset your modem.there should be a pin at its back side.
that could be one of problems.sometimes it just needs be restarted.not to turn the power off but reset.
pavel

---

### Post by gamingworld on 2005-04-14
Can't risk it, my step dad will murder me if ANYTHING happens to this. I don't want to risk it. This computer is really unstable...

---

