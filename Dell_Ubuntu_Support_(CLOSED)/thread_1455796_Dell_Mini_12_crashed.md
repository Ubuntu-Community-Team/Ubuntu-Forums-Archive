---
title: "Dell Mini 12 crashed?"
date: 2010-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grangerpotter on 2010-04-16
Hey everyone,

I'm a newbie here (my first post in fact) who sadly do not know much about Ubuntu and I'm hoping someone here can help me. So a little background: I bought a Dell Mini 12 in July last year, used it maybe once or twice and then stored it in its box because I got another new laptop. However, I will be travelling around a bit in July so have decided to take the Mini with me instead of a full size laptop. 

Anyway so today, I turned it on, everything works perfectly and I was soon surfing the net, checking my mail and googling things for an least an hour, I then charged the battery and realized that since I haven't turned it on since July, there must be new software updates so I dutifully clicked on "check for new updates". The Mini then downloaded the updates and when that ended, I clicked on "install new updates" and a few seconds after that, the screen went blank (with a peach colored background). No weird sounds, nothing. I pressed a couple of buttons (Escape, space, delete) but the peach colored blank screen refused to budge. So I turned it off and restarted the laptop. The Dell logo came on, then the Ubuntu logo and then the same peach blank background appeared. I waited 30 minutes, gave up and called Dell since I have warranty on it until 2012. 

The lovely people at Dell told me: ooops, Ubuntu? Yeah sorry, we don't have any support for that, only for Windows. I was surprised and went: You must be joking right? I got this from Dell and the darn Ubuntu was installed by Dell itself and you're telling me you can't help? Dell goes, yeap, you got it. Awesome!

Anyone have any idea what I should do now? Any clue what happened? Anyone experienced the same thing before? I spoke to a friend who knows a bit about computers and she thinks it's a software crash/interrupted/corrupted and that I have not accidentally killed the Mini. The problem now is I can't get past the peach colored screen to do anything. For the record, it's on Ubuntu 8.04. I really hope someone in the forum can help or offer some advice how I should proceed next.

Thanks for taking the time to read and any help is very much appreciated. Thank you guys!

---

### Post by Kai Summers on 2010-04-16
[LIST=1]
[*]Switch on your computer
[*]Wait  until the Bios finished loading (you probably see a logo of your  computer manufacturer)
[*]The following messages will show up:
Grub loading stage1.5

Grub loading, please wait...

Press ESC to enter the menu
[*]Quickly  press the Escape key, which will bring up a boot menu
[*]Select  the line ending with '(recovery mode)', probably the second line,  something like: 
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
[*]After a minute or so, it will give you the recovery mode menu.
[/LIST]

At this point, you have several options.
 A quick rundown&#8230;
 resume &#8211; continue booting, normally. Pretty self explanatory.
clean &#8211; try to free up some drive space. Allow the system to delete temp  or unused files or directories.
dpkg &#8211; repair broken packages. If a package install did not work  correctly, attempt to finish the install or satisfy some dependencies.
root &#8211; the root console for specialized commands. If you have something  specific to do, not offered here in the menu.
xfix &#8211; attempt to repair the X server. If the X server is hosed, this  may not do any good.

Try dpkg see if that has fixed your computer then try xfix if no success with dpkg, if that doesn't work come back to us and you can try more specialist commands in root.

Good Luck, hope that helps!

---

### Post by grangerpotter on 2010-04-16
Hi Kai,

Thank you for replying. I tried following your advice and this is what happened:

I turned on the laptop, the Dell logo comes on (underneath the logo on the bottom right it says F2 BIOS and F12 (something I wasn't quick enough to read) and then it quickly went to the Ubuntu logo and then the same thing happened: peach colored blank screen.

No such message as "Grub loading stage1.5, Grub loading, please wait..."

I'm sorry to sound ignorant but when you said wait until BIOS finished loading, do you mean I should hit the F2 key at the Dell logo to go into BIOS?

---

### Post by Kai Summers on 2010-04-16
No its not the BIOS we need to get into. Usually there is a grub loading screen, When you see the press F2 & F12 check screen keep hitting Escape repeatedly hopefully there is a grub screen and its just loading to fast to see it. If no luck come back and let us know.

---

### Post by grangerpotter on 2010-04-16
Tried to do as you said, the second I saw the F2 and F12 , I hit Escape once and then something that look like rows of words (could be the Grub screen?) appeared for half a second and then the screen went black (instead of the peach background) and nothing else happened. Restarted the laptop, repeat the above with the same results. I'm thinking of buying an external DVD drive tomorrow and just booting Ubuntu from the DVD that came with the purchase. Would that work then? Thanks again!

---

### Post by Kai Summers on 2010-04-17
Yeah thats an idea. Just to let you know that you can copy the DVD onto a USB storage drive, but you would have to enable boot from USB in the BIOS.

Out of interest that screen (the black one) that come up did it look like a root screen? Could you type and would the computer accept commands. as a quick test just type ls to see if it will list files & folders.

---

