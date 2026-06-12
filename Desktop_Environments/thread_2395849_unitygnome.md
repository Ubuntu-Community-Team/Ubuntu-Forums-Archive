---
title: "unity/gnome"
date: 2018-07-07
forum: Desktop Environments
---

### Post by jgw on 2018-07-07
I installed, and am running with 18.04   I just remembered that I was looking at a unity option page and then forgot until now.  I was under the assumption that I am running with gnome interface, now.  If true then how could I have had a unity option page.  Is there a way to see what, exactly, I am using?  Is it possible to have both running at the same time?  If I am running both this might explain some of the freezes, etc. that I have been experiencing.

Thank you..............

---

### Post by bodhin2 on 2018-07-07
new here, but it is my understanding this is the new gnome.  i may be wrong.

---

### Post by #&amp;thj^% on 2018-07-07
> **jgw said:**
> I installed, and am running with 18.04   I just remembered that I was looking at a unity option page and then forgot until now.  I was under the assumption that I am running with gnome interface, now.  If true then how could I have had a unity option page.  Is there a way to see what, exactly, I am using?  Is it possible to have both running at the same time?  If I am running both this might explain some of the freezes, etc. that I have been experiencing.

Thank you..............

Yes it is still possible to install Unity via command or installation media.
I need to heed the new rules here regarding Unity as it is no longer a supported flavor here in UF but lives here: [https://community.ubuntu.com/c/desktop/ubuntu-unity-dev](https://community.ubuntu.com/c/desktop/ubuntu-unity-dev) 

But to install it run:
```
sudo apt install ubuntu-unity-desktop

```
And best to use lightdm also.
Please read here to keep me out of trouble: [https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux) 
To show what you are now using do:
```
echo $DESKTOP_SESSION
```
And will show Gnome instaed of Unity.
EDIT: BTW I very much doubt you are running both unless you installed the package I mentioned above.
Good Luck

---

### Post by jgw on 2018-07-08
Thank you for the replies!

I don't think I was clear.  I did a clean install of 18.04 and have been using it for a few weeks now.  I was rooting around and suddenly found a page that had options for unity with some things checked and others not.  I have not installed unity which I the reason for this post.  If I have installed it, for some reason unknown, how do I get rid of it?  (trying to stay as vanilla as possible)

Thank you.............

---

### Post by bodhin2 on 2018-07-08
wish i could help but i am a chocolate guy - just a joke.  maybe if i can get some time i can poke around a bit and maybe if you cane send us in the right direction that may make it easier.   what page are you speaking of????

---

### Post by #&amp;thj^% on 2018-07-08
> **jgw said:**
> Thank you for the replies!

I don't think I was clear.  I did a clean install of 18.04 and have been using it for a few weeks now.  I was rooting around and suddenly found a page that had options for unity with some things checked and others not.  I have not installed unity which I the reason for this post.  If I have installed it, for some reason unknown, how do I get rid of it?  (trying to stay as vanilla as possible)

Thank you.............

To see use what I first posted
```
echo $DESKTOP_SESSION
```
I do have Unity so mine will show:
```
 echo $DESKTOP_SESSION
unity

```
And Check for this also:
```
 apt policy ubuntu-unity-desktop
ubuntu-unity-desktop:
  Installed: 0.1
  Candidate: 0.1
  Version table:
 *** 0.1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```
And thanks for making your request clearer. :)

---

### Post by deadflowr on 2018-07-08
>  If I am running both this might explain some of the freezes, etc. that I have been experiencing.

How dire are the freezes?
Are they short, where things just stop for a moment,
or do they completely shutdown the system, leaving only a total restart to fix?


(Ftr, you can't run both gnome and unity at the same time without doing some hefty lifting on your own.
So I highly doubt that would be in anyway any kind of issue.
And in fact perhaps installing the unity desktop might give you a base to see if the freezes are session related or maybe more nefarious; ie, a kernel or Xorg bug
You can just switch desktops at login to try them out and see if the freezing is common across desktop sessions)

There are probably a couple dozen bugs on gnome-shell (Ubuntu's 18.04 default desktop) freezing.
But the type of freezes reported are probably differing. so helps to know to narrow that down.

Some random thoughts

---

### Post by monkeybrain20122 on 2018-07-08
> **jgw said:**
> I installed, and am running with 18.04   I just remembered that I was looking at a unity option page and then forgot until now.  I was under the assumption that I am running with gnome interface, now.  If true then how could I have had a unity option page.  Is there a way to see what, exactly, I am using?  Is it possible to have both running at the same time?  If I am running both this might explain some of the freezes, etc. that I have been experiencing.

Thank you..............


I have been running both for a while and didn't have any problem (just removed gnome shell last week, but they had coexisted since almost the first day when 18.04 was released). OK, to be clear by "running both" I meant I have both installed though I almost use unity exclusively except to log into gnome shell once in a blue moon to check it out and then happily log back into unity.  So maybe there are issues in gnome shell that I didn't notice.

But your freeze may also stem from something deeper like graphic driver issues.

---

### Post by jgw on 2018-07-09
Wow!  Thanks for all the replies!

First:
echo $DESKTOP_SESSION                        got me "ubuntu"
apt policy ubuntu-unity-desktop             told me that ubuntu-unity-desktop did not exist
So, I expect I was full of beans on this one.

Sometimes the freezes are short and waitable.  Other times they require a re-boot.  The re-boot ones usually happen when I am in firefox or I have clicked on the dotted thing at the end of the dock.  I did find out, however, that when I accomplish the same thing, with "super a" it doesn't seem to freeze.    The problem with the freezes is that I have yet to figure out, exactly, what I did to cause it.  Perhaps I should figure out how to capture all my keystrokes, put them to a file, etc. and, when a freeze happens I can then go back to the file with the keystrokes and see what I did?  If, for instance, I had such a file and then had to re-boot I could save the first file and then check the second and see if there was a repeat?

I also tend to suspect that this may have something to do with my display (no basis for my suspicion) as I have this machine hooked to a 4k tv and it was a devil to setup:

  *-display     (sudo lshw -c video)
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       using a resolution of: 3840x2160 (16:9)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff

---

### Post by jgw on 2018-07-12
I am going to call this one solved.  With the suggestions I think I proved, to myself, that I was full of beans and a bit paranoid. 

thanks for all the help!

---

### Post by bodhin2 on 2018-07-12
hopefully they were at least mocha java or kenyan AA beans!   i use whole beans!

---

