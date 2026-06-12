---
title: "Sound record fails after gstreamer0.8-plugins"
date: 2006-01-07
forum: General Help
---

### Post by yookoala on 2006-01-07
Hello,

I encountered a problem on my Sony VAIO laptop recently. I found ubuntu fail on sound recording after I've installed gstreamer0.8-plugins (universe).

Actually I first encountered this problem 2 weeks ago. I didn't know what exactly is the reason but I found the sound recording function failed after I've installed many things to the laptop. _Gnome's sound recorder and Skype could not get anything from the mic_. It is very strange since I could configure the volume of the mic in "volume control" that I cound hear voice of mic input from the speaker. _The input was definatly working. It was very strange that speaker could get the input while other program could not -- no sound recording program get them_.

I then reinstalled my whole OS to see what is the actual problem.

I cleanly installed ubuntu yesterday. Then I installed the stuff one by one. Before any installation steps, I tested if the gnome sound recorder to see if sound recording work or not. At first, the recording was working normally. I did these one by one:
[LIST]I enabled the universe repository[/LIST]
[LIST]I dist-upgrade[/LIST]
[LIST]I reboot to run the upgraded kernel[/LIST]
[LIST]I install SCIM[/LIST]
Things are still fine.

I then installed gstreamer0.8-plugins (universe). And _just after that, the sound record program get nothing from mic_ just like my last installation.

Is this a bug or something? What should I do to undo this? What should I do to fix this problem? Please help. Thanks.

---

