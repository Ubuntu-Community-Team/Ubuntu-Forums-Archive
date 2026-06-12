---
title: "shutdown ends in black screen with working cursor"
date: 2009-03-22
forum: General Help
---

### Post by kubumar on 2009-03-22
Hi,

When I try to shutdown my system the screen becomes black with a working cursor. Its not every time, maybe every second or third shutdown. 

What can I do?

kubumar

---

### Post by Tanker Bob on 2009-03-22
A quick word-around is to hit Ctrl-Alt-F2 to get a console login screen, login, than type "sudo shutdown 0" at the prompt. That will shut your system down.

---

### Post by kubumar on 2009-03-22
Yeah, but thats not a solution for the real problem. And may I forgot: When the system shows the black screen, it shuts down when I press the Power-Button.

---

### Post by Tanker Bob on 2009-03-22
True, but you didn't provide any information at all about your system, so that's the best I can do. A thorough system description (OS version, processor, memory, video card and driver, etc.) may yield a better answer. Also, any changes you made to the system just before the symptoms appeared would be helpful. That's a good rule of thumb anytime you need help. You'll notice that many of us include our system info in our signatures to save time.

---

### Post by sumantagogoi on 2009-08-24
happens to me too... shutdown and restart both need to press powerbutton which sucks as i use a laptop with external monitor placed on top of the labtop and have to open the laptop everytime to reach the power button.
sys conf ibm thinkpad r50e
intel centrino prcessor
1.2 gb RAM at 333MHz
intel 855gm graphics inbuilt

---

### Post by eotakos on 2009-08-25
Count me in! 

my laptop is vaio cs11z - it is a 08 model so it is a fairly fast mashine (don't think that this can be the issue).

i have the black screen with the cursor working, but using alt+ctl f2 ,3 , ... won't work for me. I get the prompt to log on, but the keyboard is dead (nothing i type shows - but the combination to switch tty's work (odd)).

switching to the 8th (or 7th) tty i can see the output of the shutting down procedure, and the error is : 

"killing all remaining processes (or something like that)  [fail]"

bla bla...

"unmounting devices"
" / is still busy"
"will now halt"

i wish i could copy paste or something but...

Ah! i almost forgot! i'm running jaunty 9.04 64bit (in case this matters - but other than that the problem seems to be the same with kubumar and sumantagogoi)

Thanks in advance for any usefull info

bye for now :-)

---

