---
title: "Japanese Input Help"
date: 2006-03-14
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-03-14
Can anyone explain to me how the Japanese input system works in SCIM?
Lets say I want to write : watashi ha nihonjin desu
Now if I type 'watashi' what I get is "&#28168;&#12402;" which is totally meaningless.   ha works fine: &#12399;. nihon comes out like this:&#34219;&#12435; &#65292;the best result I got was &#12395;&#26412; which it least sounds the same and thats by typing ni and hon separately and so on.....
I'm using GNOME in English and I can type Chinese with no problems &#27809;&#21839;&#38988;

If I get this Japanese business sorted I might be able to convert my wife to Linux...

---

### Post by IGNIZ on 2006-03-14
[https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29](https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29)

follow this guide it worked great for me

&#12454;&#12502;&#12531;&#12484;&#12399;&#12363;&#12387;&#12365;&#12356;&#12391;&#12377;&#12397;

&#31169;&#12399;&#26085;&#26412;&#20154;&#12391;&#12377;

---

### Post by seshomaru samma on 2006-03-14
&#26377;&#38627;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#65281;
 
(but what about SCIM?)

---

### Post by IGNIZ on 2006-03-14
what do you mean?

maybe this guide can be useful?
[http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html](http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html)

and here there is a scim-nthy instead of uim-anthy

[http://sourceforge.jp/projects/scim-imengine/](http://sourceforge.jp/projects/scim-imengine/)

---

### Post by seshomaru samma on 2006-03-16
[QUOTE=IGNIZ]what do you mean?

maybe this guide can be useful?
[http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html](http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html)

and here there is a scim-nthy instead of uim-anthy

[http://sourceforge.jp/projects/scim-imengine/](http://sourceforge.jp/projects/scim-imengine/)[/QUOTE]

Thanks. I downloaded scim-anthy but when I try to install it I get an error:
[PHP]kitty@localhost:~/scim-anthy-0.8.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
[/PHP]

I suspect it might have something to do with the following bit from the readme file in the scim-anthy pack (though I'm not sure where I installed SCIM:oops: ):
> If you installed the SCIM into /usr/local or any other non-standard
  diretories, you should specify the PKG_CONFIG_PATH environment variable like
  this:

    $ PKG_CONFIG_PATH=/usr/local/lib/pkgconfig ./configure

am I right? if so when exactly do I put this command? and how?

---

### Post by MJSOnline on 2006-03-16
Hi there.  This may sound like a daft question, I hope I do not cause any offence, but once a japanese keyboard has been setup using the above link does the words that I would type such as **"Hello. how are you today?"**show and print/read back as japanese?  Does the same apply to chinese, urdu etc?  Thanks. Matthew

---

### Post by seshomaru samma on 2006-03-16
[QUOTE=MJSOnline]Hi there.  This may sound like a daft question, I hope I do not cause any offence, but once a japanese keyboard has been setup using the above link does the words that I would type such as **"Hello. how are you today?"**show and print/read back as japanese?  Does the same apply to chinese, urdu etc?  Thanks. Matthew[/QUOTE]

I'm not sure what you mean , in China we use the American keyboard setting as far as I know because Chinese doesn't have an alphabet. Let say you want to write &#29399; (dog) then first you put in the Mandarin pronunciation 'gou' then a small bar comes up and shows you all the Chinese characters that has this pronunciation and you choose the appropriate one. Japanese uses a combination of Chinese characters and 2 sets of alphabet so their input system is somewhat similar .
Does this help?
Urdu is an alphabetic system but I don’t know much about it – I think it uses the Arabic script and should have its own keyboard setting.

---

### Post by seshomaru samma on 2006-03-18
[QUOTE=IGNIZ]what do you mean?

maybe this guide can be useful?
[http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html](http://www.h4.dion.ne.jp/~apricots/mandrake/miniguide.html)

and here there is a scim-nthy instead of uim-anthy

[http://sourceforge.jp/projects/scim-imengine/](http://sourceforge.jp/projects/scim-imengine/)[/QUOTE]

Now I seem to have two Input Systems , one is SCIM with Chinese and a useless version of Japanese and the other is UIM . I want to integrate them so I can have UIM Japanese input on SCIM but didnt manage to install uim-anthy(see my post above). I wonder why SCIM's default Japanese input system is so useless?

---

### Post by IGNIZ on 2006-03-18
you should apt-get some c compiler, some programs needs specific releases of c compilers, try to apt-get some c compilers and then configure it again

---

### Post by seshomaru samma on 2006-03-18
[QUOTE=IGNIZ]you should apt-get some c compiler, some programs needs specific releases of c compilers, try to apt-get some c compilers and then configure it again[/QUOTE]

Thanks , I downloaded a bunch but I still get errors, except that now the line 
[PHP]configure: error: no acceptable C compiler found in $PATH [/PHP]
changed to:
[PHP]checking for C compiler default output file name... configure: error: C compiler cannot create executables
[/PHP]
Is there anyway I can find out which c compiler I need?

---

### Post by IGNIZ on 2006-03-18
oh god, i had the same problem some time ago, i had kubuntu that time, now i't ubuntu and i don't have this problem anymore, it's problably some c compiler version problem, try to install all versions of cpp and gcc you have in the repository, also old ones, i have all of it installed and i'm able to compile almost every c program

---

### Post by seshomaru samma on 2006-03-20
apparently I needed a C++ compiler
but now I get a new error :
```
checking pkg-config is at least version 0.9.0... yes
checking for SCIM... configure: error: Package requirements (scim >= 1.2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the SCIM_CFLAGS and SCIM_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```
Does that mean that my version of SCIM is wrong?
I believe it's the latest , I only installed Ubuntu about a month or so ago

---

### Post by MJSOnline on 2006-03-20
[QUOTE=seshomaru samma]I'm not sure what you mean , in China we use the American keyboard setting as far as I know because Chinese doesn't have an alphabet. Let say you want to write &#29399; (dog) then first you put in the Mandarin pronunciation 'gou' then a small bar comes up and shows you all the Chinese characters that has this pronunciation and you choose the appropriate one. Japanese uses a combination of Chinese characters and 2 sets of alphabet so their input system is somewhat similar .
Does this help?
Urdu is an alphabetic system but I don’t know much about it – I think it uses the Arabic script and should have its own keyboard setting.[/QUOTE]

Ok. So if I wanted to type the text "The dog walked down the street" then I could not just install the chinese keyboard layout and just type "The dog walked down the street" ?? Does that make sense?  Thanks again. M

---

### Post by ubuntu27 on 2006-03-20
[QUOTE=MJSOnline]Ok. So if I wanted to type the text "The dog walked down the street" then I could not just install the chinese keyboard layout and just type "The dog walked down the street" ?? Does that make sense?  Thanks again. M[/QUOTE]

No you cannot. 
You will have to know how to speak the language that you are typing.

For example, if you want to say "I am a genious!" in Japanese you will have to type "Watashihatensaidesu!" (Watashi wa tensai desu) to get this &#31169;&#12399;&#22825;&#25165;&#12391;&#12377;&#65281;

You cannot not just type "I am a genious" in english and get translated in Japanese. You will have to knoe how it is spoken, the pronunciation.

---

