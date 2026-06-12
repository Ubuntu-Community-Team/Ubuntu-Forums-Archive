---
title: "Guide to getting a WinEmulator?"
date: 2005-02-02
forum: Gaming &amp; Leisure
---

### Post by Kakalto on 2005-02-02
Is there a guide somewhere of how to get/install a free Windows Emulator?

Cedega is the main one, isn't it? I've tried to follow a guide to installing it, but I'm having problems. Is there a debian/ubuntu-specific howto somewhere?

Has anyone else had the problem of "Error in CVS checkout"?

---

### Post by pseudonym on 2005-02-03
Yes, Cedega costs US$5 a month. But you can compile the CVS version for free, if you want. The main difference is that the CVS version isn't so good on the copy protection, so you may have trouble installing some games (although you tend to get this problem in Cedega anyway). Some people also say that the DirectX support isn't as good either, but I haven't tried it myself. Check out [www.transgaming.org](www.transgaming.org) for info.

You might also want to take a look at Wine, which is the project Cedega was originally associated with. It's not up to par on the D3D support when compared to Cedega, but it's pretty good for running older games, especially ones which run in OpenGL. HL1, for example, runs well under Wine. But the best part about Wine is that it's free :) .

I've been playing around with Cedega for a couple of weeks and, TBH, I'm a little less than impressed. Granted, my hardware is getting a little old (Athlon XP 2000, 768MB RAM, Geforce 4 Ti 4400 128 MB), but I get surprisingly good performance when running games in windows eg. HL2 runs really smoothly at 1024x768 with most settings maxed out. But in Cedega I'm lucky to get more than 20fps and the game looks crappy (not to mention the fact that I had to spend 5 hours downloading a new copy via Steam because neither Cedega nor Point2Play (Cedega's optional GUI) liked my CDs, despiting trying all the tips to get around this issue).

The only reasonably hardware-intensive game I've been able to get running at windows-like performance has been Maxpayne2. And this is the criterion I judge Cedega by-if it can't reproduce windows-like gaming experience with the majority of my games then it's not worth it. I just wish I didn't have to pay to find this out. I'm prepared to tolerate the (very) occasional slowdown or slight graphical glitch, but beyond that I don't see the point in making excuses/compromises when it comes to games I've paid $$$ for, which I know play very well under windows. Looks like my winxp partition is there to stay for the foreseeable :-( .

---

### Post by Dylanby on 2005-02-03
For really old games you could try:
[Wine](http://www.winehq.com/) 
[ScummVM](http://www.scummvm.org/) 
[DOSBox](http://dosbox.sourceforge.net/news.php?show_news=1)

They're all free.
I've only used ScummVM so far. Works great!

---

### Post by Dylanby on 2005-02-03
Sorry, in regards to your first question see here:
[http://ubuntuforums.org/showthread.php?t=2740&highlight=chroot](http://ubuntuforums.org/showthread.php?t=2740&highlight=chroot)

---

### Post by AndersAA on 2005-02-03
[QUOTE=Kakalto]Cedega is the main one, isn't it? [/QUOTE]

I just have to correct that :p, NO, cedega isn't the main one.  Cedega is basically wine with their hacks for specific games and better directx support (and copy protection).  Wine is most defenatly the main one.

Though if your gonna play games, your probably gonna have more luck with cedega for now, but wine is gaining directx code now, and development on wine is waaay faster than cedega.

---

### Post by jdodson on 2005-02-03
[QUOTE=AndersAA]I just have to correct that :p, NO, cedega isn't the main one.  Cedega is basically wine with their hacks for specific games and better directx support (and copy protection).  Wine is most defenatly the main one.

Though if your gonna play games, your probably gonna have more luck with cedega for now, but wine is gaining directx code now, and development on wine is waaay faster than cedega.[/QUOTE]

i have no complaints with cedega, save that it costs money.  i got halflife2 working flawlessly in it along with war3, etc.  i could get those working in wine, though i would have to apply a no-cd crack, which i don't really feel comfortable with on my "legit" cd key games(i.e. the cracked exe could send my key to some other person, not sure if that happens, but a possiblity).

anyways, cedega and crossover office both claim to push code back to the regular wine tree, so eventually wine will be really good.  as you stated you can play halflife2 in vanilla wine, which is great!  did you have to nocd crack the exe?

---

### Post by AndersAA on 2005-02-03
[QUOTE=jdodson]anyways, cedega and crossover office both claim to push code back to the regular wine tree, so eventually wine will be really good.  as you stated you can play halflife2 in vanilla wine, which is great!  did you have to nocd crack the exe?[/QUOTE]

both cedega and crossover office says they push back to the regular wine tree, cx office has done a ton of it and cedega hasn't.. at all.

and I didn't say anything about running hl2 ;)

---

### Post by Kakalto on 2005-02-03
[QUOTE=Dylanby]Sorry, in regards to your first question see here:
[http://ubuntuforums.org/showthread.php?t=2740&highlight=chroot](http://ubuntuforums.org/showthread.php?t=2740&highlight=chroot)[/QUOTE]
Have another look at my original post, especially the word "free"  :o 

I would have to subscribe to get one of the prepackaged debian packs like the one they talk about in that article.

However, your post before that was very useful. Thanks. I might give Wine a try. I've had Dosbox on windows before, and I *do* have a lot of old games, so it could be useful. Not too sure about the other one, though.

Meanwhile, could someone could guide me to a forum where I could get good cedega CVS install support?

---

### Post by pseudonym on 2005-02-03
[QUOTE=Kakalto]Meanwhile, could someone could guide me to a forum where I could get good cedega CVS install support?[/QUOTE]
Try this -

[http://www.linux-gamers.net/modules/wfsection/index.php?category=1](http://www.linux-gamers.net/modules/wfsection/index.php?category=1)

---

### Post by pseudonym on 2005-02-03
[QUOTE=jdodson]i have no complaints with cedega, save that it costs money.  i got halflife2 working flawlessly in it along with war3, etc.[/QUOTE]

When you say 'flawlessly' do you mean in relation to the performance you would get under windows, or according to cedega standards? The best hardware rendering you can get under that is in DX8 mode, and then only if you're lucky. And the framerates? I haven't come across anyone who says they are as good as or better than what you get in windows...

---

### Post by Marquis_de_Carabas on 2005-02-04
I've so far only played a few games under Cedega (Grand Theft Auto III, Anarchy Online & Half Life) but they have all worked perfectly, as in at the highest graphical settings with perfectly playable framerates. GTAIII under Windows XP would only work at the lowest possible graphical settings and none of the tips I discovered in the hours of trawling through different forums could change that. So in my (admittedly limited) experience, Cedega is a worthwhile purchase.

---

### Post by rlwelch on 2005-02-05
For some older games (like Half Life and Counter-Strike) it is possible to get them working in Wine, which I like the most since it is freely available from the apt-get repositories.

Just type (as root or using sudo)
apt-get install wine

To get it.

Cedega has better compatibility with newer games, but is a pain to obtain. Transgaming (the group that produces it) offers a free version called CedegaCVS, but I could not get this version to compile using Ubuntu. I would get an error that, apparently, means I don't have the package "flex-old", but the error persisted even after I apt-got it.   :roll: 

Has anyone here successfully installed CedegaCVS on Ubuntu?

---

### Post by Kakalto on 2005-02-11
I might give CedegaCVS a go, and (in the unlikely case of it working) post here.

EDIT: Indeed it was DirectX.
I have tried CVSCedega, but I'm getting errors.
My error log: ```
make[1]: `libwine_unicode.so' is up to date.
make[1]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/unicode'
make[1]: Entering directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools'
make[2]: Entering directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/winebuild'
make[2]: Entering directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/winedump'
make[2]: Entering directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/wmc'
make[2]: Entering directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/wrc'
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT -I/usr/X11R6/include -o lex.ppl.o lex.ppl.c
./ppl.l:82:1: warning: "/*" within comment
./ppl.l:91:2: #endif without #if
./ppl.l: In function `pplex':
./ppl.l:305: error: `seen_junk' undeclared (first use in this function)
./ppl.l:305: error: (Each undeclared identifier is reported only once
./ppl.l:305: error: for each function it appears in.)
./ppl.l:305: error: `pp_pp' undeclared (first use in this function)
./ppl.l:310: error: `pp_ignore' undeclared (first use in this function)
./ppl.l:310: warning: implicit declaration of function `yy_pp_state'
./ppl.l:310: error: `pp_inc' undeclared (first use in this function)
./ppl.l:310: error: `tINCLUDE' undeclared (first use in this function)
./ppl.l:310: error: `pp_eol' undeclared (first use in this function)
./ppl.l:311: error: called object is not a function
./ppl.l:311: error: `pp_def' undeclared (first use in this function)
./ppl.l:312: error: `tERROR' undeclared (first use in this function)
./ppl.l:313: error: `tWARNING' undeclared (first use in this function)
./ppl.l:314: error: `tPRAGMA' undeclared (first use in this function)
./ppl.l:315: error: `tPPIDENT' undeclared (first use in this function)
./ppl.l:316: error: `pp_ifd' undeclared (first use in this function)
./ppl.l:316: error: `tUNDEF' undeclared (first use in this function)
./ppl.l:317: error: `tIFDEF' undeclared (first use in this function)
./ppl.l:318: error: `tIFNDEF' undeclared (first use in this function)
./ppl.l:319: error: `pp_if' undeclared (first use in this function)
./ppl.l:319: error: `tIF' undeclared (first use in this function)
./ppl.l:320: error: `tELIF' undeclared (first use in this function)
./ppl.l:321: error: `tELSE' undeclared (first use in this function)
./ppl.l:322: error: `tENDIF' undeclared (first use in this function)
./ppl.l:323: error: `pp_line' undeclared (first use in this function)
./ppl.l:323: error: `tLINE' undeclared (first use in this function)
./ppl.l:324: error: `tGCCLINE' undeclared (first use in this function)
./ppl.l:325: warning: implicit declaration of function `pperror'
./ppl.l:326: warning: implicit declaration of function `newline'
./ppl.l:326: error: `tNL' undeclared (first use in this function)
./ppl.l:334: warning: implicit declaration of function `make_number'
./ppl.l:334: error: `pplval' undeclared (first use in this function)
./ppl.l:335: warning: implicit declaration of function `new_string'
./ppl.l:335: warning: implicit declaration of function `add_string'
./ppl.l:335: error: `pp_iqs' undeclared (first use in this function)
./ppl.l:336: error: `pp_dqs' undeclared (first use in this function)
./ppl.l:340: error: called object is not a function
./ppl.l:362: error: `pp_defined' undeclared (first use in this function)
./ppl.l:362: error: `tDEFINED' undeclared (first use in this function)
./ppl.l:363: error: `tLSHIFT' undeclared (first use in this function)
./ppl.l:364: error: `tRSHIFT' undeclared (first use in this function)
./ppl.l:365: error: `tLOGAND' undeclared (first use in this function)
./ppl.l:366: error: `tLOGOR' undeclared (first use in this function)
./ppl.l:367: error: `tEQ' undeclared (first use in this function)
./ppl.l:368: error: `tNE' undeclared (first use in this function)
./ppl.l:369: error: `tLTE' undeclared (first use in this function)
./ppl.l:370: error: `tGTE' undeclared (first use in this function)
./ppl.l:375: error: `pp_sqs' undeclared (first use in this function)
./ppl.l:383: warning: implicit declaration of function `xstrdup'
./ppl.l:383: error: `tIDENT' undeclared (first use in this function)
./ppl.l:406: error: `tLITERAL' undeclared (first use in this function)
./ppl.l:409: error: called object is not a function
./ppl.l:415: error: `pp_macro' undeclared (first use in this function)
./ppl.l:415: error: `tMACRO' undeclared (first use in this function)
./ppl.l:416: error: `pp_define' undeclared (first use in this function)
./ppl.l:416: error: `tDEFINE' undeclared (first use in this function)
./ppl.l:435: error: `pp_mbody' undeclared (first use in this function)
./ppl.l:435: error: `tMACROEND' undeclared (first use in this function)
./ppl.l:439: error: `tELIPSIS' undeclared (first use in this function)
./ppl.l:448: error: `tCONCAT' undeclared (first use in this function)
./ppl.l:449: error: `tSTRINGIZE' undeclared (first use in this function)
./ppl.l:467: error: `pp_macscan' undeclared (first use in this function)
./ppl.l:474: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:474: error: `mac' undeclared (first use in this function)
./ppl.l:474: warning: implicit declaration of function `pop_macro'
./ppl.l:476: warning: implicit declaration of function `put_buffer'
./ppl.l:478: warning: implicit declaration of function `free_macro'
./ppl.l:486: warning: implicit declaration of function `MACROPARENTHESES'
./ppl.l:486: error: invalid lvalue in increment
./ppl.l:487: warning: implicit declaration of function `add_text_to_macro'
./ppl.l:490: error: invalid lvalue in decrement
./ppl.l:493: warning: implicit declaration of function `macro_add_arg'
./ppl.l:506: error: `pp_comment' undeclared (first use in this function)
./ppl.l:507: error: `line_number' undeclared (first use in this function)
./ppl.l:507: error: `char_number' undeclared (first use in this function)
./ppl.l:524: warning: implicit declaration of function `ppwarning'
./ppl.l:536: error: called object is not a function
./ppl.l:543: error: `RCINCL' undeclared (first use in this function)
./ppl.l:544: error: called object is not a function
./ppl.l:545: warning: implicit declaration of function `get_string'
./ppl.l:546: error: `tDQSTRING' undeclared (first use in this function)
./ppl.l:548: warning: implicit declaration of function `put_string'
./ppl.l:555: error: called object is not a function
./ppl.l:561: error: `tSQSTRING' undeclared (first use in this function)
./ppl.l:571: error: `tIQSTRING' undeclared (first use in this function)
./ppl.l:601: warning: implicit declaration of function `string_start'
./ppl.l:608: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:608: error: `ppp' undeclared (first use in this function)
./ppl.l:610: warning: implicit declaration of function `pplookup'
./ppl.l:612: error: called object is not a function
./ppl.l:615: error: called object is not a function
./ppl.l:621: error: called object is not a function
./ppl.l:621: error: `INITIAL' undeclared (first use in this function)
./ppl.l:623: error: `tRCINCLUDE' undeclared (first use in this function)
./ppl.l:632: error: `def_special' undeclared (first use in this function)
./ppl.l:633: warning: implicit declaration of function `expand_special'
./ppl.l:635: error: `def_define' undeclared (first use in this function)
./ppl.l:636: warning: implicit declaration of function `expand_define'
./ppl.l:638: error: `def_macro' undeclared (first use in this function)
./ppl.l:639: error: `pp_macign' undeclared (first use in this function)
./ppl.l:640: warning: implicit declaration of function `push_macro'
./ppl.l:643: warning: implicit declaration of function `internal_error'
./ppl.l:667: error: `tRCINCLUDEPATH' undeclared (first use in this function)
./ppl.l:680: warning: implicit declaration of function `isprint'
./ppl.l:696: error: `pp_macexp' undeclared (first use in this function)
./ppl.l:684: error: `bufferstackentry_t' undeclared (first use in this function)
./ppl.l:684: error: `bep' undeclared (first use in this function)
./ppl.l:684: warning: implicit declaration of function `pop_buffer'
./ppl.l:686: warning: implicit declaration of function `get_if_depth'
./ppl.l:699: warning: implicit declaration of function `expand_macro'
./ppl.l: At top level:
./ppl.l:730: warning: `newline' was declared implicitly `extern' and later `static'
./ppl.l:326: warning: previous declaration of `newline'
./ppl.l:730: warning: type mismatch with previous implicit declaration
./ppl.l:326: warning: previous implicit declaration of `newline'
./ppl.l:730: warning: `newline' was previously implicitly declared to return `int'
./ppl.l: In function `newline':
./ppl.l:731: error: `line_number' undeclared (first use in this function)
./ppl.l:732: error: `char_number' undeclared (first use in this function)
./ppl.l:737: error: `ncontinuations' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:770: error: parse error before "YYSTYPE"
./ppl.l:771: warning: `make_number' was declared implicitly `extern' and later `static'
./ppl.l:334: warning: previous declaration of `make_number'
./ppl.l: In function `make_number':
./ppl.l:778: warning: implicit declaration of function `toupper'
./ppl.l:778: error: `str' undeclared (first use in this function)
./ppl.l:778: error: `len' undeclared (first use in this function)
./ppl.l:812: error: `val' undeclared (first use in this function)
./ppl.l:812: error: `radix' undeclared (first use in this function)
./ppl.l:813: error: `tULONG' undeclared (first use in this function)
./ppl.l:818: error: `tSLONG' undeclared (first use in this function)
./ppl.l:823: error: `win32' undeclared (first use in this function)
./ppl.l:827: error: `tUINT' undeclared (first use in this function)
./ppl.l:841: error: `tSINT' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:852: error: parse error before '*' token
./ppl.l:853: warning: `expand_special' was declared implicitly `extern' and later `static'
./ppl.l:633: warning: previous declaration of `expand_special'
./ppl.l:853: warning: type mismatch with previous implicit declaration
./ppl.l:633: warning: previous implicit declaration of `expand_special'
./ppl.l:853: warning: `expand_special' was previously implicitly declared to return `int'
./ppl.l: In function `expand_special':
./ppl.l:857: warning: implicit declaration of function `assert'
./ppl.l:857: error: `ppp' undeclared (first use in this function)
./ppl.l:857: error: `def_special' undeclared (first use in this function)
./ppl.l:862: warning: implicit declaration of function `xrealloc'
./ppl.l:862: warning: assignment makes pointer from integer without a cast
./ppl.l:863: error: `line_number' undeclared (first use in this function)
./ppl.l:868: error: `input_name' undeclared (first use in this function)
./ppl.l:868: warning: assignment makes pointer from integer without a cast
./ppl.l:874: warning: assignment makes pointer from integer without a cast
./ppl.l:875: warning: implicit declaration of function `strftime'
./ppl.l:875: warning: implicit declaration of function `localtime'
./ppl.l:875: error: `now' undeclared (first use in this function)
./ppl.l:880: warning: assignment makes pointer from integer without a cast
./ppl.l:886: error: `debuglevel' undeclared (first use in this function)
./ppl.l:886: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:888: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:896: warning: implicit declaration of function `push_buffer'
./ppl.l: At top level:
./ppl.l:901: error: parse error before '*' token
./ppl.l:902: warning: `expand_define' was declared implicitly `extern' and later `static'
./ppl.l:636: warning: previous declaration of `expand_define'
./ppl.l:902: warning: type mismatch with previous implicit declaration
./ppl.l:636: warning: previous implicit declaration of `expand_define'
./ppl.l:902: warning: `expand_define' was previously implicitly declared to return `int'
./ppl.l: In function `expand_define':
./ppl.l:903: error: `ppp' undeclared (first use in this function)
./ppl.l:903: error: `def_define' undeclared (first use in this function)
./ppl.l:905: error: `debuglevel' undeclared (first use in this function)
./ppl.l:905: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:907: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:908: error: `input_name' undeclared (first use in this function)
./ppl.l:909: error: `line_number' undeclared (first use in this function)
./ppl.l: In function `add_text':
./ppl.l:929: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l:930: warning: assignment makes pointer from integer without a cast
./ppl.l: At top level:
./ppl.l:938: error: parse error before '*' token
./ppl.l:938: error: parse error before '*' token
./ppl.l:939: warning: return type defaults to `int'
./ppl.l: In function `add_expand_text':
./ppl.l:945: error: `mtp' undeclared (first use in this function)
./ppl.l:950: error: `exp_text' undeclared (first use in this function)
./ppl.l:951: error: `debuglevel' undeclared (first use in this function)
./ppl.l:951: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:956: error: `exp_stringize' undeclared (first use in this function)
./ppl.l:960: error: `mep' undeclared (first use in this function)
./ppl.l:973: error: `exp_concat' undeclared (first use in this function)
./ppl.l:979: warning: implicit declaration of function `isspace'
./ppl.l:986: error: `nnl' undeclared (first use in this function)
./ppl.l:1008: error: `exp_subst' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1035: error: parse error before '*' token
./ppl.l:1036: warning: `expand_macro' was declared implicitly `extern' and later `static'
./ppl.l:699: warning: previous declaration of `expand_macro'
./ppl.l:1036: warning: type mismatch with previous implicit declaration
./ppl.l:699: warning: previous implicit declaration of `expand_macro'
./ppl.l:1036: warning: `expand_macro' was previously implicitly declared to return `int'
./ppl.l: In function `expand_macro':
./ppl.l:1037: error: `mtext_t' undeclared (first use in this function)
./ppl.l:1037: error: `mtp' undeclared (first use in this function)
./ppl.l:1041: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:1041: error: `ppp' undeclared (first use in this function)
./ppl.l:1041: error: `mep' undeclared (first use in this function)
./ppl.l:1044: error: `def_macro' undeclared (first use in this function)
./ppl.l:1053: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1053: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1055: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1056: error: `input_name' undeclared (first use in this function)
./ppl.l:1057: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1114: warning: `new_string' was declared implicitly `extern' and later `static'
./ppl.l:335: warning: previous declaration of `new_string'
./ppl.l:1114: warning: type mismatch with previous implicit declaration
./ppl.l:335: warning: previous implicit declaration of `new_string'
./ppl.l:1114: warning: `new_string' was previously implicitly declared to return `int'
./ppl.l: In function `new_string':
./ppl.l:1119: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1120: error: `str_startline' undeclared (first use in this function)
./ppl.l:1120: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1124: warning: `add_string' was declared implicitly `extern' and later `static'
./ppl.l:335: warning: previous declaration of `add_string'
./ppl.l:1124: warning: type mismatch with previous implicit declaration
./ppl.l:335: warning: previous implicit declaration of `add_string'
./ppl.l:1124: warning: `add_string' was previously implicitly declared to return `int'
./ppl.l: In function `add_string':
./ppl.l:1127: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1127: error: `strbuf_alloc' undeclared (first use in this function)
./ppl.l:1129: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l:1130: error: `strbuffer' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1139: warning: `get_string' was declared implicitly `extern' and later `static'
./ppl.l:570: warning: previous declaration of `get_string'
./ppl.l:1139: warning: type mismatch with previous implicit declaration
./ppl.l:570: warning: previous implicit declaration of `get_string'
./ppl.l:1139: warning: `get_string' was previously implicitly declared to return `int'
./ppl.l: In function `get_string':
./ppl.l:1140: warning: implicit declaration of function `xmalloc'
./ppl.l:1140: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l:1141: error: `strbuffer' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1150: warning: `put_string' was declared implicitly `extern' and later `static'
./ppl.l:563: warning: previous declaration of `put_string'
./ppl.l:1150: warning: type mismatch with previous implicit declaration
./ppl.l:563: warning: previous implicit declaration of `put_string'
./ppl.l:1150: warning: `put_string' was previously implicitly declared to return `int'
./ppl.l: In function `put_string':
./ppl.l:1151: error: `strbuffer' undeclared (first use in this function)
./ppl.l:1151: error: `strbuf_idx' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1158: warning: `string_start' was declared implicitly `extern' and later `static'
./ppl.l:601: warning: previous declaration of `string_start'
./ppl.l: In function `string_start':
./ppl.l:1159: error: `str_startline' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1168: error: parse error before '*' token
./ppl.l:1169: warning: `push_buffer' was declared implicitly `extern' and later `static'
./ppl.l:1102: warning: previous declaration of `push_buffer'
./ppl.l:1169: warning: type mismatch with previous implicit declaration
./ppl.l:1102: warning: previous implicit declaration of `push_buffer'
./ppl.l:1169: warning: `push_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `push_buffer':
./ppl.l:1170: error: `ppdebug' undeclared (first use in this function)
./ppl.l:1171: error: `bufferstackidx' undeclared (first use in this function)
./ppl.l:1171: error: `ppp' undeclared (first use in this function)
./ppl.l:1171: error: `filename' undeclared (first use in this function)
./ppl.l:1171: error: `incname' undeclared (first use in this function)
./ppl.l:1171: error: `pop' undeclared (first use in this function)
./ppl.l:1172: error: `MAXBUFFERSTACK' undeclared (first use in this function)
./ppl.l:1175: error: `bufferstack' undeclared (first use in this function)
./ppl.l:1178: error: `line_number' undeclared (first use in this function)
./ppl.l:1179: error: `char_number' undeclared (first use in this function)
./ppl.l:1182: error: `input_name' undeclared (first use in this function)
./ppl.l:1183: error: `ncontinuations' undeclared (first use in this function)
./ppl.l:1184: error: `include_state' undeclared (first use in this function)
./ppl.l:1185: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1187: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l:1188: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1189: error: `pass_data' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1206: error: parse error before '*' token
./ppl.l:1207: warning: return type defaults to `int'
./ppl.l:1207: warning: type mismatch with previous implicit declaration
./ppl.l:684: warning: previous implicit declaration of `pop_buffer'
./ppl.l:1207: warning: `pop_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `pop_buffer':
./ppl.l:1208: error: `bufferstackidx' undeclared (first use in this function)
./ppl.l:1216: error: `bufferstack' undeclared (first use in this function)
./ppl.l:1220: error: `line_number' undeclared (first use in this function)
./ppl.l:1221: error: `char_number' undeclared (first use in this function)
./ppl.l:1222: error: `input_name' undeclared (first use in this function)
./ppl.l:1223: error: `ncontinuations' undeclared (first use in this function)
./ppl.l:1230: error: `include_state' undeclared (first use in this function)
./ppl.l:1230: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1230: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1232: error: `pp_entry_t' undeclared (first use in this function)
./ppl.l:1232: error: `ppp' undeclared (first use in this function)
./ppl.l:1235: error: `includelogicentry_t' undeclared (first use in this function)
./ppl.l:1235: error: `iep' undeclared (first use in this function)
./ppl.l:1239: error: `includelogiclist' undeclared (first use in this function)
./ppl.l:1243: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1243: error: `DEBUGLEVEL_PPMSG' undeclared (first use in this function)
./ppl.l:1253: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l:1255: error: `pass_data' undeclared (first use in this function)
./ppl.l:1260: error: `ppdebug' undeclared (first use in this function)
./ppl.l:1275: warning: implicit declaration of function `yy_current_state'
./ppl.l:1275: error: `pp_macexp' undeclared (first use in this function)
./ppl.l:1276: warning: implicit declaration of function `macro_add_expansion'
./ppl.l: At top level:
./ppl.l:1291: error: parse error before '*' token
./ppl.l:1292: warning: `push_macro' was declared implicitly `extern' and later `static'
./ppl.l:640: warning: previous declaration of `push_macro'
./ppl.l:1292: warning: type mismatch with previous implicit declaration
./ppl.l:640: warning: previous implicit declaration of `push_macro'
./ppl.l:1292: warning: `push_macro' was previously implicitly declared to return `int'
./ppl.l: In function `push_macro':
./ppl.l:1293: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1293: error: `MAXMACEXPSTACK' undeclared (first use in this function)
./ppl.l:1296: error: `macexpstack' undeclared (first use in this function)
./ppl.l:1298: error: `ppp' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1302: error: parse error before '*' token
./ppl.l:1303: warning: return type defaults to `int'
./ppl.l: In function `top_macro':
./ppl.l:1304: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1304: error: `macexpstack' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1307: error: parse error before '*' token
./ppl.l:1308: warning: return type defaults to `int'
./ppl.l:1308: warning: type mismatch with previous implicit declaration
./ppl.l:698: warning: previous implicit declaration of `pop_macro'
./ppl.l:1308: warning: `pop_macro' was previously implicitly declared to return `int'
./ppl.l: In function `pop_macro':
./ppl.l:1309: error: `macexpstackidx' undeclared (first use in this function)
./ppl.l:1311: error: `macexpstack' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1314: error: parse error before '*' token
./ppl.l:1315: warning: `free_macro' was declared implicitly `extern' and later `static'
./ppl.l:478: warning: previous declaration of `free_macro'
./ppl.l:1315: warning: type mismatch with previous implicit declaration
./ppl.l:478: warning: previous implicit declaration of `free_macro'
./ppl.l:1315: warning: `free_macro' was previously implicitly declared to return `int'
./ppl.l: In function `free_macro':
./ppl.l:1318: error: `mep' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1330: warning: `add_text_to_macro' was declared implicitly `extern' and later `static'
./ppl.l:506: warning: previous declaration of `add_text_to_macro'
./ppl.l:1330: warning: type mismatch with previous implicit declaration
./ppl.l:506: warning: previous implicit declaration of `add_text_to_macro'
./ppl.l:1330: warning: `add_text_to_macro' was previously implicitly declared to return `int'
./ppl.l: In function `add_text_to_macro':
./ppl.l:1331: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1331: error: `mep' undeclared (first use in this function)
./ppl.l:1337: warning: implicit declaration of function `max'
./ppl.l:1337: error: `ALLOCBLOCKSIZE' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1346: warning: `macro_add_arg' was declared implicitly `extern' and later `static'
./ppl.l:502: warning: previous declaration of `macro_add_arg'
./ppl.l:1346: warning: type mismatch with previous implicit declaration
./ppl.l:502: warning: previous implicit declaration of `macro_add_arg'
./ppl.l:1346: warning: `macro_add_arg' was previously implicitly declared to return `int'
./ppl.l: In function `macro_add_arg':
./ppl.l:1349: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1349: error: `mep' undeclared (first use in this function)
./ppl.l:1368: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1368: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1370: error: `input_name' undeclared (first use in this function)
./ppl.l:1371: error: `line_number' undeclared (first use in this function)
./ppl.l:1378: error: `pp_macexp' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1386: warning: `macro_add_expansion' was declared implicitly `extern' and later `static'
./ppl.l:1276: warning: previous declaration of `macro_add_expansion'
./ppl.l:1386: warning: type mismatch with previous implicit declaration
./ppl.l:1276: warning: previous implicit declaration of `macro_add_expansion'
./ppl.l:1386: warning: `macro_add_expansion' was previously implicitly declared to return `int'
./ppl.l: In function `macro_add_expansion':
./ppl.l:1387: error: `macexpstackentry_t' undeclared (first use in this function)
./ppl.l:1387: error: `mep' undeclared (first use in this function)
./ppl.l:1396: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1396: error: `DEBUGLEVEL_PPLEX' undeclared (first use in this function)
./ppl.l:1398: error: `input_name' undeclared (first use in this function)
./ppl.l:1399: error: `line_number' undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1411: warning: `put_buffer' was declared implicitly `extern' and later `static'
./ppl.l:1151: warning: previous declaration of `put_buffer'
./ppl.l:1411: warning: type mismatch with previous implicit declaration
./ppl.l:1151: warning: previous implicit declaration of `put_buffer'
./ppl.l:1411: warning: `put_buffer' was previously implicitly declared to return `int'
./ppl.l: In function `put_buffer':
./ppl.l:1415: error: `pass_data' undeclared (first use in this function)
./ppl.l: In function `do_include':
./ppl.l:1439: error: `includelogicentry_t' undeclared (first use in this function)
./ppl.l:1439: error: `iep' undeclared (first use in this function)
./ppl.l:1441: error: `includelogiclist' undeclared (first use in this function)
./ppl.l:1462: warning: implicit declaration of function `open_include'
./ppl.l:1462: warning: assignment makes pointer from integer without a cast
./ppl.l:1467: error: `seen_junk' undeclared (first use in this function)
./ppl.l:1468: error: `include_state' undeclared (first use in this function)
./ppl.l:1469: error: `include_ppp' undeclared (first use in this function)
./ppl.l:1470: error: `pass_data' undeclared (first use in this function)
./ppl.l:1473: error: `debuglevel' undeclared (first use in this function)
./ppl.l:1473: error: `DEBUGLEVEL_PPMSG' undeclared (first use in this function)
./ppl.l:1474: error: `input_name' undeclared (first use in this function)
./ppl.l:1474: error: `line_number' undeclared (first use in this function)
./ppl.l:1474: error: `include_ifdepth' undeclared (first use in this function)
./ppl.l: In function `push_ignore_state':
./ppl.l:1488: error: `pp_ignore' undeclared (first use in this function)
./ppl.l: At top level:
lex.ppl.c:15101: warning: `yyunput' defined but not used
make[2]: *** [lex.ppl.o] Error 1
make[2]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/kakalto/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2
``` 

... and, at TransGaming, they don't technical support CVSCedega, and at linux-gamers.net (where the CVSCedega Howto is), someone has had the problem before (on warty), but no-one has come up with a solution.

---

### Post by haiku on 2005-02-20
Hey kakalto, I was getting that same error when trying to make cedega.  I googled the file that was getting the errors (ppl.l) and some french site came up, and thanks to a translator I read that you could get around the error by getting rid of all the comments at the top of both ppl.l files.

I did that, and sure enough got past that point in the compile.  Only to get another error a ways down the path 

```
bitblt.c:3:27: warning: X11/Intrinsic.h: No such file or directory
bitblt.c: In function `BITBLT_InternalStretchBlt':
bitblt.c:1300: error: `Pixel' undeclared (first use in this function)
bitblt.c:1300: error: (Each undeclared identifier is reported only once
bitblt.c:1300: error: for each function it appears in.)
bitblt.c:1300: error: parse error before "xor_pix"
bitblt.c:1303: error: `xor_pix' undeclared (first use in this function)

```

currently looking into this.

---

### Post by haiku on 2005-02-20
To get past the Intrinsic.h error, I went to this webpage

[http://cvsweb.xfree86.org/cvsweb/xc/lib/Xt/Intrinsic.h?rev=3.10&content-type=text/vnd.viewcvs-markup](http://cvsweb.xfree86.org/cvsweb/xc/lib/Xt/Intrinsic.h?rev=3.10&content-type=text/vnd.viewcvs-markup)

created the file /usr/include/X11/Intrinsic.h

then i just pasted the contents of the Intrinsic.h at the website above into my new file.. compiling a little further now.

EDIT: Got it compiled, no clue how to configure it, its being pissy.

By the way, it looks like the Intrinsic.h file is in the libxt or libxt-dev package. 

good luck, i'm too tired to continue

---

### Post by Kakalto on 2005-02-22
Thanks heaps, Haiku. It's now installed.

The only problem I have, is that I'm not sure where the command for cvscedega is...

EDIT: Found the command. However, no matter what game I attempt to run, it comes up with this:```
/tmp/fileUaA9ZA:7: Error in sourced command file:
Previous frame inner to this frame (corrupt stack?)
``` 
... and then goes to the debug prompt.

Does anyone know why this is happening?

---

### Post by rapala61 on 2005-02-24
... i didnt have to pay for it, i just got a cedega 4.2.1 deb. torrent and installed it...
just tried it with counter strike and half-life 1, and everything looked good.

---

### Post by KLineD on 2005-02-25
[QUOTE=rapala61]... i didnt have to pay for it, i just got a cedega 4.2.1 deb. torrent and installed it...
just tried it with counter strike and half-life 1, and everything looked good.[/QUOTE]

You know? that's great but it's illegal if you didn't paid for it.

---

### Post by rapala61 on 2005-02-25
#-o

---

### Post by jdodson on 2005-02-25
[QUOTE=pseudonym]When you say 'flawlessly' do you mean in relation to the performance you would get under windows, or according to cedega standards? The best hardware rendering you can get under that is in DX8 mode, and then only if you're lucky. And the framerates? I haven't come across anyone who says they are as good as or better than what you get in windows...[/QUOTE]

ok i will qualify.  when i saw flawlessly i guess i mean something that is pretty bug free.  so it was defect free, as in no crashes, errors or whatever.  i also mean that it does not run like a slideshow.  so a flawless game would run very fluid and come off without a hitch.  i.e. stable.

as far as the rendering, the game looks awesome!  it has the best graphics i have ever seen.  as far as i can tell from screenshots that i have seen and my in game experience, i see no difference.  there is at times some lag but i don't really care about that too much as it is so rare it is almost not worth mentioning.  the fire effects, water, sound, physics, control, character modeling of the game are flawless.  the story needs some help though.

i never said the game was better than windows, nor did i attempt to imply it.  but in my opinion, that is to say, in my own way of doing things, running a game i got for free(my brother in law gave it to me) in cedega that takes a slight perfomance and graphical hit is no big deal.  because if i ran windows my entire computing lifestyle would take a hit.  so for me it is better to be running gnu/linux and suffer a bit of a cramp in halflife2 than to dual boot into xp to run a game.  i play halflife 2 rarely anyways so it would not warrant an xp partition.  plus i only have 1 xp license and it came for my laptop.  so i have no legal way to install xp.  even if i did i would not, my laptop is the last bastion for microsoft in my house anyway :) 

i only run cedega for two games anyway.  war3 and halflife2.  both games run flawlessly(see above definition) and both i play rarely.  the other games i play are either GPLed or other OSS licensed or native games like ut2004 or neverwinter.  now i would not purchase a game that did not have a direct port to gnu/linux and even those days are vastly closing.  with more and more awesome free games hitting the market, the reason for me purchasing a game gets less and less.

---

