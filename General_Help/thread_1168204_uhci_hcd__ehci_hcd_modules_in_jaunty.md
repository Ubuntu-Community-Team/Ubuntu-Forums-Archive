---
title: "uhci_hcd / ehci_hcd modules in jaunty"
date: 2009-05-23
forum: General Help
---

### Post by smani on 2009-05-23
Hello,
was wondering if anyone knew what happened to the uchi_hcd / ehci_hcd kernel modules in jaunty, are they now compiled directly into the kernel and not as modules anymore? The problem is I need to remove the usb modules from the kernel before suspending, otherwise the computer will immediately resume (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252)). Is there any other way to disable USB?
Thanks!
smani

---

### Post by Aviopene on 2009-07-17
Hi!

Yes, they are compiled in the kernel. I read somewhere that it's for ensuring that ehci is loaded before uhci or ohci, otherwise it can't correctly load.

I wonder why my default 2.6.28-13 kernel doesn't have a /proc/config.gz, but the symbols in System.map are still present and, ehci/uhci are still (somewhat) working.

I have a similar problem too. My USB 2.0 disks don't get attached to ehci hub, so I get 2.0 disks running at 1.0 speed. I'd like to unload all usb-related modules, but I can't.

As far as I know, we'll have to recompile our own kernel if we want to get load/unload for these modules. Otherwise, you can try a roll-back to an older kernel...

Well, I'm quite disturbed from this behaviour of Jaunty, and I'm also disturbed because I don't see any other solution than changing to an older kernel. :confused:

Bye
Avio

---

### Post by Moshanator on 2009-12-20
I have the same problem (having to stop USB before suspend) and [here]("http://ubuntuforums.org/showthread.php?p=8530567")'s a workaround. Give it a try.

---

### Post by smani on 2009-12-20
Thanks a lot for your reply. I'll quickly make a script that does this automatically and then post back.

---

### Post by smani on 2009-12-20
Okay, script attached. Place it in /etc/pm/sleep.d (making it executable and removing the .txt extension) and it will do the magic :D (p.s. I am not really happy with storing the id's of the disabled devices in files under tmp, but can't really think of more elegant solutions...). Thanks again for your hint!

Cheers

smani

---

### Post by Moshanator on 2009-12-20
Thanks, nice script. Are those long numbers IDs of connected USB devices?
Also, the script works, it unbinds and binds everything as needed, but after resuming the mouse (and the rest of USB, I suppose) is sluggish and responds very slowly. No such thing occurs when unbinding/binding manually from the terminal. When I suspend, resume, the mouse becomes slow, then I repeat the unbind/bind process manually, everythings starts working perfectly again.
EDIT:
I fixed this by adding another pair of bind/unbind calls into the resume block. I have no idea why they're needed, but everything works nonetheless. Will post a fixed version soon.

---

### Post by Moshanator on 2009-12-20
Here it is.
Is there anywhere we could submit this fix? So that it would be incorporated in the next Ubuntu release?

---

### Post by smani on 2009-12-20
An ugly hack like this is very unlikely to be incorporated in any release. But I'll link to the post in launchpad bugreport ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289252)) so that other people will find it easily. Lastly, it appears that a related bug has been fixed upstream ([http://bugzilla.kernel.org/show_bug.cgi?id=11268](http://bugzilla.kernel.org/show_bug.cgi?id=11268)), though I don't know if the patch didn't make it into 2.6.31 or does not fix our issue, I'll test 2.6.32 / 2.6.33 some day and in case it persists I'll report back there if I got some time to waste, otherwise I'll simply wait until the mainboard dies and replace it by one without a garbage BIOS like this one :D

Cheers

smani


Edit: what do you mean by "Are those long numbers IDs of connected USB devices?"

---

### Post by Moshanator on 2009-12-21
e.g. what does 0000:00:1d.0 mean? Is it a driver, a device, or something else?

---

### Post by Silas (son of Silas) on 2009-12-21
This doesn't seem to work for me. The PC still resumes immediately unless its the first suspend after a reboot.

If I run powertop and wait for the suggestion: > Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config
 then press U as suggested, I am then able to suspend, I think thereby confirming that it is indeed the same issue you are describing in this thread.

Could you possibly please help me troubleshoot this?

I assume that when suspending the scripts that are in '/etc/pm/sleep.d' are executed including the one on this thread, which unloads the USB devices so that they don't cause the pc to automatically resume, then reload when the PC resumes.

If my understanding is correct, how can I check if your script is actually running and working as desired?

UPDATE:
I ran > sudo chown -R root /etc/pm/sleep.d and now it seems to be working (well its worked twice so far, I will try it a few more times.

---

### Post by smani on 2009-12-21
> **Moshanator said:**
> e.g. what does 0000:00:1d.0 mean? Is it a driver, a device, or something else?

From what I know basically BUS device ID's, see [http://wiki.xensource.com/xenwiki/BDFNotation](http://wiki.xensource.com/xenwiki/BDFNotation) for example.

> **Silas (son of Silas) said:**
> 
If my understanding is correct, how can I check if your script is actually running and working as desired?


Basically you could make that the scripts logs some information somewhere, say modify the last section to
```
case "$1" in
	hibernate|suspend)
		echo "Unbinding ports" >> /tmp/mycustomlog.log
		unbind_usb;
	;;
	thaw|resume)
		echo "Binding ports" >> /tmp/mycustomlog.log
		bind_usb;
	;;
	*)
	exit 1;
	;;
esac;
```

---

### Post by mehturt on 2010-01-19
this workaround fixed the problem for me as well, but for some reason my wireless USB device (Asus WL-167g) stopped working after a few suspend/resumes.. it could not connect to the wireless network
I needed to unplug and plug the USB device for it to work again, I am not sure whether it is related to this, but it did not happen to me before..

---

### Post by smani on 2010-01-19
You could try unloading the driver of the usb device before disabling the usb ports and then reloading it after the ports got reenable, that is modify the script in a similar fashion to

```

case "$1" in
	hibernate|suspend)
		rmmod <module_name>;
		unbind_usb;
	;;
	thaw|resume)
		bind_usb;
		modprobe <module_name>;
	;;
	*)
	exit 1;
	;;
esac;

```
where you need to find the correct <module_name>, for example by looking at the output of lshw.

---

### Post by mehturt on 2010-01-19
what is strange to me that the USB device did not work even after a few reboots.. I needed to unplug it manually and then plug it in again.. strange

---

### Post by smani on 2010-01-19
That is indeed strange, sort of looks like the card gets really confused somehow. Try with the module nevertheless, it might allow the card to suspend in a more gracefully way hence preventing it getting confuesed.

---

### Post by mehturt on 2010-01-19
I have identified the driver to be rt73usb, so I did the trick you suggested, but it is not working - it behaves the same as without it.
I need to physically unplug the USB device and plug it in in order to start working.  And I have absolutely no idea why it does not work even after restart.
I have spotted a difference in lsmod's output; when the wireless is working, there is:
aes_i586 2
when it is not working, there is:
aes_i586 0
As I understand aes_i586 has something to do with encryption, could it be the reason why I cannot connect to my encrypted network?  Even if that's true, I have no idea what causes it.

---

### Post by smani on 2010-01-19
Hm... Here is a shot in the blue, but what might be the problem is that the aes module is somehow orphaned when the usb ports are disabled... Before suspending (i.e. when things are working), try looking at the output of lsmod and check all dependencies (i.e. the used by column) of the modules you suspect are involved, then try unloading all of them in the correct order and reloading them on resume in the reversed order.

---

### Post by mehturt on 2010-02-03
I played with this a little yesterday.. what I do is:
- stop wicd
- remove module rt73usb
- poweroff the usb port (echo suspend > /sys/bus/usb/@#$/power/level)
The led light on my usb dongle goes off; then:
- poweron the usb port (echo auto > /sys/bus/usb/@#$/power/level), or echo on > ...
- modprobe rt73usb
- start wicd
But the wireless no longer connects.. I think it's a bug in the driver..

---

