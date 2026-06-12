---
title: "Computer not turning on all the way **free cookies to the first person to help**"
date: 2009-02-27
forum: General Help
---

### Post by NoranaC on 2009-02-27
So, when I turn on my computer, it goes through all of it's usually starting-up stuff.  When the main Linux desktop opens, I can't do anything.  I can move the mouse pointer around but nothing else.  Sometimes the links that I have on my desktop show up and sometimes they don't but I can't click on them.  And the only thing I can do is a manual restart.

I was having sound problems - sometimes it worked and sometimes it didn't.  I tried to fix it by cruising the Ubuntu forums and, being very clever, tried something that somebody else did but don't remember what it was.  I removed some software and tried to install some other software which didn't work.  I tried to find the post that I got it from and, so far, have had no luck. That was the last thing that I did.

Before that, I was having problems were it was being slow to shut down (3-5 minutes) and, when it did shut down, the on light on the front stayed on and the fans in the back (that have led lights) stayed light up.

I'm totally mailing cookies to the first person who helps me solve this.

---

### Post by wpshooter on 2009-02-27
If you are still using Feisty, then my suggestion would be that you replace it with an installation of either Hardy or Intrepid.  I think this will probably solve most of your problems.

---

### Post by NoranaC on 2009-02-27
> **wpshooter said:**
> If you are still using Feisty, then my suggestion would be that you replace it with an installation of either Hardy or Intrepid.  I think this will probably solve most of your problems.

I upgraded to Hardy a few months ago...

---

### Post by Therion on 2009-02-27
> **NoranaC said:**
> I'm totally mailing cookies to the first person who helps me solve this.
First, I'll need to know a little more about these cookies.  

As in what kind, and, are we talking homemade or store-bought?

Also, when this issue occurs, is the keyboard responsive?  Can you, for instance, Ctrl+Alt+F2 and drop to a virtual console?

---

### Post by NoranaC on 2009-02-27
Homemade of course!
Probably chocolate chip....

---

### Post by Therion on 2009-02-27
> **NoranaC said:**
> Homemade of course!
Probably chocolate chip....
Mmmm... Roger that.  Then we can continue.  

How about keyboard function?  Is that possible?

---

### Post by NoranaC on 2009-02-27
While it's starting up, the keyboard works.  I can hit DEL or TAB to get into setup or get into the bios and I can use the keyboard to mess around in there.  But once the OS is up, no amount of keypunching makes it do anything.  Not even ctl-alt-del.

---

### Post by Therion on 2009-02-27
> **NoranaC said:**
> While it's starting up, the keyboard works.  I can hit DEL or TAB to get into setup or get into the bios and I can use the keyboard to mess around in there.  But once the OS is up, no amount of keypunching makes it do anything.  Not even ctl-alt-del.
Okey doke.  Here's what we're gonna do...

Reboot the problematic PC.

When you get to the GRUB counter (the little black and white screen that counts down 3...2...1...) hit the Escape key.

Select "Recovery Mode"

Wait a minute for Ubuntu to do it's groove thaaaaaang.

Hopefully you will wind up at a command prompt and blinking cursor. 

When you get to that point very carefully type in the following commands.  If everything goes correctly you are going enter into a configuration "wizard" that is going to prompt you for information regarding your system.  Answer these questions as best you can.  If you get stuck, post back here and explain.  To move through the menus you will need to use the Tab key.  The Spacebar allows you to make selections in the menus.

**dpkg-reconfigure -phigh xserver-xorg**

When you're all done with this, reboot the PC from the command line by entering:  

**reboot**

Now cross your fingers, pray to your heathen deity and hope for the best...


**BONUS EDIT:**

See this walkthrough for more help (lots of pictures!).  Skip down to the first grey picture, since you will need to enter into the configuration screen a little differently than how it's done in this tutorial.  From the first grey picture onward the tutorial will help you reconfigure your XServer and hopefully give you a functioning system again:

[http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm)

---

### Post by Therion on 2009-02-27
I'm going to assume one of two things has occured at this point...

Either, 1. My cookies are inbound (packed with two slices of white bread to keep them fresh in transit I hope) or, 2. I just tooootally smoked your install.

---

### Post by NoranaC on 2009-02-27
No dice.  :(

When I follow your directions, all I get is a message saying "overwriting possibly customized configuration" and then gives me the command prompt.

When I try the instructions that you linked me to, I get a few of those gray screens asking my only questions about how I want my keyboard and mouse set up and does not give me any of those complicated questions that I was promised...

---

### Post by Therion on 2009-02-27
> **NoranaC said:**
> When I try the instructions that you linked me to, I get a few of those gray screens asking my only questions about how I want my keyboard and mouse set up and does not give me any of those complicated questions that I was promised...
d'OH... That's because I'm an idiot.

See that **-phigh** argument?  I should have left that out.  Mea culpa.

Okay.  Lets try this again...

Executive Summary:  Reboot... Escape key... Recovery Mode... Groove Thaaaaang... Command prompt.

**dpkg-reconfigure xserver-xorg** (this time *sans* -phigh!)

... Grey screens galore...  Reboot... Incense, prayers, virgin sacrifice et al. aaaaaaand mail cookies.

---

### Post by NoranaC on 2009-02-27
Still only questions about my keyboard and mouse set up.  

I tried preying to three different gods but haven't been able to find any virgins to sacrifice unless a cat will count.

---

### Post by Therion on 2009-02-27
Okay something's not adding up here...  

Try this one more time, keep the -phigh but preface the command with sudo:

**sudo dpkg-reconfigure -phigh xserver-xorg**

The -phigh should, in a perfect world, automatically reconfigure X for you.  You're using recovery mode which shouldn't require root privileges but I could be dorking on that fact.  Try it with sudo and report back.  

Spare the cat though, the smell of burning cat hair will only piss-off the Gods.

---

### Post by NoranaC on 2009-02-27
It asks me for the root password before it gets to the command prompt anyway.

---

### Post by Yellow Pasque on 2009-02-27
Therion, that command doesn't have the power it used to with older versions of Ubuntu/X.org. 'Tis a shame because it was an easy way to instruct people to configure their xorg.conf

Anyway, to Norana, now that you've got a generic xorg.conf file, does starting Ubuntu normally still behave as it did when you started this thread? Also, do you have a USB keyboard?

---

### Post by NoranaC on 2009-02-27
It does still behave the same way as when I started the thread.  I have a USB keyboard but used a converter to plug it into the purple or the green one (whichever one is for the keyboard).

---

### Post by abn91c on 2009-02-27
what's you video card? you may need to remove Compiz

---

### Post by NoranaC on 2009-02-27
I switched to a NVIDIA video card about six months ago.  The "new" on is a VGA JATON Video-PX7600GS-256 R and that's copied directly from the newegg invoice.

---

### Post by Yellow Pasque on 2009-02-27
It would REALLY help if you could remember what you did when trying to fix your sound, or at least point us to the instructions you followed.

---

### Post by NoranaC on 2009-02-27
It was three command lines that I entered into the terminal.  The first one started out sudo-apt get remove.  I searched for it among the forums but it seems to be one of those stores from Terry Pratchett's world that disappears as soon as you buy something from them.
It was somebodies post about how their sound wasn't working and this is what they had already tried.  What should they do next.

I will keep looking for the post.... forever and ever.

---

### Post by NoranaC on 2009-02-27
OMG! I found it!!

I did this:
* killall pulseaudio
* sudo apt-get remove pulseaudio
* sudo apt-get install esound
* sudo rm /etc/X11/Xsession.d/70pulseaudio

except the last line didn't work.

---

### Post by Therion on 2009-02-27
> **NoranaC said:**
> OMG! I found it!!

I did this:
* killall pulseaudio
* sudo apt-get remove pulseaudio
* sudo apt-get install esound
* sudo rm /etc/X11/Xsession.d/70pulseaudio

except the last line didn't work.
I think I see the problem.  Just not sure how to fix it...  Thinking you're going to need to reinstall PulseAudio.

---

### Post by Yellow Pasque on 2009-02-27
Excellent. Let's try and work backwards (to get your system running, then we can work on the sound issue).

Boot to the recovery mode and drop to the root prompt. The following command will open a log in a text editor. After you open the file, hold 'Page Down' until you get to the end.
```
nano /var/log/dpkg
```

Now, use the up arrow until you come to the point where the log mentions your removal of pulseaudio. The goal of looking through the log is to see what packages were removed when you did the *apt-get remove pulseaudio*. I realize the log will probably be somewhat cryptic to you, but do your best.

Now:
```
apt-get remove esound
apt-get install pulseaudio <and any other packages that got removed when you removed pulseaudio>
```

---

### Post by NoranaC on 2009-02-27
> **Temüjin said:**
> 
Boot to the recovery mode and drop to the root prompt. The following command will open a log in a text editor. After you open the file, hold 'Page Down' until you get to the end.
```
nano /var/log/dpkg
```
>[/code]

When I type in nano /var/log/dpkg, it opens a blank file and says new file on the bottom of the screen just about all of the control instructions.

---

### Post by Yellow Pasque on 2009-02-27
Sorry, should have been:
```
nano /var/log/dpkg.log
```

---

### Post by NoranaC on 2009-02-27
I tried just doing the 
apt-get remove esound
apt-get install pulseaudio
in the root prompt without knowing what else (in anything) I am missing.

AND IT WORKED!!!!

I really appreciate all of the help from all three of you and please send me messages with your address and I'll send you homemade cookies!  It's the least I can do to thank you guys for spending a Friday night helping get my computer in its legs...

---

### Post by Yellow Pasque on 2009-02-27
You're welcome, and while I appreciate the sentiment of cookies, beer makes me fat enough as is.

---

