---
title: "Finding memory leak"
date: 2018-05-07
forum: Desktop Environments
---

### Post by bjorn1232 on 2018-05-07
30 min-1 hour after starting my computer, all 16 GB of my RAM is filled up by something making the computer slow and impossible to work with.
Htop and System monitor doesn't show me which program is responsible for this. Is there some tool I can use to find out what program steals all of my RAM?

[https://i.imgur.com/jm8P8Pa.png](https://i.imgur.com/jm8P8Pa.png)

Please do not link the "Linux ate my ram"-page. It has nothing to do with this problem (my RAM is being *used *by something, it's not being borrowed).

---

### Post by kerry_s on 2018-05-07
seems like a lot of chrome running, i got 10 of chrome running. try doing a:
killall chrome

& see if your memory comes back.

---

### Post by bjorn1232 on 2018-05-08
> **kerry_s said:**
> seems like a lot of chrome running, i got 10 of chrome running. try doing a:
killall chrome

& see if your memory comes back.

It does not. 
By the way, neither Htop or System Monitor says Chrome is using much memoy. 
Is there a way to find out which service, application or script is leaking memory?

---

### Post by kazakore on 2018-05-08
htop then sort order by Memory should give you an idea of what is hogging it all.

---

### Post by monkeybrain20122 on 2018-05-08
xorg and chrome seem to be the culprits. what is your graphic card, which version of Ubuntu? For chrome tabs using a lot of resources use the[ lazy tabs]("https://chrome.google.com/webstore/detail/lazy-tabs/aabgbgciohhaogajcnacpgilhmacdahc?hl=en") addon. I can keep 20+tabs in Chrome on machine with only 4 G or rams with no slow down (Ubuntu 16.04 and 18.04 on unity, FF does a lot better with over 300 tabs)

---

### Post by bjorn1232 on 2018-05-09
> **kazakore said:**
> htop then sort order by Memory should give you an idea of what is hogging it all.
In the image, processes are ordered by memory.

> **monkeybrain20122 said:**
> xorg and chrome seem to be the culprits. what is your graphic card, which version of Ubuntu? For chrome tabs using a lot of resources use the[ lazy tabs]("https://chrome.google.com/webstore/detail/lazy-tabs/aabgbgciohhaogajcnacpgilhmacdahc?hl=en") addon. I can keep 20+tabs in Chrome on machine with only 4 G or rams with no slow down (Ubuntu 16.04 and 18.04 on unity, FF does a lot better with over 300 tabs)

Ubuntu 16.04 with a R9 390. The same thing occurs with a brand new 580 Nitro.

---

### Post by bjorn1232 on 2018-05-22
Does anybody know of a way to find memory leaks with this OS?

---

### Post by again? on 2018-05-22
Monitor your total chrome memory use...
```
watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} /[c]hrome/{x=x+$4;y=y+$6} END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'\'''
```
Look at the chrome setting "Continue running background apps when Google Chrome is closed" in **chrome://settings/system**

Additionally, you could test another display manager to see if the issue is with gdm3 causing high memory use.
Has been a problem in the past but I don't use anymore so not aware of current issues.
```
sudo apt --no-install-recommends install lightdm lightdm-gtk-greeter
```
You should see a dialog to select display manager.
If not, run...
```
sudo dpkg-reconfigure gdm3
```
Reboot.

---

### Post by bjorn1232 on 2018-05-27
> **guber2 said:**
> Monitor your total chrome memory use...
```
watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} /[c]hrome/{x=x+$4;y=y+$6} END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'\'''
```
Look at the chrome setting "Continue running background apps when Google Chrome is closed" in **chrome://settings/system**

Additionally, you could test another display manager to see if the issue is with gdm3 causing high memory use.
Has been a problem in the past but I don't use anymore so not aware of current issues.
```
sudo apt --no-install-recommends install lightdm lightdm-gtk-greeter
```
You should see a dialog to select display manager.
If not, run...
```
sudo dpkg-reconfigure gdm3
```
Reboot.

Thank you for your reply. Much appreciated! 

Your little bash script doesn't increase, it constantly displays 0% memory and 0 memory size. 

I have disabled said options now and will see if that helps. 

I am using lightdm already. Reconfigured it using dpkg-reconfigure. Will see if any of these actions has helped.

Thanks again.

---

### Post by again? on 2018-05-27
> **bjorn1232 said:**
> Thank you for your reply. Much appreciated! 

Your little bash script doesn't increase, it constantly displays 0% memory and 0 memory size. 


I noticed it doesn't display properly when the terminal window is a small size.
Try with the terminal window maximized.

---

### Post by bjorn1232 on 2018-05-27
> **guber2 said:**
> I noticed it doesn't display properly when the terminal window is a small size.
Try with the terminal window maximized.

Woah. Now it works. Wierd glitch. Chrome doesn't use as much memory anymore, it seems like.
Total RAM usage seems to be fine now, it won't break above 7 GB. For anyone else having this problem, this is what I did:
[LIST]
[*]chrome://settings/system
[*]Turned off background apps
[*]Turned off hardware acceleration
[*]dpkg-reconfigure lightdm
[*]Reboot
[/LIST]

Thank you very much for your help guber2!

---

