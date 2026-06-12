---
title: "Sound and/or video issue(s)"
date: 2009-02-13
forum: General Help
---

### Post by Zoquara on 2009-02-13
I don't even know where to begin on describing the problem(s) I've been having...

I don't use my computer for a lot... Web browsing, watching movies, and playing WoW (now with Wine, since I just switched to Ubuntu a few weeks ago) At first, I thought the issues I was having were only in WoW (and as such, they'd have belonged in the Wine forums, I know) but tonight, while trying to watch a movie, I realized it wasn't..

First issue: My sound is REALLY low. To listen with my headset, I have to have my headset and the program's volume maxxed. Same with using my monitor's built-in speakers... and for my other set of speakers, they have to be turned up to where I can always hear a hum. Not exactly a pleasing situation... and even then, many things are barely audible. Last time I posted with this issue,  someone suggested I get the PulseAudio aaplet.. and I maxxed all outgoing volumes in it, and that helped, but it still has very low volume. 
Second issue: Random... freezing. Scrolling down a webpage, or watching a video (off the web or from a DVD), the visual effects stop completely, although the sound is completely uneffected and doesn't even lag or glitch.


I'll admit right now: I'm lost as heck with Ubuntu. I knew my way around Windows fairly well, but this is totally different. I knew that making the change, and am willing to learn, but don't quite know where to start. I'm not sure what info would be helpful in this, but here's a try at it:
I'm using Ubuntu 8.04 on a Compaq Presario SR5113WM. The only current change to my computer is I added some RAM (up to 1.5 gigs, now)

Thanks in advance for any help!

---

### Post by unimatrix on 2009-02-13
I'm familiar with all of your problems (and believe it or not, I'm far from the only one)

For the sound issue, you should probably max the PCM (and/or Front) in your mixer settings and then use Master to actually set the volume. Here's the screenshot of my mixer:
[IMG]http://img10.imageshack.us/img10/9480/screenshotvolumecontrolal2.png[/IMG]
If you don't find PCM (and/or Front) you will probably have to enable it under Properties.

Also bare in mind that sound in Linux works differently than it does in Windows. It's kinda annoying and hard to get used to, but the volume is much lower in general. That doesn't mean you can't get a decent volume, but your volume settings will usually be much higher than in Windows to achieve the same sound level. I don't know why the ALSA guys still haven't fixed this after so many years, but apparently they don't see an issue like we do.

Random freezing? You'll have to be a bit more specific.
Your system freezes when you scroll? Freezes how? So that you need to reboot? Please be more specific.
I assume you meant temporary freezing.

So please also provide your system specs.

---

### Post by Zoquara on 2009-02-13
It doesn't freeze to the point I need to reboot... It's temporary, only lasts a few seconds, and happens just often enough to be really obnoxious.

My comp. specs can be found [here.]("http://www.walmart.com/catalog/product.do?product_id=5982771#Specifications") 

Thank you so much for your help. I followed the sound guide (hopefully correctly!) and the sound is a bit better now, although still low :confused: Eh, I'll learn this eventually. Just need an Ubuntu for dummies guide for now!

---

### Post by unimatrix on 2009-02-14
In the sound mixer, try going under Preferences, checking ALL the checkboxes, and then max all the sliders all the way to 100%. Maybe that way you will find one that actually makes a difference. Just a suggestion tho.

As for the freezing.
The first thing I'd try would be to disable Compiz. Do this by going to System --> Preferences --> Appearance --> Visual Effects (tab) --> and select "None"

I see you got an nVidia that's not really the newest. You did install the video drivers right? Just checking.

---

### Post by Zoquara on 2009-02-15
> **unimatrix said:**
> 
As for the freezing.
The first thing I'd try would be to disable Compiz. Do this by going to System --> Preferences --> Appearance --> Visual Effects (tab) --> and select "None"

I see you got an nVidia that's not really the newest. You did install the video drivers right? Just checking.

I'll try that, and yes, I installed them. Thank you!

---

### Post by indeterminate on 2009-02-15
It looks like your sound card is one of the onboard Intel HDA ones... I've had 2 computers with that chipset and the Linux volume was really low, but in Windows it was much higher. See if [this thread]("http://ubuntuforums.org/showthread.php?t=389560") helps.

---

