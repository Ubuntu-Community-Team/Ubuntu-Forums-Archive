---
title: "Only Logs Into Guest After Fresh Install Of Xubuntu 12.04."
date: 2013-01-16
forum: Desktop Environments
---

### Post by BlinkinCat on 2013-01-16
Hi all,

I have searched about issue but can't understand some of the solutions, so will describe the problem as best as I can. Fresh install, when logging into user the normal screen appears with a graphic glitch in the top corner. Mouse OK but there is no top panel at all.
No Bottom Panel either. However Guest can be logged onto O.K.

It would be very much appreciated that with any possible solution, that you spell out any commands in simple terms as my knowledge is limited. 

Cheers - :)

Edit - I was able to perform full downloads via guest.

---

### Post by Toz on 2013-01-16
Maybe a corrupt cache?

Try logging out, going to the first tty (Ctrl+Alt+F1), logging into the console as normal user, then:
```
cd ~/.cache
rm -rf sessions
```

Then go back to GUI login (Ctrl+Alt+F7) and try logging in as normal user again.

If it still doesn't work, there may be some hints in the normal user's ~/.xsession-errors file.

---

### Post by BlinkinCat on 2013-01-16
Thanks Toz,

I will certainly do that but I thought I would add info - I was able to set up all 4 users (admin) and the problem exists for each account.

I will now do as you say - thanks - :)

---

### Post by BlinkinCat on 2013-01-17
I'm probably doing it wrong - all I get

First command - invalid option

```

cd:usage: cd [-L|[-P[-e]]][dir]

```The second command returns nothing - don't know if I'm entering it incorrectly.

Edit : Would this problem have resulted from the fact that my previous installation consisted of Unity 12.04.1 plus Gnome Shell with Xubuntu 12.04 and xfce 4.1 being installed on top ?

Seriously thinking of a completely fresh installation of xubuntu 12.04 (formatting /home) and starting again (copying bookmarks,videos, etc) I only want one version.

---

### Post by Toz on 2013-01-17
Looks like you are typing it in incorrectly. Try this version:
```
cd $HOME/.cache
rm -rf sessions
```

---

### Post by BlinkinCat on 2013-01-17
As far as I can tell -

```

cd $HOME/.cache
~/.cache$rm -rf sessions
~/.cache$

```Thers's something I am just not getting - :mad:

---

### Post by BlinkinCat on 2013-01-17
Hi Toz,

I only realized a short time ago that I had copied 12.04 and not 12.04.1
Would that make any difference ?

---

### Post by Toz on 2013-01-17
Actually, that worked. Now try logging in again as a normal user. Does it work? If it doesn't, while still logged in as the normal user, go back to Ctry-Alt-F1, run this command, and post back the link that is generated:
```
pastebinit $HOME/.xsession-errors
```

---

### Post by Toz on 2013-01-17
> **BlinkinCat said:**
> Hi Toz,

I only realized a short time ago that I had copied 12.04 and not 12.04.1
Would that make any difference ?

It shouldn't.

---

### Post by BlinkinCat on 2013-01-17
Hi Toz,

Sorry for the delay - As I knew it was early morning where you are, I thought I would experiment. I reinstalled ubuntu 12.04.1 so I could burn another Xubuntu 12.04.1 Disk.

When I installed it, exactly the same problems occurred. Do you wish me to do the pastebinit command, or do you wish me to repeat the earlier ones.

In the meantime I will download the updates.

Cheers and thanks - :p

Edit - Repeated the commands in #5 with exactly the same results.
           Will now go ahead with pastebinit command.

---

### Post by BlinkinCat on 2013-01-17
Hi again -

pastebinit
```

http://paste.ubuntu.com/1541855/

```Cheers - ;)

---

### Post by Toz on 2013-01-17
Sorry for the delayed replies - work seems to be getting in the way.

Just to confirm, this is from a brand new Xubuntu 12.04 install?

Are you still getting the graphical glitch? If so, can you explain a little more about what it is? And what is the make and model of your computer and what video card do you have?

---

### Post by BlinkinCat on 2013-01-17
Sorry for my delayed reply  - I nodded off - :p

Computer is Intel core i7 2600 Sandy Bridge, 4GB ddR3 1 TB HDD.
```

guest-fgeTFT@ABC:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
guest-fgeTFT@ABC:~$ 

```Glitch on screen for all 4 users is approximately 2 cm wide x  2/3 cm deep horizontal white rectangle located in the top left hand corner about 2 cm from the top of screen and about 1/2 cm in from LHS of screen.

I hope that helps - all the best - I think I have just missed you again.

And yes, this a brand new 12.04.1 installation other than the /home partition which has been used for about the last 1 1/2 years (I think) ie for 11.10 Ubuntu and Gnome Shell and Xubuntu and Xfce but I am stretching my memory. Refer lower down the page for info about recent alterations to partitions.

I have been seriously thinking of not formatting /home and as a result may have a very fresh install, albeit requiring quite a lot of work with Bookmarks etc. What do you think ?

And then there was the implementation of this thread -
[http://ubuntuforums.org/showthread.php?t=2103648](http://ubuntuforums.org/showthread.php?t=2103648) - when I removed /var, /tmp and /var partitions. Guest can't run Gparted so I can't show what the partitions look like now.

An alternative -
```

guest-fgeTFT@ABC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.2G  3.0G  5.8G  35% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           775M  872K  774M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   88K  1.9G   1% /run/shm
/dev/sda2       463M   59M  381M  14% /boot
/dev/sda6       735G  337G  362G  49% /home
none            1.9G   27M  1.9G   2% /tmp/guest-fgeTFT
guest-fgeTFT@ABC:~$ 

```With it's enlarged excess of partitions, Xubuntu and xfce ran very well for many months. Not sure where swap is - maybe doesn't show up with that command ?

---

### Post by Toz on 2013-01-17
Did all 4 users have pre-existing home directories?

You can view info about the swap file with this command:
```
swapon -s
```

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> Did all 4 users have pre-existing home directories?

You can view info about the swap file with this command:
```
swapon -s
```

As far as I understand it, Initially after setting up one Account, I would add 3 other users.

```

guest-mvrjqn@ABC:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    7813116    0    -1
guest-mvrjqn@ABC:~$ 

```

---

### Post by Toz on 2013-01-17
Try creating a new account that doesn't have a previous /home directory. See if it works for this account.

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> Try creating a new account that doesn't have a previous /home directory. See if it works for this account.

I'm not sure how to do this - I usually would use users/groups to create a new user. How do I avoid having a previous home directory ?
Sorry that I'm not real bright Toz.

---

### Post by Toz on 2013-01-17
No thats right. Just create a new account using the users/groups application then try to login as that user. But just login, don't copy any files over just yet. Lets see if a new user can login and get a desktop.

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> No thats right. Just create a new account using the users/groups application then try to login as that user. But just login, don't copy any files over just yet. Lets see if a new user can login and get a desktop.

Yes, using user/groups I was able to set up another account which worked with no distortion. I'm on it now.

Edit - I assume this will work out with me copying backed up user files into new users and then eventually deleting original accounts.

---

### Post by Toz on 2013-01-17
It must be something in the configuration files of the /home directory that you are "keeping". You could try, from the Ctrl+Alt+F1 console screen to rename the existing $HOME/.config/xfce4 directory:
```
mv $HOME/.config/xfce4 $HOME/.config/xfce4.BAK
```
...but keep in mind that this will reset xfce and you will lose all of your existing Xfce customizations.

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> It must be something in the configuration files of the /home directory that you are "keeping". You could try, from the Ctrl+Alt+F1 console screen to rename the existing $HOME/.config/xfce4 directory:
```
mv $HOME/.config/xfce4 $HOME/.config/xfce4.BAK
```...but keep in mind that this will reset xfce and you will lose all of your existing Xfce customizations.

Do I just do this when logged into new user or the original user ?

---

### Post by Toz on 2013-01-17
Make sure you are _not_ logged in as the original user. Go to the first tty (Ctrl+Alt+F1), login to the text console there as he original user, and run the command.

Then go back to the GUI (Ctrl+Alt+F7) and login as the original user and see if its back to normal.

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> Make sure you are _not_ logged in as the original user. Go to the first tty (Ctrl+Alt+F1), login to the text console there as he original user, and run the command.

Then go back to the GUI (Ctrl+Alt+F7) and login as the original user and see if its back to normal.

Other than loss of wallpaper (no prob) all works with files etc intact. Should I repeat the excercise with the other  3 users or does the command need to be varied?

I am very grateful for all of your help Toz -:p

I think I made a mistake and was logged in as original User.

---

### Post by Toz on 2013-01-17
I think that you only need to do this with users who you are keeping their home directories. For any new users, they seem to be fine.

If you need to do this again, the command will remain the same for all user accounts because $HOME will always reference the current user's home directory - whoever the current user may be.

---

### Post by BlinkinCat on 2013-01-17
> **Toz said:**
> I think that you only need to do this with users who you are keeping their home directories. For any new users, they seem to be fine.

If you need to do this again, the command will remain the same for all user accounts because $HOME will always reference the current user's home directory - whoever the current user may be.

I will set about resetting the other 3 users accounts then. I didn't seem to mess anything up by being logged into original user account other than the loss of wall paper - all files are intact. I am very grateful for all of your help Toz - likely I will be marking as "solved" unless I catch up with you later.  Must be getting a little late there - :p

---

### Post by BlinkinCat on 2013-01-17
Hi Toz,

Ran all commands for 4 users - deleted new account that I had created.
Everything now seems to be fine thanks very much with just a little tidying up to do.

You are a genius Toz

Will now mark as "solved"

Cheers - :guitar:

---

### Post by BlinkinCat on 2013-01-19
Hi Toz,

I have re-opened this thread briefly to ask if the command in post #20 could have resulted in the users losing their sudo privileges ?  I receive a message "user is not in sudoers file" when I try to issue a sudo command in my minor 3 user accounts. To clarify, I am the only user on this machine using the other 3 users for such things as bookmarks, etc.

Could the issue be rectified via Case 1A of - [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo) ?
I wasn't sure if the method would work for Xubuntu.

  Edit: Boy oh Boy am I embarrassed - :oops:

After doing a little thinking,  I realized I could achieve what I wanted with the following command on my main user account.
```

sudo adduser username sudo

```All the best Toz if you read this, I have learnt a lot from both you and CharlesA in the last few weeks. Thanks kindly for that - I will again mark as Solved.

Cheers - :p

---

