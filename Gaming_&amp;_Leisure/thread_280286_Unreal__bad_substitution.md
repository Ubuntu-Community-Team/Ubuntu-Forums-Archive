---
title: "Unreal : bad substitution"
date: 2006-10-19
forum: Gaming &amp; Leisure
---

### Post by tjotser on 2006-10-19
Hi all, I have installed Unreal Tournament GOTY on Edgy and i get this error:

thomas@thomas-desktop:~$ sh '/media/linuxstore/ut/ut' 
/media/linuxstore/ut/ut: 29: Syntax error: Bad substitution
thomas@thomas-desktop:~$ sh /media/linuxstore/ut/ut 
/media/linuxstore/ut/ut: 29: Syntax error: Bad substitution

I have also lloked at this thread : 
[http://ubuntuforums.org/showthread.php?t=76940](http://ubuntuforums.org/showthread.php?t=76940)

I'm stuck at what to do next, can i get the "old terminal" back ?
Thanks for your time and any help..:mrgreen:

--FIXED IT-- sort of... I found the ut-bin in /ut/system

---

### Post by BLTicklemonster on 2006-10-30
I can't get it to work at all. Nothing installs in my .loki directory. How did you get it to install in the first place?


*edit:

Eeek, I just noticed you said you fixed it sort of...

No idea how to make a bin file run, so I did this, and boy howdy!

```
ticklemonster@ticklemonster:~/ut/System$ sh ut-bin
ut-bin: 15: 4: not found
ut-bin: 15: &#65533;: not found
ut-bin: 15: ELF&#65533;&#65533;4&#65533;A: not found
ut-bin: 15: &#65533;i&#65533;Ka]&#65533;&#65533;&#65533;$lk}zkx!1u&#65533;: not found
ut-bin: 15: cannot create &#65533;F&#65533;&#65533;&#65533;&#65533;t2P9n&#65533;Ve&#1138;Z%&#65533;MR:&#65533;
pB4&#65533;gD[=,/&#65533;&#65533;&#65533;&#65533;n(&#65533; &#65533;&#65533;h&#65533;&#65533;&#65533;Q&#65533;IV&#65533;LY&#65533;i?&#65533;E&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/
                                                                &#65533;L&#65533;d&#65533;
                                                                              &#65533;&#65533;4|.
           Klbtu4&#65533;&#65533;&#65533;0&#65533;&#65533;-&#65533;4-
                                                   &#65533;0&#65533;&#65533;/
                                                                &#65533;&#65533;.
                                                                      
&#65533;0
   <*|0;&#65533;
                   HP0
                         W1
                               c&#65533;/
                                     rT/
                                           h.
                                                -
                                                   &#65533;/&#65533;1
                                                               &#65533;&#65533;/
                                                                     &#65533;&#65533;-
                                                                           &#65533;@1
 &#65533;0
      &#65533;&#65533;0
            &#65533;-
                 &#65533;-
                       1-
                           CX-
                                 N&#65533;/
                                       e&#65533;.
                                             s\0
                                                   &#65533;&#65533;.
                                                         &#65533;x/
                                                               &#65533;$.
                                                                     &#65533;L-
                                                                           &#65533;\.
 &#65533;&#65533;.
       &#65533;&#65533;.
             &#65533;-
                   &#65533;0
                         '&#65533;.
                               =-
                                     Q(-
                                           f&#65533;0
                                                 {D.
                                                       &#65533;-
                                                           &#65533;.
                                                                 &#65533;
                                                                     .
                                                                      &#65533;l/
                                                                            &#65533;0.
  &#65533;41
        &#65533;&#65533;,
              &#65533;&#65533;.
                    h0
                        /
                             %&#65533;:,Stf<u&#65533;/&#65533;@-
                                                        &#65533;&#65533;-&#65533;/
                                                                   &#65533;&#65533;0&#65533;0
                                                                              (&#65533;-=H/
           M
               0c(.
                          &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;&#65533;m&#65533;&#65533;1<&#65533;2&#65533;&#65533;?&#65533;F&#65533;&#65533;of&#65533;p&#65533;&#65533;
x: Directory nonexistent&#65533;&#65533;&#65533;&#65533;G&#65533;&#65533;!&#65533;P
ut-bin: 15: &#65533;L&#65533;&#65533;y-.&#65533;
                        ~B: not found
&#65533;: not found-
t: not found&#65533;d
ut-bin: 17: Syntax error: word unexpected (expecting ")")
ticklemonster@ticklemonster:~/ut/System$ 

```

I wonder if I could use some of them thingies for my name in ut lmao.

---

### Post by BLTicklemonster on 2006-10-31
Okay, thanks, I got it working now, and posted a how to on it [http://ubuntuforums.org/showthread.php?p=1694247#post1694247](http://ubuntuforums.org/showthread.php?p=1694247#post1694247)

---

