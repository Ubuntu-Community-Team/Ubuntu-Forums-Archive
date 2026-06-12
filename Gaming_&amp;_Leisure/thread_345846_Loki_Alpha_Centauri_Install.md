---
title: "Loki Alpha Centauri Install"
date: 2007-01-24
forum: Gaming &amp; Leisure
---

### Post by Tarvok on 2007-01-24
I recently acquired a copy of the Loki Games version of SMAC, and I can't even install it. (I've searched around, and fount plenty of solutions for dealing with the segfault should I ever actually get it installed; none describing this proglem). This is what I do, and what I get:

```
tarvok@Rider:/cdrom$ sudo sh setup.sh
This installation doesn't support glibc-2.0 on Linux / x86_64

Please contact Loki Technical Support at support@lokigames.com

```

Any ideas?

Ah, just call me Captain Duh. I just noticed that x86_64 bit, and have the idea that it doesn't like my 64 bit operating system.

Still, any ideas?

---

### Post by Tarvok on 2007-01-26
More info may be helpful. I'm on an Athalon Sempron 64 2800, Radeon 9800, on-board nForce 3 sound, 3/4 gig of RAM, running Dapper 6.06 LTS (64 bit).

---

### Post by DarthFrog on 2007-03-22
[http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml](http://patrick.wagstrom.net/weblog/linux/ubuntu/alphaCentauri.xml)

 It starts up fine.  Sound is very choppy and crunchy with static.  However, the game crashes on the first turn.  Nuisance.  

   I love this game and really want to get it working.  I have it running in a VMWare session running Red Hat 9.  I rather suspect that it needs glibc 2.1 or earlier and that the modern glibc is what's causing the problem.  In which case, scarfing the RH 9  libc to Edgy and pointing  the SMAC binary to use them might well get it working.  I just have to figure out how to do that. :-) 

  I like CIv IV and Warlords well enough but IMHO Alpha Centauri is still the best in the genre.  I was one of the original beta testers for this game for Loki.

--
Cheers,
Rob

---

### Post by JMO707 on 2007-04-02
Do you have any idea if there is anyway to hear music on the game?

For what I have seen in the Loki FAQ, they were planning to had that feature in a future patch, and trying to play something from outside the game and then enter to it, just make all the fx's and voices go mute.

=(

---

### Post by Tarvok on 2007-06-10
Well, because I have moved up to Feisty and now, for some reason, my Windows copy won't run in Cedega, I have gone back to trying to get the Loki version working again. I tried it in 64 bit again, and got the usual error. I've reinstalled Feisty again, this time using an i386 version. The installer worked! Of course, just running "smacpack" results in a segfault. So I am attempting [these instructions]("http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games"). The command, according to these instructions, go something like this:

```
tarvok@Rider:~$ D_LIBRARY_PATH=/usr/local/lib/Loki_Compat/ /usr/local/lib/Loki_Compat/ld-linux.so.2 /usr/local/games/smac/smac.dynamic
/usr/local/games/smac/smac.dynamic: error while loading shared libraries: /usr/local/games/smac/smac.dynamic: cannot open shared object file: No such file or directory
```

As you can see, the file they call "smac.dynamic" does not exist in my installation. (In addition, the name of the directory they suggest is AlphaCentauri, don't know if that means anything) I can change it to just plain "smac" which does exist, though I suspect that is the static binary they warn me against. This is the result I get:

```
 D_LIBRARY_PATH=/usr/local/lib/Loki_Compat/ /usr/local/lib/Loki_Compat/ld-linux.so.2 /usr/local/games/smac/smac
/usr/local/games/smac/smac: error while loading shared libraries: /usr/local/games/smac/smac: ELF file OS ABI invalid
tarvok@Rider:~$ 

```

I also note that my installation does not show up in loki_update's list. Perhaps this is a clue?

---

### Post by Tarvok on 2007-06-12
Um... bump?

Should I start a new thread with that last message, so I can get that magical "0 replies" attached to it?

---

### Post by merlyn on 2007-06-13
I might be barking up the wrong tree here, but I have noticed a number of posts where people have had similar problems running ix86 games on a 64 bit system.

A solution that is often suggested is to install the ix86 version of the required library in addition to the 64 bit version.

It may help your situation.

Cheers.

---

### Post by Tarvok on 2007-06-13
> **merlyn said:**
> I might be barking up the wrong tree here, but I have noticed a number of posts where people have had similar problems running ix86 games on a 64 bit system.

A solution that is often suggested is to install the ix86 version of the required library in addition to the 64 bit version.

It may help your situation.

Cheers.

> **Tarvok said:**
> I've reinstalled Feisty again, this time using an i386 version. 

Ahem. ;)

---

### Post by johnny4north on 2007-06-13
thanks 4 the link tarvok.  thanks for the wisdom merlyn. :)

---

### Post by Stormspireiv on 2007-06-15
I've been trying for a long time to find a good way to get the Loki Alpha Centauri Planetary Pack working on Feisty...and after a long time googling different things, I came up with this nice walkthrough someone created.  It even includes the patch for the game.

I haven't tested it yet (downloading patch now...since all the mirrors on loki_update won't work...), but it seems this guy got it all working. Multiplayer and all. I will post my results as soon as I get them.

Here is the link:
[http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/)

Edit: The patch provided on that site will not work for me. It doesn't give me any errors, it just closes the console window...  If anyone can get any patch working, please let me know.

---

### Post by Tarvok on 2007-06-16
This looks promising. However, when I hit this point, I get an error:

```
tarvok@Rider:/usr/local/games/smac/smac-6.0a-alpha$ sudo sh update.sh
update.sh: 60: loki_patch: not found
tarvok@Rider:/usr/local/games/smac/smac-6.0a-alpha$
```

I get the feeling I'm missing something pretty obvious. What am I doing wrong?

---

### Post by Stormspireiv on 2007-06-16
Maybe it needs loki_patch installed to run.  I found the link, but it comes with no instructions to properly install it and I am still quite a newbie to linux and can't figure out how.

[http://www.libsdl.de/download/loki/loki_patch/](http://www.libsdl.de/download/loki/loki_patch/)

---

### Post by Tarvok on 2007-06-16
> **Stormspireiv said:**
> Maybe it needs loki_patch installed to run.  I found the link, but it comes with no instructions to properly install it and I am still quite a newbie to linux and can't figure out how.

[http://www.libsdl.de/download/loki/loki_patch/](http://www.libsdl.de/download/loki/loki_patch/)

That seems to be source code. I see no instructions to "make install" or anything like that, so I am unsure as to what one would do with that.

There is a binary file "loki_patch in ./smac-6.0a-alpha/bin/Linux/alpha. Perhaps the shell script can't find the file for some reason. I tried grabbing the file from the Linux directory and putting it into the smac-6.0a-alpha directory, but that didn't help anything.

---

### Post by leech on 2007-06-17
loki_patch was linked to on that page.  The link is [http://icculus.org/~msphil/loki/x86/](http://icculus.org/~msphil/loki/x86/)

I'm going to have to try this out.  Been dying to get this working again, I had it working great not too long ago....

Leech

---

### Post by leech on 2007-06-17
Hey, I did find this for X86_64 users.

[quote]]If you have problem installing on an x86_64, just make the following modifications to setup.sh

Change

```
DetectARCH()
{
status=1
case `uname -m` in
i?86) echo "x86"
status=0;;
*) echo "`uname -m`"
status=0;;
esac
return $status
}
```

to

```
DetectARCH()
{
status=1
case `uname -m` in
i?86) echo "x86"
status=0;;
*) echo "x86"
status=0;;
esac
return $status
} 
```

Leech

---

### Post by leech on 2007-06-17
One last final thing.  

Hopefully this should work.  I have a newer patch, that includes the patches from this guy, though I have no place to put it.  If you do a search for smac 6.0b you'll find it.

First apply this patch, and second, if you have composite enabled, disable it.  This is what causes more crashes.  Not sure why, but it does.  Now if I could only get my sound to not suck on my laptop, life would be good.

---

### Post by Tarvok on 2007-06-19
Where does loki_patch need to be for the script to find it?

---

### Post by Stormspireiv on 2007-06-22
> **leech said:**
> One last final thing.  

Hopefully this should work.  I have a newer patch, that includes the patches from this guy, though I have no place to put it.  If you do a search for smac 6.0b you'll find it.

First apply this patch, and second, if you have composite enabled, disable it.  This is what causes more crashes.  Not sure why, but it does.  Now if I could only get my sound to not suck on my laptop, life would be good.

I applied the patch, but it made it run worse (movies don't work and most words don't show up).  When I start a game, it still crashes giving me this error
```

/usr/local/games/smac/smacx.dynamic: symbol lookup error: /usr/local/games/smac/smacx.dynamic: undefined symbol: XGetWindowAttributes
```

What do you mean by "if you have composite enabled"? Is this my problem?

---

### Post by Doctoxic on 2007-07-04
> **Stormspireiv said:**
> I applied the patch, but it made it run worse (movies don't work and most words don't show up).  When I start a game, it still crashes giving me this error
```

/usr/local/games/smac/smacx.dynamic: symbol lookup error: /usr/local/games/smac/smacx.dynamic: undefined symbol: XGetWindowAttributes
```

What do you mean by "if you have composite enabled"? Is this my problem?

i have exactly the same problem  - any suggestions?

many thanks

doc

---

### Post by Stormspireiv on 2007-07-10
YAY! I got AC to work! I haven't tried multiplayer yet though. Here are the steps:

1. Install the game.
2. Install the latest patch. I have the 6.0b patch.  Here is a link [http://files.filefront.com/smac+60b+x86run/;9769317;/fileinfo.html]("http://files.filefront.com/smac+60b+x86run/;9769317;/fileinfo.html")
3. Grab the loki compatible libs from [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games) and extract them.
4. Make sure you don't have beryl or compbiz running.
5. Add this to your /etc/X11/xorg.conf and restart xorg afterwards
```
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```
6. If you installed the game under root, you need to either change the ownership of the .loki directory in your home folder from root to the user of your choice or run the game as root.
7. Use this command (as root if you didn't change the ownership of the .loki directory) to run AC:
For Alpha Centauri:
```
LD_PRELOAD=/path/to/libstdc++-3-libc6.2-2-2.10.0.so /path/to/smac.dynamic
```
For Alien Crossfire
```
LD_PRELOAD=/path/to/libstdc++-3-libc6.2-2-2.10.0.so /path/to/smacx.dynamic
```
Of course replace the "/path/to/" with the actual path to the file.

Edit: When trying to do this on my laptop, I kept getting errors when loading the old lib files so I tried running it normally with smacpack.  Strangely, it worked. It works on my desktop also.  You may or may not have to do steps 3 and 7.

---

### Post by Doctoxic on 2007-07-11
Stormspireiv - thanks :D

got it working with smacpack  - the LD commands kept giving me all the errors i previously posted

i got hold of the b patch in the end so you can ignore my pm

also your library files were different (or at least more of them) than the ones i had downloaded from some other source - not sure if this made a difference in the end

thanks again

doc

---

### Post by Fresnel on 2007-09-23
Hi! My Alpha centauri game broke just yesterday and it was most likely caused by upgrading xorg to 7.3.
(after few game turns I would get wierd x errors) 
Just yesterday everything was fine and now statically compiled smacpack would crash instantly after beginning a new game or after a few turns. Tried all instructions and faqs etc. and finally found a solution.
BTW. using Debian Lenny/Unstable if it makes any difference.

1. Downloaded these loki-compat libraries and gentoo ones too.
[http://www.linuxrising.org/files/lokicompat.tar.bz2](http://www.linuxrising.org/files/lokicompat.tar.bz2) (fedora)
[http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.2.tar.bz2](http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.2.tar.bz2) (gentoo)

2. Extracted gentoo libraries to /path/to/loki_compat and extracted fedora ones on top of gentoo
libraries 

(without this step i would get error
"Inconsistency detected by ld.so: dynamic-link.h: 62: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!"
fedora core libraries are more compatible for some reason)

3. Created a shell script with favorite text editor 

COMPAT=/path/to/loki_compat/
export LD_LIBRARY_PATH=$COMPAT
LD_ASSUME_KERNEL=2.2.5 $COMPAT/ld-linux.so.2 /path/to/smac/smac.dynamic

4. made that executable and copied it to path
>optionally edit menu/desktop shortcuts

run the script and hope for the best
have fun if it works!

(used these instructions as partial guidance)
[http://www.fedoraforum.org/forum/archive/index.php/t-118038.html](http://www.fedoraforum.org/forum/archive/index.php/t-118038.html)

---

### Post by Jaearess on 2007-10-07
Fresnel: thank you, thank you, thank you!

After trying and trying I was would never be able to play past naming my first base, but with your instructions, everything seems to be working fine! :)

Finally, I'm playing Alpha Centauri again!

---

### Post by Stormspireiv on 2007-10-20
An update for Gutsy:

For some reason, I think Feisty's desktop effects packages conflicted with SMAC.  That is why some people needed to disable compositing in their xorg.conf

In Gutsy (or Feisty), with Compiz Fusion, it doesn't seem to conflict and you can have compositing enabled. You still have to switch to the metacity window manager before starting SMAC, otherwise the game looks transparent.  I use fusion-icon to quickly switch between window managers. [http://ubuntuforums.org/showpost.php?p=3387228&postcount=16](http://ubuntuforums.org/showpost.php?p=3387228&postcount=16)

So, for Gutsy, all you should have to do is install from CD, apply the patch, switch to Metacity (if you are running compiz), and run.

---

### Post by KhaaL on 2007-11-19
Does anyone know if it's possible to run this game in windowed mode?

---

