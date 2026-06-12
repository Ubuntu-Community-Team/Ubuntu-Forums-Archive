---
title: "Ubuntu Hindi problems"
date: 2006-03-25
forum: Desktop Environments
---

### Post by sandygmaharaj on 2006-03-25
First a couple of emails exchanged.

> 
**Sandeep wrote:**
    Hi Anil
    Saw your post on ubuntu forums. Would be obliged if you could help.

    I installed ubuntu 5.10.
    Saw hindi sites in firefox, were getting displayed perfectly.

    Ran updates. Ran automatix.
    Now, hindi sites are not getting displayed properly.

    Also, I changed interface to hindi. Again the Gnome interface is not rendered correctly, as is also visible in the image that you posted on the forum.
    The gnome interface comes correct in FC 4 and if I remember correctly it was coming correctly in the ubuntu live CD also.

    Is there something that I am not doing correctly?

    Thanks
    Sandeep



> 
**Anil wrote:**
Hi Sandeep

Thanks for contacting me.

Yes, there are some issues associated with Hindi support in Ubuntu. I tried automatix some time back on Breezy, and it did a lot of destruction systemwide. I have never used automatix since then, and do everything manually.

First, check if the hindi fonts are still in your fonts directory (/usr/share/fonts/truetype/ttf-devanagari fonts). If they're not there, you need to reinstall them using synaptic. If they are there but not being displayed properly, you can still try "reinstalling" the fonts through synaptic.

Another thing: You perhpas upgraded your firefox to 1.5 through automatix. That version of firefox isn't well-supported on Breezy. However, you can try setting the character encoding to UTF-8 in firefox. (view--> character encoding--> utf-8 )

Also, try setting default font for firefox as "bitstream vera sans".

Please post this in forums too, so that others may also benefit. We shall communicate from there.

Anil


So, the fonts are still there. Infact I can see devnagri characters but they are not getting displayed the way they should be. For example, &#2367;  (chhoti 'i') occurs after the character when it should come before it.

Yes, I did upgrade to firefox 1.5. The encoding is UTF-8 but still the same problem.

Also, the main problem, when I start a session selecting hindi as the language, the menu names are not correctly displayed. They come as they are in the image in this [post]("http://www.ubuntuforums.org/showthread.php?t=102778") by anil.

Also, the devnagri fonts are much smaller than roman fonts at the same size.

Surprisingly, everything is fine when written in Gedit.

I also have pango library installed on my system.

FC4's gnome version in hindi is able to display everything properly. Wonder what could be the problem.

---

### Post by anil_robo on 2006-03-27
> **sandygmaharaj]First a couple of emails exchanged.

So, the fonts are still there. Infact I can see devnagri characters but they are not getting displayed the way they should be. For example, &#2367 said:**
> 

Sandeep try getting hold of a Dapper Live CD and check this problem. As far as I can remember, I never had such problems in Breezy. This problem with chhoti matra however, is consistent in all versions of windows!

> Yes, I did upgrade to firefox 1.5. The encoding is UTF-8 but still the same problem.

Try [http://hi.wikipedia.org](http://hi.wikipedia.org) and let me know if you dont see the fonts correctly.

[quote]Also, the main problem, when I start a session selecting hindi as the language, the menu names are not correctly displayed. They come as they are in the image in this [post]("http://www.ubuntuforums.org/showthread.php?t=102778") by anil.

Yes, some of the menu names are displayed strangely. This may be an issue with the fontset rather than anything else. The indian fonts used in Ubuntu were developed by a company in Pune, and I think their implementation in Ubuntu is not 100% fine - something is lacking somewhere.

> Also, the devnagri fonts are much smaller than roman fonts at the same size.

Yes, they have to be.

Reason: Devanagari fonts have to leave some room for matras both above and below the character. That leaves little room for the character itself! Quite logical.

> Surprisingly, everything is fine when written in Gedit.

> FC4's gnome version in hindi is able to display everything properly. Wonder what could be the problem.

Well, I can't really pinpoint the problem - my technical expertise is very limited in Linux. Maybe someone knowledgeable enough can find the answer and  post it here! :rolleyes:

---

### Post by sandygmaharaj on 2006-03-27
[QUOTE=anil_robo]Sandeep try getting hold of a Dapper Live CD and check this problem. As far as I can remember, I never had such problems in Breezy. This problem with chhoti matra however, is consistent in all versions of windows!



Try [http://hi.wikipedia.org](http://hi.wikipedia.org) and let me know if you dont see the fonts correctly.[/QUOTE]

Back to original firefox, it displays everything fine.


[QUOTE=anil_robo]Yes, some of the menu names are displayed strangely. This may be an issue with the fontset rather than anything else. The indian fonts used in Ubuntu were developed by a company in Pune, and I think their implementation in Ubuntu is not 100% fine - something is lacking somewhere.



Yes, they have to be.

Reason: Devanagari fonts have to leave some room for matras both above and below the character. That leaves little room for the character itself! Quite logical.





Well, I can't really pinpoint the problem - my technical expertise is very limited in Linux. Maybe someone knowledgeable enough can find the answer and  post it here! :rolleyes:[/QUOTE]

If somebody has any tips about this, pls do post.

---

### Post by sandygmaharaj on 2006-04-01
Okay. So, finally solved the Ubuntu interface problem. From System->Font, select one of those Hindi fonts (Gargi or Lohit, I prefer Gargi) and the interface is rendered properly.

Firefox 1.5 is still broken but I use firefox shipped with Ubuntu and it works fine.

Thanks anil and [ravi]("http://linuxhelp.blogspot.com/") for your help.

---

### Post by krsnendu on 2007-06-12
I want to be able to input from the keyboard so that sanskrt font prints our with the proper ligatures, (combined forms of letters). I've googled around and can't find the solution. I have SCIM running, I have hindi font etc installed, and I can type devanagari letters, but I want to be able to do combined consonants. Can anyone give me some clues how to do it?

---

