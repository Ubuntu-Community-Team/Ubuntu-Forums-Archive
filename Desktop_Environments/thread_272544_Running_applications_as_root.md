---
title: "Running applications as root"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Darrage on 2006-10-06
I'm completely new to Ubuntu, and Linux as a whole, so this is probably a very newbish question. However, I've searched the forums, wiki, and Ubuntu documentation unsuccessfully, so please don't be too cruel. ;)

I've installed the latest version of GParted, as I have free harddrive space lost (I made my Ubuntu partition too large, so reduced it, now it's stuck in no mans land), that I can't add to my Windows partition with GParted 0.1 (supplied as default).

The default version can be accessed via system->administration, however, my new version is saved to desktop. When I try to run it, I'm told I can't as I don't have root priviliges. I know when using the terminal I just use sudo and my account password, but there's no password field to fill in on GParted to show I'm root, do I have to somehow run it from the terminal?

---

### Post by ssalman on 2006-10-06
from your post, it sounds like you are running the live CD??

I'm not sure how you installed GParted, and why it is laying on your desktop:-k...but if you still have it there, fire up a terminal window and type "sudo ~/desktop/gparted" that should do it (not sure about capitalization, as I'm on a windows box now). there shouldn't be any password required.

But I think you are having other issues, as when you correctly install GParted it should not sit on your desktop, and the default GParted worked great for me so far, and I have done a lot of partitioning with it....

hope that helps. :)

---

### Post by Darrage on 2006-10-06
It's sitting on my desktop because I didn't want to lose it, it seemed to be the best place. 

The default GParted has very little NTFS support, it says so in the help files and everything. ;)

Thanks for your help. *reboots into Linux to test it*

---

### Post by Aranel on 2006-10-06
To run any app as root, enter:

gksudo application's-command

You'll be prompted for your root password, then it'll come up. In this case, you'd probably need to type "gksudo gparted," although I'm not sure that's the correct command for it. To find out, right-click on its item on the menu and click "Properties."

I hope that helps.

---

### Post by Darrage on 2006-10-06
gksudo gparted brings up the 0.1 version of it. Though in properties for the new version it says 'gparted'.

*stuck*

---

### Post by ssalman on 2006-10-06
what happened when you ran "sudo ~/desktop/gparted"?

what about running "gksudo ~/desktop/gparted"???

again, I'm not sure about capitalization...;)

---

### Post by Darrage on 2006-10-06
"Command not found" :(

If you want to see exactly what I've done to my harddrive, by the way. [http://www.ubuntuforums.org/showthread.php?t=272573](http://www.ubuntuforums.org/showthread.php?t=272573)

---

### Post by ssalman on 2006-10-06
Okay, I guess to eliminate alot of the confusion, your best bet is to download the gParted Live CD, and boot it, it should have the latest GParted. you can find it [here]("http://gparted.sourceforge.net/livecd.php"). its only 30MB so it shouldn't take long to download (if you have DSL/Cable).

Once you got your HD mess in order you can then reinstall Ubuntu.

I'm sure there is easier ways to get this fixed, but if you are not familiar with Linux yet, I will opt for the simplest solution possible... even if it's a long one. :)

post back if you still have issues. Good luck.

---

### Post by Darrage on 2006-10-06
It seems that I just wiped my Windows partition...on the bright side, I have less reason to worry about the free 27 gig...:neutral:

---

### Post by ssalman on 2006-10-06
I'm sorry to hear that... That is how I learned how to play with my HD partitions long time ago...:) and that's when I started backing up all my important stuff... ;)

I hope you didn't lose any important files permenantly.

You'll get better with time... just be more careful next time...:p

---

### Post by Shortgeek on 2006-10-06
Agreed. I'm still learning; I just wiped a lot of my school papers a couple days ago installing Vista.

---

