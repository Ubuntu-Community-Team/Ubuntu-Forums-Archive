---
title: "Font rendering"
date: 2005-04-19
forum: Desktop Environments
---

### Post by Jagec on 2005-04-19
Hi there!

I'm having problems with fonts rendering. Fonts on all Debian based distros looks quite different comparing to other distros. Bistream Vera Sans Mono for instance looks quite different on Fedora, Slack and all Debian based distro, not just Ubuntu. What's the catch? How to make fonts looks the same as in the other Linux distros?
I found "official" screen shots somewhere on the Ubuntu web pages with normal fonts, so, I suppose that they might look normal. How can I manage it?

Thank you.

P.S. I found some howtos for making it the same as in Windows, but that's not what I'm looking for. Just want'em look the same as in the all distros.

---

### Post by kassetra on 2005-04-19
[QUOTE=Jagec]
P.S. I found some howtos for making it the same as in Windows, but that's not what I'm looking for. Just want'em look the same as in the all distros.[/QUOTE]

I had just the opposite reaction - my fonts in Ubuntu looked much better than in any other distro I used, but here is one suggestion:
Edit /etc/fonts/local.conf and enable the freetype autohinter module.  The last section of the file will appear as: 

 

  ```
 <!--  

  <match target="font">
   <edit name="autohint" mode="assign">
     <bool>true
   </edit>
 </match>
-->


```    

 Remove the comment tags <!--  and --> then run 

    ```
defoma-reconfigure
```    And / Or you can always follow these instructions:
[http://www.ubuntuforums.org/showthread.php?t=4456](http://www.ubuntuforums.org/showthread.php?t=4456)

---

### Post by Jagec on 2005-04-21
I reinstalled my Ubuntu and did that what you said ant the only thing I can say is that tweak rocks !!!! Thanks mate!

P.S. You should enable that option by default Ubuntu guys ;) You did a great job with Hoary and thank you all for giving us a great desktop distro :) I will replace my good old Slackware with Ubuntu these days on my main system!!! Thats for sure ;)

P.P.S. For Ubuntu guys: Just don't make the same mistake as Red Hat did with all these redhat-config-* tools. The only thing for desktop users you should make is the graphical installer - I don't need one thoe. And the 1 or 2 DVD images for dial-up users. 1 with all the software and the second one with development tool, kernel sources and some extra software. Besides that, you did a great job. Bravo Ubuntu guys ;)

---

### Post by addikt on 2005-04-23
kassetra, thx so so much !!!! omg I can't explain how good this looks ... it's an exact duplicate of clear type on Xp now !!!! woot  :grin: 

wonders if most newbies know about this wicked tweak  :neutral:

---

