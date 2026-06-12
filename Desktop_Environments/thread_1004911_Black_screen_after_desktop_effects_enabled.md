---
title: "Black screen after desktop effects enabled"
date: 2008-12-07
forum: Desktop Environments
---

### Post by brandon90c on 2008-12-07
Hello, I installed Ubuntu 8.10 a few weeks ago and the window corruption problem with the nvidia v177 drivers bothered me for the longest time so I decided to install the nvidia v180 beta drivers a few days ago. But now after I enable desktop effects or login with them enabled, I get a black screen.

I can actually hit <ctrl><alt><f1> (or go to any other virtual terminal). then <ctrl><alt><f7> to return to X and the picture works perfectly, but I would prefer not to have to do this every time I login.

I have absolutely no problems with desktop effects disabled. Terribly sorry if this has previously been solved in another thread. Google doesn't come up with anything. Thanks in advance for any help. :)

---

### Post by trailblaze on 2009-01-22
I am having the same problem.. I am running Ubuntu 8.10 from a USB drive, but it is persistant.  This occured after i installed the 180 drivers for my NVIDIA Geforce 7000m card.  Does anyone have a solution we could try?

---

### Post by ontognosy on 2009-01-30
add me to the list :(

7000m, installed 180 drivers as per this thread: [http://ubuntuforums.org/showthread.php?t=1036788]("http://ubuntuforums.org/showthread.php?t=1036788") (HOWTO: Install Nvidia drviers including DKMS module).

it's weird.  i don't really mind the quick switch from x to tty and back to x.  after that everything works beautifully.

ideas?

---

### Post by nonoitall on 2009-02-03
I also have this problem - on a GeForce 7000M as well.

---

### Post by JDMB20TDA on 2009-02-10
Ati x1300pro, and ati drivers same problem.
wasnt able to getrid of black screen.
Eventually after trying a number of things I was able to get it to boot past Ubuntu loading screen and into the login.
The compiz/ati drivers were disabled...
What was a work around for this issue? you said you alt + ctrl f7 to get to 
terminal. what then?
 I logged in a number of times with nothing changing.
thanks sorry Im very new to this any bit of help is appreciated.
thanks.

---

### Post by malachi1990 on 2009-02-10
For the Nvidia users, try using a 177.xx or 173.xx driver, or if those don't work, the 96 series works well, if a bit slow.  

If compiz still doesn't work, you can enable metacity compositing by copying and pasting this into terminal.  


gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

I got this from this site: [http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/)

@JDMB20TDA
  Wish I could help, but I can suggest is trying a different driver.

---

### Post by JDMB20TDA on 2009-02-10
could compiz be at fault?
and how could I be sure it wont happen again?
being im not 100% sure I know what I did to get it back working again...
Thanks for the help.

---

