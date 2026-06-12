---
title: "What did I Do Wrong  Now?"
date: 2009-05-03
forum: General Help
---

### Post by 2jessiejames on 2009-05-03
Good afternoon 
 I installed Ubuntu as a dual boot with my XP Pro Os several months ago and after installation found the problem that I'm about to describe .. Tried to figure it out, gave up, and went back to using XP professional till I had time to address the problem. 
 I now have time to continue with my exploration of the system, and have spent several hours trying to discover what  went wrong  ... to no avail. 
When I enter the system everything I type appears to be being encrypted. for example I type :
   
"** How do I correct this problem?**"            the following appears ..............  
[B]
" Dr, er C jrp..jy ydco iprxn.mZ" [/B]     

When "**this**" is retyped using the new letters "**ydco**" it appears as   "**fejr**"  then  "**fejr**" becomes "**u.hp**"   
                        

  Additionally when I boot up choosing  windows and use windows explorer to look for the second drive installed (_there are two 160 gig drives installed)_ I cannot find any reference to the second drive that Ubuntu is installed on .... (No D hard drive)
 Could someone shed some light on how I have screwed up? 
                                        Thanks in advance for any information you may provide 
                                                                                  2jessiejames

---

### Post by pbpersson on 2009-05-03
Are you really using Feisty Fawn?

If you have a hard drive formatted as ext3 for Linux, Windows will not be able to see it.

You would need to right-click on "My Computer", then go to "Manage" and then "Disk Management" or something like that to see the drive - it will say "unknown format" because Windows has tunnel vision.

When you installed Ubuntu is it possible that you chose the wrong keyboard type?  If so, boot into recovery mode and from the terminal type the following to re-configure your XServer:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by adamfaulkner1 on 2009-05-03
It sounds like you have the wrong keyboard settings. If this is the case, you would need to click System -> Preferences -> Keyboard -> Layouts Tab, then make sure it has the correct model (Generic 105 Key (Intl) PC works for me).


Perhaps when you installed ubuntu, you chose the wrong keymap?

But I'm not sure if you can login.

As to the windows question, a windows installation cannot understand the way linux stores its files (a filesystem). I would look at [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by Locutus_of_Borg on 2009-05-03
1: keyboard layout is wrong
2: windows lacks ext3 driver

both can be easily remedied by probably the first link in google

---

### Post by geirha on 2009-05-03
Looks like you've set the keyboard to [Dvorak](http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard) layout, instead of the standard qwerty. To fix, you'll want to go to System -> Preferences -> Keyboard. Click the layout tab, then click the Add button. Choose the keyboard's country from the "Layouts:" drop down box, and make sure the "Variants:" drop down is set to Default (and specifically not Dvorak).

Make the new layout default, or remove the previous one.

---

### Post by 2jessiejames on 2009-05-03
Thanks for everyone's Speedy reply!  And everyone was on the mark!  I had carelessly selected "Dvorak." 
I must have done it prior to the name and password selection, making it a little more difficult to correct! As I had to decipher the password and name, before I could make the correction.  
 I'm sure I will be back many times as I have decided to try to move to a Linux based operating system .... while well versed in MS operating systems ... this is like having to learn a new language .. 
                                   Thanks again for your responses!

Ps  And for pbperrson .. I wasn't running " Feisty Fawn'   but  Ubuntu 8.10 ...

---

