---
title: "WMV on breezybadger???????"
date: 2006-03-01
forum: Desktop Environments
---

### Post by s_h_a_d_o_w_s on 2006-03-01
I have breezy and i really need to be able to watch WMV's 


HELP!!!!!!

---

### Post by Ramses de Norre on 2006-03-01
sudo gedit /etc/apt/sources.list
add this: ```
## penguin liberation front primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```

sudo apt-get update
sudo apt-get install w32codecs

search also the wiki for restricted formats

---

### Post by s_h_a_d_o_w_s on 2006-03-01
i tried it and when i tried to watch a WMV, it didn't work

is there maybe a video converter for breezy?

---

### Post by quonsar on 2006-03-01
"didn't work" is a really poor description of the problem.

what app tried to play it? 
what error message resulted? 

i play wmv's all the time.  if you expect help you must at least expend the effort to explain what is going on.

---

### Post by ronmarley1 on 2006-03-01
mPlayer with the w32codecs should do the trick

---

### Post by pacificdrums on 2006-03-01
I just use vlc media player and it plays them fine.

---

### Post by s_h_a_d_o_w_s on 2006-03-01
I mean can you plaw WMV's after downloadinig (on totem or realplayer10)

---

### Post by followme on 2006-03-01
just make sure you're not trying to watch a WMV with DRM (digital rights management).  

You can download it to your desktop and watch it or if it's streaming, it should start playing once it buffers

---

### Post by geuis on 2006-03-01
Is there a way for Firefox to play WMV files that are embedded into webpages? Firefox keeps prompting for a missing plugin.

---

### Post by ronmarley1 on 2006-03-02
[QUOTE=geuis]Is there a way for Firefox to play WMV files that are embedded into webpages? Firefox keeps prompting for a missing plugin.[/QUOTE]

see my post above

---

### Post by akiro.yamamoto on 2006-03-02
Mplayer with the mplayer plugin works for me.
I have the w32codecs installed.
Of course I'm still using Firefox 1.0.7. so YMMV.

---

### Post by geuis on 2006-03-02
ron I followed the install directions but when I goto pages with embedded windows media player files I still get the missing plugin warning in firefox and it wont play the files.

Im just trying to get this, if possible, to play wmv files in the browser when they are embedded.

Geuis

---

### Post by akiro.yamamoto on 2006-03-03
geuis:
Check this post. [http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)
I may have to add that link to my sig, it seems to be a popular question. ;)

Actually you should use the mozilla-mplayer plugin from the repos.

---

