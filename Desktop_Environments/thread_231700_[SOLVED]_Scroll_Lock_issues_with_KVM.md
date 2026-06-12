---
title: "[SOLVED] Scroll Lock issues with KVM"
date: 2006-08-07
forum: Desktop Environments
---

### Post by chapterthree on 2006-08-07
Hi All,

I have a KVM that uses a Hotkey to switch between machines.  That hot key is Scroll-Lock Scroll-Lock (twice).  This seems to work fine under Windows, but when I am on my Ubuntu machine, and I hit scroll lock twice, nothing happens.  It seems that that Ubuntu does not recognize or is not sending the Scroll-Lock keystroke down to the KVM.

Any ideas on what I should do to troubleshoot this issue?


**Solution** (at least solved for me):

> **zenon212 said:**
> I was messing around trying to solve this KVM/Scroll Lock problem and found something interesting. Everything in my TrendNet KVM Manual says that the Scroll Lock is the key to use, but when I hit the Num Lock key twice in either Ubuntu or Vista it switches just fine. I only looked because the Scroll Lock wasn't lighting up the LED. I hit the Number Lock key once to turn it on and light up the LED and then again to turn it off and I was switched back to my Windows box.

So, for me, Num Lock works in both, but Scroll Lock only works in Windows.


**(Better) Solution:**
> **obryan said:**
> For the session that you are in, you can use xmodmap -e 'add mod3 = Scroll_Lock'

To make this permanent for all subsequent sessions add add mod3 = Scroll_Lock to the file /etc/X11/Xmodmap

---

### Post by Jedi Josh on 2006-08-08
I am having the same issue also.  I have even tried using a keyboard emulator (gtkeyboard I think) to send the Scroll-Lock command that way and it didn't work either.  Anyone have any other ideas?

---

### Post by bulldog on 2006-08-08
Well you can set key commands in gconf-editor ->apps->metacity.
But I don't know if that works with a KVM switch.
You could try however,maybe you're lucky.

---

### Post by Jedi Josh on 2006-08-14
I wasn't able to make any headway with this yet.  Is it just my KVM?  I have a [Cables Unlimited SWB-9000UA]("http://www.cablesunlimited.com/products/Prod_Individual3.aspx?groupcode=I3283"). It says it is Linux compatible.  To make things even more complicated I am using a MS Wireless Keyboard and Mouse.  Anyone else have any ideas?

---

### Post by WirelessMike on 2006-08-31
This appears to be related almost exclusively to usb keyboards and usb kvm switches.  Is anyone having this issue with ps2?  I used to have a ps2 kvm switch and it worked fine.  Now I use a usb kvm switch and like you, I'm stuck.  I wonder if redefining the keyboard using
> sudo dpkg-reconfigure xserver-xorg
will make any difference...  I'll try

***update***
Didn't work.  Used xev to determine if key was recognized and it is recognized as "Scroll_Lock".  That leaves me stumped.  Xmodmap didn't help, either.  Interestingly, my friend's debian box recognizes the same kvm switch fine, so apparently, the issue is unique to (k)ubuntu.  I've read a few other posts on this and apparently in 3 releases the issue is still unresolved.  I still like (k)ubuntu, but I'm thinking of trying out debian...
***/update***

---

### Post by talen.quickblade on 2006-10-19
thanks mike for the information, lets me know that its not me that is causing the problem... its worth a little piece of mind.  Let me also offer eveyone two work arounds for KVM switches requiring the use of scroll lock key.

1) - use **CTRL+ALT+F1** to go to a full terminal
   - double tap your Scroll Lock key normally (this works for me)
   - When coming back to the Ubuntu machine use **CTRL+ALT+F7** to return to GDM

2) - I have successfully emulated the double tap using the xset utility on the command line. The command is as follows: *[I]"xset led on; xset led off"*[/I]
I'm sure this can be refined as I do not know the specific led number that should be used, but this has successfully made my KVM switch change source machines.

I hope that this helps everyone until they get the problem corrected. (I'll pray that it is in Edgy).

---

### Post by Propwash on 2006-12-24
I am running 6.10 and also a Debian box (3.1).  I have a 2 port PS/2 KVM switch from Startech ([www.startech,com](www.startech,com)) model number SV221MICRO.  It uses a double tap on the Scroll Lock to switch.  My keyboard is an IBM model "KB 7953".  Everything works fine.

---

### Post by chapterthree on 2007-01-09
> **talen.quickblade said:**
> 1) - use **CTRL+ALT+F1** to go to a full terminal
   - double tap your Scroll Lock key normally (this works for me)
   - When coming back to the Ubuntu machine use **CTRL+ALT+F7** to return to GDM
This does work, thanks!

I think I have found a semi-solution.  I say semi because I can not make it permanent...yet.  I'm hoping somebody will understand what is going on and can offer a suggestion.

Semi-Solution:
1. Login to system and bring up a terminal.
2. Install xkeycaps, apt-get install xkeycaps
3. Run xkeycaps from the terminal.
4. This will bring up a prompt asking you what keyboard you want to use.  Mine defaulted to the standard PC 105 Key.  I just clicked OK.
5. Now a virutal keyboard should be displayed.  You should have a button on the left that says 'Restore Default Map'.  Click this, and then click the Restore button on the dialog that pops up.
6. Now you can use double scroll lock to switch the KVM until you reboot the system.

OK, so now with that explanation out of the way, does anybody know why doing a 'Restore Default Map' seems to restore the Scroll Lock functionality for me?

[Edit: I forgot to mention that I am using 6.10.[/Edit]

---

### Post by thor918 on 2007-02-11
hi. I'm using ubuntu server (No X installed), and have a kvm switch with the scroll lock hotkey. 
the hotkey works in my case, but it also does the linux pause function on the terminal.
I just found out now that it was the scroll lock that made me belive that the linux machine had froze, because it dosent take input when it is activated.(embarrassing)

Would it be possible to deactivete the scroll lock feature in linux?
or perhaps map the pause feature of the scroll lock to my pause button on the keyboard?

---

### Post by pieroxy on 2007-07-15
I got another more useful workaround. The problem is that the KVM doesn't respond to the "Scroll Lock" key being typed twice, but it responds to the "Scroll Lock" LED being lit ON and OFF.

There is a package called "blinkd" which can program and make the keyboard led blink. Just type "sudo aptitude install blinkd".

From there, you can try to make the Scroll Lock key blink with the command:

blink -s -r 1

WARNING: If your KVM is connected to your machine, you won't be able to get back to your Linux machine since the LED is constantly blinking: It will switch to the other machine as soon as you get to your linux.

The command to stop the linking is "blink".

So you can type on your command line (in any shell) :

blink -s -r 1 ; sleep 1 ; blink

So that the LED will blink only for 1 second. That will switch to the other machine and will let you come back to your linux.

So this is a nice workaround. The question is: How can I have my "Scroll Lock" key activate the  "Scroll Lock" LED so that on both my machines I can switch to the other one the same way ?

---

### Post by pieroxy on 2007-07-15
Actually, there is a program called "xset" that can set and unset LEDs of a keyboard.

The following command will switch your KVM but is not as risky as the previous one:

xset led 3 ; sleep 1 ; xset led 3 led off

There ya go !

---

### Post by kg5pa on 2007-09-24
I carefully tested this yesterday, and the scroll lock issue is a result of either X or the GDM. It works fine when you are booting up, until you get to the GDM login, at which point it cuts it off.
Running 7.0.4 release with usb mouse/keyboard KVM. Surely there must be a way to fix it permanently.... I do not have that problem with a RedHat version...

---

### Post by digital_exhaust on 2007-09-24
I have a Belkin KVM that uses the scroll lock key as well, and I have tried every method outlined above and had no success what so ever.... 

Not really a helpful post, just wanted to share my experience... if anyone has any other ideas, I'd love to see them!!

---

### Post by chapterthree on 2007-12-27
Somebody found a solution!!!  Apparently NumLock works in some cases (and it does for me, yay):

[http://ubuntuforums.org/showpost.php?p=2716292&postcount=18](http://ubuntuforums.org/showpost.php?p=2716292&postcount=18)

> **zenon212 said:**
> I was messing around trying to solve this KVM/Scroll Lock problem and found something interesting. Everything in my TrendNet KVM Manual says that the Scroll Lock is the key to use, but when I hit the Num Lock key twice in either Ubuntu or Vista it switches just fine. I only looked because the Scroll Lock wasn't lighting up the LED. I hit the Number Lock key once to turn it on and light up the LED and then again to turn it off and I was switched back to my Windows box.

So, for me, Num Lock works in both, but Scroll Lock only works in Windows.

---

### Post by gtr225 on 2008-01-04
Thanks for the tip. Numlock works fine for me as well. I didn't even think to try that.

---

### Post by obryan on 2008-05-27
For the session that you are in, you can use xmodmap -e 'add mod3 = Scroll_Lock'

To make this permanent for all subsequent sessions add add mod3 = Scroll_Lock to the file /etc/X11/Xmodmap

---

### Post by chapterthree on 2008-05-30
> **obryan said:**
> For the session that you are in, you can use xmodmap -e 'add mod3 = Scroll_Lock'

To make this permanent for all subsequent sessions add add mod3 = Scroll_Lock to the file /etc/X11/Xmodmap

Sweet, this works too!  I'll add to original post.

---

