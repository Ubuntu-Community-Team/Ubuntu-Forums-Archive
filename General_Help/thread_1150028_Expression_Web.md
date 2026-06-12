---
title: "Expression Web"
date: 2009-05-05
forum: General Help
---

### Post by Mirge on 2009-05-05
I was wondering if anybody found a way to run Microsoft Expression Web in Ubuntu 9.04. WineHQ app DB shows it as unsupported and doesn't run right at all... but was wondering if anybody else managed to get it working somehow?

I bought a legitimate copy of this and want to be able to use it in Ubuntu 9.04 if possible. Right now it's installed on my other tower running Windows Vista, but would be EXTREMELY nice to have it running in Linux on this PC.

I also tried Quanta Plus, which is OK, but definitely no replacement for Expression Web. And I tried Kompozer, which constantly segfaulted on me at seemingly random intervals... I'm downloading kompozer 0.8a2 source and will try that as well since I haven't really even gotten to try Kompozer, but ideally I would like to be able to use Expression Web.

Any ideas/suggestions?

EDIT:
[http://ubuntuforums.org/showthread.php?p=7181332](http://ubuntuforums.org/showthread.php?p=7181332)

This is why I'm trying 0.8a2 (see above link)

---

### Post by Mirge on 2009-05-05
Kompozer 0.8a2 seems stable... managed to play around with it for a few minutes (longer than 0.7), but definitely isn't a replacement for Expression Web (lol I just realized the the abbreviated version is EW).

Also seemed to have black 'patches' sometimes, but I assume that's related to the ATi driver I have installed.

Would really like to get Expression Web running in Jaunty.

---

### Post by Mirge on 2009-05-05
WineHQ says Dreamweaver 8 installs and runs no problem using wine... might bite the bullet and try that I guess.

---

### Post by Mirge on 2009-05-05
Dreamweaver 8 trial works PERFECTLY using Vista mode in wine... seemed to freeze almost instantly when I'd switch into Split or Code view when I was using the XP mode. Tried Vista and it's overall a lot snappier and hasn't locked up on me! Guess I'll hafta shell out some cash and buy DW 8....

Note: Did not use crossover or anything other than the latest wine (devel).

Hope this helps others.

---

### Post by FluffyElmo on 2009-05-05
You could also use Virtualbox if you have a copy of Windows lying around. You can share folders between the host and guest OSs, plus using seamless mode the windows applications integrate very well with other Ubuntu programs. 

[http://virtualbox.org](http://virtualbox.org)

It may be more system intensive than you want, I find it very snappy with a dual core system and plenty of RAM but your results may vary.

---

### Post by Mirge on 2009-05-05
Well, glad I didn't buy DW yet... it's freezing in Vista mode now too!

I have a Dual core AMD 64 bit processor with 8GB RAM, but I honestly don't know where my Windows CD's/DVD's are anymore. Just moved and they're packed up somewhere, but I honestly don't have any desire to put windows back on this PC period heh. Ubuntu is amazing... just wish Dreamweaver 8 would not freeze.

---

### Post by Mirge on 2009-05-05
Well on that freeze I couldn't even see any windows on top of Dreamweaver 8... so I opened a terminate, typed sudo reboot, pass.. and luckily that rebooted the computer. Wasn't sure if that would work or not since I couldn't see anything.

Just fired it back up... Vista mode.. and it seems to be fine again. Not sure what's up with it though :(.

Not fine, freezing again..... it seems like if I do a lot of activity at once, I can force it to crash. Switching between views (Code, Split, Design) fast repeatedly will cause it to crash.

Feel like I'm talking to myself lol... changed to Windows 2003 in wine... opened the exact same file (I discovered it's only BIG files that cause the freezing). It's running fast again and no freezing/crashing. Lets see if it actually stays that way this time.

Yeah that didn't last long. Froze up on me again. Tired of trying now... it's a known bug according to Winehq, just noticed. I tried crashing an almost empty HTML document and it was just fine... very quick.. better than running it natively on Windows even.

---

### Post by FluffyElmo on 2009-05-05
Virtualbox would give reliability and should be more than fast enough of your system. I can understand not wanting to put Windows back on, even in a virtual machine, but for some apps it's the only way to reliably get work done. Seamless mode will let you run just Dreamweaver and it will look pretty much the same as under wine. 

I understand your frustration, when wine works it's actually better than windows but you can't always depend on it.

---

### Post by Mirge on 2009-05-05
Guess I might be forced to dig up a Windows disc...

Right NOW wine is working awesome with dreamweaver 8. I turned off some visual aids, etc to help performance... and it seems to actually have worked, but as I've learned within the past couple hours that doesn't mean a whole lot long-term heh (or even short-term in my case).

We'll see what happens. Next time DW freezes up on me, I'm gonna try VirtualBox I guess.

---

### Post by Mirge on 2009-05-05
OK, trying VirtualBox...... DW didn't crash yet, but I'm gonna try VB anyway. Will edit this post to update.

What's kind of ironic is I used VirtualBox in Windows to test out Ubuntu 8.10 just before 9.04 came out lol... now I'm using VirtualBox to run Windows Vista!

---

### Post by Mirge on 2009-05-06
Installed VirtualBox, installed Windows Vista, installed Guest Additions...

How do I get the resolution to be 1440x900? Max I can get right now is 1024x768, which is like... yeah, not gonna work :).

I'd appreciate any advice, thanks.

EDIT: DOH! Nevermind, I maximized the window & it automatically changed the resolution! How convenient is that! lol

---

### Post by Mirge on 2009-05-06
I cannot for the life of me get sharing to work... I added a shared folder through VirtualBox, but I can't find a way to access it in the virtual machine. Any ideas?

---

### Post by Mirge on 2009-05-06
Found my answer at: [http://ubuntuforums.org/showthread.php?t=681037](http://ubuntuforums.org/showthread.php?t=681037)

This worked. I didn't try net use x: yadda... because I was trying the "Map network drive" GUI util in windows... which failed. net use x: worked despite that!

---

### Post by Mirge on 2009-05-06
Heh, after some tinkering... I finally got my virtual machine running exactly the way it should. Now I have a fully working Expression Web in linux again :)...... I mean, technically it's in Linux, even if through a Vista virtual machine haha.

Performance-wise... it's dang fast! The only time it's slow is when initially connecting to \\vboxsvr shared folder....... after that, saving, etc is lightning quick!

---

### Post by radi0j0hn on 2009-05-08
For what it's worth, I've been pretty happy with Kompozer once you get the quirks figured out. My company produced an entire e-book from compiled HTML using the Windows version of Kompozer ("How To Use The Digital Camera You Just Bought!") and it worked perfectly with embedded MP3 audio, side tabs, tables and more.

I use it with Ubuntu as well.

It might be worth a try before going to a lot of other trouble and expense. 

I'm always a bit worried about MS web authoring products, as they tend to slip in code that -gee whiz- only seems to work best when viewed with Internet Explorer.

Now with IE8, they seem to be backing off, but it looks like a real standards mess out there.

[www.alicejandersen.com](www.alicejandersen.com) is done with Kompozer.  AJA did the layout of the e-book and is now doing the print version, BTW.  I can't draw a straight line, but I can write!

---

