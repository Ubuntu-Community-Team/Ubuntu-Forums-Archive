---
title: "Is RuneScape still broken in Ubuntu?"
date: 2009-10-31
forum: Gaming &amp; Leisure
---

### Post by xakh on 2009-10-31
I was hoping the new stuff introduced in 9.10 would allow me to enter high detail. No dice eh? Any ideas?

---

### Post by teward on 2009-10-31
**EDIT: Changed Content**

Might be your hardware, and not Ubuntu.  Seen this happen with non-Ubuntu computers that were old and running Win2000.

---

### Post by xakh on 2009-10-31
> **TrekCaptainUSA said:**
> **EDIT: Changed Content**

Might be your hardware, and not Ubuntu.  Seen this happen with non-Ubuntu computers that were old and running Win2000.

My Pangolin Performance ran RuneScape fine when I first got it back when it was equipped with 8.10. Ever since 9.04, however, I've been unable to play.

---

### Post by lnxnut on 2009-11-01
I run runescape on 4 computers 2 being Nvidia, 1 ATI, 1 Intel.  All of them will freeze running runescape in hd with java 6.  If you want to play in HD, here is what you must do if you want the freezing to be gone. install compiz switch, quick google search and you will find it easily.  2nd you have to remove java 6 and the plugins and everything associated with java 6, you can do this through synaptic. Install java 5 back with the plugins.  You will not have the option for full screen HD, but you will have full screen in the browser option. Now you can play runescape all day long and not worry with freezing. One more thing, I tested 9.10 some in beta and I did not see java 5 as an option.  May want to stick with 9.04, 8.10 or 8.04 until the java thing gets ironed out.

---

### Post by blazemore on 2009-11-01
I wrote a script to fix Runescape HD issues in 64 bit Jaunty and above.
Don't run it as root. It will prompt you for sudo when it needs to.

You can then run "firefox32" for a version of Firefox that will work with Runescape.
I just wrote this script for me; it's not very polished.

---

### Post by xakh on 2009-11-01
the firefox32 thing doesn't work, it acts like it doesn't even have java.

---

### Post by analog2digital on 2009-11-02
Yeah, I am having the same issues. Didn't work in 9.04, and still wont work in 9.10, and unfortunately the "firefox32" didn't work for me either =/ but thanks for the valiant effort. 

Oh well... its only a game.

---

### Post by blazemore on 2009-11-02
Try running the script yourself, line by line. It was the magical cure for me, and something might be going wrong somewhere.

---

### Post by lnxnut on 2009-11-02
question: Can you play runescape with java6 without the game freezing in HD?

---

### Post by Thrasherrich on 2009-11-02
i just tried this, erm it runs fine in low detail, but on high it lags like hell, on windows it ran fine however.

i managed despite the lag to get on HD and it seems to be the shadows and floor detail that makes mine lag.

---

### Post by blazemore on 2009-11-02
This actually works out the box on 32 bit ubuntu. It's only 64 bit that has issues. It will lag like hell if you have Compiz enabled. Try diabling compiz with the following command
```
metacity --replace
```

Alternatively, install and run the fusion-icon package,which puts a nice icon on your notification area which lets you easily toggle between this kind of thing.

---

### Post by xakh on 2009-11-02
So in other words, to play RuneScape, I basically need a 32 bit system? That sucks.

---

### Post by doorknob60 on 2009-11-02
Try this: [http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu](http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu)

HD has always been a little iffy on Linux, but using 32 bit Firefox and Java usually at least helps.

"So in other words, to play RuneScape, I basically need a 32 bit system? That sucks."

NO! x86_64 is 100% compatible with 32-bit software, and in Ubuntu you can have 64 bit and 32 bit versions of a program installed alongside each other, including Firefox and Java, like in the guide. Also, I should point out that Standard Detail (including full screen) works 100% perfect for me with 64 bit Java.

---

### Post by xakh on 2009-11-02
> **doorknob60 said:**
> Try this: [http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu](http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu)

HD has always been a little iffy on Linux, but using 32 bit Firefox and Java usually at least helps.

"So in other words, to play RuneScape, I basically need a 32 bit system? That sucks."

NO! x86_64 is 100% compatible with 32-bit software, and in Ubuntu you can have 64 bit and 32 bit versions of a program installed alongside each other, including Firefox and Java, like in the guide. Also, I should point out that Standard Detail (including full screen) works 100% perfect for me with 64 bit Java.
I've been running the low quality, but I like textures.

---

### Post by blazemore on 2009-11-03
So google around for a tutorial on getting 32 bit Firefox and Java running under 64 bit. There are quite a few, as Java didn't used to work under 64 bit at all.

---

### Post by xakh on 2009-11-03
:D Thanks blaze. I googled around and I found one. You guys rule. Now to figure out one thing, is it possible to run the 32 and 64 bit browsers side by side?

---

### Post by doorknob60 on 2009-11-04
> **xakh said:**
> :D Thanks blaze. I googled around and I found one. You guys rule. Now to figure out one thing, is it possible to run the 32 and 64 bit browsers side by side?

*ahem*

[http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu](http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu)

---

### Post by blazemore on 2009-11-04
Yes since they are separate executables. I have one Firefox with no toolbars or anything, with runescape.com as the homepage.

---

### Post by jeditalian on 2009-11-15
judging by the fact that the HD on youtube works now, your script must be alright. judging by the fact that HD doesnt work in runescape, and i tested it in windows and it still didnt work, the problem is either jagex, my drivers, or the fact that i had to downgrade on my motherboard from a really nice one to an MSI-7184, because nobody sells socket 939 motherboards anymore, and i can't figure out how to make my pretty red overclocking motherboard work without USB ports, and i think the ps2 is out too, but i havent tried because ive swapped the boards around like 5 tmes now, and i just picked up a ps2 keyboard to test it next time i swap it out. who'da thunk that runescape would require a high end graphics card? 
i seem to have blown up my onboard USB trying to fix a really nice logitech headset with a severed plug.. what is strange is all the usb devices worked fine, i had the broken headset unplugged from the computer, i took a shower, and when i returned, nothing usb worked. it got power but no data. then i tried a pci usb addon card, but i still couldn't get into bios to turn off the onboard usb. so i scoured the internet for a socket 939 mobo and all i found was a crappy MSI board with no driver cd. i bought it since it is seemingly the last socket 939 motherboard in existence. so the moral of the story is: test it out in windows, if it doesnt work in windows, then you can't blame ubuntu or firefox. you can blame jagex or whoever made your graphics card. 
now where do i ask someone how do i fix my blowed up USB and possibly ps2 ports on a foxconn winfast 6150bk8mc because i want my 10/100/1000 back and my nVidia Geforce/nForce and my onboard overclocking capabilities

---

### Post by jeditalian on 2009-11-16
ok nvm. i just swapped motherboards, using a ps2 keyboard and a usb pci card. after all the difficulties in windows64to get the realtek hd audio drivers installed, i tested runescape andit worksin hd. (as you cantell, thisps2 keyboarddoesnot.) well, HD works in windows, but i triedboth waysin ubuntu 9.10, normal firefoxand firefox32 from terminal, but still the same message from runescape when i try to switch toHD mode. ubuntu recognizes allmyhardwarefine so it is a software issue, but for some people, could still be a hardware issue, if your graphics card is not good enough for their HD mode. now if you will excuse me, i have to reverse the connection to my front end usb port because i plugged it in backwards :D oh yeah, and i am typing with the USB keyboard now, because the ps2 keyboard has a crappy spacebar. fixed my motherboard for $2! well except for the fact that all the onboard usb is dead. EDIT: no matter which way i plug in the front end usb cable, it doesnt work, but that may be because i have a 5 port card and the 5th port is internal, and i have an extension cable plugged in, and the front end cable plugged in behind it. the extension cable comes out where my floppy drive is supposed to be, so i still have a port in the front. yea, its ghetto, and i have 6 less functional usb ports, but my keyboard is a hub, so i still have 6 functional usb ports, and 6 non functional.. and a ps2 keyboard plugged in for BIOS and OS selection purposes.

---

### Post by jeditalian on 2009-11-16
i should actually STFU until i know exactly whats up. im getting some NVIDIA drivers for linux now. then i will edit again and tell you if HD works.
Edit: no luck. i can doit in windows. got the recommended nvidia driver dealio but it wont save my configuration so i have to change my resolution everytime i login, & runescape website said i had java 1.006 or something but the update manager says im up to date so idk what 2do

---

### Post by j7%&lt;RmUg on 2009-11-16
It runs fine for me on any detail, i run 9.10 and it has worked fine for me since 8.10.

---

### Post by Windows Nerd on 2009-11-16
It works perfectly fine for me in HD, but havent tested fullscreen (I havent been a member for almost a year now, I just don't have enough time in my life anymore), albiet with no sound. I didn't try and fix it because I never really got around to it. 

God, I really miss RS, but unfortunately I have made decisions with my life that leave me no time for it anymore. I wish I could revert some changes in the game too, but that is a completely different topic.

Scott

---

### Post by jeditalian on 2009-11-19
yeah. i drank my half full wine jug. stupid me. i didnt know they were worth that much, or maybe they werent when idid that but itwas long ago beforetradelimits. i dont really playanymore, but thisisntabout runescape. this is about ubuntu.
maybe there issome commonality between all those that HD doesn't work for.. like, Nvidia perhaps?

---

### Post by Triggerhapp on 2009-11-22
64bit machines cannot currently do HD. I have reported this bug to them already ;P

---

