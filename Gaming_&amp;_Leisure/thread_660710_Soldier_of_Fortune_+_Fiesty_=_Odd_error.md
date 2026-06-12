---
title: "Soldier of Fortune + Fiesty = Odd error"
date: 2008-01-07
forum: Gaming &amp; Leisure
---

### Post by NPALeech on 2008-01-07
I know old Loki games can be tricky to install/run, but this time I'm completely stumped. I toss in the disc, open a terminal, switch to the directory, and this is what happens:

leech@ObscureHost:/media/cdrom0$ sudo sh setup.sh
Password:
setup.sh: 9: function: not found
x86
leech@ObscureHost:/media/cdrom0$ 

If i try to ./ execute it:

sudo ./setup.sh
sudo: unable to execute ./setup.sh: Permission denied

I'm not sure how to even begin solving this problem. Last I remember, it was working perfectly on Dapper. So I'm stumped.

---

### Post by NPALeech on 2008-01-08
Bump.

Anyone? I'm at a loss here, I've never encountered anything like this before. lol

I just tossed Dapper on my laptop, and it doesn't give me this error, so it's not a damaged CD or anything like that.

---

### Post by Perfect Storm on 2008-01-08
Try this;

```
cp -r /media/cdrom0/setup.sh ~/Desktop
cd ~/Desktop
chmod +x setup.sh
sudo ./setup.sh
```

---

### Post by NPALeech on 2008-01-08
Thanks, but still no go.

> :~/Desktop$ cp -r /media/cdrom0/setup.sh ~/Desktop
:~/Desktop$ cd ~/Desktop
:~/Desktop$ chmod +x setup.sh
:~/Desktop$ sudo ./setup.sh
Password:
./setup.sh: 9: function: not found
x86
l~/Desktop$ 

---

### Post by taduikis on 2008-01-22
Hi.
Got the same problem with Heroes of Might and Magic III.
Solved it by installing ksh and running setup.sh with ksh, instead of sh.
```

sudo apt-get install ksh
sudo ksh setup.sh


```

Good luck!

---

### Post by NPALeech on 2008-01-25
> **taduikis said:**
> Hi.
```

sudo apt-get install ksh
sudo ksh setup.sh


```

Good luck!

Thank you! Seriously I was just about to give up on this, but that worked perfectly.  I never would have thought to install a different shell for it. Good job.

---

### Post by beko on 2008-02-27
I was looking for a solution for this problem too and your fix worked excellent . Thank you

---

### Post by Larryish on 2008-04-26
awesome. thank you much

---

### Post by go_beep_yourself on 2008-09-17
Does only the original SoF install in Linux? What about SoF2 and where can I get the Linux installer for SoF2?

---

### Post by vikhr on 2008-11-23
:) Awesome..
I had the same issue..with SOF..and tried to debug the bash script and warily type in google and bang..here i am.. 
Thank you very much..ubuntu community rocks..!:guitar:

---

### Post by vikhr on 2008-11-23
Another issue crops up which is
[SIZE="3"]dirname: missing operand
Try `dirname --help' for more information.
Couldn't run Soldier of Fortune (sof-bin). Is SOF_DATA_PATH set?[/SIZE]
and again help was found in another ubuntu forum thread..
So to put it all together for an avg user who will hit the roadblock next time, here it is:
[SIZE="3"]sudo mount /home/user1/SoldierofFortune/SoldierofFortune.iso /media/cdrom -o loop[/SIZE]
(if it is an image file)
[SIZE="3"]sudo apt-get install ksh
cd /media/cdrom
sudo ksh setup.sh[/SIZE]
type absolute path of sof script [SIZE="3"]/usr/local/games/sof/sof[/SIZE] and bang the cd key dialog box will popup hopefully..

---

### Post by crazyfuturamanoob on 2009-02-08
I did everything posted above.
```

$ sudo ksh setup.sh
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at support@lokigames.com

```
How about amd64?

---

