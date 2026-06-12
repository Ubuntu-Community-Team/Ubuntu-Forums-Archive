---
title: "Dell with mouse issues"
date: 2011-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Vilasman on 2011-04-23
Hi. I have a dell 1520 inspiron that is sorta running Ubuntu 11 beta. I say sorta because sometimes it works ok... usually after awhile it gets to a point that I can open a program, click on 2 to 3 things and then the mouse and mouse pad simple stops working. I can move the mouse but I cant click on anything. I have installed and un installed ubuntu 10.1, 10.10 and 11 about 5 times. I format the hard drive each time.  
I checked and the computer has BIOS version A02. What should I do?

---

### Post by KegHead on 2011-04-23
Hi!

Have you tired:

system..preferences..mouse?

KegHead

---

### Post by Vilasman on 2011-04-23
I think I may have looked under mouse at one time but didnt see anything that I thought was wrong. 
I am using the computer now. I could be typing along and all of a sudden the computer will lock up. I will be able to move the cursor... but clicking on something, anything does nothing. The only thing I can do is turn it off. If i turn it back on, usually i can make three moves. Enter my password, click on a program say chrome or firefox and then say enter a url. The site will open.And I can move the cursor around on the page. But I can't click on anything.
Turn the puter off again. Back on, three steps. Say I select a program this time, click on one thing in the program. Can't select anything else.
Do this a few times get frustrated, take drive out and format it with another computer, put back in... try lynx 10.1. Get to the point where it updates and then it locked up. Then I saw a download for 10.10. Go through everything above. Works for an hour of so and it goes back to locking up.
Take drive out again. Reformat. This time put in Netal 11 beta. It started doing the same thing. I let the computer sit for a couple hours. It has been working since about 3 pm until now 10 pm. But I full expect it to lock up at some point

---

### Post by mörgæs on 2011-04-24
You should upgrade BIOS. I know that an A04 has been released, and maybe there is an even newer.

---

### Post by Novacaptain on 2011-04-29
Hi, I'm new to the forums in a sense. Usually I find solutions here, posted as replies to other people and it works great. Right now I'm having trouble that I can't find any help for. This thread seemed appropriately on-topic, but I apologize if I'm doing it wrong.

I'm using a Dell Studio 17 64bit with a  Synaptics PS/2 Touchpad . Everything was working fine in ubuntu 10.10, clicking, scrolling, etc. 

Yesterday I upgraded to 11.04 and what happens now is that the mouse simply stops responding after a while. It works fine while logging in but as soon as I do something such as:

opening a terminal and starting up a program 
starting a web-browser (firefox or chrome) and going to check my mail.
Opening a text editor...
Im not sure exactly what triggers it really

the touchpad buttons and movement simply stop responding (i might even be moving it at the time, it just stops)

I've tried xinput - list
and it shows as up as a slave to the virtual core pointer, with device id 11.

SynPS/2 Synaptics TouchPad 

In the xorg.0.log xorg.1.log, I don't find any errors related to loading the driver, and it seems to be working fine at least for a while.

What I've tried so far:

#1
modify /etc/default/grub;
edit the line;
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
(all one line)
then run;
update-grub

#2
Starting a session in classic (with and without effects) and unity
starting with the previous linux kernel in classic (with and without effects) and unity.

help?

---

### Post by mörgæs on 2011-04-29
Hi, welcome to the fora. 

I would have opened a new thread, but let's not fight about details now :-)

How does 11.04 work in a live boot?

---

### Post by Novacaptain on 2011-04-29
On a live CD 11.04 works perfectly. Even two-finger scrolling, horizontal scrolling and disabling the touchpad while typing (which was not working that well in 10.10 for me) is fine.

---

### Post by mörgæs on 2011-04-29
Then my guess is that a clean install (with wired internet access) will solve the problem.

---

### Post by Novacaptain on 2011-04-30
It worked with an install that only cleared the system-wide settings.

I had to do some fixing to get the audio to play through the headphone jacks again. All in all, 11.04 seems to work better "out of the box" than 10.10 did, so things seem to be moving in the right direction. Thanks for the help.

---

