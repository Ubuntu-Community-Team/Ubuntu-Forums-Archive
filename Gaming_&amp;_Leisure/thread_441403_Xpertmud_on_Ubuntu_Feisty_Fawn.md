---
title: "Xpertmud on Ubuntu Feisty Fawn"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by Hiko96786 on 2007-05-12
Aloha,
   I am trying to compile and run xpertmud. I am following the directions from this webiste.. [http://docs.btmux.com/index.php?title=Xpertmud:Getting_Started&printable=yes](http://docs.btmux.com/index.php?title=Xpertmud:Getting_Started&printable=yes) 
I have installed all dependencies listed and got the source using subversion ...
 svn co [https://xpertmud.svn.sourceforge.net/svnroot/xpertmud](https://xpertmud.svn.sourceforge.net/svnroot/xpertmud) xpertmud
After that, I did a make -f Makefile.dist and it fails with the following error...
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** YOU'RE USING autoconf (GNU Autoconf) 2.61.
*** KDE requires autoconf 2.52, 2.53 or 2.54
make[1]: *** [cvs] Error 1
make: *** [all] Error 2

So I looked for autocong in the add/remove software app and the Synaptic Package Manager and it does not show up. So, what next? Do I need to find and install autoconf from source or something? Also, does anyone know where I can find the .deb of xpertmud? That would help. And as a last question, how could I get a package, say xpertmud, into a repository and how do I maintain it? 
Mahalo,
Edward

---

### Post by bobtherocket on 2007-05-12
Same issue. :P

---

### Post by Hiko96786 on 2007-05-25
Ok I sort of got it to work.....
I basically did all the following and got it to the poitn where I can get the map and all that but I am getting repeating messages on the Status Window...more later...ok so here is what I did....
Downloaded the latest svn from sourceforge.net
installed alien
converted all xpertmud*.rpm files to xpertmud*.deb I used version alpha 3.1alpha2 also downloaded from sourceforge.net
installed all four debs
setup the xpertmud client
Started xpertmud got the libperl.so missing error.
installed libperl-dev because of libperl.so message.
made a dir called /home/{user_name}/.kde/share/apps/xpertmud/perl and python
Copied all the .pl and .pm files from the svn trunk over to the perl directory
Copied all the py to the python directory
Started xpertmud...it worked map and all but got the GOTFIRST thing going on..
Fixed that by opening frontiers.pl in a text editor and found the following text in the file:
   parse("damagelog.pl");

After the semicolon ( ; ), added a space/return and then paste the following text:
   addTrigger("GOTFIRST",qr/&GOTFIRST Character Name=1/, sub { return undef; }, 1);
NOTE: replace in the text "Character Name" (underlined above) with your character's name.  For example:
   addTrigger("GOTFIRST",qr/&GOTFIRST Sildanis Kimetry=1/, sub { return undef; }, 1);
Now my frontiers.pl looks like:
   *snip*

   parse("damagelog.pl");
      addTrigger("GOTFIRST",qr/&GOTFIRST Sildanis Kimetry=1/,sub { return undef; }, 1);
        addTimer("BT_HOUSEKEEP",61,sub {
   *snip*

Saved frontiers.pl 
Started xpertmud. Everything works including map. Only issues I have remaining are it does not send my login information to the mux and the following keeps coming up every few seconds....
 
Sildanis Kimetry/GOTFIRST - Set.
Sildanis Kimetry/TACHEIGHT - Set.
Sildanis Kimetry/HUD_TACTICAL - Set.
Sildanis Kimetry/HUD_FINDCENTER - Set.
Sildanis Kimetry/HUD_CONTACTS - Set.
Sildanis Kimetry/HUD_STATUS - Set.
Sildanis Kimetry/HUD_STATUSI - Set.
Sildanis Kimetry/HUD_STATUSW - Set.
Sildanis Kimetry/HUD_HEAT - Set.
Sildanis Kimetry/HUD_SPEED - Set.
Sildanis Kimetry/HUD_HEADING - Set.
Sildanis Kimetry/HUD_DECOMILE - Set.

It is playable but with that popping up every few seconds it mnakes it hard. I am looking at the perl files and the pm files as well to see if I can figure this out. After that I would like to figure out how to build a .deb package and get it into the repositories. It is a very cool game and xpertmud changed the learning curve a lot. Also note I have only done this for Frontiers. So I am not sure it will work on any other Battletech mux. Any ideas, suggestions or comments? I signed up for sourceforge as well and am going to ask Entropy for help. 
Mahalo,
Edward

---

