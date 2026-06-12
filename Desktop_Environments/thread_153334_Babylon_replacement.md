---
title: "Babylon replacement?"
date: 2006-03-31
forum: Desktop Environments
---

### Post by atheist on 2006-03-31
I installed linux (Ubuntu) a week ago first time and I love it! Everything works so far.
In order for to get rid of Windows complitely I need to find the last thing - Babylon ([www.babylon.com)](www.babylon.com)). The key advantage of Babylon is that it give a word translation into Russian with just a mouse click. Can someone recommend a replacement?

---

### Post by rwabel on 2006-04-07
[quote=atheist]I installed linux (Ubuntu) a week ago first time and I love it! Everything works so far.
In order for to get rid of Windows complitely I need to find the last thing - Babylon ([www.babylon.com)]("http://www.babylon.com%29"). The key advantage of Babylon is that it give a word translation into Russian with just a mouse click. Can someone recommend a replacement?[/quote]

there is stardict and ktranslator, don't know about russian. give them a shot

---

### Post by medya on 2007-04-27
you can use StarDict and you can import babylon dictionaries... read [more here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

---

### Post by neymac on 2007-10-23
Yes, there is a replacement for Babylon in Ubuntu, I'm using it.
xFarDic
It uses the database file *.xdb.
To convert the babylon free dictionaries files to *.xdb format you need a scrtipt found at
[http://osp.ir/projects/bgl2x](http://osp.ir/projects/bgl2x), download and edit this script to change the cp1256 (used for Farsi and arabic caracteres) to cp1252 (it is a superset of iso-8859-1 caracteres) or in your case change it to cp1251 (used for Cyrillic if you speak russian), make it executable, download the free babylon dictionary you want (in BGL format from [http://www.babylon.com.br/DicionariosGlossarios.asp?s=5](http://www.babylon.com.br/DicionariosGlossarios.asp?s=5) or from your language shown babylon's site ), run the script in a terminal  (./bgl2x.py <name_of_dictionary_file.bgl>)
After little time will be created the file <name_of_dictionary_file.xdb> converted.
Now you need the program xFarDic:
I downloaded it from [http://www.xfardic.org/html/index.php?newlang=eng](http://www.xfardic.org/html/index.php?newlang=eng)
Although I'm using Gutsy I installed the Feisty deb package and worked very well for Brazilian Portuguese.

PS: The codepages kinds you can see at [http://en.wikipedia.org/wiki/Codepage](http://en.wikipedia.org/wiki/Codepage)

---

### Post by jfbaro on 2007-10-24
Hey guys,

Would any of these replacements work by just clicking the word? Or would I need to enter the word (or sentence) into a textField? I think this feature is quite handy on babylon (Windows). I have a license for babylon and asked them about a Linux version, they said there is no demand for one. I will not renew my license for Babylon as I am quite confortable with Kubuntu.
Thanks

---

### Post by ali80 on 2008-03-11
yes,by highlightening the word it would show the meaning for about 5 secoonds,and everything is customizeable , i am using xFarDic now,it has some featues even babylon doesnt
it is a great dictionary ,give it a try

---

### Post by ozlemG on 2008-03-28
> **medya said:**
> you can use StarDict and you can import babylon dictionaries... read [more here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

hi, i am quite new to use ubuntu and linux... i followed your structure for replacing the babylon but i could not run the  comman 'sudo make all install', 

'''make: *** No rule to make target `install'.  Stop.''' is displayed on terminal,, So, i stack on this point. any help or suggestion?

thanks  a lot.

---

### Post by go_beep_yourself on 2008-05-07
I believe the new Babylon dictionary files are in .bgf format and no longer .dict. The dictionaries I am currently using are not up to par. They don't say whether a noun is masculine or feminine. Also there can be several translated words without examples or ways to differentiate them that can make them inappropriate for the context used. I wish there was a way to convert those .bgf files into something Linux could use. Thanks for you listening.

---

### Post by go_beep_yourself on 2008-05-08
> **medya said:**
> you can use StarDict and you can import babylon dictionaries... read [more here]("http://blog.shevin.info/2007/04/how-to-implement-babylon-dictionaries.html")

That did not work for me. I tried StarDict, but that software is complicated, not user friendly, so I'd have to spend a lot of time to learn how. But KTranslator is easy to use. Also KTranslator works with several formats, StarDict, but not BGL, I converted the BGL files with those instructions. In these screenshots, look at the number of words the converted dictionaries gave me. The conversions gave me three files. I tried the ifo stardict file (second picture). That didn't work. Then I tried the dictd files (first picture). Neither worked.

---

### Post by marciowb on 2008-07-17
There is [Stardict]("http://stardict.sourceforge.net"). Try it and love it! It's fantastic! Better than Babylon. Belive me.
If you need some help to full install it or its TTS or glossaries, see tips at: [http://www.marciowb.net/blog/2008/07...a-linux-para-o](http://www.marciowb.net/blog/2008/07...a-linux-para-o)

Regards,
Marcio Wesley Borges
[http://www.marciowb.net/blog/](http://www.marciowb.net/blog/)

---

