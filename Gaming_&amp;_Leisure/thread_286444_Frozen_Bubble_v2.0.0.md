---
title: "Frozen Bubble v2.0.0"
date: 2006-10-27
forum: Gaming &amp; Leisure
---

### Post by ivoencarnacao on 2006-10-27
Frozen Bubble v2.0.0 is [OUT](http://www.frozen-bubble.org/news/)!

Me wants!


Those [Debian](http://www.frozen-bubble.org/downloads/) guys already have it! 

Giev [Ubuntu](http://www.ubuntu.com/news/610released) Frozen [Bubble](http://www.frozen-bubble.org) 2!

:mrgreen:

---

### Post by madmetal on 2006-10-27
would it be at dapper repos sometime?

---

### Post by Matusel3 on 2006-10-27
Oh man, I want too!!!

---

### Post by ruimoura on 2006-10-28
Me too !!

---

### Post by towsonu2003 on 2006-10-28
you might wanna see this one: [https://wiki.ubuntu.com/BackportsHowto?highlight=%28backports%29](https://wiki.ubuntu.com/BackportsHowto?highlight=%28backports%29)

---

### Post by Perfect Storm on 2006-10-28
I'm atm. writting a howto install it.

---

### Post by Fass on 2006-10-28
Does anyone know if you can play the game with your mouse this time around, or are you still tied to the keyboard? That's the only thing I didn't like with this game.

---

### Post by towsonu2003 on 2006-10-28
> **Artificial Intelligence said:**
> I'm atm. writting a howto install it.

could you please let us know when it's ready? I tried checkinstall, but it can't install it (bug?)

thanks:)

---

### Post by Perfect Storm on 2006-10-28
Use 
sudo make install then sudo checkinstall

checkinstall is far from perfect when it comes to installation.


I ran into perl problem, which require some editing in the frozen bubble starter script and I'm no perl guy.

Do we have a perl guy in da house?

---

### Post by loko on 2006-10-28
i tried it but it fails t compile.

it needs sdl_pango, but i cannot see it in the repos...


any solution for this?



EDIT: i compiled sdl_pango from source and installed it.

now if i try to compile frozenbubble i get this error:

```
user@laptop:~/frozen-bubble-2.0.0$ make
perl -ne "print \$1 if m|\\\$version = '(.*)';|" c_stuff/lib/fb_stuff.pm > VERSION
make[1]: Betrete Verzeichnis '/home/user/frozen-bubble-2.0.0/c_stuff'
test -e Makefile_c || perl Makefile.PL INSTALLDIRS=

   **ERROR**: Frozen-Bubble patches are needed in SDL_Pango (impossible to create an executable calling the function SDLPango_CreateContext_GivenFontDesc)
```

but i cannot find any patches related to sdl_pango

---

### Post by Perfect Storm on 2006-10-28
Aye, same error. It need some hacking in the >Frozen bubble script

---

### Post by ruimoura on 2006-10-28
The game has been written in Perl/SDL and developed on a Mandriva Cooker Gnu/Linux distribution. You will need:

    * Perl: the most popular scripting language out there
    * SDL: the "standard" cross-platform multimedia C library
    * SDL_image: an image file loading library for SDL
    * SDL_mixer: a multi-channel audio mixer library for SDL
    * sdlperl: glue between perl and SDL; FB2 has been validated with versions 1.20.0, 1.20.3 and 2.1.2 (since old versions are quite hard to find, you may want to get yours from [http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz](http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz))
    * SDL_Pango: glue between Pango and SDL; at the time of FB2 release, latest stable was 0.1.2 and it needed an API patch ([http://zarb.org/~gc/t/SDL_Pango-0.1.2-API-adds.patch](http://zarb.org/~gc/t/SDL_Pango-0.1.2-API-adds.patch))


In the end talks about that patch ...

---

### Post by loko on 2006-10-28
> **ruimoura said:**
> The game has been written in Perl/SDL and developed on a Mandriva Cooker Gnu/Linux distribution. You will need:

    * Perl: the most popular scripting language out there
    * SDL: the "standard" cross-platform multimedia C library
    * SDL_image: an image file loading library for SDL
    * SDL_mixer: a multi-channel audio mixer library for SDL
    * sdlperl: glue between perl and SDL; FB2 has been validated with versions 1.20.0, 1.20.3 and 2.1.2 (since old versions are quite hard to find, you may want to get yours from [http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz](http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz))
    * SDL_Pango: glue between Pango and SDL; at the time of FB2 release, latest stable was 0.1.2 and it needed an API patch ([http://zarb.org/~gc/t/SDL_Pango-0.1.2-API-adds.patch](http://zarb.org/~gc/t/SDL_Pango-0.1.2-API-adds.patch))


In the end talks about that patch ...

thanks ruimoura,

i patched sdl-pango with the patch you pointed out, and now frozenbubble compiles

---

### Post by loko on 2006-10-28
mh, it compiles without a problem but i get this error when i want to start it:

```
user@laptop:~$ frozen-bubble
Can't locate fb_stuff.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/bin/frozen-bubble line 61.
BEGIN failed--compilation aborted at /usr/local/bin/frozen-bubble line 61.
user@laptop:~$
```

---

### Post by ruimoura on 2006-10-28
Well, i'm waiting for someone to say that it works, so that i can try it :).

Ps: why the hell don they just make a damn installer for all distros??? That really sucks ... Don they just learn?

---

### Post by thekidder on 2006-10-28
Worked fine for me (edgy). Just remember to have libsdl1.2-dev and libsdl-mixer1.2-dev installed. You also need to compile SDL_Pango from source - don't forget to patch it with the patch on the frozen-bubble site. After that, it should compile and run fine.

---

### Post by ruimoura on 2006-10-28
:-k 

Roger that.

---

### Post by loko on 2006-10-28
i have installed all the related stuff, and i patched it correct, it also compiles without error, but it wont run (see error message above)

---

### Post by guillaumeh on 2006-10-28
Here are the checkinstall packages for Frozen Bubble and libSDL_pango patched:

[http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble](http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble)

---

### Post by jldugger on 2006-10-28
I've gone ahead and filed a bug in launchpad for a feature request. If you have any comments to add to it, feel free. Also, if you want to know when Ubuntu gets the job done, subscribe to the bug.

[https://launchpad.net/distros/ubuntu/+source/frozen-bubble/+bug/68908](https://launchpad.net/distros/ubuntu/+source/frozen-bubble/+bug/68908)

---

### Post by Swab on 2006-10-28
> **guillaumeh said:**
> Here are the checkinstall packages for Frozen Bubble and libSDL_pango patched:

[http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble](http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble)

Will these packages work in Dapper or just Edgy?

---

### Post by juraj on 2006-10-28
I actually managed to install this game on dapper after a whole lot of tries and failures! Damn, it was worth it ;) 

Anyway, if I, relatively new with linux, could do it, you can do it too. Be sure to uninstall previous frozen-bubble, just get all dev libs that are required (they're all mentioned on the download page, get libsdl-net1.2-dev too), get the sdl pango library and patch it, and install it (here's mine checkinstall .deb... I hope it will work for you, although it probably will not: [http://rapidshare.com/files/1070815/sdl-pango_0.1.2-1_i386-fbpatch.deb.html)](http://rapidshare.com/files/1070815/sdl-pango_0.1.2-1_i386-fbpatch.deb.html)).

The thing is, you'll not be warned about those missing dev libs, it just won't work :P

Then just make and sudo make install, or do a sudo checkinstall (without sudo, checkinstall didn't work for me...)

Anyway the game owns. And it has multiplayer!! ;)

Note, when compiling sometimes you won't see why exactly it failed - make will just bitch about a missing file. This was a nightmare for me. To find out more, go in the each directory - server, c_stuff and po - and do a make in each one. Fix what's wrong, and at least you'll find out what's wrong... although at that point I recommend you to delete that mess altogether and untar the tarball again.

---

### Post by JockeTF on 2006-10-28
> **guillaumeh said:**
> Here are the checkinstall packages for Frozen Bubble and libSDL_pango patched:

[http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble](http://blog.pronux.org/index.php?2006/10/27/104-frozen-bubble)
Works like a charm in edgy, Thanks! :)

---

### Post by plb on 2006-10-28
I hope this one gets backported.

---

### Post by Perfect Storm on 2006-10-29
It already have been done, checkout Darkmages game repo: [http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=showcat&catid=36](http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=showcat&catid=36)

His announcement (in the comment box): [http://gaming.gwos.org/index.php?option=com_content&task=view&id=164&Itemid=1](http://gaming.gwos.org/index.php?option=com_content&task=view&id=164&Itemid=1)

---

### Post by ruimoura on 2006-10-29
Yeah !! It's working !!!

Thkx Artificial :)

---

### Post by Nomis on 2006-10-29
Thank you very much Artificial Intelligence. Works great. :-)

---

### Post by Somniis on 2006-10-29
Not many people playing online. :(

---

### Post by Perfect Storm on 2006-10-29
Well, it just been released. Have some patience ;)

---

### Post by Sukarn on 2006-10-29
> **Artificial Intelligence said:**
> It already have been done, checkout Darkmages game repo: [http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=showcat&catid=36](http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=showcat&catid=36)

His announcement (in the comment box): [http://gaming.gwos.org/index.php?option=com_content&task=view&id=164&Itemid=1](http://gaming.gwos.org/index.php?option=com_content&task=view&id=164&Itemid=1)
The repository enteries mention dapper. Do they work for edgy also?

---

### Post by Perfect Storm on 2006-10-29
There's an edgy repo as well.

---

### Post by AlphaMack on 2006-10-29
Sweet. :D

---

### Post by sharperguy on 2006-10-29
Amaranth made me some debs to install it, which worked great

Hope they get put into an official backport,although u cant backport something unless its in ubuntu+1 from where you are, ie edgy+1.

---

### Post by tribaal on 2006-10-29
Hehehe such a cool game!

Thanks a lot guys!

---

### Post by smeager on 2006-10-29
Here is a the repo for Frozen Bubble 2 on edgy (stright from the Frozen Bubble site)

```
##### Frozen Bubble 2.0 #####
deb http://thomas.enix.org/pub/debian/packages edgy main
```

installed without any problems and runs great.

(it's just what I need, something else to waste more of my time instead of working;) )

---

### Post by ruimoura on 2006-10-29
I'm allready kicking some *** on the multiplayer online mode :)

---

### Post by Swab on 2006-10-29
The soundtrack is even more sublime than before!  Seriously great game, can't wait to install this at work for some LAN play!

---

### Post by juraj on 2006-10-30
Is there a fb-music-high package?

---

### Post by Shay Stephens on 2006-10-30
Sweet, I love that game.  Can't wait to play it.

---

### Post by bruce89 on 2006-11-01
> **juraj said:**
> Is there a fb-music-high package?

No, it's all Vorbis audio now anyway.

I notice there are no AMD64 packages, so I compiled it myself.

---

