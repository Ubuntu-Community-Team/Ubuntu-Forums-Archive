---
title: "Firefox crashing on Facebook uploads"
date: 2009-01-14
forum: General Help
---

### Post by mathfreak123 on 2009-01-14
Whenever I use facebook, everything is fine until I try to upload photos using the Java uploader. I've searched for solutions of this problem, but it seems that I can only find solutions to problems of the Java applet remaining a gray box, and nothing more.

My problem is that whenever I enter the Facebook page for the Java photo uploader, the applet not only remains a gray box; Firefox stops responding. I have to force quit and restart its session.

I'm running a Wubi install of 8.10, and I use Firefox 3.0.5. What can I do to stop firefox from crashing when I attempt to use the Facebook photo Java uploader?

EDIT: It was able to work this time around, but it made Firefox unresponsive for a while.

---

### Post by kokkus on 2009-01-14
I have the same problem, including uploading to youtube, mogulus and veoh.com.
I hope this problem will be solved soon or if someone has a solution.
I Know it's not the web browsers problem, coz I tried with other browsers too.
I believe it has something to do with the flash plugin
This bug only comes when I upload files using a flash script like on facebook, youtube and veoh.

---

### Post by captain_conrad on 2009-03-04
hi guys

I have the EXACT same problem! 

If its the first time for the day that i am using facebook photo uploader, it works properly, uploads all 60 photos, (and it takes its sweeeeeeeet meeeeeerry time to do this) and then instead of the lovely little ¨upload successfull¨ window, it says ¨Upload unsuccessfull¨.
](*,)

But here´s how i have been able to get around it. Switching the PC completely off and back on again., logging in to facebook, first time using the photo uploader, I upload only +/-20 photos at a time, which i would have to do three times. Its way more time consuming other than uploading all 60 photos one shot, but thank goodness it posts them...

Even though this has worked for me, I am still limited to one album upload, after finishing the first album (of 3 uploads x 20 photo). If i try to use the java uploader thingie, it then turns into a grey square (where the uploader should be) and then my firefox freezes up, and then i have to force quit, after which it will not even allow me to open up firefox at all! I have to then completely reboot my PC.](*,)

The first thing i did do wrong is having 6 desktops running with things on them (rhythmbox, evolution email, another firefox with ubuntuforums, virtualbox, and skype). I then tried the whole upload scenario again (after rebooting) and this time nothing else running other than facebook photo uploader. And the same thing happens, i can upload a few photos at a time, but the second time i use the same java uploader thingie, boom! grey screen and firefox frozen, force quit, reboot.](*,)

Please please please i hope somebody finds a way to fix this, i am a HUGE fan of photos on facebook.

thank you

---

### Post by barbolanero on 2009-03-04
I too share this problem. Only that in my case it's more randomatic. It just happens sometimes, and other times works perfectly. Who knows why, probably some flash thing I'd guess.

---

### Post by emarkay on 2009-03-04
IMHO suggest looking into this on the FF boards, too - it may be an issue with FF not Ubuntu.

---

### Post by David Valentine on 2009-03-09
> What can I do to stop firefox from crashing when I attempt to use the Facebook photo Java uploader?Assuming you have Sun Java 6 installed, try creating a link from your firefox plugins directory to the executable:```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin.so
```It worked a charm for me.

---

### Post by Procuro on 2009-03-11
On my 64 bit installation I just use fireuploader to upload stuff to facebook and youtube. It works with other websites as well: [https://addons.mozilla.org/en-US/firefox/addon/4724](https://addons.mozilla.org/en-US/firefox/addon/4724) 

At least its a nice workaround until the java issue is fixed :)

---

### Post by Mythology on 2009-03-13
I'm on Intrepid and yesterday when I installed it and tried to checkout a video on youtube... firfox froze. Everytime I tried to watch a video on Youtube, it would freeze the browser. It was so frustrating because when I was running Live CD, everything worked *perfectly*. I even got a little more sound/volume out of it.

And when I installed Ubuntu, there was barely any sound. EVERYTHING was turned up to the maximum (that's always the first suggestion.)

I've used 8.04 before too. 

I eventually concluded that I will never be able to use Ubuntu as my sole OS because of the sound, video and internet problems that can never seem to get fixed.

But I am keeping it. Because I tried to partition over it and I kept get grub errors (17 and 22). I really got fed up and decided ..what the hell. I will keep Ubuntu and go on playing around on it. Another thing that contributed to the decision was the fact that I finally figured out how to make the GRUB default to XP so I dont have to sit around and click to XP. (Usually I turn computer on and walk away immediately to get some coffee or something.)

I wish someday I can sort out these problems. :$ But that's what's so great about this forum. People JUMP to help us newbies out.

---

### Post by Mythology on 2009-03-13
I'm on Intrepid and yesterday when I installed it and tried to checkout a video on youtube... firfox froze. Everytime I tried to watch a video on Youtube, it would freeze the browser. It was so frustrating because when I was running Live CD, everything worked *perfectly*. I even got a little more sound/volume out of it.

And when I installed Ubuntu, there was barely any sound. EVERYTHING was turned up to the maximum (that's always the first suggestion.)

I've used 8.04 before too. 

I eventually concluded that I will never be able to use Ubuntu as my sole OS because of the sound, video and internet problems that can never seem to get fixed.

But I am keeping it. Because I tried to partition over it and I kept get grub errors (17 and 22). I really got fed up and decided ..what the hell. I will keep Ubuntu and go on playing around on it. Another thing that contributed to the decision was the fact that I finally figured out how to make the GRUB default to XP so I dont have to sit around and click to XP. (Usually I turn computer on and walk away immediately to get some coffee or something.)

I wish someday I can sort out these problems. :$ But that's what's so great about this forum. People JUMP to help us newbies out.

---

### Post by emptyoceans on 2009-03-16
As suggested on some other forums, I just disabled all java add-ons and now it goes straight to the upload photos album. 

Tools > add ons > (disable)

Hope that helps!

---

### Post by lethalfang on 2009-08-24
Facebook upload freezes my firefox. 
My only way around it so far is to use Seamonkey (my alternative browser) and then use simple uploader.

---

### Post by mathfreak123 on 2009-11-22
I'd just like to say the problem seems to be solved. I'm using Karmic Koala, and I used the icedtea6-plugin for my Java uploader problems. It works really well.

---

