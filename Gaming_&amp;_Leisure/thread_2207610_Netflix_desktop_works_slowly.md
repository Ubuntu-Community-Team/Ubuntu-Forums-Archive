---
title: "Netflix desktop works slowly"
date: 2014-02-24
forum: Gaming &amp; Leisure
---

### Post by GJ86 on 2014-02-24
Hello. So I hope this is the right place for my thread.
Well I just installed Ubuntu 12.04 LTS and find out that Netflix desktop works really bad... the movies are not in hd, the picture is really bad and the audio and video are not sync...
The thing is that on the same laptop (asus eee) when i was running windows 7 netflix worked fine and with no problems, on the other hand Hulu worked real awful while on Ubuntu Hulu works perfectly. This is kind of strange.
I'm using Netflix with Hola Unblocker added in Netflix desktop (i live in Europe).
so i'm guessing, is there anything i can do to have Netflix working fine like before in win7.
thank you. :)

---

### Post by zybersun on 2014-02-24
Not sure if you tried this already. But I used these two links to set up Netflix on Ubuntu 13.10 64bit. I have no issues at all and so far it is running better on Ubuntu than it did on other distro's and runs as good as it runs on Windows 7 64bit. With the links below the order I installed everything was Pipelight first and than I followed the second link to install Netflix.

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)
[http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/](http://linuxg.net/how-to-use-netflix-on-ubuntu-13-04/)

---

### Post by GJ86 on 2014-02-24
Thank you for the reply. I'll try and post the results. Hope it works.

---

### Post by Robert_Fairing on 2014-02-24
I am using Ubuntu 13.10 and have done everything I can find but still cannot get Netflix to work.

---

### Post by zybersun on 2014-02-25
> **Robert_Fairing said:**
> I am using Ubuntu 13.10 and have done everything I can find but still cannot get Netflix to work.

Did you try the instructions in the links I posted above? I am having no issues at all with Netflix on 13.10 64bit.

Also I am not sure what kind of hardware you have, that could make a difference as well.

---

### Post by Robert_Fairing on 2014-02-25
I have a Dell inspiron N7110 with 8 gig. I followed every step on the two links you provided. I am not new to Ubuntu but still at the beginners level. This is a new to me computer and I just installed Ubuntu 13.10. I may need more basic information but after following every step you provided I still cannot watch Netflix by trying to open from FF, Chromium, of the Netflix loader. In fact I have not even gotten to where the netflix loader will show up on my tool bar. It starts to load then quits.

---

### Post by Robert_Fairing on 2014-02-25
Just a thought, would my adblock plus or ghostery be interfering?

---

### Post by Robert_Fairing on 2014-02-25
Nope. still will not work.

---

### Post by GJ86 on 2014-02-25
So in my case I removed the Netflix Desktop and installed Pipelight and enabled the user agent switcher, so I watch Netflix directly from Chrome now. It works much much better now but still have some issues.. The video is really good and the audio is now sync but when I hit the full screen mode the picture starts to have some malfunctions like stopping every 5 seconds for a very brief time... like little slide shows lasting a millisecond (I don't know how to explain it, hope this helps). I have an Asus EEE 1005HA with 1GB of RAM. Maybe I'll try it with Lubuntu or Xubutnu to see if it does for me with a lighter OS..

---

### Post by Robert_Fairing on 2014-02-25
Pipelight and user agent installed and still no Netflix.

---

### Post by GJ86 on 2014-02-25
What do you get when you try to start Netflix? The loading stops or you get this
[IMG]http://cdn.asherbond.com/screen-shots-are-my-art-at-the-moment/evelyn-abundis-aka-ubuntis-gets-locked-out-of-netflix-web-site-because-she-uses-ubuntu-instead-of-windows-or-macintosh.png[/IMG]

---

### Post by GJ86 on 2014-02-25
if you are using User Agent in Chrome you have to click on the User Agent icon and select something like Windows/Firefox 15 or something like this... I don't remember it right now.

---

### Post by GJ86 on 2014-02-26
Today I've managed to solve the problem. I installed a fresh version of Xubuntu and when I installed Pipelight I got an error in Netflix that says player error error code 1001 which is related to Silverlight.. so then I installed Netflix desktop and the error message was gone when I watched it in Chromium or Firefox and it works really smooth whit no issues like when I was running it in Ubuntu. The only thing was that Netflix desktop won't start for me in Xubuntu so I purged it and  Netflix still works for me in Chromium real fine.

---

### Post by Robert_Fairing on 2014-02-27
That solved my problem. Thanks!

---

### Post by zybersun on 2014-02-27
Sorry for the late reply. Busy and not online that much lately. I am glad you got things working.

---

