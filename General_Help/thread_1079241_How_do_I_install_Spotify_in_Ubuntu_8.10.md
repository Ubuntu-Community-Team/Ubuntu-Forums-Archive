---
title: "How do I install Spotify in Ubuntu 8.10?"
date: 2009-02-24
forum: General Help
---

### Post by Lingonet on 2009-02-24
Hello!

I have aquestion regarding Spotify. How do I install it in Ubuntu Intrepid? I have heard other talk about they having Spotify on their Ubuntu computers, and I have no idea how to install it.

How do I do that?

Thank you!

---

### Post by Lingonet on 2009-02-25
This is weird. I have not gotten a reply. Please reply!

---

### Post by dhughes on 2009-02-25
Since there isn't a Linux version the Spotify website's download section says "If you are using Linux, you might want to  run Spotify under Wine. " 

[http://www.spotify.com/en/download/other/](http://www.spotify.com/en/download/other/)

---

### Post by Lingonet on 2009-02-27
What's Wine and how do I Spotify in it?

---

### Post by fridez on 2009-03-06
" Wine is a translation layer (a program loader) capable of running Windows applications on Linux and other POSIX compatible operating systems." 

[http://www.winehq.org/]("http://www.winehq.org/")

how to run spotify under wine: 
[http://www.spotify.com/en/help/faq/wine/]("http://www.spotify.com/en/help/faq/wine/") 
:D

---

### Post by Azyx on 2009-03-13
> **Lingonet said:**
> What's Wine and how do I Spotify in it?

I just did:

sudo apt-get install wine

Then i downloaded the windows version of spotify-installer on my desktop and dubbelclick on the file, and wine started the installer and then install spotify under wine, and a spotify icon appears on my desktop and under wine-->Programs--Spotify.

Unbelivable simple :)

---

### Post by Gryphon-ni on 2009-03-25
I also use this as the command line to launch spotify in wine, it sizes everything up nicely for me:

```
env WINEPREFIX="/home/USERNAME/.wine" wine explorer /desktop=1,610x450 "C:\Program Files\Spotify\spotify.exe"
```

Obviously change USERNAME to whatever your own username is.

---

### Post by Johnsie on 2009-03-30
I wish someone would make a decent installer/script to automate this on Linux. Windows installation was quick 'n easy. With Ubuntu it can and should be the same, otherwise it's +1 for Windows again.

---

### Post by Johnsie on 2009-03-30
Actually I take that back. Installing this was as simple as:

> sudo apt-get install wine

And then downloading and running the installer. It even made an icon on my desktop. It's a shame the audio quality with this is alot better on Windows than it is on Linux.

---

### Post by Azyx on 2009-03-30
> **Johnsie said:**
> Actually I take that back. Installing this was as simple as:



And then downloading and running the installer. It even made an icon on my desktop. It's a shame the audio quality with this is alot better on Windows than it is on Linux.

Don't u haven't a soundproblem then? I can not understand how it could be better than on my Ubuntu machine?

---

### Post by munozdj on 2009-06-30
About the sound quality in wine, you have to change the audio settings. Go to wine config (type winecfg in your Terminal window), then go to the Audio tab. You will find some DirectSound options at the bottom of the window. What you need to do is change the Hardware Acceleration option from Full (default) to Emulation. I made that change and now Spotify works just as it does in Windows.

---

