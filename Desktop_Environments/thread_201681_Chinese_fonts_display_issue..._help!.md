---
title: "Chinese fonts display issue... help!"
date: 2006-06-22
forum: Desktop Environments
---

### Post by ePierre on 2006-06-22
Hello everybody!

After having successfully installed Dapper on my Asus laptop, I realized that the Chinese fonts were pretty strange in any application I used (gaim as long as Firefox).

In fact, the system mixes a lot of fonts to display the texts (see the screenshot included, extracted from [www.ubuntu.com.cn](www.ubuntu.com.cn) website for more explanation...).

I found out two articles speaking about that problem: [Chinese Display in Dapper Beta]("http://ubuntuforums.org/showthread.php?t=165216&highlight=chinese+fonts") (on this forum), and [Configure ubuntu chinese display]("http://http://fuyichin.blogspot.com/2006/06/configure-ubuntu-chinese-display.html") (on a blog).

The first method seems to be interesting, but since I am not interested with Japanese, I tried to replace the xml value by cn, restart my X session, and.. nothing happened, Exactly the same. When using the XML value "ja", I got exactly the same result.

I tried the second method, which seems to be a bit strange, because it asks to modify the file **/etc/fonts/fonts.conf**, but in this file, it is written we should not modify it!
Anyway, I try to modify it as needed, by puting the Japanese font XML value under the Chinese one, but I got the same result as before: nil.

It is pretty annoying, especially since I do not know what to do! Of course, I tried to install a couple of fonts from Synaptic, with no result...

By the way, my system is basically in English, but I can type Chinese using SCIM...

Does anyone has an idea on how to do?

Thanks in advance! :D

---

### Post by fdimmling on 2006-06-22
Hi,

AFAIK the problems stems from the fact that you have Unicode coded text but fonts that contain different parts of the Asian glyphs. I had not the time so far to work on the problem for Dapper but the basic strategy is to remove as many Asian fonts as possible. As far as I have seen Dapper has an Arphic Unicode font. This font alone (kai and song or ming type) should be enough for displaying all Chinese (simplified and traditional) in Firefox, Thunderbird etc. (For me it is not so easy because I need TeX and TeX needs the GuoBiao and Big5 coded versions of  the Arphic Truetype fonts.)  You can also look for the Bitstream Cyberbit font which is fairly complete with respect to Chinese characters. 

If you like we can stay in contact by PM. I have to solve this problem for me anyway. I have written a Chinese dictionary program and the different fonts are boring.

Friedrich

---

### Post by Endukugga on 2006-07-02
Hi, I wrote another HOWTO for a better Japanese fonts display in Ubuntu 6.06. You can have a look [here]("http://ubuntuforums.org/showthread.php?t=206280"). I think it applies to Chinese as well, you just need a good Chinese font.

I hope you find it useful. Feedback is welcome!

---

### Post by MantenaBr on 2006-10-20
Hi, 

I had the same issue here.
This is how I solved it

[link to another post]("http://www.ubuntuforums.org/showpost.php?p=1641255&postcount=2")

Peace

---

