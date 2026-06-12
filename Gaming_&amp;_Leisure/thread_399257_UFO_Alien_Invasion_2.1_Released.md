---
title: "UFO: Alien Invasion 2.1 Released"
date: 2007-04-02
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2007-04-02
UFO: Alien Invasion 2.1 Released

I'm not going to ramble like I have in my other posts today, just sharing the news.

Homepage: [http://www.ufoai.net/](http://www.ufoai.net/)
Download: [http://sourceforge.net/projects/ufoai](http://sourceforge.net/projects/ufoai)

--

Linux Library Requirements (stolen from sourceforge):

You need the following package versions to run the game:
glibc >= 2.4
SDL >= 1.2.7
SDL_ttf >= 2.0.7
ogg >= 1.1
vorbis >= 1.1
libjpeg >= 6.2
zlib >= 1.2.3
libpng

If you encounter problems, please try to run the game with:
./ufo +set vid_ref sdl

You can even try to disable sound by typing:
./ufo +set snd_init 0

---

### Post by Hortinstein on 2007-04-02
hmmm looks interesting...is it any good?

---

### Post by charlieg on 2007-04-02
It is very, very good.

---

### Post by jazzgossen on 2007-05-22
I downloaded it from getdeb, but many of the text strings seem to be missing. Is that normal? For example, when choosing to start a new campaign, the settings for the campaign are listed at the right of the screen, and then there's a line saying "txt_standard_campaign", where I assume there should be a longer description.

---

### Post by TDogg310 on 2007-05-26
I would really like to play this game, so I followed the instructions for installing on Debian-based distributions on [http://ufoai.ninex.info/wiki/index.php/Debian](http://ufoai.ninex.info/wiki/index.php/Debian).  When I run ./configure in ~/ufoai/trunk, I get the following error message:

checking for SDL_ttf.h... no
checking for SDL_ttf/SDL_ttf.h... no
configure: error: You must have the SDL_ttf development headers

Synaptic indicates that I have libsdl-ttf2.0-dev installed, including /usr/include/SDL/SDL_ttf.h.  What should I do?

---

### Post by jazzgossen on 2007-05-28
TDogg310: If you just want to play the game, you shouldn't have to compile it. Try downloading the "hotfix" file from the sourceforge project page instead: [here]("http://sourceforge.net/project/showfiles.php?group_id=157793").

I solved my problem by installing with that file instead of using the deb files from getdeb.

---

### Post by TDogg310 on 2007-05-28
That worked, but now I have another problem.  Ubuntu just updated the restricted drives in addition to the kernel, so when I restarted, I received an Nvidia API mismatch error message and had to disable the Nvidia drivers.  I tried using Envy, but when I restarted I ran into the exact same problem.  I have no idea what to do next.  Before the update, the Nvidia drivers were working just fine.

Update

I went back to the previous kernel version and the game works just fine

---

### Post by Tuna-Fish on 2007-06-04
The newest kernel just doesn't yet have a nvidia module. I've got no idea why.

---

### Post by hikaricore on 2007-06-05
You have to reinstall the binary video drivers with a kernel update..

---

### Post by searayman on 2007-06-25
i installed via the .run file thingy but i can not get it to start when i try to start it from termianl i get this:

mike@mike-desktop:~$ ufoai
Killed
mike@mike-desktop:~$ 

any ideas?

---

### Post by hikaricore on 2007-06-25
Do not post the same question in multiple threads.

---

### Post by neilb on 2007-06-27
For some reason the hotfix install left me without text content

I tried the solution from the game wiki

$ LANG=en; ./ufoai

but it didn't help.

I looked in base/i18n/en/LC_MESSAGES and found no files.

I went to sourceforge and downloaded the internationalisation files and unpacked  base/i18n/en/LC_MESSAGES/ufoai.mo into place.

Then tried again

$ LANG=en; ./ufoai

and it worked fine

---

### Post by Smitje on 2007-07-07
Hi nielb

I'm having trouble with the ufo messages as well
I do have the mo file bu no others, and I keep seeing bolter_fifle_txt and stuf like that in game
did you find a bunch of txt files or just the one .mo?
 (and where did you find them)

Cheers
Smitje

---

### Post by shaft350x on 2007-10-15
> **jazzgossen said:**
> I downloaded it from getdeb, but many of the text strings seem to be missing. Is that normal? For example, when choosing to start a new campaign, the settings for the campaign are listed at the right of the screen, and then there's a line saying "txt_standard_campaign", where I assume there should be a longer description.

I'm getting the same "errors" everything that looks like it should have some sort of text block simply says "txt_something"

---

