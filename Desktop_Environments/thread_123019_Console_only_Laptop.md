---
title: "Console only Laptop"
date: 2006-01-29
forum: Desktop Environments
---

### Post by 3x3cvt0r on 2006-01-29
Hi am planning on a "Cubuntu" (Console only Ubuntu) for  system administrators.  The reason behind this is that our office has a spare 200 MHz IBM laptop with 64MB, and 4GB hard drive.  I understand that X.org will really take up a lot of space and resources so i decided to forgo all GUI's and just live in the console with this one.  I am already looking at a few console based applications for the following functions.

1.  Mail client 
2.  Jabber messenger client
3.  Text (vim/nano)

i'd to ask the following questions:

a.  Is this plan/project feasible?
b.  how can I change the resolution of the console fonts?  currently its too big for my taste, i'd like to make it smaller so I can fit more in my screen.
c.  are there any console based spreadsheets out there?

Thanks for any replies.

---

### Post by stuporglue on 2006-01-29
I'd actually recomend installing Xubuntu. It does include X, but with only 4GB, you're not going to use the laptop for major storage and might as well use the space to make life easier. 

Oleo is a text based spreadsheet. Haven't used it though. 
[http://www.gnu.org/software/oleo/oleo.html](http://www.gnu.org/software/oleo/oleo.html)

Xubuntu uses XFCE for it's WM, and I've used it on a 200 MHz with 65MB computer before. It's not bad if you only run one program at a time. Gnumeric would then be a good spreadsheet program. Abiword for documents (or Vim if you prefer), and Xpdf for pdfs. 

Xubuntu link: [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

EDIT: 
DSL is a great option for old laptops too. I have it on a PI with 24 Mb of RAM. [http://damnsmalllinux.org/](http://damnsmalllinux.org/) It's a 50 Mb download and based on Knoppix. I wouldn't say it flys on my computer, but it's speed is reasonable. You can enable apt and install a variety of Debian packages.

---

### Post by mcduck on 2006-01-29
That's a nice idea. Who needs X anyway ;)

1. pine and mutt come to mind.

2. what's wrong with IRC :confused:  Sorry, I have no idea about this one.

3. vim & nano are both nice, and I also like jed much.

a. absolutely. 

b. You can set CLI resolution in grub config (/boot/grub/menu.lst) by adding 'vga=792' to your kernel line. (for 1024*768 and 24b colors) Or replace 792 with other code for other resolutions.

By the way, don't forget mplayer, so you can use 'mplayer movie.mpg -vo aa' to watch your movies on Cubuntu. And MPD + ncmpc for music player :D

---

### Post by 3x3cvt0r on 2006-02-01
thank you for inputs. Ill start working on.  But please more comments are welcome!

---

### Post by SlowHorse on 2006-02-01
Even if I'm using X, I still prefer cplay over other media players: [http://mask.tf.hut.fi/~flu/hacks/cplay/](http://mask.tf.hut.fi/~flu/hacks/cplay/)

---

### Post by zojas on 2006-02-22
centericq is the canonical text IM client. pretty much its only limitation is that you can only have 1 account of each protocol type (e.g., 1 jabber account and 1 aim account, etc) but it works really well, supports ssl and gpg encryption too.

---

### Post by lamego on 2006-02-22
Why don't you just use the "server" option for the install ?
It will only install the ubuntu core (no gui apps), then you can install the console based apps as you like using apt...

---

### Post by oimon on 2006-02-22
Us sysadmins have a tendency to fiddle :) 

Personally if someone gave me a laptop wth console only, i would probably end up installing fluxbox on it (ubuntu server + fluxbox is a good combo for low spec machines although compiling flux is worth while since i read that the breezy package runs slowly). or for a usb stick install then DSL linux (already mentioned once by somebody) or puppy linux - worth checking these guys out.
vectorlinux is slackware based and works fast too

---

### Post by carlosqueso on 2006-02-22
IceWM is nice on a slow machine.....it's what I used till I upgraded the memory on my desktop ubuntu box.

---

### Post by LadyDoor on 2006-09-16
1) Check out mutt
2) Check out bitlbee
3) emacs/vim/nano

c) check out SES (simple emacs spreadsheet). It can export a tab-separated-values spreadsheet openable in any standard spreadsheet software.

And you might consider installing ratpoison, which is an *extremely* lightweight desktop and has mottoes like "At last, the true purpose of X--better text resolution!" And if you haven't already, *definitely* install GNU Screen.

--Door

---

### Post by zojas on 2006-09-16
I second that. it should be easy to set up a thin X session, using ratpoison, or any of the slew of other light window managers. 

back in the day I used to run X on a 90MHz pentium. using pretty much anything besides gnome or kde should be plenty fine.

it's usually easier to get nice high resolution text in X then on the console/frame buffer :)

---

