---
title: "internet problem with my dell"
date: 2010-02-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Joel91 on 2010-02-25
[B]Hi everyone..

I have Dell Latitude model PP01L, Windows 2000 and is windows XP

my problem is that when I try to connect to internet via ethernet my modem is connecting my router and my router is connecting my Dell with ethernet so i connect to iternet.. it works for a few seconds but then it doesn't work anymore neither my other computers with wireless... i though it was and ip conflict right? but then i open my internet options set my IP adress manually and default gate away.. etc but still doesn't work i reset my router and all other computers work again and mine for a few seconds again... then puf not doesn't work any computer again ... 

Sorry for my bad english.[/B]

---

### Post by Joel91 on 2010-02-26
bump? please any suggestions?

---

### Post by Joel91 on 2010-02-27
bump.

---

### Post by pablo180 on 2010-02-27
Have you tried connecting to the internet with other computers other than the Dell? Do they connect OK via ethernet?

Also, have you tried connecting the Dell directly to the modem, i.e. not using the router at all?

---

### Post by Joel91 on 2010-02-27
yes i have tried that and it works with other computers connected via ethernet, and yes my dell connected directly to the modem works fine :S problem is i need the router cus then my dad cant use the wireless neither my brothers =(

---

### Post by pablo180 on 2010-02-27
OK, so let me just see if I have understood you. 

Your other computers all connect fine wirelessly, but every time you connect either via ethernet, or wirelessly, it disconnects you after a few minutes and everyone else as well?

But if you don't connect, everyone else can use the internet without any problems, i.e. it is only your Dell that causes the problem?

---

### Post by Joel91 on 2010-02-27
yes but its not the ethernet nor the router cuz i have 1 computer (this one im using) its connected via ethernet and the other 2 computers are using wireless so about my computer the dell one it dont have wireless so i connect via ethernet and yes when i connect with this one works for a few seconds then the internet dont work until i reset the router men sorry for the bad english please tell me if u understood me now

---

### Post by coffeeaddict22 on 2010-02-28
Hi,
Just after you disconnect, open a terminal and get the output of ```
tail /var/log/dmesg
```

It'd also help to see what ```
nm-tool
route -n
``` both show.

---

### Post by Henery on 2010-02-28
I had trouble with my connection on my dell with any ubuntu older than intrepid what version are you trying?

---

### Post by Joel91 on 2010-03-02
dont know were i find the version
here it says Latitude C610
Ref Number 01014

---

### Post by pablo180 on 2010-03-02
Hi Joe, 

You can find out your version by clicking on System and then Administration and then System Monitor. 

When that loads up just click the System tab (if it isn't on it already) and then let us know what is written there under Ubuntu.

---

### Post by Joel91 on 2010-03-03
[coffeeaddict22]("http://ubuntuforums.org/member.php?u=636580") where i open terminal?

ok [pablo180]("http://ubuntuforums.org/member.php?u=79805") im going to check it out

---

### Post by coffeeaddict22 on 2010-03-04
Hi,
Terminal: Applications/Accessories/Terminal; I strongly recommend you right click and choose "Add to Panel" as you do end up using it a fair bit (that'll put an icon on the top panel you can use instead of having to go through the menus).

For the easiest way to identify your version in a form you can paste back, in the terminal type ```
uname -a
```
Also, while you're connected, also type in ```
nm-tool
``` and post that back.

---

