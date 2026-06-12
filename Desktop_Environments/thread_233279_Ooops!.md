---
title: "Ooops!"
date: 2006-08-09
forum: Desktop Environments
---

### Post by RedFive on 2006-08-09
Okay, I'm an aerospace engineering student, but I must be retarded. I was trying to compile a version of gaim that supposedly supports webcams and something called libcairo2 was giving me a hard time. the configure file for gaim wanted GTK+, but when I tried to install that through Synaptic, it was complaining about libcairo2.

Long story short, being as retarded as I have just found out that I am, I decided to remove libcairo2 and try to reinstall it. I know, I know...don't ask.

Then all of the sudden it's removing -- basically everything that depends on libcairo. Even the GUI. 

So I got the gui back and a few other things through apt-get while I was stuck in the terminal. I just installed Xubuntu on here the other day and I'd like to get back to that state without having to start from scratch with the CD.

Is there a magic command that will restore everything to the stock Xubuntu state?

*crosses fingers* :o

---

### Post by vijirajan on 2006-08-09
Try reinstalling xubuntu-desktop. This will have a dependency on all the packages required for a standard desktop system.

sudo apt-get install xubuntu-desktop

---

### Post by RedFive on 2006-08-09
Okay I tried your suggestion. It's complaining and saying it's in an "impossible situation" and doesn't want to do it.

---

### Post by RedFive on 2006-08-09
Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: gaim but it is not going to be installed

---

### Post by vijirajan on 2006-08-09
Try the fix broken packages option. 

sudo apt-get install -f xubuntu-desktop

If it doesn't work, you may have to install the gui packages one by one. I was in a similar situation couple of months ago, and it took me a while to get my system back to its previous state. In the mean time let me see if I can find any other packages that would solve your problem.

Good luck!

---

### Post by RedFive on 2006-08-09
Yeah, already tried the -f. No go.

---

### Post by vijirajan on 2006-08-09
How about this?

sudo apt-get install --reinstall xubuntu-desktop

---

### Post by RedFive on 2006-08-09
I seem to have somehow tricked Synaptic into reluctantly downloading something. I tried the xubuntu-desktop by itself, but obviously got the same error that I got in terminal. But Then I selected all the other packages that said xubuntu-desktop in their name, and it's downloading 254 files. Some of which look promising...gimp, some mozilla and thunderbird stuff...

I'll try the command you just posted after this goes through whatever it's doing. Guh, maybe I should retreat back to windows!

---

### Post by RedFive on 2006-08-10
Yeah, what I did didn't work. And your last post returns the same error as before.

Any ideas?? :(

---

### Post by VK2XCI on 2006-08-10
> Okay, I'm an aerospace engineering student, but I must be retarded.  :rolleyes: 

How many times can you re-engineer something, knowing each attempt brings it's own  problems? Ask Bill Gates! :-P 

Cut your losses and start over!

---

### Post by RedFive on 2006-08-10
Bah, you're probably right.

Booting into the CD now!

---

### Post by RedFive on 2006-08-10
All fixed.

Now to get things back the way they were...


Last install I was having problems getting it to run at 1600x1200. I run it in windows just fine, so I know it's not a problem. I ran the config program in the terminal, but it doesn't change the resolution. In the GUI the options under display properties never changes after i've run the config program and restarted. I've looked through lots of other posts, but haven't found the answer yet...

---

### Post by maniacmusician on 2006-08-10
It is almost certainly a driver thing. look into xorg.conf, what driver are you using? 

sudo mousepad /etc/X11/xorg.conf

it should be in there. for instance, mine is about halfway down and it says:

> 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
EndSection


---

### Post by RedFive on 2006-08-10
> Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Should be the right one...

---

### Post by maniacmusician on 2006-08-10
hmm yeah the via driver seems to be buggy for lots of people. though you seem to be lucky that this is the most of your troubles. the only thing I can think of is that the via driver may not be loading as it should. so i guess you could try 

sudo modprobe via

if that fixes it then you have to make sure via loads at boot. i think the way to do that is 

sudo mousepad /etc/modules and add via to the list. 

good luck

---

