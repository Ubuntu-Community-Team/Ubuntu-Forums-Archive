---
title: "Magic SysRq Keys Don't Work"
date: 2008-12-09
forum: General Help
---

### Post by Unanimated on 2008-12-09
Whenever I try to use Magic SysRq keys, mainly Alt+SysRq+RSEIUB, nothing that should happen happens. The only thing that does is that a bunch of save screenshot dialogs come up. This is what the guy said in the legendary tutorial to do to enable them without reconfiguring the kernel:
```
echo * > /proc/sys/kernel/sysrq
```
Where * is a number. He says putting 1 enables everything about them, and that's what I put. I tried it again, and nothing happened. This is what I put in the terminal:
```
sudo su ((just sudo didn't work))
echo 1 > /proc/sys/kernel/sysrq
```
It didn't work. Any help? I've been holding down the buttons for about 3 seconds before moving on to the next one.

EDIT:
```
sudo gedit /proc/sys/kernel/sysrq
```
That doesn't work, either. It comes up with a blank gedit window, with a document titled sysrq.

---

### Post by bapoumba on 2008-12-10
Which version of ubuntu and kernel are you using?
I used SysRq only once, on Hardy, and it worked OK.

---

### Post by effenberg0x0 on 2008-12-10
Confirmed. And no clue on how to fix it yet.

---

### Post by unutbu on 2008-12-10
Try this:
```
echo 1 | sudo tee /proc/sys/kernel/sysrq 
```

Note that /proc/sys/kernel/sysrq should be set to 1 on a fresh intrepid install. At least that was the case on my machine.
You should not need to issue the above command unless you've altered the value before.

---

### Post by Unanimated on 2008-12-12
I'm using Intrepid, 8.10, with kernel 2.6.27-9-generic. I have never touched, tampered with, or even new that the /sysrq file existed until recently, so I haven't messed with that at all.

Also, the command you gave doesn't change the /sysrq file at all, so I'll just manually put a 1 in it, unless I shouldn't.

---

### Post by tgalati4 on 2008-12-12
Perhaps you need to try the key combinations one at a time:

Control-Alt-SysRq-r       (wait a few seconds after each command)
Control-Alt-SysRq-e
Control-Alt-SysRq-i
Control-Alt-SysRq-u
Control-Alt-SysRq-s
Control-Alt-SysRq-b


They need to be done in a sensible order.  I don't know if I have the correct order but I know the last one does a reboot "b".

Each sequence does a specific shutdown procedure.  There's a good wikipage out there describing the magic keys.

This will work with most system hangs, but some kernel panics leave the system in a frozen state where only a poweroff will work.

---

### Post by lswb on 2008-12-12
Are you by chance using a laptop or some unusual keyboard? On some laptops the sysrq key is activated in combination with a Fn key. Which means that to use the ALt-sysrq key presses actually requires pressing 4 keys at once. Inconvenient but not impossible.

---

### Post by Unanimated on 2008-12-12
I've tried putting Ctrl+Alt in front of it, to no avail.

Also, I'm using a generic keyboard from Best Buy, nothing special.

---

### Post by Unanimated on 2008-12-16
Still not fixed..

---

### Post by Unanimated on 2008-12-19
bump

---

### Post by unutbu on 2008-12-19
When you press Alt-SysRq-*, are you using the left Alt key?
On my keyboard (by default in Intrepid), the right Alt key was set to something else. Try using the left Alt key if you haven't been already.

If it doesn't work, please post the output of 
```

cat /proc/sys/kernel/sysrq
```

---

### Post by Fabimaru on 2008-12-27
Hi,

I could not make the magic sysrq keys work under xorg. If I go back to the (real) console, it works. If I do the following under the root account (well, after a "sudo bash"):

echo s > /proc/sysrq-trigger

it really does the emergency sync (I can see that in the syslog), whether I'm under X-Window or the console.

I'm using Kubuntu 8.10 amd64, but I tried the Ubuntu flavor in the VM, and it's the same. With an OpenSuse within KVM, no problem.
I'll try a previous version of Ubuntu some day.

I'm still searching for an explanation.

---

### Post by Reilithion on 2009-01-15
I'm unable to use Magic SysRq either.

```
$ cat /proc/sys/kernel/sysrq 
1
```

I can Alt-SysRq-h all day, with either Alt key, and nothing shows up in /var/log/syslog to suggest that the kernel ever even heard the key-presses.
```
echo h > /proc/sysrq-trigger
```
This, however, results in a message showing up in /var/log/syslog detailing the various Magic SysRq commands.

This is really annoying, and just a bit scary, since I have no way to perform a graceful shutdown in the event of a freeze.

---

### Post by Unanimated on 2009-01-24
Well, this appears to be a major bug in Intrepid. Perhaps someone should report it to Launchpad?

EDIT: I tried using the left Alt key instead of the right one with the same result.

---

### Post by yellowbean on 2009-02-01
This is really frustrating and potentially a huge issue if the Ctrl-Alt-Backspace shortcut for restarting X is removed in Jaunty. I even tried resetting the print-screen shortcut under Preferences to a different key combination and I still can't get Alt-Sysrq + k (or any other command) to work. I've tried both Alt keys on my keyboard, and have generally read every thread on this topic that Google has been able to find for me. I haven't found a single working solution.

---

### Post by pleurastic on 2009-04-04
I've tried off and on for months and cannot find the answer either.  Using Hardy.

---

### Post by unutbu on 2009-04-04
I don't have a solution for you, but just out of curiosity: do you use any special keyboard software like SCIM, or does this problem occur on a fresh install of Hardy?

---

### Post by albinootje on 2009-04-04
> **Unanimated said:**
> Well, this appears to be a major bug in Intrepid.

Some months a friend of mine told me that she heard about this option and was happy about it, we wanted to try it, and it didn't work.
We found out in the Gnome keyboard settings that something needed to be changed before it started working.
I don't remember what it was exactly but I think it had to do with the Print Screen key.
I think I disabled that combination, and then it worked.

---

### Post by linuxape on 2009-04-06
I am new to linux and had the peace of mind that Alt+SysRq+* is a the saviour.....but it has never worked for me.  I am using a IBM T43p machine with Intrepid and Gnome.  I had to do a series of hard reboots recently and am scared if I am doing irreparable harm to my HDD this way.  This is as many has mentioned before is really scary specially Ctrl+Alt+Backspace option will be optional by default in Jaunty.

Instead I get a huge number of screen captures that completely overwhelms the system to a crawl.

Please someone fix this issue.

---

### Post by Reilithion on 2009-05-14
Upon upgrading to Jaunty (9.04) I am now able to use Magic SysRq as long as I use the left Alt key on my keyboard.  It appears to me that the issue has been fixed.

> **linuxape said:**
> I am new to linux and had the peace of mind that Alt+SysRq+* is a the saviour.....but it has never worked for me.  I am using a IBM T43p machine with Intrepid and Gnome.  I had to do a series of hard reboots recently and am scared if I am doing irreparable harm to my HDD this way.  This is as many has mentioned before is really scary specially Ctrl+Alt+Backspace option will be optional by default in Jaunty.

Instead I get a huge number of screen captures that completely overwhelms the system to a crawl.

Please someone fix this issue.

I believe your problem is not that Magic SysRq is not working (indeed, did you activate it?  What does cat /proc/sys/kernel/sysrq in a terminal say?) but that your Gnome keyboard shortcuts have something set up for Alt-PrintScreen.

To fix this, you can go to System -> Preferences -> Keyboard Shortcuts, find the shortcut that says Alt+Print (probably "Take a screenshot" or "Take a screenshot of a window" under "Desktop") and change it to something more reasonable, like Ctrl+Print.

---

### Post by onthenarrowpath on 2009-09-08
I'm encountering the same problem: The trigger in /proc/sys/kernel/sysrq is on 1, and still I'm unable to use the sysrq features. I've tried both ways, the keyboard shortcuts and the command-line.

---

### Post by e64462 on 2010-07-14
This problem has plagued me for months it seems. But finally, rebinding Screenshot to ctrl+Print rather than just Print fixed it for me. Thanks!

---

### Post by Protocol84 on 2010-08-27
I know this is an old topic but if changing the print screen key combo did not help you may need to use Alt+SysRq+R as your first magic key combo. It Switches the keyboard from raw mode, the mode used by programs such as [X11]("http://en.wikipedia.org/wiki/X11") and [svgalib]("http://en.wikipedia.org/wiki/Svgalib"), to [XLATE]("http://en.wikipedia.org/w/index.php?title=XLATE&action=edit&redlink=1") mode which is needed to send commands directly to the kernel.

---

