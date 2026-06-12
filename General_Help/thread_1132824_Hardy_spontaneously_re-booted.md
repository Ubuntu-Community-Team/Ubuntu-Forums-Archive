---
title: "Hardy spontaneously re-booted"
date: 2009-04-22
forum: General Help
---

### Post by meanmrmustard on 2009-04-22
My Hardy installation just automagically re-booted.
When it started again it was extremely slow, couldn't get a terminal to open, the cursor would freeze for about ten seconds at a time then it would move again but just for a second or two. Trying to open Thunderbird just froze the screen again.

I ssh'd into the machine and took a look at dmesg but I don't know if it's telling me something relevant or not so I've uploaded a portion of it.

I'd appreciate if someone would take a look at the file and maybe give me a pointer or two.
Maybe another log would help?

[http://pastebin.ca/1399653](http://pastebin.ca/1399653)

thanks

---

### Post by WatchingThePain on 2009-04-22
Hi,
I'm no expert but to start there seems to be a lot of nvidia stuff in there.
Computers can shutdown if the power supply is not enough or if they get too hot.

---

### Post by meanmrmustard on 2009-04-22
> **WatchingThePain said:**
> Hi,
I'm no expert but to start there seems to be a lot of nvidia stuff in there.
Computers can shutdown if the power supply is not enough or if they get too hot.

I appreciate the input from everyone, expert or not.
The machine has been running Hardy since it was released and Gutsy before that. Nothing has been added - all the same hardware as when it was originally installed.
 
I had been running XGL but just switched back to the nvidia driver and xserver-xorg as it was originally. Since I had just tried XGL a couple days ago, I thought that was what was slowing things down but it's slow just same after I switched back.

---

### Post by WatchingThePain on 2009-04-22
So this seems like it's all related to video drivers.
O.k. options.
Where did you get your nvidia driver from?.
As you are aware there is more than one way of getting the video driver and some work better than others.
To isolate the problem:
Maybe switch temporarily to vesa driver to see if that prevents it rebooting.

file etc/X11/xorg.conf may need editing.

To check errors during boot type dmesg | less in terminal.

Also be patient as later tonight the experts will come on.
If we just check the fundamentals it will help you later.

---

### Post by meanmrmustard on 2009-04-22
> **WatchingThePain said:**
> So this seems like it's all related to video drivers.
O.k. options.
Where did you get your nvidia driver from?.
As you are aware there is more than one way of getting the video driver and some work better than others.
To isolate the problem:
Maybe switch temporarily to vesa driver to see if that prevents it rebooting.

file etc/X11/xorg.conf may need editing.

To check errors during boot type dmesg | less in terminal.

Also be patient as later tonight the experts will come on.
If we just check the fundamentals it will help you later.

I don't remember if I downloaded it from Nvidia or what.

I'm looking at xorg.conf and it has neither nv or nvidia listed - nor vesa for that matter.
Here's the file 
[http://pastebin.ca/1399916](http://pastebin.ca/1399916)

It's been quite a while since I've had to edit this file but it doesn't look right to me.
edit:
Also I used to reconfigure xserver-xorg with the "dpkg-reconfigure..." command. It no longer lets me choose a driver or resolution in the process. Not sure how to do it any more.

---

### Post by meanmrmustard on 2009-04-22
Anyone?

---

### Post by WatchingThePain on 2009-04-23
Yeah that's not right at all.
There is meant to be a section like:

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "All"
    BoardName      "All"
EndSection

My suggestion was to put VESA (the basic driver)for now.

On your system under system , hardware, restricted drivers nvidia should have a tick in the box.
Try using another tool to auto configure the xorg file.

Xorg -configure

 Read at the end it makes a file called xorg.conf.new which you might need to copy to /etc/X11/xorg.conf using the cp command.

If it tells you it failed you may need to then try manually adding the missing sections.
The section with horizontal and vertical refresh rates is important.
There are lots of xorg.conf examples around in the forums.


Also have you tried booting up in recovery mode the type the command:   xfix


When xorg is working, typing startx at the command line should give you a black screen with a white x in the middle.

---

### Post by meanmrmustard on 2009-04-23
Watchingthepain

Alright!
The first thing I did was run xfix in recovery mode.
Everything's normal again - so I guess it was the nvidia driver.
I'll download a new one (I believe I got the nvidia-glx package from the repos originally) and see what happens when I get compiz running again.
Thanks again.

Mr. M
 
Installed the newest(?) nvidia driver using EnvyNG and the screen has returned to locking up and the machine will probably re-boot if I wait long enough.

---

### Post by WatchingThePain on 2009-04-23
Ok progress Good,
Remember with envy you have to remove the drivers before any full OS update.

---

### Post by meanmrmustard on 2009-04-23
> **WatchingThePain said:**
> Ok progress Good,
Remember with envy you have to remove the drivers before any full OS update.

I think I may try to manually install a different driver with Envy - I used the automatic feature first time.

With the Ng version there's no need to remove drivers before an upgrade - unless I read that wrong.

---

### Post by meanmrmustard on 2009-04-23
> **meanmrmustard said:**
> I think I may try to manually install a different driver with Envy - I used the automatic feature first time.

With the Ng version there's no need to remove drivers before an upgrade - unless I read that wrong.

Well....  it doesn't like any of the proprietary drivers.

---

### Post by WatchingThePain on 2009-04-23
Hmm I think maybe ng is different then but better safe than sorry.
I use a combination of proprietary driver and editing xorg.
You can also build the driver from source if nothing else works.
There should be other posts in the forum pertaining to your card with Hardy.
Believe it or not setting up nvidia on Ubuntu is relatively easy compared to other distros (and other cards)!.

---

### Post by meanmrmustard on 2009-04-24
> **WatchingThePain said:**
> Hmm I think maybe ng is different then but better safe than sorry.
I use a combination of proprietary driver and editing xorg.
You can also build the driver from source if nothing else works.
There should be other posts in the forum pertaining to your card with Hardy.
Believe it or not setting up nvidia on Ubuntu is relatively easy compared to other distros (and other cards)!.

Building from source is the only thing I haven't tried at this point - so I guess that's next.
I've been using nvidia cards since Warty and have never seen anything like this.

I was mistaken the box didn't re-boot, it simply shut down and restarted X.
I'll start another thread.

---

