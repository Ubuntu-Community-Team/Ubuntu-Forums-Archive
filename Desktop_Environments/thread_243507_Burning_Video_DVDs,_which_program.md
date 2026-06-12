---
title: "Burning Video DVDs, which program?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Theimon on 2006-08-25
I have searched and tried several different programs to burn video dvds with but none seem to work or even support it....and I'm talking about your usual .vob, .bup and .ifo files
I could try NeroLinux except I cannot get it working on my Ubuntu which is a AMD64 version (NeroLinux is 32bits), so if anyone has any suggestions I'd be more than happy to try it out.

---

### Post by fdimmling on 2006-08-25
k3b is burning video dvds, but you have to provide the necessary data, the usual .vob etc. 
To make these files out of mpeg files you have to use a dvd authoring tool like qdvdauthor or kmediafactory. But these programs are rather alpha or beta status so far. You can author dvds with them but you will most probably face some problems and shortcomings and maybe - as in my case - your stand alone dvd player may refuse to show the menu or somethin like that while kaffeine or xine  or totem has no problem with the burned dvd.

There is some more way to out-of-the-box authored video dvds in Linux. Be patient and start playing around - preferably with dvd-rw to save your money.

Good luck

Friedrich

---

### Post by _mrv on 2006-08-25
Hi,

I use dvdstyler; great piece of software:

[http://dvdstyler.sourceforge.net/]("http://dvdstyler.sourceforge.net/")

 _mrv

---

### Post by Theimon on 2006-08-25
Thank you both for your responses.

Both k3b and Dvdstyler are good options. I've searched and tried lots of different programs but up till now I didn't find anyone which supports dvd-video. The windows way was easy, start Nero, select dvd-video, throw your vobs in there and you're up and running. But it seems dvd-video isn't supported that way in Linux. I'll go take a look at the tips you gave me. Thank you :)

---

### Post by ohgod on 2006-08-25
If you've already got the dvd structure all setup in a folder (the .vob & .ifo files) you can turn them into an .iso like so:

```
mkisofs -dvd-video -o output.iso foldername/ 
```

Then you can burn them in NeroLINUX by using the 'Burn image' feature.  

K3b has a dvd-video option but for some reason it never worked for me :(  So I went this route instead.

---

### Post by orb9220 on 2006-08-25
Well I use windows dvdshrink under wine. Works great compresses to video_ts folder like you have or create a ready to burn iso by right clik in nautilus.

DVDshrink will give you the control you need in the dvd movie ripping. Deselects unwanted foriegn language,compress extra's to the max so you have less compression on main movie. Or hit the reauthor button and just rip the main movie. Will create a dvd compliant folder or iso for burning.

---

### Post by fdimmling on 2006-08-25
> **Theimon said:**
> 
Both k3b and Dvdstyler are good options. I've searched and tried lots of different programs but up till now I didn't find anyone which supports dvd-video. The windows way was easy, start Nero, select dvd-video, throw your vobs in there and you're up and running. But it seems dvd-video isn't supported that way in Linux. I'll go take a look at the tips you gave me.

With k3b it is just as easy. You select File->New Project->Video DVD and drag in the Viedo_Ts and Audio_TS directories and click the Burn button. However with my stand alone video recorder you have to select the DAO mode for burning.

Friedrich

---

### Post by Surf Man on 2006-09-01
Nerolinux is offering free application if you have purchased 6 ultra or above in the past and have a number:rolleyes: .

---

### Post by 3rdalbum on 2006-09-01
Nerolinux doesn't transcode video, though.

I'm very interested in a solution, too; where I can take MPEG files directly from my capture box, transcode them and burn to video DVD, without having to use MEncoder or Transcode from the command line. I don't have the next couple of months free to read the man pages :-)

---

### Post by Theimon on 2006-09-02
I didn't have time (work started again after 2 weeks vacation) yet to try and test some things but I'm very glad to see some new options as well. I will keep them in mind.

---

### Post by lagartoflojo on 2006-09-02
Maybe what you are looking for is tovid. It will take avi/mov/mpg files and turn then into DVD-compliant MPEG. It can create menus and burn the disc. Get it in [www.tovid.org](www.tovid.org)

---

