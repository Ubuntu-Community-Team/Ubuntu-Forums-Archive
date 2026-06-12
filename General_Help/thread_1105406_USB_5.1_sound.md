---
title: "USB 5.1 sound"
date: 2009-03-24
forum: General Help
---

### Post by jmadero on 2009-03-24
Hi All,

Trying to find ANYONE who can help me get my 5.1 working right. I have the GWC 5.1 USB, have found a few references online from people saying that they have gotten it to work (most notably the person in the newegg comments who said they got it to work and put how).

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101](http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101)

The comment says to make my .asoundrc look like this

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

unfortunately every time I put anything in my rc that has the line pcm!.default {

I get this error when I test it out (by test it out I mean going to system -> preferences -> sound, pushing test)

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. 

anyone? if someone does know and happens to also use AIM, I'd love to finally get 5.1 up in Linux. If this is possible private message me and I'll give my username.

Thanks all!

---

### Post by fooman on 2009-03-24
the following guide worked for me....btw, i only had to do THE EASY WAY and had working 5.1 in minutes:

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

hope that helps.

oops,  sorry...didn't notice that its usb....give that guide a shot anyways,  it still might help.

---

