---
title: "Starting xbindkeys at boot, as root"
date: 2009-05-06
forum: General Help
---

### Post by swinky on 2009-05-06
I'm running Ubuntu 9.04 on a Toshiba Satellite L305. I have been working for a while on a workaround to the brightness keys (fn+F6 and fn+F7). The fn key refuses to be read, but I have managed to get super+F6 and super+F7 to do the same functions using xbindkeys. The problem is that I cannot figure out how to get xbindkeys to run when I boot the computer. Because this workaround uses acpi_fakekey, xbindkeys also needs to be run as root.

I tried a script in /etc/init.d and I think the script is runs, but when the computer boots, xbindkeys is not running. dmesg reports xbindkeys tries to run but then segfaults:
> [   33.841950] xbindkeys[2856]: segfault at 0 ip b7cac939 sp bfbd7098 error 4 in libc-2.9.so[b7c35000+15c000]
If that same script is run manually, xbindkeys starts fine. The script itself is really just one line that tells xbindkeys to run and the location of the file:
> #! /bin/sh
/usr/bin/xbindkeys -f /etc/xbindkeys/xbindkeysrc
(I opted to put the config file in /etc rather than my home directory, as is the default with xbindkeys)


I have tried putting it in crontab (with sudo crontab -e) and added the line "@reboot /etc/init.d/xbindkeys" (because I know that the script works) and also tried it with "@reboot /usr/bin/xbindkeys -f /etc/xbindkeys/xbindkeysrc". Neither seems to do anything, xbindkeys still is not running at boot.

Are there any other ways to start xbindkeys at boot, and as root? These are the only two ways I can think of and neither seem to work.

Help is *greatly* appreciated, I have spent so much time on this workaround and this is the last hurdle to get over. Toshiba laptops can be really picky when it comes to Linux.

---

### Post by BslBryan on 2009-05-06
Hello, swinky.  :-)

Okay, so, there are a couple of options.

The first thing you can do is ```
gksudo gedit /etc/sudoers
```

And add this line to the end of the document:
```
username ALL= NOPASSWD: /etc/xbindkeys/xbindkeysrc 
```

Or, you can do System --> Preferences --> Sessions, and click on the Startup Programs tab.
Then, click +Add.

For the "command" line, you can paste this:
```
echo "yourpasswordhere" | sudo -S /etc/xbindkeys/xbindkeysrc 
```

The first way seems a little more secure, though, IMO. :-)

Anyway, best to you, swinky.  I hope I've been of some help.

---

### Post by swinky on 2009-05-06
Great, thank you! I added the line in sudoers and started up xbindkeys in the start-up programs, works like a charm! I really appreciate the help! :)

---

### Post by BslBryan on 2009-05-06
No problem. :-)  

I'm really glad I could help!

---

### Post by kpkeerthi on 2009-05-06
Just add this line to 
```

/usr/bin/xbindkeys -f /etc/xbindkeys/xbindkeysrc 

```
to **/etc/rc.local**. Commands in this file will run at boot with su privileges. No need for changing sudoers.

---

### Post by swinky on 2009-05-07
Actually, putting it in /etc/rc.local doesn't work either, I think it has the same problem that puting a script in /etc/init.d/ has. I'm not entirely sure WHAT that problem is, but so far it has only worked by changing the sudoers file and setting it to start up with Startup Applications.

---

### Post by BslBryan on 2009-05-07
> **swinky said:**
> Actually, putting it in /etc/rc.local doesn't work either, I think it has the same problem that puting a script in /etc/init.d/ has. I'm not entirely sure WHAT that problem is, but so far it has only worked by changing the sudoers file and setting it to start up with Startup Applications.

Hmm...  That's strange, as I would have pointed you first to kpkeerthi's idea if it had crossed my mind. :-k

Anyway, at least we *have* come up with a way for it to work.  

Regards, swinky. :-)

---

### Post by lunatico on 2009-05-13
> **BslBryan said:**
> 
The first thing you can do is ```
gksudo gedit /etc/sudoers
```

And add this line to the end of the document:
```
username ALL= NOPASSWD: /etc/xbindkeys/xbindkeysrc 
```


I'm trying to run a different script from /etc/rc.local but get the same problem, the script is actually not executed.
I was going add that line to the /etc/sudoers file but it says it is a read-only file and can't save the changes.
I'm on 9.04 UNR if that matters.

Is this a problem with 9.04? I used to run scripts on /etc/rc.local with no problems before.

---

### Post by swinky on 2009-05-13
> 
Is this a problem with 9.04? I used to run scripts on /etc/rc.local with no problems before. 

I don't really know if it is a 9.04 problem or not. xbindkeys was the only thing I've ever had real issues starting at boot. 

As far as editing the sudoers file, make sure you are editing it with root access. You should also edit it with the visudo command rather than using nano/gedit/vi etc. You'd have to ask somebody with a little more knowledge than me *exactly* why that is, but I do know that it helps to prevent the file from being screwed up. And it is an important file, to be sure.

Open up a terminal window and type
```
sudo visudo
```

It will then ask you which editor you want to use. I am pretty sure the default is nano (which is definitely easier to use.) Add the line at the bottom and save it.

If you've never used nano before, it is a pretty easy terminal file editor. Just scroll down to the bottom with either the down key or page down key. Add the line to the bottom of the file and press ctrl+x to exit. When you exit, it will prompt you if you want to save it. Hit the Y key. It will ask what you want to save it as, just hit enter.

---

### Post by lunatico on 2009-05-13
> **swinky said:**
> As far as editing the sudoers file, make sure you are editing it with root access. You should also edit it with the visudo command rather than using nano/gedit/vi etc. You'd have to ask somebody with a little more knowledge than me *exactly* why that is, but I do know that it helps to prevent the file from being screwed up. And it is an important file, to be sure.


Thanks! sudo visudo did the trick!

---

