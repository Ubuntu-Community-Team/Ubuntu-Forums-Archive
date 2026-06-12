---
title: "Upgrade to Hardy failed"
date: 2009-05-30
forum: General Help
---

### Post by kruegger on 2009-05-30
Hi, boys and girls

A couple of days ago I found out that Gutsy is not suported any more.
I then tried to upgrade to Hardy. When the upgrading was about to end, a window opened asking wether I wanted to keep the local GRUB file, among other choices.


I selected this one (because I had configured my menu.lst manually for dual booting) and upgrading froze; the two windows kept open, I can use Ubuntu except sound programs but upgrading is not fully accomplished.


[Here is a screen: pantalla1ie9328.png](http://www.imaxenes.com/imagen/pantalla1ie9328.png.html)

I've got an open terminal in the upgrade manager window but I am clueless on how to proceed.

It is the second time it happens. It smells of bug but I'm not sure.

I wanted to avoid a fresh installation from Hardy cd but... ¿what would you do?

Thanks.

---

### Post by YenTheFirst on 2009-05-30
I'm not sure why it's frozen, so I'm sorry I can't help you with that.

However, I think Hardy might come with a kernel upgrade, so it *might* be necessary to have the updater modify your menu.lst, and then you can manually re-apply the dual boot changes afterwards. (I'm not 100% sure, though)

---

### Post by lykwydchykyn on 2009-05-30
Try opening a terminal and doing these commands:
```

sudo dpkg --configure -a
sudo aptitude -f install
sudo aptitude dist-upgrade

```
That should get things sorted out.

---

### Post by kruegger on 2009-05-30
> **lykwydchykyn said:**
> Try opening a terminal and doing these commands:
```

sudo dpkg --configure -a
sudo aptitude -f install
sudo aptitude dist-upgrade

```
That should get things sorted out.

Hi, lykwyd

I've still got the Updater window open .

In that window, there is a terminal open: root@ubuntu, as in a live cd. 

I've just typed the first command and it says the state data base area is blocked by other process.
To close this Updater window ,(which must be that blocking process), do I have to shut down the whole system?. 

If I do, when I start it anew, will those commands fix the problem?

Can I close this window from command line?

Thanks

---

### Post by lykwydchykyn on 2009-05-30
I don't know if it will reboot if grub install was interrupted.

You shouldn't need to reboot just yet.  

try typing "exit" in that shell and see what happens. If it doesn't continue the upgrade, close out those windows, then run the commands.

---

### Post by kruegger on 2009-05-31
> **lykwydchykyn said:**
> I don't know if it will reboot if grub install was interrupted.

You shouldn't need to reboot just yet.  

try typing "exit" in that shell and see what happens. If it doesn't continue the upgrade, close out those windows, then run the commands.

You were right. It didn't reboot after I "shutdown -h now" the system. I didn't remember that "exit" command. Surely it would have closed that window only.

Anyway, I have restored Gutsy from a backup and I'm in business again.;)

Hardy upgrade, take three.

Let's see what's up now.

Thank you, Lykwyd.

---

### Post by Soul-Sing on 2009-05-31
When upgrading,it is better to get rid of "third party" software.
From getdeb for instance. Make sure that your sources.list is basic, and clean.

---

### Post by kruegger on 2009-05-31
> **leoquant said:**
> When upgrading,it is better to get rid of "third party" software.
From getdeb for instance. Make sure that your sources.list is basic, and clean.

Yes, my sources.list is clean. When I tried third party software in the past I ended up reinstalling Ubuntu.:???:

---

