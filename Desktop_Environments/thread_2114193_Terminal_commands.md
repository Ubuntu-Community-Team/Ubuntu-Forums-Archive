---
title: "Terminal commands"
date: 2013-02-09
forum: Desktop Environments
---

### Post by KegHead on 2013-02-09
Hi!

Reading blogs recently and wondering if the following commands really help:

sudo gedit /etc/init.d/rc

sudo gedit /etc/default/grub

---

### Post by fj401971 on 2013-02-09
Help with what?  Those commands open up files for reading/editing....  

rc is for boot scripts
and grub is for your grub (bootmaster) configuration...

Not really sure of your question...

---

### Post by sudodus on 2013-02-09
> **KegHead said:**
> Hi!

Reading blogs recently and wondering if the following commands really help:

sudo gedit /etc/init.d/rc

sudo gedit /etc/default/grub

What do you want to do?

I haven't tampered with [FONT="Courier New"]/etc/init.d/rc[/FONT] yet.

I do change the [FONT="Courier New"]/etc/default/grub[/FONT] file to improve the behaviour during boot and in text screens. You need to run sudo update-grub for the changes to work. They will be transferred to [FONT="Courier New"]/boot/grub/grub.cfg[/FONT]

---

### Post by KegHead on 2013-02-09
Hi!

I'm always looking for speed!

Just curious if these commands will make any difference.

KegHead

---

### Post by sudodus on 2013-02-09
> **KegHead said:**
> Hi!

I'm always looking for speed!

Just curious if these commands will make any difference.

KegHead

You can decrease the time at the grub menu by changing
```
GRUB_TIMEOUT=10
```
in [FONT="Courier New"]/etc/default/grub[/FONT]

Boot will be ugly but slightly faster, if you switch off splash: remove splash in
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

---

### Post by tgalati4 on 2013-02-09
Perhaps some links to the blogs in question.  What kind of speed improvements are you looking for?  If you want to boot faster, you can recompile your kernel and remove a lot of stuff that is not applicable to your hardware.

You can put tuning parameters in the rc file to take effect at boot time.  The grub file can pass kernel parameters--which can also effect speed.  What are your goals?

---

### Post by KegHead on 2013-02-09
Hi!

I'm interested in using all four cores booting up.

Is this the correct command:

sudo gedit /etc/init.d/rc

Any other commands go with it?

Thanks!

KegHead

---

### Post by tgalati4 on 2013-02-09
I was under the impression that multiple cores are used during bootup.

```
man ureadahead
```

After several boots, your system is profiled and the time it takes to load files is tracked so that other boot processes can be performed during that "dead" time.

If you really want to swallow the red pill and crawl down that rabbit hole, then install and get smart with bootchart:

Mint14-Extensa upstart # apt-cache search bootchart
bootchart - boot sequence auditing
pybootchartgui - boot sequence visualisation

```
sudo apt-get install bootchart pybootchartgui
```

Show us your results.

---

### Post by KegHead on 2013-02-09
Hi!

You are correct.

It must be something new in 12.10.

KegHead

---

### Post by KegHead on 2013-02-09
See attached.

---

### Post by stinkeye on 2013-02-09
> **KegHead said:**
> Hi!

I'm interested in using all four cores booting up.

Is this the correct command:

sudo gedit /etc/init.d/rc

Any other commands go with it?

Thanks!

KegHead
All that command does is open the **/etc/init.d/rc** script in gedit
as root so you can edit it.
...and you should use [COLOR="Red"]gksudo[/COLOR] when running gui applications as root.
Mess with the file and you may not be able to boot.

---

### Post by KegHead on 2013-02-09
Hi!

Copy the info.

I'm pretty happy with the performance, but always looking for more.

It looks like 12.10 covers a lot of bases.

Guess I'll wait for my 8 core overclock build.

KegHead

---

### Post by KegHead on 2013-02-10
Hi!

Closing out.

Thanks for replies.

KegHead

---

