---
title: "Alt Gr stop working after some random time"
date: 2008-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dbeltran on 2008-10-19
I have a dell inspiron 1501 with intrepid. The problem is that the alt gr stop working after some random time have pass. Rebooting solve the problem but not definitely because it backs after time. I've seen this issue before in hardy after updating the kernel to 2-6-24-21 going back to 2-6-24-20 seems to solve the problem. But now, after upgrading to intrepid the issue is back.

I've investigated a little with xev and the keycode seems to change. When everything is good i get the same response after pressing and releasing the alt gr key:

KeyPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x66, subw 0x0, time 133997, (408,298), root:(486,389),
    state 0x0, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4000001,
    root 0x66, subw 0x0, time 134080, (408,298), root:(486,389),
    state 0x80, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

When the problem appears i get a keycode of 159 and not 108 like it should be.

Any idea?,

Thanks in advanced,

David

---

### Post by fluxer on 2008-10-27
I have a Dell Vostro 1000,
and I have the same problem,
if you find a solution, please put it on the forum

Thanks

---

### Post by dbeltran on 2008-10-27
Hi,

At the moment, no solution. I have reproduced the problem yesterday. I think is a memory corruption in the Bios since there is a similiar issue with a unknown genereted key pressed after some random time. This last issue can be fix desconnecting the cord and battery, but it come back after the time.

Perhaps Dell should say something about this questions.

Greetings,

David

---

### Post by fluxer on 2008-10-28
Hi,

I don't think you're right about the corruption in the BIOS,
cause it worked flawlessly in the previous kernels and in my Windows installation.

The problem started with the new kernel (2.6.24-21-generic),
so I'll just go back to the previous kernel and wait for the next kernel.

Thanks anyway

---

### Post by ordilem on 2008-11-06
I have the same problem with ubuntu 8.10 (kernel : 2.6.27-7) on votro 1000 (Bios 2.6.3)


Thank

---

### Post by oriotecc on 2008-11-07
I got the same problem after updating to Intrepid. Using 2.6.27-7-generic. I've got an Inspiron 1501 as well.

---

### Post by dbeltran on 2008-11-12
Still no solution to this problem

This is my output obtained from xev after pressing the alt gr key:
KeyPress event, serial 33, synthetic NO, window 0x4c00001,
    root 0x66, subw 0x0, time 2284545, (438,180), root:(458,301),
    state 0x0, keycode 156 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x66, subw 0x0, time 2284741, (438,180), root:(458,301),
    state 0x0, keycode 156 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

The output from uname -a is:
Linux portatil 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

attached is the dmesg output from today.

Thank you in advance,

David

---

### Post by questron on 2008-11-17
Hi!

From my observations, I think it's more the behaviour described in the comments of this bug:
[https://bugs.launchpad.net/ubuntu/+bug/283934](https://bugs.launchpad.net/ubuntu/+bug/283934)

It seems to occur only after a cold boot - but not after a reboot. Can anyone confirm?

greetings,
chris

---

### Post by oriotecc on 2008-11-19
> **questron said:**
> Hi!

From my observations, I think it's more the behaviour described in the comments of this bug:
[https://bugs.launchpad.net/ubuntu/+bug/283934](https://bugs.launchpad.net/ubuntu/+bug/283934)

It seems to occur only after a cold boot - but not after a reboot. Can anyone confirm?

greetings,
chris

Rebooting does help some times, but it is far from a guarantee. In fact, I just rebooted twice to fix it, but so far no such luck. It seems to be entirely random.

---

### Post by dbeltran on 2008-11-20
I cant say reboot doesnt work. At the moment, I only can confirm that cold boot increase the probability of getting the error.

---

### Post by questron on 2008-11-30
A new solution came up in launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298675):](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298675):)

> I read in a german forum that you have to run

sudo aticonfig --initial -f

to solve the problem when you are using new ati-drivers (fglrx). This way changes are transferred to xorg.conf. I don't really understand that but for the last hours the keyboard has been running fine. Hope this helps.

Can anyone confirm this? 

I can't check it right now as I have to run Vista until the key works again (developing on a german keyboard without alt-gr isn't that funny).

greetings,
chris

---

