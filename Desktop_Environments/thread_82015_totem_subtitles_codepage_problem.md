---
title: "totem subtitles codepage problem"
date: 2005-10-25
forum: Desktop Environments
---

### Post by flower on 2005-10-25
I've been desperately trying to get my totem subtitles show in cyrillic letters, but .. no success. I get either underscore for every letter (unicode fonts) or latin accented letters (non- unicode fonts). 

in the font dialog there's no codepage selection and I've tried several fonts (in fact all my installed fonts), but no luck ... 

I can't find a ".totem" folder in my home to check for config files also...

I was using knoppix/xine some time ago and it was rendering the subs great :(

so ... anybody who can share expirience with cyrillic subtitles ?

---

### Post by PenguinZdravko on 2005-11-04
Hi, flower! I have the same problem. I don't know how to fix it, but i want tto to request for help!
P.S.: &#1053;&#1072;&#1081;-&#1087;&#1086;&#1089;&#1083;&#1077; &#1085;&#1072;&#1084;&#1077;&#1088;&#1080;&#1093; &#1086;&#1097;&#1077; &#1077;&#1076;&#1080;&#1085; &#1073;&#1098;&#1083;&#1075;&#1072;&#1088;&#1080;&#1085; &#1074; &#1090;&#1086;&#1079;&#1080; &#1092;&#1086;&#1088;&#1091;&#1084;.

---

### Post by VortX on 2005-11-13
Had the same problem and here's how I solved it:

1. Open for edit the file totem_config (located in "/home/<username>/.gnome2/"):

```
gedit ~/.gnome2/totem_config
```

2. Find the lines:
```
# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1
```

For cyrillic (windows-1251) replace with:
```
# encoding of the subtitles
# string, default: iso-8859-1
subtitles.separate.src_encoding:windows-1251
```

For Unicode replace windows-1251 with UTF-8

---

### Post by flower on 2005-11-13
hei 10x very much ... I didn't realize the totem config is in gnome subfolder... 
I'm going to try this right away ... 10x once again

---

### Post by flower on 2005-11-13
yeah ... I'll try it some other time ... 
breezy fu**ed again, and I have to find out what's this time ...

---

### Post by shemet on 2005-11-15
[QUOTE=VortX]Had the same problem and here's how I solved it:

1. Open for edit the file totem_config (located in "/home/<username>/.gnome2/"):

```
gedit ~/.gnome2/totem_config
```

2. Find the lines:
```
# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1
```

For cyrillic (windows-1251) replace with:
```
# encoding of the subtitles
# string, default: iso-8859-1
subtitles.separate.src_encoding:windows-1251
```

For Unicode replace windows-1251 with UTF-8[/QUOTE]
Takyv fajl niama :)
Totem 1.2.0
GStreamer version 0.8.11

---

### Post by cheirekov on 2005-11-24
[QUOTE=shemet]Takyv fajl niama :)
Totem 1.2.0
GStreamer version 0.8.11[/QUOTE]
That means that: "There is no such file"
I try to create it but the subtitles are still like this: "??? ?????? ????"
Please help! .

---

### Post by drmr on 2006-03-26
I just want to add that this solution is when using totem-xine. I'm still searching for solution when using Totem and GStreamer 0.10 but no luck for now:)

---

### Post by louis_nichols on 2006-05-03
[QUOTE=drmr]I just want to add that this solution is when using totem-xine. I'm still searching for solution when using Totem and GStreamer 0.10 but no luck for now:)[/QUOTE]

I'd like to know, too. Although xine is ok... But perhaps I'll need gstreamer sometime.

---

### Post by Sandu on 2006-05-14
[QUOTE=shemet]Open for edit the file totem_config (located in "/home/<username>/.gnome2/"):[/QUOTE]
Russian subtitles (encoded windows-1251) also appears as "???????" in Totem-gstreamer.
I could not find totem_config file in dapper Drake Beta. Search does not helped too.

But I solved this problem with **recode**. Just recoded my windows-1251 .srt file into utf8.
1. Install **recode** with Synaptic.
2. Open terminal and run:
```
recode windows-1251 <full_path_to_subtitles_file.srt>

```
This utilite will recode text file from windows-1251 encoding into default system locale (utf8, in my case). 
You must use your encoding instead of "windows-1251". And do not forget to save backup - it will rewrite original file!

---

### Post by louis_nichols on 2006-05-14
[QUOTE=Sandu]Russian subtitles (encoded windows-1251) also appears as "???????"/
I can not find totem_config file in dapper Drake Beta. Search does not helped too.
Where it is?[/QUOTE]
I think it's there only if you have totem-xine installed. If you have totem-gstreamer, it won't be.

---

### Post by Sandu on 2006-05-14
.

---

### Post by Sandu on 2006-05-14
[QUOTE=louis_nichols]I think it's there only if you have totem-xine installed. If you have totem-gstreamer, it won't be.[/QUOTE]
Totem-gstreamer. 100 %.
But it will be better to recode all your  .srt files with ```
recode
```
 and do not change totem_config each time when new language of subtitles is used (russian/romanian for example).

---

### Post by louis_nichols on 2006-05-14
[QUOTE=Sandu]Totem-gstreamer. 100 %.
But it will be better to recode all your  .srt files with ```
recode
```
 and do not change totem_config each time when new language of subtitles is used (russian/romanian for example).[/QUOTE]
recode is a pretty good workaround but I don't think it's really necessary. I mean, one person will quite likely only want to see subtitles in their native language and will have no reason to change the encoding of subtitle files.

---

