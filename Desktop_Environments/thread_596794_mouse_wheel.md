---
title: "mouse wheel"
date: 2007-10-29
forum: Desktop Environments
---

### Post by jwheel on 2007-10-29
Hi, new to the forums and new to Linux in general. I installed Ubuntu 6.06 just this past weekend, so far everything is working great. One of my biggest pet peaves is no mouse wheel, I HATE not being able to scroll.

I have read a LOT of stuff that has worked for other people, all having to do with editing the /etc/X11/xorg.conf file, but none have worked out for me. I will explain my situation and see if anyone else has any ideas specific to my situation.

I have a logitech wireless optical USB mouse, (pretty standard mouse)
I have a Belkin 4 port KVM. the KVM does not have ports for USB so I have to use a PS/2 adapter.

I originally had an issue with the KVM and the mouse going crazy whenever I switched back and forth. I found a fix for that and was able to resolve it. I can't for the life of me remember what it was though.

Any help is much appreciated. Thanks in advance!

---

### Post by ofb on 2007-10-30
Um... yeah that /should/ just work. 

Did you do the install with the KVM hitched up? Back in the 6.06 day I recall you were advised to not install with KVM in use. I did, with no problems, but I use ioGear. I've always wondered if the warning came about due to problems with Belkins.

And yeah, sometimes PS2/USB adaptors are a problem with KVMs.

Since we're clutching at straws here, have you tried connecting directly to the computer to see if the problem still exists after reboot? (Don't hot-swap connectors. Turn the power off.)

Another thing is see if the LiveCD works okay, direct connected, & through the KVM.

Kinda need to experiment a bit to get more clues.

---

### Post by jwheel on 2007-10-30
That's a good idea. When I installed Ubuntu, I don't believe I had the KVM hooked up. I will try what you suggested and post the resultes.

Thanks

---

### Post by ofb on 2007-10-30
Incidently, why are you using 6.06? Is it for the LTS? Support for the current 7.10 goes to 2009-04, compared to 2009-06 for 6.06 LTS, so if you're starting now there's not much difference.

Support means securty and bug patches, but you don't get version upgrades. While lagging in version should only mean lagging in features, I do have to wonder if perhaps you'd have better luck with a more recent Ubuntu. Certainly you'd have more people on the forum running the same software as you if you were running 7.10.

Something to keep in mind, anyway. If you have the same trouble when running under the LiveCD, definitely burn 7.10 and try it for comparison.

Also, what is the precise model name or number for your mouse? Looking around, I do see people having trouble with some Logitech mice. The model name will help with searches. Ditto with the Belkin.

One related thread I've dug up,
[http://ubuntuforums.org/showthread.php?t=187018](http://ubuntuforums.org/showthread.php?t=187018)

---

### Post by jwheel on 2007-10-30
I'm using 6.06 server because of the LTS, it goes until 2011 which I thought would be a nice thing to know. Plus, like I said in my first post I'm VERY noobie to Linux in general and I found an write up on steps to install a LAMP with 6.06 server, easy to follow step by step for a noobie like myself. So that's the biggest reason. Now that I have it working, since I'm doing this just for knowledge, not really to run a web server per se, I may just go ahead and install 7.10 and start over from the beginning. 

The 7.10 client live cd worked fine. which makes me think it's either the changes I made in order to get the KVM to work that caused problems with the mouse wheel, or maybe it's just 6.06. Others have successfully gotten 6.06 to work though. When I get home from work, I will revert my changes I made for the KVM and see what that does. 

I will post more tonight. Thanks for the help though.

---

### Post by jwheel on 2007-10-30
Well, I removed the changes that I made in order to resolve the KVM issue, rebooted and now my mouse wheel works again. Below is the information on what I did in order to resolve my Belkin KVM crazy mouse fiasco.


Edit /etc/modules
ensure it has the following:

mousedev
psmouse proto=PS/2


Edit /etc/modprobe.d/options
ensure it hase the following:

options psmouse proto=PS/2

When I did that, I can successfully switch back and forth between my 2 PCs without the mouse going all funky on me. BUT I lose the mouse wheel in the process. 

My Wireless mouse is a USB Logitech "Cordless Click! Plus Optical" it has left click, right click, wheel and 2 buttons that I have never used before by the thumb area. In fact, I never even realized they were there before. lol

---

### Post by ofb on 2007-10-30
Was there nothing in that thread of use? I thought at least one of the chaps was having the missing-wheel problem too.

On the bottom of your mouse, there should be a sticker with a model number. My sticker is two-tone clear on transparent red plastic, which makes it nearly impossible to read, but it's there.

Dunno how the Belkin comes into it. The much cheaper & simpler ioGear works flawlessly. 

(Sole ioGear issue: PS2 connectors don't lock. Cheap ps2 are sloppy, and that gets worse if you add leverage with a cheap USB/PS2 adaptor. Since the ioGear is essentially a cable dongle, the whole mess tends to be bounced around any time you're in back moving cables. Infrequently, this left me with frozen mouse & keyboard on whichever machine was in use. Solution was to tie & tape the ioGear node into a secure mass that couldn't work momentarily loose.)

... by the way, here's a minor Linux KVM gotcha. You use ScrLk to switch the KVM? ScrLk of course pauses terminal, and in Linux you often work in the CLI. So your first stab of the ScrLk pauses your open terminal process, and it's not unpaused until the second stab of ScrLk on your way back. Leaving you wondering why that process was taking so long, until you remember that's what ScrLk was supposed to do.

---

### Post by jwheel on 2007-10-30
> Was there nothing in that thread of use? I thought at least one of the chaps was having the missing-wheel problem too.

That thread is actually where I found the info to change the KVM behavior so it would not completely freak out my mouse when I switch back and forth. Before that change, the mouse wheel did work. 

Since I'm doing this all just to gain experience working in Linux anyway, I'm thinking I will just install 7.10 server this weekend and give that a shot. I dunno if it will work or not, but it will be good practice for me either way. 

Thanks for all the help.

---

### Post by kbracer on 2007-10-30
I have a Belkin KVM w/ Logitech mouse and find that I have to switch back and forth a few times to get the wheel working. It also appears to help to be scrolling the wheel when I switch the KVM to the Ubuntu machine.

---

