---
title: "Dead ends everywhere"
date: 2006-01-07
forum: General Help
---

### Post by SoulReaper on 2006-01-07
Ok I'm pulling my hair out here


I cannot connect the internet, actually I cannot connect to a network at all.  I have installed 2 different Network cards.  Both the same model.  At this point I am assuming that not having a driver is causing the card to go unrecognized.  I have been searching like crazy and I cannot find an actuall driver download.  Every link I come accross doesn't actually download, it just leads me here :  [ftp://ftp.dlink.com/NIC/dfe530tx+/Driver/Linux/RTL8139.C](ftp://ftp.dlink.com/NIC/dfe530tx+/Driver/Linux/RTL8139.C) 

The card is a D-Link DFE-530TX+


I have no clue what to do at this point.

---

### Post by healychan on 2006-01-07
First, check to see if you card supported by ndiswrapper in here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

If you can find your card there and ndiswrapper does support it, look at this HOWTO [https://wiki.ubuntu.com/forum/hardware/ndiswrapper]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper")

Good luck

---

### Post by duminas on 2006-01-07
Pop open a terminal (Applications > Accessories > Terminal), and execute this:
```
sudo modprobe 8139too
```You should then be able to use your NIC. **If this succeeds** we'll need to do one more thing, but post back and let us know if it works or not.

Ndiswrapper uses the Windows driver, so if the above does not work, try it out. If you require aid with it, feel free to ask.

---

### Post by SoulReaper on 2006-01-07
[QUOTE=duminas]Pop open a terminal (Applications > Accessories > Terminal), and execute this:
```
sudo modprobe 8139too
```You should then be able to use your NIC. **If this succeeds** we'll need to do one more thing, but post back and let us know if it works or not.

Ndiswrapper uses the Windows driver, so if the above does not work, try it out. If you require aid with it, feel free to ask.[/QUOTE]


I typed that code.  It asked for a password, and I typed in the password I set for the machine.  (I used the same PW for everything on it)  It says sorry try again.  I have to be missing something here.  Do I need to do something more than just type that command in the terminal?

BTW I did not see my card on the list, not sure if that matters.

And how do I go about doing this with a windows driver?  Should I find a windows driver, D/L it burn it to CD and then what?  


Have I mentioned I'm not so good at this stuff yet lol?

---

### Post by Iandefor on 2006-01-07
[quote=SoulReaper]I typed that code. It asked for a password, and I typed in the password I set for the machine. (I used the same PW for everything on it) It says sorry try again. I have to be missing something here. Do I need to do something more than just type that command in the terminal?

BTW I did not see my card on the list, not sure if that matters.

And how do I go about doing this with a windows driver?  Should I find a windows driver, D/L it burn it to CD and then what?  


Have I mentioned I'm not so good at this stuff yet lol?[/quote] Did you make sure the password was typed in the proper case (IE, UPPER CASE as opposed to lower case)? Linux differentiates between a character in upper case and the same character in lower case.

---

### Post by SoulReaper on 2006-01-07
[QUOTE=Iandefor]Did you make sure the password was typed in the proper case (IE, UPPER CASE as opposed to lower case)? Linux differentiates between a character in upper case and the same character in lower case.[/QUOTE]

Yes I did.  I actually tried both ways just in case I made a mistake

---

### Post by SoulReaper on 2006-01-07
Well...I'm still clueless.  


Stinks when you wanna play but you can't figure something out.

---

### Post by Iandefor on 2006-01-07
[quote=SoulReaper]Well...I'm still clueless.  


Stinks when you wanna play but you can't figure something out.[/quote] It does stink. I'm sorry, the only thought I'd had was the one about case-sensitivity.

---

### Post by SoulReaper on 2006-01-07
[QUOTE=Iandefor]It does stink. I'm sorry, the only thought I'd had was the one about case-sensitivity.[/QUOTE]

I can't do anything administrative.  Nothing happens once I put in my password.  In fact it doesn't even say passwaord incorrect.  Nothing. 

Is that strange?  I know the password is correct b/c I used the exact same one as my XP system case and all.

---

### Post by Iandefor on 2006-01-07
[quote=SoulReaper]I can't do anything administrative. Nothing happens once I put in my password. In fact it doesn't even say passwaord incorrect. Nothing. 

Is that strange? I know the password is correct b/c I used the exact same one as my XP system case and all.[/quote] Does it just give another command prompt? If so, it probably got the module loaded and working. Reboot and see if the netowkr card works now.

---

### Post by SoulReaper on 2006-01-07
[QUOTE=Iandefor]Does it just give another command prompt? If so, it probably got the module loaded and working. Reboot and see if the netowkr card works now.[/QUOTE]


Oh, I'm not even in the command prompt anymore.  This is just period.  Under the adminstrative options on the drop down menus.  I will try restarting though, because the one time it did give me a fresh prompt.


Is that all I should have had to do though?  not install anything?

---

### Post by SoulReaper on 2006-01-08
Yeah, something is definately up.  When I go system>administration>___(insert orption here)____ I am prompted for my password.  I put in the password, and nothing happens.  Nothing at all.

Just guessing but if my password is incorrect it swould at least say so right?

---

### Post by duminas on 2006-01-08
At the least, it would say something like "Incorrect password" or "Sorry, try again".
And the modprobe I told you to do would not persist between reboots--to make the loading of that module persist, you would need to edit /etc/modules... however, that requires root privileges, which you do not seem to be able to accomplish.

Might I ask what, when you are logged in as your regular user, the following command outputs on the command-line?
```
$ groups
```This would list groups of which you are a member. If you're not in both **adm** and **admin**, that might be the problem.

---

### Post by SoulReaper on 2006-01-09
[QUOTE=duminas]At the least, it would say something like "Incorrect password" or "Sorry, try again".
And the modprobe I told you to do would not persist between reboots--to make the loading of that module persist, you would need to edit /etc/modules... however, that requires root privileges, which you do not seem to be able to accomplish.

Might I ask what, when you are logged in as your regular user, the following command outputs on the command-line?
```
$ groups
```This would list groups of which you are a member. If you're not in both **adm** and **admin**, that might be the problem.[/QUOTE]


It shows me as being in both of those.  I'm puzzled, and I cannot wait for my books to get here from Amazon lol.

---

### Post by handy on 2006-01-09
I don't know if any of the info here will be of assistance, it is the only thing I can do to help with my limitted knowledge, sorry.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Scroll down to this section:-

**********************************************
# 16 Rescue Mode

    * 16.1 How to gain root user access without login
    * 16.2 How to modify kernel boot-up arguments, to gain root user access
    * 16.3 How to use Ubuntu Installation CD, to gain root user access
    * 16.4 How to change root user/main user password if forgotten
    * 16.5 How to change GRUB menu password if forgotten
**********************************************

All the best.

handy

---

### Post by SoulReaper on 2006-01-09
[QUOTE=handy]I don't know if any of the info here will be of assistance, it is the only thing I can do to help with my limitted knowledge, sorry.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Scroll down to this section:-

**********************************************
# 16 Rescue Mode

    * 16.1 How to gain root user access without login
    * 16.2 How to modify kernel boot-up arguments, to gain root user access
    * 16.3 How to use Ubuntu Installation CD, to gain root user access
    * 16.4 How to change root user/main user password if forgotten
    * 16.5 How to change GRUB menu password if forgotten
**********************************************

All the best.

handy[/QUOTE]

I'll definately take a look when I get home tonight.  That looks to be what I might be looking for.  Thanks!

---

