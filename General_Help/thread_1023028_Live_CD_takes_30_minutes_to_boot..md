---
title: "Live CD takes 30 minutes to boot."
date: 2008-12-27
forum: General Help
---

### Post by Andy218 on 2008-12-27
Hi. I am an Ubuntu noob with a slight knowledge of Ubuntu. 

Now, as stated, I am no expert, but I have used the live cd on more than one occasion under 7.10 and it was a heckuvah lot faster than what i am doing here. I have burned the Hardy 8.10 iso to a disk, and then, well just re-read the title. I have actually gotten up to the screen with the little black X after about 20 minutes but i just shut it off.

So, before you all bombard me with possibilities as to why it is doing this, let me rule some out for you.

1. It's not my hardware.

I have and HP machine with 4 gigs of ram, an Intel Pentium Dual Core 64-bit 2.3 Ghz, and an nVidia Geforce 7100. On top of that, I was able to run feisty with no problems at all on a 7 year old, compaq pesario with an amd sempron, less than 1 gig of ram, and virtually no graphics card at all. I have also tried the cd on numerous other machines to no avail. Therefore, its not limited to my machine. And if you still want to argue hardware, I am running Vista Home Premium 64-bit and it runs like a dream.

2. It's not the CD's.

I have burned the iso, on three different kinds of cd's at 3X speed. Thats the slowest I can go.

So, I am left with 1 conclusion to this: It must be the iso. 

But since i just don't want to download it again just to find out that it still doesn't work, I would like a diagnosis from the most unified community in the history of computing. 

So, without further a due, here is my question.

What the heck is going on with this circular demon that is a 700mb storage device?:confused:

(Also, this is a bit off topic, but i was planning to install hardy to an 8 gig pen drive, but every tutorial i look at has a screen shot still showing the install icon. Is there a way to install it to the thumb drive 100% exactly like i would a normal HDD?):confused::confused::confused:

(Tell me if i should put that question in another scetion plz)

---

### Post by LoneWolfJack on 2008-12-27
Are you getting "buffer I/O error" from the live CD?

---

### Post by Elfy on 2008-12-27
If it's not the hardware and it's not the burn - did you check the md5sum of the download?

I would also check the integrity of the burn - there is an option to do so when it boots.

Have you tried it with safe grpahics - F6 from the boot menu.

---

### Post by Andy218 on 2008-12-27
Holy Heck! I didn't expect replies that fast.

To question 1. No i am not getting the I/O error. Speaking of witch, i don't know if there is a cd black list or anything, but the white 700mb sony audio cd's give the i/o error on boot.

EDIT: To question 2. How do i check the md5sum of the download? and yes, i have tried the cd defeck check and safe graphics mode.

Edit: Re downloaded iso and burned again this time the 64 bit version. Same result. Orange thing just goes back and forth and my cd drive goes quiet.

Could it be the program used to burn?

Edit again: Thanks for being so quick and awesome!

---

### Post by ju2wheels on 2008-12-27
Use the md5sum program on the iso and it will generate a hashed value for the iso. If it does not match the one provided online, then your iso file is bad.

```

md5sum ubuntu.iso

```

MD5s
```

ea6d44667ea3fd435954d6e1f0e89122 *ubuntu-8.10-alternate-amd64.iso
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso
f9cdb7e9ad85263dde17f8fc81a6305b *ubuntu-8.10-desktop-amd64.iso
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
8d35fea8c16597a6f4dd07f8e18e2166 *ubuntu-8.10-mid-lpia.img
e3028a105a083339be8e5af5afbe7444 *ubuntu-8.10-server-amd64.iso
a2ec9975a91e1228c8292ed9799dc302 *ubuntu-8.10-server-i386.iso

38e3f4d0774a143bd24f1f2e42e80d63 *ubuntu-8.04.1-alternate-amd64.iso
bbd21ded02c06b41c59485266833937a *ubuntu-8.04.1-alternate-i386.iso
b78ef719e3361e726b89bab78c526ad0 *ubuntu-8.04.1-desktop-amd64.iso
c69e34e92d5402d1b87e6babc739f774 *ubuntu-8.04.1-desktop-i386.iso
e7351d79903588699a383ae77854f734 *ubuntu-8.04.1-server-amd64.iso
7232c6004ba438890cd09aded162dc8e *ubuntu-8.04.1-server-i386.iso

```

---

### Post by Andy218 on 2008-12-27
I can't do that because im not running linux, im running windows. BEsides, i have redownloaded it 3 times and it still doesn't work. Im thinking its the program used to burn.

Can you recomend a program ideal for burning linux?

---

### Post by LoneWolfJack on 2008-12-27
Here you can find a windows program for creating a md5 cheksum:
[http://www.nullriver.com/products/winmd5sum]("http://www.nullriver.com/products/winmd5sum")

---

### Post by daetsy on 2008-12-27
The Ubuntu download page points to [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

I used it all the time in windoze and it never burned a coaster!

---

### Post by 73ckn797 on 2008-12-27
Google "CDburnerxp". It is a good Windows burning program and free at that.

---

### Post by Andy218 on 2008-12-27
DONT LEAVE PLEASE!!!!!!!!! IT INSTALLED BUT DO NOT LEAVE I HAVE A BIGGER PROBLEM I NEED HELP OR I WILL DIE.

Ok guys. NEW DELEMA.

I burned with infra recorder, booted and installed to thumb dirve.
Yippe, skippy.

Yeah, Guess what?

I overwrote the vista bootloader, but i am typing this in vista.

So, it finnishes i unplug the thumb drive to make sure vistas ok, I try to boot. To my horror i see GRUB ERROR 25. At that point, i thought i was dead. Then i plug in the usb drive with linux and the boot loader came up and i booted to vista. :P:P:):popcorn:

Did grub install partialy on both drives, or what? o.0

Either way, it works just fine, but my mom went ape **** when i told her, (I promised not to screw around with the new comp) and ordered me to fix it pronto. 

The situation:

:I have full access to vista. Haven't tried ubuntu yet.
:Grub is really wierd.
:I have to go to the bathroom really bad.
:[COLOR="Red"]I NEED A RESPONSE TONIGHT OR I AM DEAD.[/COLOR]
[COLOR="Black"]Help me..... PLEASE!!!!!!!!!!!!!:frown::frown::frown::frown::frown:[/COLOR]

---

### Post by eBoxNet on 2008-12-27
check this..it may help you : [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

---

### Post by 73ckn797 on 2008-12-27
If you have the WIndows disk, boot from it and go to recovery then type "fixmbr". If that does not work type"bootfix".

---

### Post by Jammanuser on 2008-12-28
> **73ckn797 said:**
> If you have the WIndows disk, boot from it and go to recovery then type "fixmbr". If that does not work type"bootfix".

He uses Vista, so he would first have to open up the command prompt in recovery, and then type the following commands:

```
bootrec /fixmbr
bootrec /rebuildbcd
bootrec /fixboot
```

Good luck. :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by 73ckn797 on 2008-12-28
> **Jammanuser said:**
> He uses Vista, so he would first have to open up the command prompt in recovery, and then type the following commands:

```
bootrec /fixmbr
bootrec /rebuildbcd
bootrec /fixboot
```Good luck. :)

Cheers! :popcorn:

-Jam man

:guitar:

I do remember that upon your comments. I stand corrected. 


Off topic:
I do not and have not used Vista, so I am not familiar with the differences from XP. I have had to monkey with my son's Vista system but did not make it a point to "learn" those procedures beyond accomplishing my intended purposes. XP works for what I still need it for and I am not going to pay $129.00 for Vista. Though I have seen the OEM Vista system builder for sale at Micro Center for $99. Once I no longer have to have Windows for several needs, then I will dump it.

---

### Post by Jammanuser on 2008-12-28
> **73ckn797 said:**
> I do remember that upon your comments. I stand corrected. 


Off topic:
[COLOR="Red"]I do not and have not used Vista, so I am not familiar with the differences from XP.[/COLOR] I have had to monkey with my son's Vista system but did not make it a point to "learn" those procedures beyond accomplishing my intended purposes. XP works for what I still need it for and I am not going to pay $129.00 for Vista. Though I have seen the OEM Vista system builder for sale at Micro Center for $99. Once I no longer have to have Windows for several needs, then I will dump it.

That's good, because XP is much better than Vista anyway! :) That is why I just recently tri-booted my computer with XP, and Ubuntu 8.10...Vista came pre-installed unfortunately, and so I thought it would be better to just add XP to my computer, rather than get rid of Vista completely...besides there's a few new cool features that Vista has and XP doesn't, so I thought I would just keep it, and use XP for all my Internet browsing, music playing, and a few other things. :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by 73ckn797 on 2008-12-28
> **Jammanuser said:**
> That's good, because XP is much better than Vista anyway! :) That is why I just recently tri-booted my computer with XP, and Ubuntu 8.10...Vista came pre-installed unfortunately, and so I thought it would be better to just add XP to my computer, rather than get rid of Vista completely...besides there's a few new cool features that Vista has and XP doesn't, so I thought I would just keep it, and use XP for all my Internet browsing, music playing, and a few other things. :guitar:

Cheers! :popcorn:

-Jam man

:guitar:


Now if the OP has followed through on all of the tips we will see "Solved" in the post title.

Jam Man huh? Got an axe?

---

### Post by Jammanuser on 2008-12-29
EDIT: delete

---

### Post by Andy218 on 2008-12-31
Hi guys. Sorry i took so long.

Guitars are awesome! I have an LTD Les Paul myself.

Anyway, back on topic, i fixed teh vista boot loader via EeasyBCD, but now when i try to boot from linux via the boot menu, i get the dreaded blinking cursor that many people with a Hackintosh* (1) experience. Is there a way i can add the pendrive ubuntu to the bootloader via EasyBCD? If there is, i need a click by click (Down to the very pixel on the screen where i should click) Instructions!

* Hackintosh: A copy of Mac OS X that is patched to run on Intel PC's and some AMD PC's. *Dictionary of Random and Useless Information.* :D

EDIT: Should I start a new thread for this?

EDIT AGAIN: Little thing to add to the Ubuntu Database of Random Infromation: ISO Recorder v3 + Ubuntu Hardy = Slowest computing in history. It was like trying to run vista ultimate on a machine made in 1995

EDIT AGAIN AGAIN: HOLY S*** HOLY S*** ITS A HOLLOW BODY LES PAUL HOLY S*** HOLY S***

---

### Post by Jammanuser on 2008-12-31
> **Andy218 said:**
> Is there a way i can add the pendrive ubuntu to the bootloader via EasyBCD?

I'm not sure...but I would suggest asking over at the [EasyBCD forum]("http://neosmart.net/forums/forumdisplay.php?f=7"), where you will get an answer to that question! :P

Cheers! :popcorn:

-Jam man

:guitar:

P.S. Les Pauls are nice, btw! I only wish I had one...:D

---

### Post by Andy218 on 2008-12-31
You can get my les for only about 250-300, but you may need to lower the bigdey thing (Havent fully develpoed my guitar vocabulary XD) BEcause my 12th fret on every string sounds a little off.

METALICA!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Jammanuser on 2008-12-31
> **Andy218 said:**
> You can get my les for only about 250-300, but you may need to lower the bigdey thing (Havent fully develpoed my guitar vocabulary XD) BEcause my 12th fret on every string sounds a little off.

METALICA!!!!!!!!!!!!!!!!!!!!!!!!!!

Any chance you could direct my to the site that sells it (assuming of course you bought it on the Internet)? ;)

METALICA!!!!!!!!!!!!!!!!!!!!!!!!!! :D

---

### Post by Andy218 on 2009-01-11
Erm... sorry. I bought it at City Music. =( But im sure if you look up LTD les Paul on musicians friend you will find it. =)

---

### Post by Jammanuser on 2009-01-11
> **Andy218 said:**
> Erm... sorry. I bought it at City Music. =( But im sure if you look up LTD les Paul on musicians friend you will find it. =)

Ok...no problem. ;) BTW, did you ever get your question answered...i.e. the one about if EasyBCD can add working entries for a pendrive? 

-Jam man

:guitar:

---

