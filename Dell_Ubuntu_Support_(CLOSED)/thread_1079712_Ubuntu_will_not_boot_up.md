---
title: "Ubuntu will not boot up"
date: 2009-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mommarowe on 2009-02-24
on my 2-month old Dell Inspiron 6000.  I had 40+ updates to run last time it booted up, so I said, yes, install them.  the laptop went dead during the updates, and now I get nothing but a white screen when the computer "boots" up.  I have no clue what to do.  Can anyone help me?  So frustrating that Dell won't talk to me about it since it's Ubuntu and since it's ONLY 2 months old.  Help please!  Thanks!:KS

---

### Post by Mordac85 on 2009-02-24
What exactly do you mean 'went dead during the updates'?  Did you loose power and/or the system shutdown while it was in the middle of the updates?

So where are we now? Do you get past POST (initial Dell splash screen), does grub start to load, do you get the splash screen?  Where exactly is it failing and do you get any message that flash up before the screen goes white?

---

### Post by mommarowe on 2009-02-24
Thanks for your reply/questions.  Yes, it went dead/lost power during the updates.  It goes thru the Ubuntu screen with the moving bar underneath the name "Ubuntu" (the bar that moves side to side as if Ubuntu is loading).  Then the next thing I get is a "white" screen and nothing more.  It goes nowhere else or does anything else but look at me with its white eyes - lol.  Can you help me?

---

### Post by sirebral on 2009-02-25
sudo apt-get update

Can you run that in a terminal?

---

### Post by mommarowe on 2009-02-26
I can if you mean do I have any computer I can run it on?  I'm not sure what you mean.  The only option I have right now is putting something on a thumb drive and trying that in a USB port on this laptop.  I'm not sure what you're asking me, though.

---

### Post by sirebral on 2009-02-26
try accessing terminal via Ctrl - Alt - F1.  then try.  You need to login when you get to the terminal window.

---

### Post by mommarowe on 2009-02-26
now I get a message that some index files failed to download, have been ignored or old ones used instead.  dpkg was interrupted; you much manually run dpkg - congifure -a to correct the problem.  I tried entering dpkg - configure -a and I get something about options marked produce a lot of output.....  What do I do now?

---

### Post by sirebral on 2009-02-27
Get a pen and pad and repeat the process taking notes.  Hearing that _something_ happened is to vague for me to answer you.

---

### Post by mommarowe on 2009-02-27
I understand.  Well, believe it or not, I did it!!  I don't have a clue what I did, but I eventually got back to the update manager screen and it actually ALLOWED me to continue the updates.  After they loaded, everything seems to be operating fine!! Yahoo!!  Thanks for your help!  Wish I understood more to explain it, but I just don't.  Thanks again!

---

### Post by sirebral on 2009-02-27
If you managed to run apt-get install update in the terminal I told you to get to then you might have completed some broken code.

Your problem was that your code was broken.  By being able to run an update manager you had the opportunity to complete the broken code.

I'm glad your computer is working now.  I hope you learned a little about the power of linux as well.

---

### Post by mommarowe on 2009-04-20
[FONT="Arial Narrow"]TRYING TO WORK THRU PROBLEMS AGAIN.  A friend borrowed the computer, and I believe the thing died while unplugged and perhaps updating?  Really have no idea.  I can run apt-get install update in the terminal (I think that's what I'm doing- LOL).  then I have to say yes for permission to do so.  Then I have a black screen with the letter Y on every line down the left side of the screen.  I don't know if something is running (it's taking a long time) or if it's not working.  I would actually reformat the hard drive and start from scratch, BUT I have no CD drive on this thing AND have only an external HD that I've loaded the CD files onto.  Any thoughts?  Thanks again!

---

### Post by mommarowe on 2009-04-20
Oh, these are some messages I've gotten too:  The configuation detials for GNOME power manager have not been installed correctly.  

An error occurred while loading or saving configuation information for update-notifier.  Some of your confi settings not work properly – adding client to server’s list failed.  CORBA error

---

