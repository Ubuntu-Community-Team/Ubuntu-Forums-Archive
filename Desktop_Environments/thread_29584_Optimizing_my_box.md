---
title: "Optimizing my box?"
date: 2005-04-24
forum: Desktop Environments
---

### Post by greenwom on 2005-04-24
Slow loading aps

I've finally got my box on-line and "apt-get"ed everything I needed.

I started out very happily with a DVD now that I had the codecs....
and then..... 

I got a error about drop frames and the system being slow and another line about needing to be optimized.

I then noticed that all of my aps seem a little slugish in loading but I have nothing to compare it to.  

My question is how/where/what settings should I be looking to tweak 
or
is this maybe hardware not being reconized properly or I've the wrone ubuntu for my system?

Everything works it's just a little slugish/ is there anyway to benchmark?

sony viao pcg/fx35/D
AMD 499Mhz, 256ram
i386 hoary download.

---

### Post by Dr Gonzo on 2005-04-25
I'd bet you need to enable DMA on your cdrom drives.

Search around.  There are many, many threads pertaining to this, with solutions.

---

### Post by greenwom on 2005-04-25
Thanks, I'll look into DMA but what about the rest of my machine? are there any other tweeks I should look at for load time and startup time.

---

### Post by tread on 2005-04-25
Startup scripts. Get sysrc (damn, I forgot the name!) and remove the services you don't need.

And unless you have a reason to stick to gnome, switch to openbox/windowmaker/fluxbox.

Also, fiddle around with hdparm settings.

I don't remember enough to give you a detailed answer, but searching on the above should get you started :)

---

### Post by Dr Gonzo on 2005-04-25
Get more memory. :)  Max it out, if you can.  Most of the time spent opening apps with a low mem machine is because of swapping.

---

### Post by tomchuk on 2005-04-25
Install and run prelink "prelink -avfmR" which will grind your drive for a bit, but will result in much faster application startup. Things like OpenOffice.org, kde and other big c++ apps will start much faster.

Make sure DMA is enabled on your drives (man hdparm and search the forums)

Besides that, don't expect much from Gnome on a 500 MHz CPU. 256 MB is fine, but might be a little bit of a stretch with OOo, Evolution, a bunch of applets and terminals, and Firefox open.

I'll second the fluxbox/openbox suggestion, but if you're hooked on a full-feature desktop environment, XFCE4 is a great lightweight alternative to Gnome. Those should all be available from universe or multiverse. 

For lighter apps try Skipstone instead of Firefox, Balsa or Sylpheed instead of Evolution, gnome-office instead of openoffice, xmms is nice and light, as is aterm instead of gnome-terminal or xterm.

---

### Post by fordfan753 on 2005-04-26
[QUOTE=tomchuk]Install and run prelink "prelink -avfmR" which will grind your drive for a bit, but will result in much faster application startup. Things like OpenOffice.org, kde and other big c++ apps will start much faster.

Make sure DMA is enabled on your drives (man hdparm and search the forums)

Besides that, don't expect much from Gnome on a 500 MHz CPU. 256 MB is fine, but might be a little bit of a stretch with OOo, Evolution, a bunch of applets and terminals, and Firefox open.

I'll second the fluxbox/openbox suggestion, but if you're hooked on a full-feature desktop environment, XFCE4 is a great lightweight alternative to Gnome. Those should all be available from universe or multiverse. 

For lighter apps try Skipstone instead of Firefox, Balsa or Sylpheed instead of Evolution, gnome-office instead of openoffice, xmms is nice and light, as is aterm instead of gnome-terminal or xterm.[/QUOTE]

I prelinked my old machine (Compaq, Intel PIII 650, 128MB RAM) and I recommend it to anyone, everything just loads so much faster, it's the best thing I ever did to Hoary on this computer.

---

### Post by greenwom on 2005-04-26
I'm new to Linux and Ubuntu w/ Gnome is my first GUI and I like it allot.

My issue right now that's pissing me off a bit is that I cann't get much done without my wireless card working.  

The only way I can get online in Ubuntu to play (at home)  is with my wireless card and I can't get that working ....

Given that I get that working I can then work on tweaking the system.

I've searched for "enabling DMA and haven't found anything that makes sense.  There's alot of hits in the forum but I can't find a good walk through and something defines what DMA is.

I guess it would be nice if there was a script that could look at your system/ ask you questions and then configure the OS to your box a little better.  I'm not looking for a hands free install but I'd like some of the basics like my DVD player and my wireless card to work.

---

### Post by BAshworth on 2005-04-26
Look for threads on hdparm.  Or better yet, type sudo hdparm -tT /dev/hda and see what you're drive is performing at.

---

### Post by greenwom on 2005-04-26
Ok So I did the hdparm -tT

I get 

timed cached reads: 652 MB in 2.00 seconds = 325.56 MB/sec
timing buffered disk reads: 10 MB in 3.07 seconds = 3.26 MB/sec

I ran is a second time and got 

timed cached reads: 572 MB in 2.00 seconds = 285.05MB/sec
timing buffered disk reads: 52 MB in 3.07 seconds = 16.87 MB/sec


So now I humbly submit the question.... NOW WHAT DO I DO?

what setting should I be looking at.

---

### Post by tread on 2005-04-26
[Hdparm usage](http://linuxtimes.net/modules.php?name=News&file=article&sid=457) 

Basically, the idea is, get the current stats, tweak parameters taking down stats each time till we find the best possible setup.
The url should help, its got a nice writeup.

---

### Post by elasticwings on 2005-04-26
Have you tried ndiswrapper to get your wireless card working?  I have gotten two wireless cards working with ndiswrapper.  The ones I have are the Netgear Wireless G PCMCIA card and a D-Link Wireless G USB adapter.  I'm not at home right now so I don't know the model numbers.

---

### Post by greenwom on 2005-04-26
I've downloaded ndiswrapper and the driver the project site sujests 

but when I go to follow the drirections I get lost because the directories it points to are not there in Ubuntu......  So I don't know what to do........

The other thing that bothers me is that there are posts in thif forum that state that thier card worked out of the box. (same wpc11 card as I have)

So I'm a bit upset with this  (my wireless conection is the only one I have)

I still have gotten the DMA issue resolved, xine-check is shedding some light but I haven't gotten anywhere.........  I want Linux to work and perform at the best level possible.  

I'm almost ready to become a advocate and install Ubuntu for others but I need to know how to fix these problems.....

---

### Post by greenwom on 2005-04-26
Ok so I think I got the DMA thing figured out

I used

sudo hdparm -d1 /dev/hdc


So do I need to put this in a script somewhere to have this  done at boot up or will this setting stick with that command?

I hope this isn't a premature post ----  The DVD player is running.

---

### Post by dninja on 2005-05-04
[QUOTE=tomchuk]Install and run prelink "prelink -avfmR" which will grind your drive for a bit, but will result in much faster application startup. Things like OpenOffice.org, kde and other big c++ apps will start much faster.
[/QUOTE]

I assume that this needs re-running when new things are installed to keep everything fully optimized, if so then it is best to wait till you have a fully installed and stable system.

---

### Post by Psquared on 2005-05-04
[QUOTE=BAshworth]Look for threads on hdparm.  Or better yet, type sudo hdparm -tT /dev/hda and see what you're drive is performing at.[/QUOTE]


Interesting, this is what I got:

> 
/dev/hda:
 Timing cached reads:   2412 MB in  2.00 seconds = 1204.38 MB/sec
 Timing buffered disk reads:   70 MB in  3.07 seconds =  22.81 MB/sec


---

