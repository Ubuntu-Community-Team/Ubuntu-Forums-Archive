---
title: "Hellllppppp!!!!"
date: 2009-06-13
forum: General Help
---

### Post by bigxr on 2009-06-13
Hi,
I've just tried Ubuntu after buying an IBM T43 from ebay with it pre loaded.
I love it! I've been an avid PC user since the 1980's, and MS devotee, but I have to say Ubuntu v 9 point something is the best looking and behaving OS i've ever tried. (freespire aint bad either!) However.........
I wanted to run PICO SCOPE, an oscilloscope adapter for the PC, it only works in windows. I decided, as I've been around PC's most of my adult life I'll try for a dual boot, and only use windows for the few progs that wont run on Ubuntu. 
With me so far? read on, it all goes exponential!
I copied the instructions from a pretty good web site, apcmag.com, and it was all going swimmingly until I came to the bit where it says "load ubuntu from your live cd" eh? In a panic, I downloaded ubantu from the Ubuntu site ( 600 megs!) some time later I tried to boot from it. No such luck. I dont know why, its set to boot from cd first, but it just boots up in win xp. I loaded a checksum prog, and it all fits, there's nothing wrong with the disk, it just doesnt boot. 
Not only that but in windows, the wifi adapter and soundcard isnt loaded and because the primary partition with windows on it is now called F instead of C the blinkin driver recovery file from lenovo wont work either.
My problem is that I just keep digging I'm now like a politician caught with his pants down, panicking! I decided to delete all partitions by booting from the win xp boot disk, and start again. I gave the windows partition just 20 gigs, and left 60 gigs for the Ubuntu. Now a laptop that should (was) be a fully functioning 80 gig hdd decent machine running a blinkin lovely OS, instead I've got a poorly working win XP with a meagre 20 gig hard drive. And I still cant get the wifi or sound card configured.
I've decided to put the laptop in a dark place under the stairs and let it soak for a while. In the meantime. can anybody suggest a plan of action for me? how can I reload ubuntu? and does anybody know how I can recover my wifi and soundcard?
HEELLLLLPPP!!!!!

---

### Post by TheNosh on 2009-06-13
in the future try to give threads names that are more specific to your problem.

the first thing i would check is how you burned your ubuntu live disk, did you jst burn the iso onto a disk as a file (common mistake). or did you use a proper disk imaging app like imgburn?

---

### Post by Alexis Phoenix on 2009-06-13
Hi - err, whoops would be the technical term then?

On the Windows side of things, I suggest you look for drivers using the laptop's wired internet connection - even if it means using dial-up - you can let it try to search automatically that way.  Surely you know you can change drive letters (which are actually mount points, I am told) within Windows?

As to booting the Ubuntu live CD - there should be a magic key you can press to get a bios boot menu.  This would override the setting in the bios er, settings.  I would check that the CD drive actually works correctly too.

As to Pico Scope - I looked into that for my own interest a few years ago - I'm sure I read something about it working with Linux - maybe that was for an older version of the device than you have - however there is definitely oscilloscope software for Linux, I know because I used it with my sound card as the input device.

---

### Post by bigxr on 2009-06-13
Hi,
Thanks, for the replies, I'll try to push this along..
I didnt know what thread to post this on, its my first time so be gentle!
I burned the disk as a file, is that wrong? Is there an instruction page that tells 
how to burn as something else? I would have thought any out of the ordinary instructions would be better sited near to the download instructions?
You can't rename a drive letter if its your *primar*y partition. It says you can in some forums, but try it, you cant. 
There is some technical windows-esk reasons why not, and there probably is some complicated workaround way of doing it, but I dont know of any. Also windows will always choose to put itself in a clean partition, if there's any question marks it will ignore and rename, thats why its best to dual boot windows loaded first, so windows can retain the C drive letter.
As for Pico scope, I saw a link that allowed use on linux, but when you get down to it, it means virtually writing the damn program yourself, which I'm not up to. As you can see I'm tied in knots trying to set up a dual boot!!!   :oops:
Anyway, thanks for the replies, keep 'em coming!

---

### Post by TheNosh on 2009-06-13
burning an iso
[INDENT][http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)[/INDENT]

if it's burned as data it won't be bootable, you need an image burning program like InfraRecorder (used in the tutorial) or imgburn

---

