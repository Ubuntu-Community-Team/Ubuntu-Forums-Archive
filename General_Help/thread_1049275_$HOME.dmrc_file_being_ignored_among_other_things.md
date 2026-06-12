---
title: "$HOME/.dmrc file being ignored? among other things"
date: 2009-01-24
forum: General Help
---

### Post by HarmonicaGoldfish on 2009-01-24
Last week I made a big mistake and enabled some updates that I should not have enabled (pre-released updates (Intrepid Proposed) ). My x-server appears to have gotten somewhat borked. It takes anywhere from 3 to 10 attempts to boot my Dell Inspiron 1525 laptop (Ubuntu/Ubuntu studio blend 8.10) through to the desktop. It usually gets to the Ubuntu Studio splash then gives me a screen of coloured lines, then intermittent black and grey screens. 
 
When I do get through to the desktop, it is only after I get this message and click ok. This part is new, it only began happening yesterday. I have NO idea what it means.

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.



At the same time as all of this is happening, I have a recurrence of an old issue with Firefox 3 where it takes up the whole screen and I need to hit f11 twice to fix it each time I launch the browser. This first happened about a month ago, but at the time was fixed with an update I believe.

Do you think these things are related?

Is it possible to rollback my settings to before last weekend? Kind of like Windows system restore? 

Any ideas on how to fix the boot issue? 

Thanks so much for any help!

---

### Post by philinux on 2009-01-24
In this order from a terminal.

chmod 700 /home/username

chmod 644 /home/username/.dmrc

---

### Post by taurus on 2009-01-24
Boot into recovery mode.  Then, _assuming_ your login name is harmon, run

```
chown -R harmon:harmon /home/harmon
chmod -R 755 /home/harmon
chmod 644 /home/harmon/.dmrc
shutdown -r now
```
Now, see if you still get that message when you log in as harmon and with your password.

---

### Post by HarmonicaGoldfish on 2009-01-24
Do these two strings of commands have the same results?

```
chmod 700 /home/username

chmod 644 /home/username/.dmrc
```

and 

```
chown -R harmon:harmon /home/harmon
chmod -R 755 /home/harmon
chmod 644 /home/harmon/.dmrc
shutdown -r now
```

I do not know how to boot into recovery mode. So if they have the same results, I'll do the first option :) Otherwise, how do I boot into recovery mode?

Also, do you think this is related to boot issue with the video display?
thanks!

---

### Post by taurus on 2009-01-24
When you first turn on your machine (or reboot), you would get a message from the BIOS and after that, you would see the word GRUB on the top corner.  You have 3 seconds (you probably would see the count down on the top right) to press the Esc key to bring up the menu.  In there, use the arrow to highlight the second line (recovery mode) and boot from that.

---

### Post by philinux on 2009-01-24
> **HarmonicaGoldfish said:**
> Do these two strings of commands have the same results?

```
chmod 700 /home/username

chmod 644 /home/username/.dmrc
```

and 

```
chown -R harmon:harmon /home/harmon
chmod -R 755 /home/harmon
chmod 644 /home/harmon/.dmrc
shutdown -r now
```

I do not know how to boot into recovery mode. So if they have the same results, I'll do the first option :) Otherwise, how do I boot into 
recovery mode?

Also, do you think this is related to boot issue with the video display?
thanks!

The official page,
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by HarmonicaGoldfish on 2009-01-24
Thanks for the tips. I went through the steps on the official page provided by philinux (thanks). I've logged out and back in, but am a bit afraid to restart! I never know if I'll get through to a desktop. Guess I better try it out. Wish me luck.

---

### Post by HarmonicaGoldfish on 2009-01-24
So it took 4 tries to reboot. There is definitely something wrong with the video display. But when it finally went through to desktop I did not have the HOME error so that part was fixed. Thanks!

Anyone know of how to fix the booting issue?

---

### Post by cariboo on 2009-01-24
Start in recovery mode and at the menu select xfix, once it has created a new /etc/X11/xorg.conf, choose resume and continue on to your desktop.

You stated you didn't know how to start in recovery mode. WHen you see grub starting press the escape key to view the grub menu. Use the arrow keys to go to recovery mode and hit enter.

Jim

---

### Post by derhov on 2009-01-26
Thanks, taurus.  That worked for me.

---

### Post by HarmonicaGoldfish on 2009-01-26
> **cariboo907 said:**
> Start in recovery mode and at the menu select xfix, once it has created a new /etc/X11/xorg.conf, choose resume and continue on to your desktop.

You stated you didn't know how to start in recovery mode. WHen you see grub starting press the escape key to view the grub menu. Use the arrow keys to go to recovery mode and hit enter.

Jim

Just tried this. I seem to have 4 different 8.10 kernels. How do I know what to choose? Is this normal? Could this be part of my issue?

---

### Post by jocko on 2009-01-26
> **HarmonicaGoldfish said:**
> Just tried this. I seem to have 4 different 8.10 kernels. How do I know what to choose? Is this normal? Could this be part of my issue?
It's perfectly normal to have several kernels to choose from, when kernels are upgraded the old one is kept as a backup in case the new one doesn't work.
For every kernel there are two boot options in the menu, one normal and one recovery mode. So the menu may say something like this:
```
Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic ([COLOR=Red]recovery mode[/COLOR])
Ubuntu 8.10, kernel 2.6.27-10-generic
Ubuntu 8.10, kernel 2.6.27-10-generic ([COLOR=Red]recovery mode[/COLOR])
```To get to [COLOR=Red]recovery mode[/COLOR], select the second option from the top [newest kernel and ending with ([COLOR=Red]recovery mode[/COLOR])], just like [Taurus]("http://ubuntuforums.org/showpost.php?p=6609352&postcount=5") said...

---

### Post by HarmonicaGoldfish on 2009-01-26
Thanks for the clarification! I tried that and it didn't work. I guess I am looking at a re-install.

---

### Post by jdzitro on 2009-01-28
Thanks for posting those commands. They worked perfectly after logout/login.

The issue never made any real problems for me, but it was just kinda annoying.

---

### Post by HarmonicaGoldfish on 2009-01-28
Just to follow up, I ended up doing a fresh install of 8.10 and I am so glad I did! All of my issues have been resolved as well as a couple of other issues that I didn't mention - such as not being able to use my network manager. Before, when I disconnected from the Internet I had to reboot (you can imagine how much fun that's been, having to reboot and reboot and reboot for the past week) because my network manager was 'unmanaged', but now it works just fine. Wonder if some of the problem was that it was an upgrade and not a fresh install? In any case, glad I'm back to normal.

How does one put a [solved] tag on a thread? I think there used to be an option for that. Can't find it?

---

