---
title: "Can't Anyone help with serious system crash?"
date: 2009-03-26
forum: General Help
---

### Post by cdoebbler on 2009-03-26
About a week ago my system crashed. I can enter the login and password, but then just get a blank orange screen...no desktop.

Moreover, I can Ctl-Alt-F1 into Terminal mode, which allows me to see files or boot with a distro disk, but in neither mode can I edit my files as they are locked.

Is there no way that I can reset the desktop. None of the few responses I received to an earlier posting helped at all. I can reach the internet to update or upgrade and I still can't seem to get my desktop back.

:confused:
Maybe I was wrong to switch to Linux. Although I hate paying Bill Gates at least some support is better than losing six months work and spending three weeks trying to get help. Since October 2007 when I started using this list I have started four threads...none have lead to usable answers. I guess Linux is just not for everyone?

---

### Post by Dngrsone on 2009-03-26
Can you copy your home folder out to separate media?  Perhaps a reinstall would be in order.

Have you tried safe boot?

---

### Post by change_mode on 2009-03-26
In your other topic you said you removed a package that you "weren't using". If that's what caused the problem, just reinstall that package.

sudo apt-get install packagename

If you want to remove unneeded packages, you can use

sudo apt-get autoremove

---

### Post by heartburnkid on 2009-03-26
Worst case scenario: reinstall from the LiveCD.  When you get to the partitioner, select "Manual".  For each partition, right-click, select Edit, and uncheck Format, then set up your mountpoints however you like.  This should allow you to reinstall Ubuntu without reformatting your drives (and thus, without losing your data).  You will need to reinstall your apps afterwards, however.

---

### Post by sefs on 2009-03-26
...Before you put your mouse pointer anywhere near a partitioner  or trying a re-install I would strongly advise that you boot with a live CD (I prefer knoppix as it usually automatically displays all your drives on the desktop) but the ubuntu live cd will do too, and copy all the files you need from your home directory to a safe place like a usb key or external drive.   Then you can muck around with re-installing or trouble shooting.

But safe guard your files first before you do anything if you think you are at risk of losing them.  Do not go from the frying pan into the fire.

---

### Post by lovinglinux on 2009-03-26
> **cdoebbler said:**
> Since October 2007 when I started using this list I have started four threads...none have lead to usable answers. I guess Linux is just not for everyone?

Let's see:

[B][Thread # 1 -  Power failure while upgrading to Hardy]("http://ubuntuforums.org/showthread.php?t=799773")
[/B]
> **cdoebbler said:**
> Tried 'sudo dpkg --configure -a && sudo apt-get -f install' (which was sugegsted on another linux list) and it got upgrade running again. Maybe this will help someone else.:)

You solved the problem and posted the solution on the same day, so there is no need for people to reply with additional instructions.


**[Thread # 2 -  Ubuntu does not work with UN HQ Wifi]("http://ubuntuforums.org/showthread.php?t=1009298")**

> **cdoebbler said:**
> No page/site works.

There is clearly a connection and if I use the computer elsewhere (out side of UN) I can get the internet. I don't understand...unles sthey weer wrong at Un helpd desk in telling me there is no special security. 

Could any Monzilla add-ons cuase problems like this?

Since your wireless works outside and you can get a strong signal in the UN, the problem is not on Ubuntu, but in the UN infrastructure or on your web browser settings. As you said, the UN help desk staff doesn't have the knowledge about Linux. So I guess you should suggest the UN IT manager to hire more competent people. I'm afraid the Ubuntu community can't help you with this problem, because they have no access to the UN network. If they do, I bet someone would fix it pretty fast.


**[Thread # 3 - Help...I get blank screen after login]("http://ubuntuforums.org/showthread.php?t=1101257")**

Not everyone can do miracles. It seems that you removed some important packages and you don't know which packages are they. The best course of action in my opinion is to do a clean install as already suggested. If you have a separate partition for /home, then you will have most of your settings preserved and probably you won't even feel the difference.

Uninstalling stuff that you don't know what it is can compromise any kind of system. Is not Ubuntu fault. It's yours. This event should be considered as a lesson experience. Don't mess with things you don't understand.

I'm sorry if I sound harsh, but I'm starting to get annoyed with posts complaining about the support from the community, bashing Linux and Ubuntu or threatening to go back to Windows. BTW, since you are using Ubuntu since October 2007 and created only 3 threads requesting support, then I'm pretty sure Ubuntu has been working pretty well and stable on your machine, until you messed it up. 

My experienced here since I switched to Ubuntu has been nothing but excellent. The forum community does not deserve this kind of treatment.

---

### Post by spcwingo on 2009-03-26
If your internet still works just boot up, press CTRL+ALT+F1, and type one command:

```
sudo apt-get install --reinstall ubuntu-desktop
```

You never know, it just may work.  ;-)

---

### Post by spcwingo on 2009-03-26
If your internet is still working in the terminal just boot up, press CTRL+ALT+F1, and type these commands:

```
sudo apt-get install --reinstall ubuntu-desktop
```

followed by:

```
sudo apt-get clean && sudo reboot
```

You never know, it just may work.  ;-)

---

### Post by cdoebbler on 2009-03-26
Thanks for all the quick replies.

Unfortunately, I have tried everyone of them but reinstalling the system. I have not tried this because I do not think /home is separate partition and I think I may lose all my work.

1. I can't open or copy most files as they are locked. I see them on a CD boot in Ubuntu 8.04, but can't do anything with the files that I see and can't even open most directories, except in Terminal where chmod and even rm does not work...because files are locked, I think. 

2. I have no internet connection with the computer. I have tried terminal connections without success and can boot from disk and get a connection but can't update the locked files under my usual user account. For this reason sudo apt-get install solutions do not work.

3. Yes, tried safe boot, but screen still freezes. 

I apologize from knocking the support. I know you all try. I am desperate however as I have about three days to turn in grades and will have to give sixty students incompletes. I love ubunut but really use it because I either have to (can't afford to pay on my salary as a law professor at third world university of about 500 USD per month) or have to use a hacked copy of MS. The problem is the university foolishly only supports Gates junk. Nevertheless, the university support says if I switch my system to MS they think they can retrieve my information--six months of writing, research, and the semester's grades. I don't mean this as a knock on linux, which has served me well for several years, it is just the reality I face if I can't repair this myself ... with help of friends.

---

### Post by lovinglinux on 2009-03-26
> **cdoebbler said:**
> Nevertheless, the university support says if I switch my system to MS they think they can retrieve my information--six months of writing, research, and the semester's grades.

Don't do that. I bet they haven't a clue about what they are talking and you will probably loose everything. Windows cannot read ext3 file system and you probably have only one partition, which means you will have to wipe and format the hard drive to install Windows with a different file system (NTFS). Then I guess only those companies specialized in data recovery will be able to get something back, if this is even possible.

Unfortunately, I can't help you. I'm not experience enough to solve your problem, but probably someone else will guide you through the necessary steps to find a solution.

Please be patient. If you don't get an useful response within 24 hours, then bump the thread, by posting again here that you still can solve the problem. Don't create more threads. Soon or later someone will step in with a better solution. If nobody can solve the problem, then I guess the best course of action is to send the drive to a respectful data recovery company. This will cost some money, but since you didn't formatted the drive (by installing Windows for example), then I'm pretty sure a specialist will be able to recover everything.

---

### Post by abn91c on 2009-03-26
those symptoms are of a broken compiz, there are many post in the forums about your problem, if you can't get in in recovery mode then try in the terminal ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by change_mode on 2009-03-27
> **cdoebbler said:**
> 
1. I can't open or copy most files as they are locked. I see them on a CD boot in Ubuntu 8.04, but can't do anything with the files that I see and can't even open most directories, except in Terminal where chmod and even rm does not work...because files are locked, I think. 

Open a terminal and enter:

sudo nautilus

---

### Post by stderr on 2009-03-27
You say problems began when your system crashed. Was this a case of rebooting via the power button, or following an update, or...?

It could be graphics drivers, compiz, home directory/user profile. But I'm confused with these 'locked' files. What message do you actually get when you try to e.g. chmod one of your files in your home directory from the terminal? And what message do you get when you try to sudo chmod it? Would be good if you could run and post the output of (replacing afile.txt with an actual file):

  $ echo $USER
  $ ls -l afile.txt
  $ chmod +x afile.txt
  $ sudo chmod +x afile.txt

---

### Post by gorucan on 2009-03-27
set yourself root password then copy it to external disk, reinstall and paste contents of home dir back

---

### Post by gorucan on 2009-03-27
> **change_mode said:**
> Open a terminal and enter:

sudo nautilus
sudo nautilus? better gksudo...?

---

### Post by change_mode on 2009-03-27
> **gorucan said:**
> sudo nautilus? better gksudo...?

Doesn't really matter.

---

