---
title: "help installing"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Jungle-Cat on 2006-06-26
hi, i have just inherited my mum's old laptop. i wish to install ubuntu but am having trouble. simple probelm, HOW do i install it. i cant explore the cd's folder; (it currently has winXP sp2 on it). its an old laptop.
pentium MMX processor 267mhz

plz help me!

oh and i think i have ubunto 5.04, not wat ive suggested in the "tag"

---

### Post by Ramses de Norre on 2006-06-26
You've got a cd? Then you've got to enter the BIOS setup by pressing a key (probably del or an F key, look at the first screen when starting the machine for instructions) and set the boot sequence so that the laptop boots from the cd drive first. Then save changes, insert the ubuntu install disc and reboot, the laptop should boot from the cd then and the installer should start.

EDIT: and I think you're better off installing dapper instead of breezy.

---

### Post by Jungle-Cat on 2006-06-26
ive got cd drive to be primary boot, but it continues to boot form the hard drive. (ill try again)

wat do u mean by "dapper instead of breezy"

---

### Post by cyracks on 2006-06-26
Download the latest version of (k)ubuntu (dapper) burn it to cd, go to bios (pres delete when you start computer) and select cd-rom as primary boot device. Reboot computer and cd-rom should be recognized

---

### Post by Ramses de Norre on 2006-06-26
Did you burn the cd yourself? In that case you probably burned a data disc containing the iso file instead of burning the iso image, you'll need to burn the cd with an option like 'burn cd image' in your burning program, so not just burning that one file to the disc. (man, too much 'burn' in one post)

And dapper is the newest stable release of ubuntu, it's 6.06. You said you have 5.04 which is an older release (even older as breezy I see now) so I've you're doing a fresh install I suggest you install dapper.

---

### Post by Jungle-Cat on 2006-06-26
id rather not dl it...chances are it wont work either. im tight on dl's and cant risk wasting it on something that wont (liekly) work

---

### Post by shuttleworthwannabe on 2006-06-26
Jungle-cat
I must say you are gutsy! WinXP on an MMX!! That is cool!
May I also suggest Xubuntu Dapper, it may just surprise you with some exnhanced performance.
 
Good luck!

---

### Post by Jungle-Cat on 2006-06-26
i didnt put xp on it, there was a lot of rif raf bout the os when my mum got the laptop (for 25 buks at a garage sale, thats AU dollars, in US maybe 14 buks) and in the end my dad said just put xp on it. both me and my bro said put 2000 on, much the sam just run better.

i want ot remove windows full stop, thats why im looking at ubuntu.

the cd i have, i didnt burn my self. my bro got a heap of cd's shipped to him for free from u good people.

any suggestes other that get "dapper" and do u guys have any evidence in a way that it will work?

---

### Post by shuttleworthwannabe on 2006-06-26
If downloading is an issue for you, have u tried the smaller Linuxes: DamnSmallLinux, PuppyLinux, etc. Check out distrowatch.com
 
Find out whether you are able to boot from CDROM. I have an old machine that would not, so check first- but, oh, you were able to install w2k right? then it should boot from CD. Xubuntu is a better option imo.

---

### Post by Jungle-Cat on 2006-06-26
im not sure if w2k was ever on it, i think we half installed it lol.

but it can boot from CD, i have it selevted has the high priority

edit;
these samller ones like puppy and stuff, dont they have near to no gui, no apps, not user friendly?

---

### Post by Jungle-Cat on 2006-06-26
to keep things orderly ill make another post rather than edit. I read an article with ratings on a guy wanting linux on his old laptop, from his ratings, and other things im now looking at Gentoo.

alpha  amd64  hppa  ia64  ppc(32 bit)  ppc64  sparc64  x86

which of those do i need?

---

### Post by Ramses de Norre on 2006-06-26
I'm pretty sure your cpu is x86, though I don't really know the model.

---

### Post by Jungle-Cat on 2006-06-26
well i doesnt matter....

i closed msn, to play bf2.
i turn the laptop (whilst it has xp on it) on for msn
the cd drive was chirping, could it be? yes! an open-source penquin was about to conquer my laptop! hooray!
its installing now...lets hope it works

---

### Post by Jungle-Cat on 2006-06-26
ok ive got it all up and going after a long install....

i selected in the install as the resolutions 1024 x 768 and below. it set it self to 800 x 600, and its not full screen!! 1024 x 768 isnt in the menu to change to.

so how can i make it full screen?

---

### Post by Ramses de Norre on 2006-06-26
Could you post the output of ```
cat /etc/X11/xorg.conf
``` and tell us which video card you're using?

---

### Post by Jungle-Cat on 2006-06-26
in the morning mate...just stayed up to 3 am (now over here in aus) to watch the soccer. we lose in the last 10 secs the umpire called a penalty, (it wasnt, it shouldnt have been) and we loss 1 nil. fukn unmpires.

---

### Post by shuttleworthwannabe on 2006-06-26
are you awake? Sorry mate with the soccer, i thought it was an unfair penalty. Anyway, yes, the DSL and puppy stuff are really trimed down; hence, I suggested xubuntu.
 
I get the feeling that kubuntu may be even equally responsive. Try MEPIS 6 rc2 if you have the bandwidth to download. If you are thinking of gentoo, then you surely are gutsy!
 
 
take care

---

### Post by Jungle-Cat on 2006-06-26
well if u read my other p[ost u will see i am now happily running ubuntu 5.04 on it.

its not full screen tho! the maximum res is 800 x 600 at 72 hz. how do i add high hz's or 1024 x 768??

and yes, im awake now!

im also looking for some games or apps to run on it, considering the comps ultra low specs. i got a duke nukem thing that didnt work cos it couldnt retrieve a shared library or something. any sgugestions on some games for Ubuntu?

---

### Post by Jungle-Cat on 2006-06-27
i cant post that xorg thing but all the values that have res's in and they all had wat i designated in the ubuntu installer; 1024 x 768 and below

---

### Post by Jungle-Cat on 2006-06-27
ok, bigger issue. i want to install a few things.

now, i dl a deb file, which extracts to 2 .tar.gz files, and a file called debian-binary.

i get these for anything i dl, (aMSN from there site FOR ubuntu) and doom legacy ports for ubuntu from the ubuntu site.

so how do i install them?

---

### Post by Jungle-Cat on 2006-06-27
how do i install Nvu?

this is just ridiculous...isnt there a linux executable?

---

### Post by Jungle-Cat on 2006-06-27
how cna i make ubuntu 1024 x 768 ? (its not in drop menu)

dont worry bout my other q's after 3 hours i worked it out

---

### Post by Ramses de Norre on 2006-06-27
I suggest you do post the file and check your video card and monitor, are they capable of the resolution you want? 
And I hope you've found aptitude or synaptic for the installing, your system will get realy messy and installing will be a pain if you're going to install everything manually..

---

### Post by Jungle-Cat on 2006-06-27
well ive been using the command line (root terminal) and putting in sudo **** filename.deb


(cant remeber the letters of the "****")

now, ubuntu runs to slow 4 me, and im looking at damn small linux and puppy linux as suggested b4.

i need to know if they come with a graphical user interface such as GNOME which came with ubuntu.

and also how they install. cos i cant use a cmd line for an install.

---

### Post by Ramses de Norre on 2006-06-27
Ok dowloading the .deb's and installing with dpkg (the magical letters;)) manually is what I meant, that's not a very good way. You should look at synaptic (graphical) or aptitude (commandline) to install programs, they use dpkg in the background but they handle dependencies and so on too. 
I don't know about the other distro's (I haven't used any distro but ubuntu and knoppix YET=) )

---

### Post by Jungle-Cat on 2006-06-27
im pretty sure the laptop supports 1024 x 768, but it just doesnt fuking work. how do i make it fullscreen

---

### Post by Ramses de Norre on 2006-06-27
I asked you already twice for the config file and some video card specs. 
No use for cursing here, we're only trying to help you.

---

### Post by shuttleworthwannabe on 2006-06-27
try [COLOR="Red"]$sudo dpkg-reconfigure xserver-xorg[/COLOR] in terminal and follow the prompts. Know your hardware becaue it will ask you for it- hence Ramses recurring requests to post your specs here. What I like to do is choose VESA under graphics display and at the resolution section choose the ones that you know work (in your case select 1024x768, I am sure other lower res will be selected by default). 
At the automatically id display, I choose NO (but this is fo rme on the ATI fglrx display). Try either.

Keep the rest as default values. then reboot.

I honestly think you need to reconsider your OS options considering the low CPU specs you have- I would strongly recommend xubuntu (it is a pity it is also a 670MB iso, it used to be about 200-300MB with just the minimum- I think inlcusion OOo bloated this).

Again, please provide us with the hardware specs so that someone who has had more experince than I do can help. And oh. the wiki is a good place to start [https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

cheers,

---

### Post by Jungle-Cat on 2006-06-28
i dont knwo the specs...and the laptop si causing me nothing other than the shits. ubuntu runs slooooooooooow so i might get something else. like puppy linux.

---

